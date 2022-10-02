---
layout: page
title: Test de primalidad de Miller-Rabin # Miller-Rabin primality test
menu: cryptography
index: 7
comments: true
mathjax: true
developing: true
---

## Preliminares

Lema
: Sea n un primo impar y n − 1 = 2s d, con d impar. Si a ∈ Z∗n entonces ad ≡n 1 o
r
existe k , 0 < r < s − 1 tal que a2 d ≡n −1.
{: .l}

Demostración
: En primer lugar, es claro que ord(a) es un divisor de 2s d, de donde ord(ad )= 2k para
algún k, 0 ≤ k ≤ s. En caso de que k = 0, entonces ad ≡n 1. En caso contrario,
k −1
k
(ad )2
6≡n 1 y (ad )2 ≡n 1. Pero como 1 tiene solo dos raı́ces, ±1, dado que n es
k −1
d
2
impar, entonces (a )
≡n −1
{: .p}

## Falsos testigos

Definición
: Sea n ∈ N un número impar. Entonces:
Se dice que a es un testigo falso de Fermat si an−1 ≡n 1.
Diremos que a es un testigo falso de Euler si a(n−1)/2 ≡n
 
a
.
n
Sea n − 1 = 2s d. Se dice que a es un testigo falso consistente si ad ≡n 1 o existe
k
k ∈ {0, . . . , s − 1} tal que ad2 ≡n −1.
{: .d}

Ejemplo
: Sea n = 65 y denotemos por F (65), E(65), S(65), los conjuntos de testigos falsos de
Fermat, testigos falsos de Euler y testigos falsos consistentes, respectivamente.
Entonces:
F (65) = {1, 8, 12, 14, 18, 21, 27, 31, 34, 38, 44, 47, 51, 53, 57, 64}.
E(65) = {1, 8, 14, 18, 47, 51, 57, 64}.
S(65) = {1, 8, 18, 47, 57, 64}.
Puede observarse que S(65) ⊆ E(65) ⊆ F (65) y que tanto E(65) como F (65) son
subgrupos de U(Z65 ), mientras que S(65) no lo es.
3
{: .e}

Teorema
: Sea n ∈ N impar y sean S(n), E(n) y F (n) los conjuntos de testigos falsos
consistentes, testigos falsos de Euler y testigos falsos de Fermat para n
respectivamente. Entonces
S(n) ⊆ E(n) ⊆ F (n) ⊆ Z∗n
Además, S(n) =
Z∗n
si y solo si n es primo.
{: .t}

Demostración
: Si n es primo, por el lema anterior, se tiene que S(n) = Z∗n . Sea pues n compuesto, es
decir, producto de al menos dos
primos distintos.
 
a
≡n a(n−1)/2 , de donde an−1 ≡n 1, y ası́
Si a ∈ E(n), entonces ±1 =
n
∗
E(n) ⊆ F (n) ⊆ Zn .
Sea pues a ∈ S(n) y n − 1 = 2s d, con d impar y sea k el menor entero tal que
k
e
e
a2 d ≡n 1. Entonces 0 ≤ k ≤ s − 1 y supongamos que n = p11 . . . pt t , con
pi , i = 1, . . . , t primos distintos.
Veamos en primer lugar el caso en el que k = 0. En tal caso, ad ≡pi 1 para todo
i = 1, . . . , t. De este modo, el orden en Zpi de a, oi , divide a d. Como d es impar,
entonces oi también es impar. Además oi divide a pi − 1 y, por tanto, a(pi −1)/2 ≡pi 1,
 
 
a
a
= 1. Ası́ pues
= 1 ≡n a(n−1)/2
lo que implica, por el criterio de Euler, que
pi
n
y, por tanto, a ∈ E(n).
k−1
Supongamos ahora que k > 0. Entonces a2 d ≡n −1. De este modo, para todo
k
k −1
i = 1, . . . , t, se tiene que a2 d ≡pi 1 y a2 d ≡pi −1. Ası́, el orden de a en Zpi , oi ,
k
k
−1
divide a 2 d, pero no divide a 2
d, con lo que oi = 2k di , con di impar. Dado que oi
divide a pi − 1, entonces 2k divide a pi − 1, de donde pi = 2k bi + 1 para un cierto
bi ∈ Z. Teniendo en cuenta que aoi /2 ≡pi −1, se tiene, por el criterio de Euler,
 
k
k
a
≡pi a(oi /2)·(pi −1)/oi ≡pi (−1)(pi −1)/oi ≡pi (−1)(pi −1)/(2 di ) ≡pi (−1)(pi −1)/2 ≡pi (−1)bi
pi
dado que di es impar. Por otro lado
n=
t
Y
i=1
e
pi i =
t
t
t
Y
Y
X
(2k bi + 1)ei ≡22k
(1 + 2k bi ei ) ≡22k 1 + 2k
bi ei
i=1
i=1
i=1
>De este modo,
t
2s−1 d =
X
n−1
bi ei
≡2k 2k−1
2
i=1
con lo que
2s−k d ≡2
t
X
bi ei
i=1
por lo que finalmente, se sigue que
s−1
a(n−1)/2 = a2
≡n
d
= (a2
k −1
d 2s−k
)
≡n (−1)2
s−k
Pt
≡n (−1)
i=1
bi ei
 
t
t  ei
Y
Y
a
a
((−1)bi )ei ≡n
=
pi
n
i=1
i=1
y, por tanto, a ∈ E(n).
{: .p}

Teorema de Miller-Rabin
: Si \\(n\\) es un número compuesto e impar, entonces
*\\[ |S(n)|\\leq\\frac{1}{4}\\varphi(n), \\]*{: .eq}
excepto para \\(n=9\\), que en cuyo caso, \\(|S(n)|=2.\\)
{: .t}

Demostración
: Supongamos en primer lugar que n es un número de Carmichael y sea n = p1 . . . pt ,
t ≥ 3 primos distintos, con pi − 1 dividiendo a n − 1 para todo i = 1, . . . , t. Sean
s1 , . . . , st tales que n − 1 = 2si (pi − 1)di , con di impar para todo i = 1, . . . , t y
supongamos, sin perdida de generalidad, que s1 ≤ · · · ≤ st . Sea s = s1 .
s
Como Zn ∼
= Zp1 × · · · × Zpt , entonces, a(n−1)/2 ≡n 1, dado que
s
si −s
a(n−1)/2 ≡pi a(pi −1)d2
≡pi 1
1)/2s
Además, (n −
es par.
Distinguimos ahora dos casos:
El primer caso es que s = si para todo i = 1, . . . , t. En tal caso, (n − 1)/2s+1 es un
múltiplo impar de (pi − 1)/2. Entonces S(n) está contenido en el subgrupo
A1 = {x ∈ Z∗n : x (n−1)/2
s+1
≡n ±1}
Sea a(k1 , . . . , kt ) el elemento de Z∗n dado por el isomorfismo del Teorema del resto
k
k
chino tal que a(k1 , . . . , kt ) 7→ (g11 , . . . , gt t ), con gi un generador de Zpi para todo
s+1
i = 1, . . . , t. Entonces a(k1 , . . . , kt )(n−1)/2
≡n ±1 si y solo si todos los ki son pares
o impares a la vez. Como t ≥ 3, entonces |S(n)| ≤ 1/2t−1 Φ(n) ≤ 1/4Φ(n).
El segundo caso es que st > s1 . Entonces (n − 1)/2s+1 es un múltiplo de pt − 1, y ası́
es par. De este modo,
s+1
S(n) ⊆ A0 = {x ∈ Z∗n : x (n−1)/2
≡n 1}
Como se tiene que A0 6= Z∗n , se sigue que |A0 | ≤ 1/2Φ(n). Además, se tiene que
S(n) ⊆ A2 = {x ∈ Z∗n : a(n−1)/2
s+2
≡n ±1}
que es un subgrupo de A0 . Entonces A2 ( A0 (Ejercicio). Por tanto,
|S(n)| ≤ |A2 | ≤ 1/2|A0 | ≤ 1/4Φ(n)
.
Queda probar el caso en el que n no es un número de Carmichael.
Se sabe que S(n) ⊆ F (n) ( Z∗n y que |F (n)| ≤ 1/2Φ(n).
Se deja como ejercicio el resto de la demostración, para lo que hay que construir un
subgrupo W ⊆ F (n) tal que
1
S(n) ⊆ W .
2
W ( F (n).
l
Ayuda: Sea W = {x ∈ Z∗n : x 2 d ≡n ±1 para algún i}.
{: .p}

## Test de Miller-Rabin

Sea n = 2s d ∈ Z impar, con d impar.
1. Se escogen a1 , . . . , at ∈ Z∗n y tales que mcd(ai , n) = 1, i = 1, . . . , t.
2. Para cada i = 1, . . . , t, comprobar
aid ≡n 1.
l
aid2 ≡n −1 para l = 0, . . . , s − 1.

Si ninguna de las dos cosas sucede, entonces n no es primo (por el primer lema). En
caso contrario, n es primo con una probabilidad de, al menos, 1 − (1/4)t.

## Un test determinista

Tal y como se dijo previamente, Agraval, Kayal y Saxena probaron que el problema de
determinar si un número es o no primo tiene complejidad de orden polinomial. El
algoritmo que proporcionan es de orden O(log12 (n)) (demasiado alto para llevarlo a la
práctica). Su idea es usar el siguiente hecho:

Lema
: Para todo a ∈ Z∗n , se tiene que (x + a)n ≡n x n + a si y solo si n es primo.
{: .l}

Demostración
: Si n es primo, entonces (x + y)n = x n + y n en Zn [x, y], y por el Pequeño Teorema de
Fermat an ≡n a si a ∈ Z∗n.
{: .p}