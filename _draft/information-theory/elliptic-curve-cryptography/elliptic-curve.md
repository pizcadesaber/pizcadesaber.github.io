---
layout: page
title: Curva elíptica # Elliptic curve
menu: elliptic-curve-cryptography
index: 1
comments: true
mathjax: true
developing: true
---

## Curvas afines

Definición
: Sea p = i,j aij x i y j ∈ F[x, y] un polinomio en dos variables, con F un cuerpo. Entonces,
C = V (p) = {(x, y) ∈ F2 : p(x, y) = 0}
se denomina curva afı́n de grado deg(C) = max{i + j : aij 6= 0}.
{: .d}

Ejemplo
: La curva
x2
a2
+
y2
b2
− 1 = 0 es una curva afı́n de grado 2.
2
{: .e}

## Tipos de curvas afines

Definición
: Se dice que una curva p(x, y) = 0 es irreducible si p(x, y) ∈ F[x, y] es irreducible.
{: .d}

Definición
: Un una curva p(x, y) = 0 se dice no singular si
 punto (a, b) de 
δp
δp
(a,
b),
(a,
b)
6= (0, 0). En caso contrario se denomina punto singular. Una
δx
δy
curva se dice no singular (o smooth) si todos sus puntos son no singulares.
{: .d}

## El plano proyectivo

Definición
: Sea F un cuerpo y sea P2 = P2F = {(a, b, c) ∈ F3 \{(0, 0, 0)}}/R, donde R es la
relación de equivalencia dada por
(a, b, c) R (a0 , b0 , c 0 ) si y solo si existe λ ∈ F∗ : (λa, λb, λc) = (a0 , b0 , c 0 )
P2F se denomina plano proyectivo sobre F. Un punto [(a, b, c)]R se escribe
simplemente como (a, b, c). Si c 6= 0 se dice que (a, b, c) es un punto finito. En caso
contrario se dice que es un punto infinito o punto del infinito.
{: .d}

## Homogeneización

Definición
: Sea p ∈ F[x, y] de grado d. La homogeneización de p, p̂ ∈ F[x, y, z] se define como
el polinomio p̂(x, y, z) = z d p( xz , yz ).
{: .d}

Observación
: 1. Para todo λ, x, y, z ∈ Z se tiene que p̂(λx, λy, λz) = λd p̂(x, y, z).
2. Si se sustituye z 7→ 1, p̂ se reduce a p, esto es, p̂(x, y, 1) = p(x, y) para todo
x, y ∈ F.
{: .r}

Ejemplo
: 1. La parábola y = x 2 se define por p = y − x 2 ∈ F[x, y]. La homogeneización de p
es p̂ = yz − x 2 .
1. Si p = 3y 2 + x 3 + xy + 5, entonces p̂ = 3y 2 z + x 3 + xyz + 5z 3 .
{: .e}

## La forma homogénea p̂ define la curva proyectiva

C = V (p̂) = {(a, b, c) ∈ P2 : p̂(a, b, c) = 0}
Notemos que p̂(a, b, c) está bien para todo (a, b, c) ∈ P ya que para
p̂(λx, λy, λz) = λd p̂(x, y, z) para todo λ 6= 0.
Por otro lado, los puntos finitos de V (p̂) son precisamente los puntos de V (p) ya que
V (p̂) = V (p) ∪ {(a, b, 0) ∈ P2 : p̂(a, b, 0) = 0}

Ejemplo
: Sean p = y − x 2 y su homogeneización p̂ = yz − x 2 . Entonces
V (p̂) = V (p) ∪ {(0, 1, 0)}
{: .e}

## Teorema de Bezout

Teorema
: Sean p̂1 , p̂2 ∈ F[x, y, z] dos formas homogéneas de grados d1 y d2 respectivamente,
que definen dos curvas distintas C1 = V (p̂1 ) y C2 = V (p̂2 ). Entonces (contando con
la multiplicidad), C1 y C2 se intersecan exactamente en d1 d2 puntos sobre la clausura
algebraica de F.

Ejemplo
: 1. Sean la parábola p = y − x 2 y la recta q = x. De este modo, dadas p̂ = yz − x 2
y q̂ = x, las curvas del plano proyectivo que definen V (p̂) y V (q̂) intersecan en
(0, 0, 1) y (0, 1, 0).
2. Sean p = x + 2y y q = x + 2y + 1 dos rectas paralelas. Entonces p̂ = x + 2y y
q̂ = x + 2y + z son sus homogeneizaciones y las curvas que definen en P2 se
intersecan en el punto del infinito (2, −1, 0).
Geométricamente, los puntos del infinito pueden interpretarse como direcciones, o
como puntos que se encuentran infinitamente lejos del origen en una dirección.
{: .e}

## Resultante

Lema
: Sean f =
Pn
i=0 fi x
i, g
=
Pm

fn
..
.
..
.
0








S(f , g) = 








f0
0
..
.
0
i=0
fn
..
.
..
.
f0
..
.
...
gi x i ∈ F[x] y sea
...
..
.
..
.
..
.
0
0
..
.
0
fn
..
.
..
.
f0
gm
..
.
..
.
..
.
...
..
.
g0
..
0
.

0
.. 

. 


gm 

.. 
 ∈ F(n+m)×(n+m)
. 

.. 

. 

.. 
. 
g0
El determinante de S(f,g) se denomina resultante de f y g y se denota por Res(f , g).
Entonces Res(f , g) = 0 si y solo si gcd(f , g) 6= 1.
{: .l}

Demostración
: La matriz S(f , g) define una aplicación Fm × Fn → Fm×n dada por (a, b) 7→ af + bg,
donde Fk se interpreta como el espacio vectorial de los polinomios con coeficientes en
F y de grado menor estricto que k.
En caso de que f y g sean coprimos, entonces existen a, b, con deg(a) < m y
deg(b) < n tales que af + bg = 1. De este modo, 1, que se interpreta como
(0, . . . , 0, 1) está en la imagen de S(f , g).
>Recı́procamente, si gcd(f , g) 6= 1, entonces no existen a, b como los anteriores, con lo
que 1 no está en la imagen de S(f , g).
La demostración del lema se concluye demostrando que (0, . . . , 0, 1) no está en la
imagen de S(f , g) si y solo si el determinante de S(f , g) es cero (el sistema formado
por las columnas de la matriz, que generan la imagen de la aplicación tiene matriz de
coeficientes de rango menor que la matriz ampliada por la columna (0, . . . , 0, 1)t ).
{: .p}

## Demostración del teorema de Bezout

Pdi
pij x j , donde pij ∈ F[y, z], i = 1, 2 y consideremos la resultante de p̂1 y
Sea p̂i = j=0
p̂2 , que es un polinomio de grado d1 · d2 en F[y, z]. Por el Teorema Fundamental del
Álgebra, la resultante puede entonces factorizarse
d1 d2

Res(p̂1 , p̂2 ) =

Y

(βi z − γi y)

i=1

de donde se tienen d1 · d2 soluciones para (y, z) tales que existe una solución αi ,
donde (αi , βi , γi ) ∈ V (p̂1 ) ∩ V (p̂2 ).


**Los siguientes ejemplos están pendientes de trasladarlos a sus secciones correspondientes.**

Ejemplo 06/04/2021
: Sea \\(s=8\in\\mathbb{Z}\_{13}\\) un secreto a almacenar de forma compartida y \\(3\\) el umbral compartido para recuperar \\(s\\). De este modo, generamos un polinomio de grado \\(2\\) en \\(\\mathbb{Z}\_{13}[x ]\\) en el que el término indpeendiente es \\(s.\\) Por ejemplo, el polinomio \\(P(x):=8+7x+2x^2.\\) Generemos las participaciones:
*\\[P(1)\\equiv\_{13}4, \\quad P(3)\\equiv\_{13}, \\quad P(4)\\equiv\_{13}, \\quad P(10)\\equiv\_{13}.\\]*{: .eq}
>Las participaciones de \\(s\\) serían \\((1,4),(3,8),(4,3),(10,5).\\)
>3 de las participaciones para reconstruir \\(s.\\)
*\\[\\begin{align}
\\begin{cases}
P(x)\\equiv\_{x-1}4\\Leftrightarrow P(1)=4, \\\\\\\\
P(x)\\equiv\_{x-1}
\\end{cases}
\\end{align}\\]*{: .eq}
>*\\[\\begin{align}
(x-4)(x-10)&=x^2-14x+40=x^2+12x+1, \\\\\\\\
(x-1)(x-10)&=x^2-11x+10=x^2+2x+10, \\\\\\\\
(x-1)(x-4)&=x^2-5x+4=x^2+8x+4.
\\end{align}\\]*{: .eq}
>*\\[\\begin{align}
(x^2+12x+1)^{-1}&\\equiv\_{x-1}1^{-1}\\equiv\_{x-1}, \\\\\\\\
(x^2+2x+10)^{-1}&, \\\\\\\\
(x^2+8x+4)^{-1}&.
\\end{align}\\]*{: .eq}
{: .e}

Ejemplo 06/04/2021
: \\(x\\equiv\_{m\_1}a\_1,\\ldots,x\\equiv\_{m\_n}a\_n\\)
\\(s=\\sum\_{i=1}^n\\)
Otra forma:
*\\[P(x)=(x-1)q(x)+4\\Rightarrow(x-1)q(x)+4\\equiv\_{x-4}3\\Rightarrow3q(x)+4\\equiv\_{x-4}3,\\; 3q(x)\\equiv\_{x-4}-1\\]*{: .eq}
*\\[P(x)\\equiv\_{(x-4)(x-1)}(x-1)\\cdot4+4\\equiv\_{(x-4)(x-1)}4x \\]*{: .eq}
*\\[ \\]*{: .eq}
{: .e}

Ejemplo 06/04/2021
: *\\[\\left(\\frac{15}{71}\\right) \\]*{: .eq}