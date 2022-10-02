---
layout: page
title: Introducción # Introduction
menu: cryptography
index: 1
comments: true
mathjax: true
---

## Criptologı́a

La **Criptologı́a** es un área de la ciencia que contiene muchas disciplinas aunque las
tres básicas son:
1. **Criptografı́a:** disciplina matemática encargada del diseño de cifradores y
protocolos.
2. **Criptoanálisis:** disciplina que trata el análisis y búsqueda de métodos para romper
cifradores y/o protocolos criptográficos.
3. **Esteganografı́a:** disciplina que trata de encontrar métodos para ocultar
información.

## Criptografı́a

La **Criptografía** es una disciplina matemática cuyo interés se centra en distintos
aspectos de la Teoría de la Información relacionados con la seguridad de esta. Sus
objetivos principales son:
1. **Confidencialidad.** La información sea solo accesible por partes
autorizadas a ello.
2. **Autentificacón.** Hace posible determinar sin
género de duda la fuente que crea una información determinada.
3. **Integridad.** Hace posible comprobar que la información a la
que se accede en un momento determinado no ha sido alterada desde el
momento de su creación.
4. **No repudio.** La información creadora de una información no pueda
posteriormente negar la autoría de la misma.

## Escítala

La escítala usada por los lacedemonios o espartanos en el siglo V antes de Cristo, es
un método constituido por un basto, alrededor del que se enrollaba una cinta de cuero
sobre la que se escribía. Tras desenrollar la cinta, el mensaje podía leerse únicamente
volviendo a ser enrollada sobre un bastón de igual grosor.

<!--Figure: escítala-->

## Cifrado de César

Usado por Julio César en el siglo I antes de Cristo, consiste en el desplazamiento del
alfabeto un número determinado de caracteres. Matemáticamente puede
representarse como la función \\(f:\\mathbb{Z}\_{27}\\to\\mathbb{Z}\_{27},\\) dada por
*\\[ f(x)\\equiv\_{27}x+k, \\]*{: .eq}
donde \\(k\\in\\mathbb{Z}\_{27}.\\)

El criptoanálisis es muy básico, pues basta conocer como se cifra una letra. Esto
puede conocerse mediante el análisis de frecuencias de los caracteres que aparecen
en el texto cifrado.

Una extensión natural es el conocido como cifrado afı́n: \\(f(x)\\equiv_{27}ax+b,\\) con
\\(a,b\\in\\mathbb{Z}\_{27}\\) y \\(\\operatorname{mcd}(a,27)=1,\\) igualmente muy fácil de criptoanalizar.

## Cifrado de Vigenere

**Blaise de Vigenere**, en el siglo XVI propone una extensión del cifrado de César,
representado matemáticamente por la función \\(f:\\mathbb{Z}\_{27}^n\\to\\mathbb{Z}\_{27}^n\\) definida como
    *\\[ f(x)\\equiv\_{27}x+k, \\]*{: .eq}
donde \\(k\\in\\mathbb{Z}_{27}^n.\\)

El criptoanálisis se lleva a cabo como en el caso del de César.

## Principio de Kerckhoff

**Auguste Kerckhoff**, criptógrafo holandés establece sus principios básicos para un
sistema criptográfico en su artı́culo de 1883 “La cryptographie militaire”. Entre ellos
destaca el conocido actualmente como Principio de Kerckhoff.

Principio de Kerckhoff
: La seguridad de un sistema de clave secreta debe recaer únicamente en el secreto de
dicha clave.
{: .t}

## Cifrador de Vernam
En 1917, Gilbert S. Vernam, ingeniero del Massachusset Institute of Technology,
propone su cifrador, conocido como **cifrador de Vernam** o **cifrador de clave de un solo uso** (one time pad):
*\\[C:=f(M)=f(M\_1M\_2\\cdots M\_n)=C\_1C\_2\\cdots C\_n,\\]*{: .eq}
*\\[M:=f(C)=f(C\_1C\_2\\cdots C\_n)=M\_1M\_2\\cdots M\_n,\\]*{: .eq}
donde \\(C\_i\\equiv_2M\_i+k\_i\\) y \\(M\_i\\equiv_2C\_i+k\_i,\\) para todo \\(i\\in\\{1,\\ldots,n\\}.\\)

Aquí, la clave es una cadena de ceros y unos aleatorios tan larga al menos como el
mensaje y de un solo uso. El cifrado de Vernam es demostrablemente seguro, pero
poco útil debido a la naturaleza de la clave.

<!--Figure: George S. Vernam-->

## Cifrado de Hill

En 1929, el matemático Lester S. Hill propone una aplicación algebraica para su uso
en Criptografı́a: \\(f:\\mathbb{Z}\_{27}\\to\\mathbb{Z}\_{27}\\), dada por
    *\\[ f(m)=Am+k, \\]*{: .eq}
donde \\(A\\) es una matriz invertible con entradas en \\(\\mathbb{Z}\_{27}\\) y \\(k\\in\\mathbb{Z}\_{27}^n.\\)

Conocidos suficientes pares de la forma \\((m,f(m))\\), el uso de Álgebra Lineal básica
permite el criptoanálisis del sistema.

## Enigma

Durante la II Guerra Mundial aparecen muchos sistemas, el más famoso de los cuales
es Enigma:
1. Enigma
1. Marian Rejewski
1. Alan Turing
1. Colossus

## Claude Shannon

En 1949, el matemático Claude E. Shannon publica su artı́culo <<Communication
Theory of Secrecy Systems>>, donde demuestra la existencia de criptosistemas
demostrablemente seguros.

<!--Figure: Claude E. Shannon-->

## Problema del intercambio de clave

A pesar del amplio uso de la Criptografía, un problema seguía abierto y sin solución
hasta los años 70: ¿Es posible el intercambio de un secreto de forma confidencial a través de un
canal inseguro?