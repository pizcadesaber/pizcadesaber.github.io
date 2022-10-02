---
layout: page
title: "Call of Duty: Black Ops 3"
menu: played
permalink: /programming/videogames/played/cod-bo3
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'cod-bo3' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>