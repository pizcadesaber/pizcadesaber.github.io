---
layout: page
title: Universal Windows Platform
menu: programming
---

**Universal Windows Platform**, abreviado como  **UWP**, nos aporta un medio para crear aplicaciones de escritorio para Windows usando Visual Studio. Principalmente, se suele utilizar para programar alguna de las siguientes opciones:
- [XAML con C#.](https://docs.microsoft.com/es-es/windows/uwp/get-started/create-a-hello-world-app-xaml-universal)
- [XAML con C++.](https://docs.microsoft.com/es-es/windows/uwp/get-started/create-a-basic-windows-10-app-in-cppwinrt)

<ul>
    {% for p in site.pages %}
        {% if p.menu == 'uwp' %}
            <li><a href="{{ p.url }}">{{ p.title }}.</a> {{p.description}}</li>
        {% endif %}
    {% endfor %}
</ul>