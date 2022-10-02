---
layout: page
title: Videojuegos
menu: programming
permalink: /programming/videogames/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'videogames' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>