---
layout: page
title: Android Studio
menu: programming
permalink: /programming/android/
---

La plataforma que utilizo para desarrollar aplicaciones Android es **Android Studio**. Para programar tiene las siguientes opciones:
- Java y XML.
- Kotlin y XML.

En ambos casos, XML se usa para definir la interfaz de usuario, y Java o Kotlin para programar las acciones.

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'android' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>