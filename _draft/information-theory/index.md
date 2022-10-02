---
layout: page
title: Teoría de la información
menu: math
permalink: /math/information-theory/
---

<ul>
    {% assign pages = site.pages | sort: "index" %}
    {% for page in pages %}
        {% if page.menu == 'information-theory' %}
            <li><a href="{{ page.url }}">{{ page.title }}.</a> {{page.description}}</li>
        {% endif %}
    {% endfor %}
</ul>