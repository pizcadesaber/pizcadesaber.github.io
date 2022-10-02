---
layout: page
title: Criptografía de curva elíptica # Elliptic-curve cryptography
menu: elliptic-curve-cryptography
index: 2
comments: true
mathjax: true
developing: true
---

## Curvas elípticas

Definición
: Una curva proyectiva no singular que tiene forma homogénea 
*\\[ y^2z+a\_1xyz+a\_3yz^2=x^3+a\_2x^2z+a\_4xz^2+a\_6z^3 \\]*{: .eq}
o respectivamente con la forma no homogénea 
*\\[ y^2+a\_1xy+a\_3y=x^3+a\_2x^2+a\_4x+a\_6 \\]*{: .eq}
donde \\(a\_i\\in F\\), se denomina una curva elíptica en la forma de Weierstrass.
{: .d}

Esta curva tiene exactamente un punto del infinito, que es el punto \\(\\mathcal{O}=(0,1,0).\\)

## Formas simplificadas de la ecuación

Dado que \\mathrm{GL}3 (F) puede actuar sobre P2 , es posible llevar a cabo cambios de variable
(que se corresponden con cambios de base) y que permiten simplificar la forma de la
ecuación.

En caso de que la característica de F sea distinta de 2, si aplicamos el cambio de
variable y 7→ 21 (y - a1 x - a3 ) proporciona la forma:
y 2 = x 3 + a20 x 2 + a40 x + a6

En el caso de característica de F distinta de 3, entonces el cambio x 7→ x - a2 /3
proporciona
y 2 = x 3 + ax + b

## Pregunta:

Pero, ¿toda ecuación de la forma anterior, es decir,
y 2 = x 3 + ax + b, a, b ∈ F
define una curva elíptica?
Para ello debemos de establecer cuándo esta curva es no singular.
Recordemos que en una curva homogénea f̂ = 0 (α, β, γ) es singular si y solo si
δ f̂
δ f̂
δ f̂
(α, β, γ) = 0,
(α, β, γ) = 0,
(α, β, γ) = 0
δx
δy
δz

Lema
: La ecuación y 2 = x 3 + ax + b, a, b ∈ F define una curva elíptica si y solo si el
discriminante ∆ = 4a3 + 27b2 6= 0.
{: .l}

Demostración
: Sea f̂ = y 2 z - x 3 - axz 2 - bz 3 . Veamos, en primer lugar, que el punto del infinito
O(0, 1, 0) es no singular. Dado que
δ f̂
δ f̂
δ f̂
= -3x 2 - az 2 ,
= 2yz,
= y 2 - 2axz - 3bz 2
δx
δy
δz
δ f̂
se comprueba inmediatamente que δz
(0, 1, 0) 6= 0. De este modo, supongamos que
z = 1 (consideramos puntos no en el infinito), obteniendo entonces
3x 2 + a = 0, 2y = 0, y 2 = 2ax + 3b
de donde, podemos reducir a 3x 2 = -a, (2a)x = -3b, dado que y = 0. Si a = 0,
entonces, x = 0 y b = 0, y la curva y 2 = x 3 es singular en (0, 0, 1). Supongamos
entonces que a 6= 0. De este modo, la condición de punto singular se satisface si y
2
2
solo si 3 -3b
= 27b
= -a, es decir, 27b2 + 4a3 = 0.
2a
4a2
>Recíprocamente, si 27b2 + 4a3 = 0, entonces x = - 3b
, proporciona (x, 0, 1), que es
2a
un punto de la curva dado que
(2a)3 (x 3 + ax + b) = -27b3 - 12a3 b + 8a3 b = -b(27b2 + 4a3 ) = 0
{: .p}

## La operación suma una curva elíptica

Sean P y Q dos puntos de una curva elíptica C. La recta que pasa por P y Q está bien
definida, incluso en el caso en que P = Q, dado que C es no singular, en cuyo caso
se toma la tangente.
Sea P ∗ Q el tercer punto de intersección de la recta con la curva, cuya existencia está
garantizada por el Teorema de Bezout.
Definimos el punto conjugado de P ∈ C, como P = P ∗ O. Se define entonces
P+Q =P∗Q

Figure: Suma de puntos
6

## El grupo de puntos de una curva elíptica

Teorema
: El conjunto de puntos de una curva elíptica, con la operación suma de puntos, tiene
estructura de grupo abeliano.
{: .t}

Demostración
: En primer lugar es claro que la operación es conmutativa y que O es el elemento
neutro, dado que P + O = P ∗ O = O ∗ (O ∗ P) = P.
Por otro lado, -P = P, ya que P + P = P ∗ P = O = O.
Para probar que la suma es asociativa, basta probar que (P + Q) ∗ R = P ∗ (Q + R).
Observemos el siguiente diagrama:
<!--diagrama-->
>Observando desde arriba, podemos ver que el punto que falta es P ∗ (Q + R), mientras
que si miramos de derecha a izquierda, se tiene que el punto que falta es (P + Q) ∗ R
{: .p}

## Expresión analítica de la suma

Lema
: Sea E una curva elíptica en P2F dada por
y 2 + a1 xy + a3 y = x 3 + a2 x 2 + a4 y + a6
Sean P1 = (x1 , y1 ), P2 = (x2 , y2 ) ∈ E(F). Entonces
-P1 = (x1 , -y1 - a1 x - a3 )
y si P1 6= P2 ,
λ=




y2 -y1
x2 -x1
si
x1 6= x2



3x12 +2a2 x1 +a4 -a1 y1
2y1 +a1 x+a3
si
x1 = x2 , P1 = P2
y P1 + P2 = P3 = (x3 , y3 ) con
x3 = λ2 + a1 λ - a2 - x1 - x2 , y3 = -y1 + λ(x1 - x3 )
{: .l}

## Métodos anteriores para curvas elípticas

Intercambio de Diffie-Hellman para curvas elípticas
: 1. Alice y Bob se ponen de acuerdo en una curva elíptica \\(E\\) y un punto \\(P\\) de \\(E.\\)
2. Alice escoge \\(a\\in\\mathbb{N}\\) y calcula \\(aP.\\)
3. Bob escoge \\(b ∈ N\\) y calcula \\(bP.\\)
4. Alice y Bob intercambian \\(aP\\) y \\(bP.\\)
5. Alice y Bob calculan \\((ab)P = a(bP) = b(aP).\\)
{: .d.ol-number}

ElGamal para curvas elípticas
: 1. Alice escoge una curva elíptica E, un punto de la curva P y un múltiplo de P,
H = aP, para algún a ∈ N.
2. Alice hace pública la terna (E, P, aP), manteniendo en secreto a.
3. Un punto M de la curva se encripta mediante la función f : E → E × E definida
por f (M) = (kP, M + kH), donde k ∈ Z es aleatorio. Dicho punto se puede recuperar mediante a ya que
*\\[ M+kH-a(kP)=M+k(aP)-a(kP)=M. \\]*{: .eq}
{: .d.ol-number}

## Número de puntos de una curva elíptica

Teorema
: Si E es una curva elíptica sobre Fq , entonces E(Fq ) ∼
= Zd1 × Zd2 , con d1 |d2 .
{: .t}

Observación
: Es posible que d1 = 1. Desafortunadamente, no es sencillo establecer el isomorfismo.
{: .r}

Teorema
: Si E es una curva elíptica definida sobre Fq , entonces |E(Fq )| = q + 1 - t, con
√|t| ≤ 2 q.
{: .t}

## Ejemplos

Observación
: Si consideramos la ecuación de Weierstrass, y 2 = x 3 + ax + b, entonces para cada
x ∈ Fq , se tienen dos puntos siempre y cuando x 3 + ax + b sea un residuo cuadrático
en Fq , uno si x 3 + ax + b = 0 y ninguno si no es un residuo cuadrático.
>Como, por término medio, se tienen aproximadamente que la mitad de los elementos
de Fq son residuos cuadráticos, podemos más o menos estimar que |E(Fq | ≈ q + 1
(pues hemos de considerar además O).

Ejemplo
: Sea y 2 = x 3 + x + 1 definida sobre F23 . Entonces ∆ = 4a3 + 27b2 = 4√+ 4 6= 0. Por
el teorema anterior (debido a Hasse), se tiene que |E(F23 ) - 24| ≤ E(2 23) = 9.
{: .e}

## Factorización con curvas elípticas

Sea n = pq un número que queremos factorizar. Se escogen varias curvas en Zn y un
punto de cada una de ellas P. En la práctica, se toma un punto P, se considera la
ecuación y 2 ≡p x 3 + ax + b, se toma un valor a y se resuelve la ecuación resultante
de exigir que P la verifique para obtener b.
A continuación, con cada una de las curvas, se comienzan a calcular múltiplos de P,
teniendo en cuenta que en cada uno de estos cálculos es necesario que existan
ciertos inversos módulo n. En caso de no existir, quiere decir que estamos
encontrando un factor de n. La idea que motiva esta estrategia es que al calcular la
suma de dos puntos, uno considera la recta que los une y se busca que dicha recta
tenga tangente “infinita”, lo que nos llevará a obtener el punto del infinito.
En el caso de una curva elíptica sobre Zn , n = pq, dicha curva puede considerarse
como “dos curvas distintas”, una sobre Zp y la otra sobre Zq . Si consideramos una
curva E sobre Zp , N es el número de puntos de E, y m es el orden de P en E,
entonces m dividirá a N. Si N es el producto de primos pequeños, entonces, para un
valor razonablemente pequeño (1000, por ejemplo?), B!P = ∞.