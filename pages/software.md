---
layout: misc
title: "Software"
author: "Sylvain White"
categories: mainCategory
---
<br/>

## Main categories

{% for p in site.pages %}
    {% if p.categories contains "mainCategory" %}
        {% assign file = p.name | replace: ".md", ".html" %}
- [{{p.title}}]({{ site.github.url }}/pages/{{ file }})
    {% endif %}
{% endfor %}
<br/>

## Sub categories

{% for p in site.pages %}
    {% if p.categories contains "subCategory" %}
        {% assign file = p.name | replace: ".md", ".html" %}
        {% assign d = file | slice: 0, 10 %}
- {{d}} - [{{p.title}}]({{ site.github.url }}/pages/{{ file }})
    {% endif %}
{% endfor %}

<br/>
