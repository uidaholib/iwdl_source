---
layout: table
title: Browse Documents
permalink: /browse/
---
{% assign items = site.data[site.metadata] %}

## Browse IWDL

This table provides sorting and basic search of the archive contents. 
Click on the "Read" link to see the full document.

<div class="table-responsive-md">
<table id="item-table" class="table table-striped">
    <thead>
        <tr>
            <th scope="col">Title</th>
            <th scope="col">Date</th>
            <th scope="col">Subjects</th>
            <th scope="col">Description</th>
        </tr>
    </thead>
    <tbody>
{% for item in items %}
        <tr>
            <td scope="row"><a href="{{ "/docs/" | absolute_url | append: item.resource-identifier | append: ".html" }}">{{ item.title }}</a></td>
            <td>{{ item.date }}</td>
            <td>{{ item.subject }}</td>
            <td>{{ item.description | truncatewords: 15 }}</td>
        </tr>
{% endfor %}
    </tbody>
</table>
</div>
