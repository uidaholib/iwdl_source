get the metadata first line *optional

set array of metadata fields desired
get length of array 
for loop iterate over that length 
access the metadata element by i 

or if we know the correct index numbers, 
iterate over the set of numbers 


gen plug that takes csv and creates md stubs with elements as front matter

{% assign fields = "title,creator,collection,location,lat-long,subject,description,date digital,date-original,date,format,digitization-specifications,iwrri-number,resource-identifier,rights-management,publisher,contributors,type,contributing-institution,metadata-cataloger,series,reference-url,cdm-number" | split: ',' %}

make pages grouping based on controlled fields, collection, series 
indexes by iwrri-number 