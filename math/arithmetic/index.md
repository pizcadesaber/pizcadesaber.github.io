---
layout: page
title: Aritmética # 
menu: math
permalink: /math/arithmetic/
---

<ul>
    {% assign pages = site.pages | sort: "index" %}
    {% for page in pages %}
        {% if page.menu == 'arithmetic' %}
            <li><a href="{{ page.url }}">{{ page.title }}.</a> {{page.description}}</li>
        {% endif %}
    {% endfor %}
</ul>