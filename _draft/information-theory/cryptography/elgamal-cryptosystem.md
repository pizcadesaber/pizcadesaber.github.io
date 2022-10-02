---
layout: page
title: Criptosistema de ElGamal # ElGamal cryptosystem
menu: cryptography
index: 8
comments: true
mathjax: true
developing: true
---

## Logaritmo discreto

Definición
Sea G un grupo finito, g ∈ G y consideremos el grupo cíclico generado por g, hgi.
Para h ∈ G, se define el logaritmo discreto de h con base g como el entero a (si es
que existe), tal que g a = h. En tal caso, se escribe a = logg h.
{: .d}

Observación
: 1. El logaritmo discreto a = logg h existe si y solo si h ∈ hgi.
2. Si ord(g)= n y a = logg h, entonces a + kn también es un logartimo discreto con
base g de h, para k ∈ Z.
3. Usualmente nos referimos al logartimo de h con base g, como el menor entero
positivo a tal que g a = h.
{: .r}

Lema
: Sea G un grupo finito y sea g ∈ G con ord(g)= n. Entonces:
1. logg hk ≡n k logg h.
2. logg (h1 h2 ) ≡n logg h1 + logg h2 .
{: .l}

## Diffie-Hellman y el problema del logaritmo discreto

El protocolo fundacional propuesto por W. Diffie y M. Hellman se puede extender a
cualquier grupo finito:
1. Alice y Bob se ponen de acuerdo en un grupo G y un elemento g ∈ G de orden
finito.
2. Alice escoge a ∈ N y calcula g a .
3. Bob escoge b ∈ N y calcula g b .
4. Alice y Bob intercambian g a y g b .
5. Alice y Bob calculan g ab = (g a )b = (g b )a .

Para calcular g ab conociendo únicamente G, g, g a y g b implica resolver uno de los
logaritmos discretos logg g a o logg g b .
Si se toman a, b suficientemente grandes (actualmente el NIST recomienda, en el
caso de Zp , p ≥ 22048 ), buscar a y b de forma exhaustiva es inconcebible desde el
punto de vista computacional. Por otro lado, mediante el uso del algoritmo de la
potencia rápida, entonces calcular g a usando O(log a) operaciones en el grupo G.

## Taher ElGamal

En 1985, Taher ElGamal propone el uso de una función de una vía con puerta trasera
basada en la dificultad del problema del logaritmo discreto.

<!--Figure: Taher ElGamal-->

Taher ElGamal introduce la base del algoritmo de firma electrónica DSS en el mismo
trabajo y es además uno de los desarrolladores del protocolo SSL.

## El criptosistema de ElGamal

1. Alice elige un grupo G, un elemento g ∈ G de orden finito n y h = g a para algún
a ∈ N.
2. Alice hace pública la terna (G, g, g a ), manteniendo a en secreto.
3. Un mensaje m ∈ G se encripta mediante la función: f : G → G definida por
f (m) = (g k , mhk ), donde k ∈ Z es aleatoriamente escogido tal que
1 < k < n − 1.

Para recuperar el mensaje original se calcula (g k )−a (mhk ) = g −ak mg ak = m.

## Implementación ElGamal

Un aspecto importante de la implementación de ElGamal es que un mensaje m no se
cifra dos veces de la misma forma dado que f (m) = (g k , mhk ), donde k ∈ Z es
aleatoriamente escogido tal que 1 < k < n − 1.
Pero, ¿qué sucede si ciframos dos mensajes distintos con el mismo valor aleatorio k?
Supongamos que f (m1 ) = (g k , m1 hk ) y f (m2 ) = (g k , m2 hk ).
Se observa rápidamente que el primer elemento del par es el mismo, lo que significa
que el k escogido es el mismo. Supongamos ahora que conocemos m2 . Entonces sea
y = (m1 hk ) · (m2 hk )−1 = m1 m2−1 , con lo que conociendo m1 o m2 , se tendría acceso
al otro.

## El criptosistema de ElGamal y Diffie-Hellman

Puede probarse que romper el criptosistema de ElGamal es equivalente computacionalmente a romper el intercambio de clave de Diffie-Hellman:

Supongamos que existe un algoritmo A que es capaz de calcular g ab a partir de
G, g, g a y g b y que queremos encontrar m a partir del par (h, d) = (g k , m(g a )k ).
Hemos de tener en cuenta que G, g y g a son públicos tal y como establece el
criptosistema de ElGamal. Entonces, mediante el uso de A podemos obtener g ak , con
lo que m = d · (g ak )−1.

Supongamos ahora que existe un algoritmo G que es capaz de romper el
criptosistema de ElGamal, es decir, conocidos G, g, g a y el par (h, d) = (g k , m(g a )k ),
G ofrece como salida m. De lo que se trata ahora es, conocidos G, g, g a y g b , ser
capaces de calcular g ab .
De este modo, proporcionamos a nuestro algoritmo G los siguientes datos: G, g, g a ,
correspondientes a la clave pública y el par (h, d) = (g b , 1), que sería el equivalente a
encriptar el mensaje (que no conocemos) (g ab )−1 usando como parámetro aleatorio
g b . El resultado que nos va a proporcionar G es m = (g ab )−1 , con lo que, calculando
m−1 , obtenemos g ab .

Observación
: El problema de, dados G, g, g a , g b para ciertos a, b ∈ Z, calcular g ab se conoce usualmente en criptografía como el problema computacional de Diffie-Hellman.
{: .r}

Ejemplo
: El criptosistema de ElGamal ha sido considerado en la literatura en diversos grupos,
como por ejemplo:
1. Z∗p , grupo cíclico de orden p − 1.
2. GF (pn ), grupo cíclico de orden pn − 1.
3. GLn (GF (pn )), el grupo de matrices cuadradas de orden n invertibles con
entradas en G(pn ).
4. E(GF (pn )), el grupo de puntos racionales de una curva elíptica definida sobre GF (pn ).
5. Jacobianos de variedades.
{: .e}