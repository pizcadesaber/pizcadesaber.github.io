---
layout: page
title: Lenguajes de programación
menu: programming
---

Un **lenguaje de programación** es un lenguaje formal que permite escribir una serie de instrucciones para controlar el comportamiento de un sistema informático.

Conocer un lenguaje de programación es fundamental para crear cualquier programa. Hay programas que pueden facilitar al usuario la tarea de escribir código mediante un editor gráfico. Esta funcionalidad se encuentra sobre todo para desarrollar interfaces gráficas de usuario. Sin embargo, para sacarle todo el rendimiento, necesitarás poder escribir tú mismo el código.

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'programming-language' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>