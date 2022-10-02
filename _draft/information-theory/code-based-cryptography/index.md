---
layout: page
title: Criptografía basada en códigos # Cryptographic attacks
menu: information-theory
index: 8
#permalink: /math/information-theory/
---

<ul>
    {% assign pages = site.pages | sort: "index" %}
    {% for page in pages %}
        {% if page.menu == 'code-based-cryptography' %}
            <li><a href="{{ page.url }}">{{ page.title }}.</a> {{page.description}}</li>
        {% endif %}
    {% endfor %}
</ul>