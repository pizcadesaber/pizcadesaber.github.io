---
layout: page
title: Introdución
menu: game-engine
---

A continuación, se da una orientación para empezar:
- **Aprende álgebra lineal.** Es necesario aprender conceptos sobre vectores y matrices como el producto escalar, producto vectorial y transformaciones.
- **Aprende C++ (o cualquier otro lenguaje de programación).** Hay que saber como programar. Se recomienda aprender C++. Será necesario saber sobre clases, métodos, herencia, polimorfismo y encapsulamiento.
- **Desarrolla un motor de cálculo vectorial.** Usa tu conocimiento sobre vectores, matrices y programación para desarrollar un motor de cálculo.
- **Aprende computación gráfica.** Familiarízate con la computación gráfica, sobre todo con la tubería de renderizado (Rendering Pipeline) y sombreadores. Evita el uso de OpenGL al comienzo. Cuesta entender su API si tienes poco conocimiento sobre los conceptos de computación gráfica.
- **Aprende OpenGL y haz muchos proyectos.** Una vez que te sientas cómodo con los conceptos de computación gráfica, aprende sobre la API de OpenGL y sus sombreadores. Haz tantos proyectos como puedas. Aprende tanto renderizar personajes como rotar y trasladar personajes. También, debes saber cómo colocar texturas y cómo funciona las luces. Se recomienda hacer tantos proyectos como se pueda para esta parte.
- **Aprende patrones de diseño.** Es necesario aprender la arquitectura de las API. Un motor de juego es simplemente una API, un entorno de trabajo, que se encarga de todo el renderizado, física y operaciones matemáticas. Es fundamental desarrollar una API que es modular, flexible, sostenible y adaptable.
> Para el desarrollo, necesitaras aprender patrones de diseño (Design Patterns). La mayoría de patrones comunes de diseño son Singleton, Observer, Strategy, Compositer, Factory entre otros.
- **Desarrolla un motor de renderizado.** Combina tu conocimiento sobre álgebra lineal, computación gráfica, OpenGL y patrones de diseño para desarrollar un motor de renderizado.
- **Revisa las leyes de movimiento de Newton.** La parte complicada del motor es el motor de física. Para desarrollarlo, es necesario conocer primero las leyes de movimiento de Newton y cómo se implementan, usando algoritmos como los métodos de Runge-Kutta.
- **Aprende algoritmos de geometría computacional.** Un motor de juego no puede serlo sin detección de colisiones. Para desarrollar un sistema de detección de colisiones, es necesario aprender algoritmos de geometría computacional tales como GJK, BVH y Sutherland-Hodgman. Estos algoritmos son usados para detectar cuándo y dónde ocurre una colisión, y qué objetos son más propensos a chocar.
- **Desarrolla un motor de física.** Una vez conocidos los algoritmos mencionados anteriormente, deberías ser capaz de desarrollar un motor de física con un sistema de detección de colisiones.
- **Desarrolla un juego. Prueba y error.** Llegado a este punto, tiene un motor de juego. Desarrolla tantos juegos como puedas para probar su funcionamiento y corregir errores que aparezcan. También, puedes implementar nuevas funciones.

Algunos libros útiles para empezar son los siguientes:
- Fletcher Dunn, Ian Parberry. *3D Math Primer for Graphics and Game Development.*
- Graham Sellers, Richard S. Wright, Nicholas Haemel. *OpenGL Superbible: Comprehensive Tutorial and Reference.*
- Mike Bailey, Steve Cunningham. *Graphics Shaders: Theory and Practice, Second Edition.*
- David M Bourg, Bryan Bywalec. *Physics for Game Developers: Science, math, and code for realistic effects.*
- Ian Millington. *Game Physics Engine Development: How to Build a Robust Commercial-Grade Physics Engine for your Game 2nd Edition.*
- Christer Ericson. *Real-Time Collision Detection.*

El primer libro trata la matemática 3D. Los dos siguientes sobre el motor de renderizado, y los últimos, sobre el motor de física.