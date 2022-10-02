---
layout: page
title: Motor de juegos
menu: videogames
permalink: /programming/videogames/game-engine/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'game-engine' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>