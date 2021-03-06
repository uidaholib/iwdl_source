## Problems

PDF problems

iwdl-1897_russell_a_reconnoissance_in_southeastern_wa	*missing, bad digitization
iwdl-1965_ross_contributions_to_geohydrology	*missing

iwdl-gladwell2_1979	
iwdl-gladwell6_1979.pdf	
iwdl-gladwell7_1979	
iwdl-gladwell8_1979.pdf	
iwdl-gladwell9_1979	
iwdl-gladwell10_1979

no thumbs, 
https://www.lib.uidaho.edu/digital/iwdl/images/thumb/iwdl-1897_russell_a_reconnoissance_in_southeastern_wa.jpg
https://www.lib.uidaho.edu/digital/iwdl/images/thumb/iwdl-1965_ross_contributions_to_geohydrology.jpg
https://www.lib.uidaho.edu/digital/iwdl/images/thumb/iwdl-gladwell2_1979.jpg
https://www.lib.uidaho.edu/digital/iwdl/images/thumb/iwdl-gladwell6_1979.jpg
https://www.lib.uidaho.edu/digital/iwdl/images/thumb/iwdl-gladwell7_1979.jpg
https://www.lib.uidaho.edu/digital/iwdl/images/thumb/iwdl-gladwell10_1979.jpg
https://www.lib.uidaho.edu/digital/iwdl/images/thumb/iwdl-gladwell8_1979.jpg
https://www.lib.uidaho.edu/digital/iwdl/images/thumb/iwdl-gladwell9_1979.jpg

## notes 

check item 201101supp, is xls 
cdm 277, iwdl-sonneville_1974 huge file, won't download.

iwdl/objects/ pdfs
iwdl/images/sm thumbs

- active nav, underline, different color, red?

- set up datatables load data
- datatables api 

## extract full text

Xpdf

pdftotext
-nopgbrk  don't create page break characters

`for f in *.pdf; do pdftotext -nopgbrk "$f"; done`

## Thumbs

CONTENTdm get thumb utility:
`/utils/getthumbnail/collection/alias/id/pointer`

run jekyll to create thumbnail-fetch.txt in utilities. 
use wget to harvest thumbs, `wget -i "thumbnail-fetch.txt"`.
if thumbs have no extension, add using `for f in *; do mv "$f" "$f.jpg"; done`.

These thumbs are very small...

## pdfs

CONTENTdm getfile utility:
`/utils/getfile/collection/<alias>/id/<pointer>/filename/<name>`

example, `http://digital.lib.uidaho.edu/utils/getfile/collection/idahowater/id/784/filename/784.pdf`

Note: `filename/<name>` is optional, and name can be arbitrarily set as long as the extension is correct.

run jekyll to create `pdf-fetch.txt` in utilities. 
use wget to harvest pdfs, `wget --wait=3 --random-wait -i "pdf-fetch.txt"`.
this downloads all PDFs in the metadata, setting the file name to the "resource-identifier".

## Item images 

IWDL images for item pages:
- 800px height 
- file name is based on "resource-identifier"

Create images from PDFs using ImageMagick ([setup instructions](https://evanwill.github.io/_drafts/notes/imagemagick.html)).
Use command `for f in *.pdf; do magick -density 500 "$f"[0] -resize x800 -flatten "sm/${f%.pdf}.jpg"; done`

## CDM Page flip view

`<iframe src="https://digital.lib.uidaho.edu/cdm/pageflip/collection/idahowater/id/{{ page.cdm-number }}/type/singleitem/pftype/pdf"></iframe>`

## metadata handling

The data file `metadata-fields.csv` contains information for populating document pages and machine readable markup. 
The "field" column matches the columns used in the collection metadata file. 
The fields will be displayed in the given order.
If the field should be displayed visually, give it a name in "display-name" (blanks will not be displayed).
If the field should be visually highlighted, add true to "featured" column (false will be displayed only on an additional click).
For machine markup, include a schema map value.

create csv mapping field to display name

## breadcrumbs

document pages have schema.org markup for breadcrumbs, used by google to give context,

https://developers.google.com/search/docs/data-types/breadcrumb

## notes

gen plug that takes csv and creates md stubs with elements as front matter

{% assign fields = "title,creator,date-original,date,description,location,lat-long,subject,collection,series,iwrri-number,resource-identifier,rights-management,publisher,contributors,contributing-institution,format,type,metadata-cataloger,date-digital,reference-url" | split: ',' %}

make pages grouping based on controlled fields, collection, series 
indexes by iwrri-number 

Csv download option, Data section of about

pdf embed options, https://pdfobject.com/static.html 

show/hide description: 
trucate, full on click hide trucate, show full.
#overflowDiv { white-space: nowrap; text-overflow: ellipsis; overflow: hidden; }
onclick remove hidden, nowrap
