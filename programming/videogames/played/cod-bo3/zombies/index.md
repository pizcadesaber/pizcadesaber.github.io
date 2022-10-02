---
layout: page
title: Zombis
menu: cod-bo3
permalink: /programming/videogames/played/cod-bo3/zombies
---

Información sobre el modo zombies.

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'cod-bo3-zombies' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>