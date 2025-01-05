---
layout: misc
title: "Divers"
author: "Sylvain White"
---
<br/>
{% for p in site.pages %}
    {% if p.categories contains "divers" %}
        {% assign file = p.name | replace: ".md", ".html" %}
- [{{p.title}}]({{ site.github.url }}/pages/{{ file }})
    {% endif %}
{% endfor %}
<br/>
