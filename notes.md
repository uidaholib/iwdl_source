
## Thumbs

CONTENTdm get thumb utility:
`/utils/getthumbnail/collection/alias/id/pointer`

run jekyll to create thumbnail-fetch.txt in utilities. 
use wget to harvest thumbs, `wget -i "thumbnail-fetch.txt"`.
if thumbs have no extension, add using `for f in *; do mv "$f" "$f.jpg"; done`.

## pdfs

CONTENTdm getfile utility:
`/utils/getfile/collection/alias/id/pointer/filename/name`

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

handle multiple lat-long: 47.49, -116.72; 47.47, -116.58 

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
