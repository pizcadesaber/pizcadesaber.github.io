---
layout: page
title: Modelado 3D
menu: art
permalink: /art/3d-modeling/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == '3d-modeling' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>

Mi programa favorito para modelar en 3D es [Blender](https://www.blender.org) (open source).