---
layout: page
title: Geometría fractal
menu: math
permalink: /math/fractal-geometry/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'fractal-geometry' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>