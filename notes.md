
## Thumbs

CONTENTdm get thumb utility:
`/utils/getthumbnail/collection/alias/id/pointer`

run jekyll to create thumbnail-fetch.txt in utilities. 
use wget to harvest thumbs, `wget -i "thumbnail-fetch.txt"`.
if thumbs have no extension, add using `for f in *; do mv "$f" "$f.jpg"; done`.

## pdfs

CONTENTdm getfile utility:
`/utils/getfile/collection/alias/id/pointer/filename/name`

## CDM Pageview

`<iframe src="https://digital.lib.uidaho.edu/cdm/pageflip/collection/idahowater/id/{{ page.cdm-number }}/type/singleitem/pftype/pdf"></iframe>`

## notes

create csv mapping field to display name

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
