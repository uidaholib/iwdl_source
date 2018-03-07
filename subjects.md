---
layout: page
title: Subjects
permalink: /subjects/
---
{%- comment -%} find all unique subjects used in the metadata {%- endcomment -%}

{% assign items = site.data.iwdl %}
{%- assign subjects = "" | split: "," -%}
{%- for item in items -%}
	{%- assign isubs = item.subject | split: ";" -%}
    {%- for s in isubs -%}
        {%- assign ss = s | strip | downcase -%}
        {%- assign subjects = subjects | push: ss -%}
    {%- endfor -%}
{% endfor %}
{%- assign uniqueSubjects = subjects | uniq | sort -%}
{%- for unique in uniqueSubjects -%}
    {%- assign count = 0 -%}
    {%- for c in subjects -%}
        {%- if c == unique -%}
            {%- assign count = count | plus: 1 -%}
        {%- endif -%}
    {%- endfor -%}
- [{{ unique  | capitalize }}, {{ count }}](https://digital.lib.uidaho.edu/cdm/search/collection/idahowater/searchterm/{{ unique | url_escape }}/field/subjed/mode/exact/conn/and/cosuppress/)
{% endfor %}

<!--
<div class="box5" id="text4" name="text" style="display:block;width:80%;">
<div id="htmltagcloud" style="margin: 0px 30px 30px; background: none repeat scroll 0% 0% rgb(64, 82, 79); padding: 4px;">

<span id="0" class="wrd tagcloud1"><a target="_blank" href="https://digital.lib.uidaho.edu/cdm4/results.php?CISOOP1=exact&amp;CISOBOX1=ada county&amp;CISOFIELD1=subjed&amp;CISOOP2=exact&amp;CISOBOX2=&amp;CISOFIELD2=creato&amp;CISOOP3=any&amp;CISOBOX3=&amp;CISOFIELD3=descri&amp;CISOOP4=none&amp;CISOBOX4=&amp;CISOFIELD4=CISOSEARCHALL&amp;CISOROOT=/idahowater&amp;t=s">{{ unique | capitalize }}</a></span>

<div style="clear: both"></div>   	  
</div>

</div>
-->
