---
layout: page
title: Godot
menu: videogames
permalink: /programming/videogames/godot/
---

Godot es un motor de videojuegos. Puedes usarlo para crear tus propios videojuegos 2D o 3D.

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'godot' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>