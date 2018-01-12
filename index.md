---
layout: page
title: Home
---
{% assign items = site.data.iwdl %}

<link href="{{ site.baseurl }}/css/vanilla-dataTables.min.css" rel="stylesheet" type="text/css">

## Browse IWDL

This table provides sorting and basic search of the archive contents. 
Click on the "Read" link to see the full document.

<style>
    #columns {
    display: flex;
    align-items: center;
    justify-content: space-around;
    flex-grow: 1;
    margin: 0;
}
</style>
<table id="doc-table" class="display">
    <thead>
        <tr>
            <th>Title</th>
            <th>Date</th>
            <th>Subjects</th>
            <th>Description</th>
        </tr>
    </thead>
    <tbody>
{% for item in items %}        
        <tr>
            <td>{{ item.title }}</td>
            <td>{{ item.date }}</td>
            <td>{{ item.subject }}</td>
            <td>{{ item.description | truncatewords: 40 }}... <a href="{{ site.baseurl }}/docs/{{ item.resource-identifier | downcase }}.html">Read</a></td>
        </tr>
{% endfor %}
    </tbody>
</table>

<script src="{{ site.baseurl }}/js/vanilla-dataTables.min.js" type="text/javascript"></script>

<script>
    var dataTable = new DataTable("#doc-table", {
        perPage: 20,
        fixedColumns: true,
        layout: {
            top: "{info}{search}",
            bottom: "{select}{pager}"
        },
        columns: [
            { select: 1, sort: "asc" }
        ]
    });
</script>
