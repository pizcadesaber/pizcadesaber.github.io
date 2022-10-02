---
layout: page
title: Dibujo digital
menu: art
permalink: /art/digital drawing/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'digital-drawing' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>