---
layout: page
title: Arte
menu: main
index: 1
permalink: /art/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'art' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>