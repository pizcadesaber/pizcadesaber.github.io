---
layout: page
title: Programación
menu: main
index: 3
permalink: /programming/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'programming' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>