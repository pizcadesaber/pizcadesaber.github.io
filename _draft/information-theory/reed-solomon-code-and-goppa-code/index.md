---
layout: page
title: Código de  Reed-Solomon y código de Goppa # Elliptic-curve cryptography
index: 7
menu: information-theory
#permalink: /math/information-theory/
---

<ul>
    {% assign pages = site.pages | sort: "index" %}
    {% for page in pages %}
        {% if page.menu == 'reed-solomon-code-and-goppa-code' %}
            <li><a href="{{ page.url }}">{{ page.title }}.</a> {{page.description}}</li>
        {% endif %}
    {% endfor %}
</ul>