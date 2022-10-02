---
layout: page
title: Test de primalidad de Fermat # Fermat primality test
menu: cryptography
index: 5
comments: true
mathjax: true
developing: true
---

## Teorema de los números primos

La construcción del RSA está relacionada con el siguiente teorema clásico de teoría de números:

Teorema de los números primos
: Sea \\(n\\in\\mathbb{N}^{\\ast}.\\) Si \\(\\pi(n)\\) es la cantidad de números primos contenidos en el intervalo \\([0,n ],\\) entonces
*\\[ \\underset{n\\to\\infty}{\\operatorname{lím}}\\frac{\\pi(n)}{n}\\log(n)=1. \\]*{: .eq}
{: .t}

Por tanto, si queremos encontrar un número primo de 1024 bits, entonces la probabilidad de que sea primo sería, aproximadamente:
1
1
21024 / log 21024
=
≈
21024
1024 log 2
308

## Cómo encontrar un primo aleatorio

Algoritmo
1. Elegir un número entero de 1024 bits de longitud (no divisible por 2, 3, 5, 7, . . . ).
2. Comprobar si el número es primo.
3. En caso contario, volver a 1.

Pero, ¿cómo comprobar que un número es primo?
Si comprobamos si un número n es divisible o no por todos los posibles divisores entre
√2 y E( n), dicho algoritmo es de orden O(n1/2 log2 n), con lo que si n ≈ 21024 , se trata de una complejidad ¡de orden exponencial!

## El Pequeño Teorema de Fermat

Anteriormente ya hemos probado que para cualquier n ∈ Z+ se tiene que si
mcd(a, Φ(n)) = 1, entonces aΦ(n) ≡n 1. Por tanto, como caso particular:
Theorem
Si p es un número primo y mcd(a, p) = 1, entonces
a- ≡p 1

## El test de Fermat

1. Elegir un número entero n (no divisible por 2, 3, 5, 7, . . . ).
2. Escoger al azar a1 , . . . , ak tales que gcd(ai , n) = 1, i = 1, . . . , k y comprobar si
ai- ≡n 1
3. Si para algún i = 1, . . . , k, ai- 6≡n 1, entonces se concluye que n no es primo.
En caso contrario se determina que n es primo.

## Falsos testigos de Fermat

Definición
: Sea \\(n\\) Un testigo falso de la primalidad de \\(n\\) es un número \\(a\\) Se dice que a es un falso testigo de la primalidad de n si a permite pasar el test de
Fermat a n, pero n no es primo.
{: .d}

Lema
: El conjunto Xn = {x ∈ Z∗n : x - ≡n 1} es un subgrupo de U(Zn ). Además, en caso
de que n no es primo, |Xn | < n/2.
{: .l}

Corolario
: El número de falsos testigos de Fermat, para \\(n\\) no primo es menor que \\(\\frac{n}{2}.\\)
{: .t}

## Números de Carmichael

Según lo anterior, la probabilidad de error del test de Fermat es de, a lo sumo, 1/2k .
Sin embargo,

Definición
: Un **número de Carmichael** es un número compuesto \\(n\\) que satisface \\(a^{n-1}\\equiv\_n1\\) para todo \\(a\\in\\mathbb{Z}^{\\ast}.\\)
{: .d}

Ejemplo
: El primer número de Carmichael es \\(561\\).
{: .e}


Teorema
: Sea \\(n\\) un número compuesto. Si \\(p\\in\\mathbb{P}\\) y \\(p^2\\mid n\\), entonces \\(n\\) no es un número de Carmichael.
{: .t}

Demostración
: Sea \\(n\\) un número de Carmichael y supongamos que \\(n=p^em\\) con mcd(p, m) = 1 y
que e ≥ 2. Por el Teorema del resto chino
U(Zn ) ∼
= U(Zpe ) × U(Zm )
>Como |U(Zpe )| = Φ(pe ) = p-(p-1), por el primer Teorema de Sylow, existe a ∈ U(Zpe ) de orden p. Sea pues, x ∈ U(Zn ) tal que su imagen sea el elemento (a, 1) ∈ U(Zpe ) × U(Zm ). Entonces, x tiene también orden p.
>Como n es un número de Carmichael, x - ≡n 1, con lo que p divide a n-1 y, de este modo, p es un factor común de n y n-1, lo que es absurdo.
{: .p}

Teorema
: Si \\(n\\in\\mathbb{Z}\\) es compuesto, impar y libre de cuadrados, entonces \\(n\\) es un número de
Carmichael si y solo si \\(p\\mid n\\) implica que \\((p-1)\\mid(n-1).\\)
{: .t}

Demostración
: Sea n = p1 . . . pk con pi i = 1, . . . , n primos distintos. Por el Teorema del resto chino,
Z∗n ∼
= Z∗p1 × · · · × Z∗pk
Sea pues x ∈ Z∗n y consideremos su imagen (x1 , . . . , xk ) ∈ Z∗p1 × · · · × Z∗p1 . Entonces
x - ≡n 1 si y solo si xi- ≡pi 1 para todo i = 1, . . . , k, de donde pi-1 divide a
n-1 para todo i = 1, . . . , k.
>Recíprocamente, supongamos que existe i tal que (pi-1) no divide a n-1 y sea x
un generador de Z∗pi . Entonces x - 6≡pi 1, con lo que el elemento
y = (1, . . . , 1, x, 1, . . . , 1) ∈ Z∗n verifica que y - 6≡n 1 y así, n no es un número de
Carmichael.
{: .p}

Teorema
: Si n es un número de Carmichael, entonces n tiene, al menos, tres factores primos.
{: .t}

Demostración
: Supongamos que n = pq con p y q números primos y supongamos, sin pérdida de
generalidad, que p > q. Si n es un número de Carmichael, entonces p-1 divide a
n-1, de donde existe y ∈ Z+ tal que n-1 = pq-1 = y(p-1). De este modo,
yp-y = pq-1, con lo que (yp-y)/p = q-1/p, así es que,
- =
yp-y + 1
-- =
∈Z
p
p
de donde se sigue que p divide a y-1 y, por tanto, y ≥ p + 1. Así pues
n-1 = y(p-1) ≥ (p + 1)(p-1) = p2-1 > pq-1 = n-1
lo que constituye una contradicción y, por tanto, n no puede ser producto de solo dos
primos.
{: .p}