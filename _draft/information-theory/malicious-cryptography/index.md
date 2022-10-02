---
layout: page
title: Criptografía maliciosa # Malicious cryptography
menu: information-theory
index: 4
#permalink: /math/information-theory/
---

<ul>
    {% assign pages = site.pages | sort: "index" %}
    {% for page in pages %}
        {% if page.menu == 'malicious-cryptography' %}
            <li><a href="{{ page.url }}">{{ page.title }}.</a> {{page.description}}</li>
        {% endif %}
    {% endfor %}
</ul>