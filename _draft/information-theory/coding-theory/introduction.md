---
layout: page
title: Introducción
menu: coding-theory
index: 1
comments: true
mathjax: true
developing: true
---

## Juego de adivinación

La siguiente tabla se puede utilizar para sorprender a algún amigo. Pide que piense un número y te diga en que columnas aparece. Así, la suma de los números que se encuentran en la primera fila de dichas columnas es el número elegido.

| 1  | 2  | 4  | 8  | 16 |
| 3  | 3  | 5  | 9  | 17 |
| 5  | 6  | 6  | 10 | 18 |
| 7  | 7  | 7  | 11 | 19 |
| 9  | 10 | 12 | 12 | 20 |
| 11 | 11 | 13 | 13 | 21 |
| 13 | 14 | 14 | 14 | 22 |
| 15 | 15 | 15 | 15 | 23 |
| 17 | 18 | 20 | 24 | 24 |
| 19 | 19 | 21 | 25 | 25 |
| 21 | 22 | 22 | 26 | 26 |
| 23 | 23 | 23 | 27 | 27 |
| 25 | 26 | 28 | 28 | 28 |
| 27 | 27 | 29 | 29 | 29 |
| 29 | 30 | 30 | 30 | 30 |
| 31 | 31 | 31 | 31 | 31 |
{: .eq}

Observemos que, por ejemplo, el número 21 se encuentra en las columnas 1, 3 y 5. Sumando los números que hay en la primera fila de cada columna en las que se encuentra 21: \\(1+4+16=21.\\)

## ¿Qué significa comunicarse?

El medio
: El medio o canal a través del que se lleva a cabo la comunicación condiciona los signos o señales que usamos en nuestra comunicación: asignamos unos determinados signos o señales a los mensajes que queremos transmitir de acuerdo al medio a través del cual nos vamos a comunicar. Por ejemplo, asignamos una letra latina, árabe, hebrea, cirílica, etc. a un sonido determinado para hacer uso del medio escrito.
{: .d}

Mensaje en el juego anterior
: Podemos escribir \\(21\\) del siguiente modo:
*\\[21 = 16 + 4 + 1 = 1\\cdot 24 + 0\\cdot 23 + 1\\cdot 22 + 0\\cdot 21 + 1\\cdot 20\\]*{: .eq}
Es decir, \\(10101\\) en binario, o equivalentemente, \\(1\\) para aquellas columnas en las que se encuentre \\(21\\) y \\(0\\) en el resto.
{: .r}

## Errores de comunicación

¿Qué es un error en la comunicación?
: En el ejemplo, la omisión de una de las columnas en las que se encuentra el 21 o indicar que se encuentra en una columna en la que no está realmente conlleva cambiar un 1 por un 0, o viceversa, es decir, el mensaje interpretado, no va a ser 21.
{: .d}

¿A qué se pueden atribuir estos errores?
: Es lo que usualmente conocemos por interferencias y que hacen que el mensaje recibido difiera del emitido.
{: .d}

## Códigos de repetición

Signos y errores
: Supongamos un alfabeto que tiene 4 signos: A,B,C,D, que queremos transmitir uno de ellos y que sabemos que la probabilidad de que se produzca un fallo en la transmisión es de 0,1. De este modo, la probabilidad de interpretar correctamente el mensaje enviado, A, será de 0,9.
{: .d}

¿Qué sucede si transmitimos el signo varias veces?
: Si enviamos AAA y se produce un error, por ejemplo, se recibe AAB, o ABA, lo lógico es interpretar el mensaje formado por la letra que más veces se repite, en este caso AAA. En este caso, la probabilidad de interpretar el mensaje correctamente, sería de (0, 9)3 + 3 · (0, 9)2 · (0, 1) = 0, 972
Sin embargo, si se envía AA y se recibe AC o BA, podemos interpretar el mensaje
como AA, CC, o BB.
{: .d}

Codificación
: Si hacemos la siguiente asignación de signos A → 00, B → 01, C → 10 y D → 11,
entonces los posibles mensajes a transmitir serían:
000000, 010101, 101010, 111111
{: .d}

## Comprobación de la paridad

Codificación
: Supongamos que queremos enviar un mensaje formado por 7 bits. Para detectar que
se produce un error en la transmisisón podemos añadir un octavo bit, 0 o 1, que haga
que el número de unos que aparezcan en el mensaje sea siempre par:
0101101 → 01011010
0001101 → 00011011
{: .d}

Decodificación
: Supongamos que se envía el mensaje 00110101.
Si se recibe 10110101 podemos detectar que se ha producido un error.
Si se recibe 11100101 podemos detectar que se ha producido un error (al menos).
Si se recibe 10010101 no podemos detectar los errores cometidos.
{: .d}

## Paridad bidimensional

Matriz de paridad
Supongamos que queremos enviar 2 bytes de información 0101001101001001 que disponemos en forma de matriz:
0
0
0
1

1
0
1
0

0
1
0
0

1
1
0
1

y añadimos, como en el caso anterior, un bit de comprobación de paridad a cada fila y columna:
0
0
0
1
1

1
0
1
0
0

0
1
0
0
1

1
1
0
1
1

0
0
1
0
1

## Paridad bidimensional

Matriz de paridad
Supongamos que queremos enviar 2 bytes de información 0101001101001001 que
disponemos en forma de matriz:
0
0
0
1

1
0
1
0

0
1
0
0

1
1
0
1

y añadimos, como en el caso anterior, un bit de comprobación de paridad a cada fila y
columna:
0
0
0
1
1

1
0
1
0
0

0
1
0
0
1

1
1
0
1
1

0
0
1
0
1

## Paridad bidimensional

Decodificación
Supongamos que se produce un error en el tercer elemento de la segunda fila:
0
0
0
1
1

1
0
1
0
0

0
0
0
0
1

1
1
0
1
1

0
0
1
0
1

Dado que cambian la paridad de la segunda fila y la tercera columna, podemos determinar que el elemento situado en la posición (2,3) es erróneo.

Si ocurren dos errores, podemos verificar la existencia de los mismos, pero no determinarlos:
0
0
0
1
1

1
1
1
0
0

0
0
0
0
1

1
1
0
1
1

0
0
1
0
1

No cambia la paridad de la segunda fila, pero sí las de las columnas 2 y 3 y, en este caso, existe más de una posibilidad.

## Paridad bidimensional

Decodificación
Supongamos que se produce un error en el tercer elemento de la segunda fila:
0
0
0
1
1

1
0
1
0
0

0
0
0
0
1

1
1
0
1
1

0
0
1
0
1

Dado que cambian la paridad de la segunda fila y la tercera columna, podemos determinar que el elemento situado en la posición (2,3) es erróneo.

Si ocurren dos errores, podemos verificar la existencia de los mismos, pero no determinarlos:
0
0
0
1
1

1
1
1
0
0

0
0
0
0
1

1
1
0
1
1

0
0
1
0
1

No cambia la paridad de la segunda fila, pero sí las de las columnas 2 y 3 y, en este caso, existe más de una posibilidad.

## Paridad bidimensional

Decodificación
Supongamos que se produce un error en el tercer elemento de la segunda fila:
0
0
0
1
1

1
0
1
0
0

0
0
0
0
1

1
1
0
1
1

0
0
1
0
1

Dado que cambian la paridad de la segunda fila y la tercera columna, podemos
determinar que el elemento situado en la posición (2,3) es erróneo.

Si ocurren dos errores, podemos verificar la existencia de los mismos, pero no
determinarlos:
0
0
0
1
1

1
1
1
0
0

0
0
0
0
1

1
1
0
1
1

0
0
1
0
1

No cambia la paridad de la segunda fila, pero sí las de las columnas 2 y 3 y, en este
caso, existe más de una posibilidad.

## Código Hamming [7,4]

Codificación
La codificación de una cadena de 4 bits viene determinada por la multiplicación módulo 2 por la matriz


1 0 0 0 0 1 1
0 1 0 0 1 0 1

G=
0 0 1 0 1 1 0
0 0 0 1 1 1 1
Por ejemplo:

1

0

0


1
 0
1 
0
0

0
1
0
0

0
0
1
0

0
0
0
1

0
1
1
1

1
0
1
1


1
1
= 1
0
1

0

0

1

1

0


0

## Código Hamming [7,4]

Codificación
La codificación de una cadena de 4 bits viene determinada por la multiplicación
módulo 2 por la matriz


1 0 0 0 0 1 1
0 1 0 0 1 0 1

G=
0 0 1 0 1 1 0
0 0 0 1 1 1 1
Por ejemplo:

1

0

0


1
 0
1 
0
0

0
1
0
0

0
0
1
0

0
0
0
1

0
1
1
1

1
0
1
1


1
1
= 1
0
1

0

0

1

1

0

0



## Código Hamming [7,4]

Decodificación
: La decodificación de un mensaje se obtiene al multiplicar módulo 2 por la matriz
0
1

1

H = 1

1
0
0
S
1
0
1
1
0
1
0

1
1

0

1

0
0
1
{: .d}

Por ejemplo:
0
1

1


0 1

1
0
0


1

0

1

1

1

0

1
0
1
1
0
1
0


1
1

0

1 = 1

0
0
1

1

0



El resultado nos marca la posición del error, lo que hemos obtenido es la tercera fila de H, con lo que el mensaje original recibido era 1 0 0 1 1 0 0

## Código Hamming [7,4]

Decodificación
: La decodificación de un mensaje se obtiene al multiplicar módulo 2 por la matriz
0
1

1

H = 1

1
0
0


1
0
1
1
0
1
0


1
1

0

1

0
0
1
{: .d}

Por ejemplo:
0
1

1


0 1

1
0
0


1

0

1

1

1

0

1
0
1
1
0
1
0


1
1

0

1 = 1

0
0
1

1

0



El resultado nos marca la posición del error, lo que hemos obtenido es la tercera fila de
H, con lo que el mensaje original recibido era 1 0 0 1 1 0 0

## Letra DNI

| Resto | 0 | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 | 9 | 10 | 11 | 12 | 13 | 14 | 15 | 16 | 17 | 18 | 19 | 20 | 21 | 22 |
| Letra | T | R | W | A | G | M | Y | F | P | D | X  | B  | N  | J  | Z  | S  | Q  | V | H  | L  | C  | K  | E  |
{: .eq}

Codificación
: Sea n el número del DNI. Entonces n ≡23 RL siendo RL el equivalente numérico de la
letra según el cuadro anterior, es decir, la codificación de n es n||RL .
Así, por ejemplo, la letra correspondiente al DNI 34845300 es R, dado que
34845300 ≡23 1
{: .d}