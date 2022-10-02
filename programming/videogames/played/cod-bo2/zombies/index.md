---
layout: page
title: Zombis
menu: cod-bo2
permalink: /programming/videogames/played/cod-bo2/zombies
---

Información sobre el modo zombies.

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'cod-bo2-zombies' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>

- *Hueso:* 1-10
- *Hueso avanzado:* 11-20
- *Calavera:* 30-60
- *Calavera con cuchillo:* 70-200
- *Calavera con escopetas:* 200+