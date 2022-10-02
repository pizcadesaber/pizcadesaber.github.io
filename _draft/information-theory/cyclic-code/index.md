---
layout: page
title: Código cíclico # Elliptic-curve cryptography
index: 6
menu: information-theory
#permalink: /math/information-theory/
---

<ul>
    {% assign pages = site.pages | sort: "index" %}
    {% for page in pages %}
        {% if page.menu == 'cyclic-code' %}
            <li><a href="{{ page.url }}">{{ page.title }}.</a> {{page.description}}</li>
        {% endif %}
    {% endfor %}
</ul>