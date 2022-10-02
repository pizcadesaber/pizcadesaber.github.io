---
layout: page
title: Teoría de códigos # Coding theory
menu: information-theory
index: 5
permalink: /math/information-theory/coding-theory/
---

<ul>
    {% assign pages = site.pages | sort: "index" %}
    {% for page in pages %}
        {% if page.menu == 'coding-theory' %}
            <li><a href="{{ page.url }}">{{ page.title }}.</a> {{page.description}}</li>
        {% endif %}
    {% endfor %}
</ul>