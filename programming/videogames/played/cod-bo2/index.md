---
layout: page
title: "Call of Duty: Black Ops 2"
menu: played
permalink: /programming/videogames/played/cod-bo2
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'cod-bo2' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>