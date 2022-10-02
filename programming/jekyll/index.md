---
layout: page
title: Jekyll
menu: programming
permalink: /programming/jekyll/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'jekyll' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>