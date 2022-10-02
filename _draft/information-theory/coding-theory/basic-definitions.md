---
layout: page
title: Definiciones básicas
menu: coding-theory
index: 2
comments: true
mathjax: true
developing: true
---

## Alfabeto y código

Definición
: Un alfabeto es un conjunto de signos que son usados para construir mensajes.
Si un alfabeto consta únicamente de los signos 0 y 1, se denomina binario. En caso de
que se usen tres signos, se dice ternario. En general, si se usan q signos, se habla de
alfabeto q-ario.
{: .d}

Definición
: Sea A un alfabeto y consideremos el conjunto An , con n ≥ 1. Un código C de longitud n es un subconjunto no vacı́o del conjunto An .
Las n-tuplas que constituyen un código C ⊆ An se denominan palabras código.
{: .d}

Ejemplo
: Sea A = {0, 1} y consideremos la repetición de cada signo exactamente tres veces.
Entonces el código viene dado por:
C = {(0, 0, 0), (1, 1, 1)}
{: .e}

Ejemplo
: Sea A = {0, 1} y consideremos el código de paridad de longitud 4. Entonces el código viene dado por
C = {(0, 0, 0, 0), (0, 0, 1, 1), (0, 1, 0, 1), (0, 1, 1, 0), (1, 0, 0, 1), (1, 0, 1, 0),
(1, 1, 0, 0), (1, 1, 1, 1)}
{: .e}

Ejemplo
: Sea C el código Hamming [7, 4] definido por la matriz

1 0 0 0 0 1
0 1 0 0 1 0
G=
0 0 1 0 1 1
0 0 0 1 1 1

1
1

0
1
Entonces
C = {(0, 0, 0, 0, 0, 0, 0), (0, 0, 0, 1, 1, 1, 1), (0, 0, 1, 0, 1, 1, 0), (0, 0, 1, 1, 0, 0, 1),
(0, 1, 0, 0, 1, 0, 1), (0, 1, 0, 1, 0, 1, 0), (0, 1, 1, 0, 0, 1, 1), (0, 1, 1, 1, 1, 0, 0),
(1, 0, 0, 0, 0, 1, 1), (1, 0, 0, 1, 1, 0, 0), (1, 0, 1, 0, 1, 0, 1), (1, 0, 1, 1, 0, 1, 0),
(1, 1, 0, 0, 1, 1, 0), (1, 1, 0, 1, 0, 0, 1), (1, 1, 1, 0, 0, 0, 0), (1, 1, 1, 1, 1, 1, 1)}
{: .e}

## Distancia Hamming

Definición
: Sea A un alfabeto y sean u, v ∈ An. La distancia Hamming d(u, v ) es el número de
posiciones en las que se diferencian las palabras u y v.
{: .d}

Ejemplo
: Sea C es código Hamming [7, 4] y sean u = (0, 0, 0, 0, 0, 0, 0), v = (0, 0, 1, 0, 1, 1, 0)
y w = (1, 1, 1, 1, 1, 1, 1).
Entonces d(u, v ) = 3, d(u, w) = 7 y d(v , w) = 4.
{: .e}

## Distancia Hamming

Definición
: Sea A un alfabeto y sean u, v ∈ An . La distancia Hamming d(u, v ) es el número de
posiciones en las que se diferencian las palabras u y v.
{: .d}

Ejemplo
: Sea C es código Hamming [7, 4] y sean u = (0, 0, 0, 0, 0, 0, 0), v = (0, 0, 1, 0, 1, 1, 0)
y w = (1, 1, 1, 1, 1, 1, 1).
Entonces d(u, v ) = 3, d(u, w) = 7 y d(v , w) = 4.
{: .e}

Teorema
: La distancia Hamming \\(d\\) es una métrica, es decir, satisface las siguientes propiedades:
1. \\(d(u, v ) ≥ 0, ∀u, v y d(u, v ) = 0 si y solo si \\(u=v.\\)
2. \\(d(u, v ) = d(v , u), ∀u, v .\\)
3. \\(d(u, v ) ≤ d(u, w) + d(w, v ), ∀u, v , w.\\)
{: .t}

## (a) d(u, v ) ≥ 0, ∀u, v por definición. Por otro lado, d(u, v ) = 0 es equivalente a decir
a que u y v no difieren en ninguna posición, es decir, u = v .
(b) d(u, v ) = d(v , u) es obvio por definición.
(c) Simplemente hemos de tener en cuenta que si u y v difieren en una posición en
concreto, entonces, o bien u y w difieren en dicha posición, o w y v difieren dicha
posición, o ambas afirmaciones. De este modo, el número de posiciones en las que
difieren u y v siempre es menor o igual que la suma de las posiciones en las que
difieren u y w y w y v.

## (a) d(u, v ) ≥ 0, ∀u, v por definición. Por otro lado, d(u, v ) = 0 es equivalente a decir
a que u y v no difieren en ninguna posición, es decir, u = v .
(b) d(u, v ) = d(v , u) es obvio por definición.
(c) Simplemente hemos de tener en cuenta que si u y v difieren en una posición en
concreto, entonces, o bien u y w difieren en dicha posición, o w y v difieren dicha
posición, o ambas afirmaciones. De este modo, el número de posiciones en las que
difieren u y v siempre es menor o igual que la suma de las posiciones en las que
difieren u y w y w y v .

## Distancia mı́nima

Definición
: Sea C un código. La distancia mínima de C, d(C), es el mı́nimo del conjunto
{d(u, v ) : u, v ∈ C, u 6= v }
Ejemplo
: (a) La distancia mı́nima del código de repetición {(0, 0, 0, 0), (1, 1, 1, 1)} es 4.
(b) La distancia mı́nima del código de paridad de longitud 4 es 2.
(c) La distancia mı́nima del código Hamming [7, 4] es 3.

## Detección y corrección

Al transmitir una palabra código, esta puede sufrir errores en el canal y, por tanto difiere de lo que se recibe. Estos errores se corrigen encontrando la palabra código
que se encuentra a menor distancia Hamming.

Definición
: Un código C es capaz de detectar hasta k errores si el hecho de cambiar hasta k
posiciones de una palabra código de C no la transforma en otra palabra código.
{: .d}

Definición
: Un código C se dice que es capaz de corregir hasta t errores si dada una palabra
código c ∈ C y se cambian t posiciones de la misma, obteniendo c 0 , entonces la
palabra código más próxima a c 0 sigue siendo c.
{: .d}

## Distancia mı́nima, detección y corrección

Teorema
: Sea C un código C y sea d(c) su distancia mı́nima. Entonces C es capaz de detectar
hasta k errores si d(C) ≥ k + 1. Del mismo modo, C es capaz de corregir hasta t
errores si d(C) ≥ 2t + 1.
{: .t}

## Supongamos que d(C) ≥ k + 1. Si en una palabra código c ∈ C, se cambian k o

menos posiciones, y se obtiene c 0 , entonces, por la definición de distancia mı́nima de
un código, c 0 ∈
/ C.
Supongamos ahora que d(C) ≥ 2t + 1. Si dada una palabra c ∈ C, se cambian a lo
sumo t posiciones, obteniéndose c 0 , entonces d(c, c 0 ) ≤ t. Sea ahora c1 ∈ C.
Veamos que d(c1 , c 0 ) ≥ t + 1.
Supongamos, por el contrario, que d(c1 , c 0 ) < t + 1, es decir, d(c1 , c 0 ) ≤ t. Entonces:
2t + 1 ≤ d(C) ≤ d(c, c1 ) ≤ d(c, c 0 ) + d(c 0 , c1 ) ≤ t + t = 2t
Lo que constituye una contradicción y, ası́, la palabra código más próxima a c 0 es c, es
decir, C es capaz de corregir hasta t errores.

## Notación general sobre códigos

Definición
: Sea A un alfabeto, y C ⊆ An un código con M palabras código y tal que d(C) = d.
Entonces nos referiremos a C como un (n, M, d)-código.
{: .d}

Ejemplo
: (a) El código de repetición C = {(0, 0, 0, 0), (1, 1, 1, 1) es un (4, 2, 4)-código.
(b) El código de paridad de longitud 4 es un (4, 8, 2)-código.
(c) El código Hamming [7, 4] es un (7, 16, 3)-código.
{: .e}

## Tasa de información

Definición
: Sea C un (n, M, d)-código q-ario. La tasa de información R se define como
R=
logq M
n
{: .d}

Ejemplo
: (a) Para el código de repetición C = {(0, 0, 0, 0), (1, 1, 1, 1), R = 1/4.
(b) Para el código de paridad de longitud 4, R = 3/4.
(c) Para el código Hamming [7, 4], R = 4/7.
{: .e}

## Códigos equivalentes

Definición
: Sea A un alfabeto y sean los códigos C, C 0 ⊆ An . Se dice que C y C 0 son
equivalentes si cualquier palabra código de C 0 puede obtenerse a partir de una
palabra código de C mediante una serie de operaciones como:
Aplicar una permutación f ∈ Sn de las posiciones del código.
Aplicar una permutación f ∈ SA de los signos que aparecen en determinadas
posiciones fijas de las palabras del código.
{: .d}

Ejemplo
: Sea el código
C = {(0, 0, 0, 0), (0, 0, 1, 1), (0, 1, 0, 1), (0, 1, 1, 0), (1, 0, 0, 1), (1, 0, 1, 0),
(1, 1, 0, 0), (1, 1, 1, 1)} y consideremos la permutación (1 2 3 4) ∈ S4 .
Entonces, el código
C 0 = {(0, 0, 0, 0), (1, 0, 0, 1), (1, 0, 1, 0), (0, 0, 1, 1), (1, 1, 0, 0), (0, 1, 0, 1),
(0, 1, 1, 0), (1, 1, 1, 1)} es equivalente al código C.
{: .e}

Ejemplo
: Sea el código C = {(0, 1, 2), (1, 2, 0), (1, 0, 2)} y sea la permutación de f de SA dada
por f (0) = 1, f (1) = 2, f (2) = 1. Entonces, aplicando f a la segunda posición de cada
palabra del código se obtiene el código equivalente C 0 = {(0, 2, 2), (1, 1, 0), (1, 1, 2).