---
layout: page
title: Test de primalidad de Solovay-Strassen # Solovay-Strassen primality test
menu: cryptography
index: 6
comments: true
mathjax: true
developing: true
---

## Residuos cuadráticos

Definición
: Sea F un cuerpo finito. Se dice que 0 6= a ∈ F es un residuo cuadrático si la ecuación
x 2 = a tiene solución en F.
{: .d}

Ejemplo
:Los residuos cuadráticos en Z7 son {1, 2, 4}.
{: .e}

Teorema
: Sea F un cuerpo finito. Si char (F) = 2, entonces todos los elementos no nulos son residuos cuadráticos. En caso contario, son exactamente la mitad de los elementos no nulos.
{: .t}

Demostración
: Sea f : F → F definida por f (x) = x 2 . Si char (F) = 2, entonces f es Z2 -lineal. Dado
que Ker (f ) = 0, se tiene que (al ser F finito, f es biyectiva y, por tanto, todos los
elementos son residuos cuadráticos.
En caso de que char (F) 6= 2, entonces f (x) = f (y) si y solo si x = ±y.
{: .p}

## El sı́mbolo de Legendre

Definición
: Sea p un primo impar y a ∈ N. Se define el sı́mbolo de Legendre de a sobre p como

   0 si a ≡p 0
a
1 si a es un residuo cuadrático en Zp
=
p

−1
en caso contrario

Ejemplo
: 
 
3
3
= −1 mientras que
= 1.
5
11
{: .e}

## El criterio de Euler

Teorema
: Sea p un primo impar y a ∈ N, entonces

 
p−1
a
≡p a 2 .
p

Demostración
: Supongamos que a 6≡p 0. Entonces a 2 ≡p ±1, ya que x 2 ≡p 1 tiene exactamente
dos soluciones, ±1 ∈ Zp y, por el Pequeño Teorema de Fermat ap−1 ≡p 1. Si a es un
residuo cuadrático en Zp , entonces existe y ∈ Zp tal que y 2 ≡p a y, por tanto,
p−1
a 2 ≡p y p−1 ≡p 1.
Sea ahora Q = {x ∈ Z∗p : x (p−1)/2 ≡p 1}. Como el polinomio x (p−1)/2 − 1 tiene, a lo
sumo (p − 1)/2 raı́ces, |Q| ≤ (p − 1)/2. Pero por lo anterior, existen, al menos
(p − 1)/2 elementos en Q, con lo que |Q| = (p − 1)/2, que son precisamente los
residuos cuadráticos.
{: .p}

## El sı́mbolo de Jacobi

Definition
: Sea n ∈ Z+ tal que n = p11 . . . pk k , donde pi i = 1, . . . , k son primos distintos y sea
a ∈ N. Entonces se define el sı́mbolo de Jacobi de a sobre n como
 ek
   e1
a
a
a
...
=
n
p1
pk
 
a
donde
i = 1, . . . , k denota el sı́mbolo de Legendre de a sobre pi .
pi
{: .d}

En el siguiente teorema se recogen algunas propiedades del símbolo de Jacobi.

Teorema
: Sean n, m ∈ Z+ y a1 , a2 ∈ N. Entonces:
   
a1
a2
1 Si a ≡n a , then
=
.
1
2
n
n

   
a1 a2
a1
a2
2
=
.
n
n
n
 
 
a
n
3
= (−1)(a−1)(n−1)/4
(Ley de reciprocidad cuadrática).
n
a
 
2
2
4 Si n es impar, entonces
= (−1)(n −1)/8 .
n
{: .t}

Ejemplo
:
Vamos a calcular el sı́mbolo de Jacobi

120
221

 

   
120
120
120
3
1
=
=
=
221
13
17
13
17
 
   
3
13
1
=
= (−1)(3−1)(13−1)/4
=
=1
13
3
3
Nota
    
2
2
2
=
= (−1)(−1), aunque 2 no es un residuo cuadrático en Z15
15
3
5
{: .e}

## Teorema de Solovay-Strassen

Teorema
: Sea n ∈ Z+ impar. Entonces
 
x
≡n x (n−1)/2 } es un subgrupo de Z∗n .
n1 El conjunto S = {x ∈ Z∗n :2S = Z∗n si y solo si n es primo.
{: .t}

Demostración
:     
x
y
xy
=
y x (n−1)/2 y (n−1)/2 = (xy)(n−1)/2
n
n
n
1
Se sigue del hecho de que
2
Por el Criterio de Euler, es claro si que n es primo, entonces S = Z∗n .
Supongamos pues que n no es primo y que S = Z∗n . Entonces n ha de ser un
número de Carmichael, dado que x n−1 ≡n 1, con lo que n = p1 p2 . . . pk , k ≥ 3 y
además pi − 1 divide a n − 1 para i = 1, . . . , k. Por el Teorema del resto chino,
Z∗n ∼
= Z∗p1 × · · · × Z∗pk . Sea entonces b ∈ Z∗p1 un no residuo cuadrático y sea
a ∈ Z∗n tal que su imagen sea (b, 1, . . . , 1), con lo que a(n−1)/2 tiene como
imagen (b(n−1)/2 , 1, . . . , 1), y dado que a(n−1)/2 ≡n ±1 (pues S = Z∗n ) y como n
es un número de Carmichael, ha de ser a(n−1)/2 ≡n 1. Pero entonces
   
   
 
a
a
a
b
1
=
...
=
...
= −1
n
p1
pk
p1
pk
para x, y ∈ S.
{: .p}

## Test de primalidad de Solovay-Strassen

Elegir un número entero n (no divisible por 2, 3, 5, 7, . . . ).
Escoger al azar
a1 , . . . , ak tales que gcd(ai , n) = 1, i = 1, . . . , k y comprobar si
 
a
(n−1)/2
≡n
n
 
ai
(n−1)/2
6≡n
Si para algún i = 1, . . . , k, ai
, entonces se concluye que n no es
n
primo. En caso contrario se determina que n es primo.
ai
3

Observación
: Como consecuencia del Teorema de Solovay-Strassen, si n no es primo,
 entonces, a
ai
(n−1)/2
∗
, con lo que
lo sumo, la mitad de los elementos de Zn verifican que ai
≡n
n
uno comprueba la primalidad de n con probabilidad al menos de 1 − (1/2)k.
{: .r}