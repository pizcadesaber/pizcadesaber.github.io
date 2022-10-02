---
layout: page
title: Jugados
menu: videogames
permalink: /programming/videogames/played/
---

Aquí se reúne una lista de videojuegos a los cuales he jugado y explico algunas cosas sobre ellos.

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'played' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>