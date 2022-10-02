---
layout: page
title: VS Code
menu: programming
categories: program
permalink: /programming/vs-code/
---

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'vs-code' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>