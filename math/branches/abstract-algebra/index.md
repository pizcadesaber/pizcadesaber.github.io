---
layout: page
title: Álgebra abstracta # Abstract algebra
menu: math
permalink: /math/abstract-algebra/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'abstract-algebra' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>