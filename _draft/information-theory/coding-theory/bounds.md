---
layout: page
title: Cotas sobre códigos
menu: coding-theory
index: 3
comments: true
mathjax: true
developing: true
---

## Motivación

A la hora de la construcción de un \\((n,M,d)\\)-código, en términos de eficiencia y
eficacia debemos atender a:
La longitud de las palabras ha de ser lo más corta posible, es decir, n debe de ser
lo menor posible.
Posibilidad de codificar muchos mensajes, o lo que es lo mismo, M ha de ser lo
más grande posible.
Posibilidad de corregir muchos errores, de donde d ha de ser lo más grande
posible.

## Cota de Singleton

Teorema
: Sea C un \\((n,M,d)\\)-código q-ario. Entonces
M ≤ q n-d+1
{: .t}

Sean \\(c\_1,c\_2\\in C\\) con \\(c\_1\\neq c\_2.\\) Entonces, \\(c\_1\\) y \\(c\_2\\) tienen, al menos, \\(n-d+1\\) componentes, distintas, pues en caso contrario, se diferenciarían en \\(n-(n-d+1)=d-1\\) componentes y así, \\(d(c\_1,c\_2)\\leq d-1\\), lo que no es posible.

Por tanto, con un alfabeto con q elementos podemos construir, a lo sumo, q n-d+1 palabras distintas.

Corolario
: La tasa de información de un código \\((n,M,d)\\)-código q-ario es, a lo sumo,
\\(1-d-1n.\\)
{: .c}

Corolario
: Si la distancia mínima relativa de un \\((n,M,d)\\)-código q-ario, d/n, es grande, entonces
la tasa de información es pequeña.
{: .c}

## Cota de Hamming

Teorema
: Sea \\(C un \\((n,M,d)\\)-código \\(q\\)-ario sobre un alfabeto \\(A\\), tal que \\(d\\geq 2t+1.\\) Entonces, *\\[M\\leq Pt
qn
n
i=0 i (q
- i)i\\]*{: .eq}
{: .t}

## Sea c ∈ C. En primer lugar, notamos que existen exactamente n(q - 1) elementos de
An que difieren de c en exactamente una posición, es decir, el número de elementos u
tales que d(c, u) = 1 es exactamente n(q - 1).
Del mismo modo, el número de elementos u tales que d(c, u) = s, 1 < s ≤ t es
exactamente
n 
(q - 1)s
s

dado que podemos tomar exactamente ns formas distintas de escoger s lugares en
los que se diferencien c y u y, para cada uno de ellos, (q - 1) símbolos distintos.
Por tanto, el número de elementos de An que están a una distancia menor o igual que
t de c es
n n
n
+
(q - 1) + · · · +
(q - 1)t
0
1
t

## Si ahora tomamos dos palabras distintas del código, c1 y c2 , entonces se tiene que no
puede existir ningún elemento u ∈ An tal que d(u, c1 ), d(u, c2 ) ≤ t, dado que, en caso
contrario,
d(c1 , c2 ) ≤ d(c1 , u) + d(u, c2 ) ≤ t + t = 2t
Si llamamos B(c, r ) al conjunto de elementos de An tales que se encuentran a una
distancia menor
que r de la palabra código c, entonces se tiene que

P o igual
|B(c, r )| = ri=0 ni (q - i)i .
Como el número de elementos de An en todos los conjuntos B(c, r ), con c ∈ C no
puede ser mayor que q n , se tiene entonces que
M·
t  
X
n
(q - i)i ≤ q n
i
i=0
de donde se sigue la desigualdad que queríamos probar.

## MDS códigos

Definición
: Un código que alcance la cota de Singleton se denomina código MDS (Maximum Distance Separable).
{: .d}

Definición
: Un código que alcance la cota de Hamming se denomina perfecto.
{: .d}

## Cotas inferiores

Problema
Encontrar un código lo más grande posible de una determinada longitud y distancia mínima.
{: }

Definición
: Sean A un alfabeto con q elementos y d, n con d ≤ n. El mayor M tal que existe un
código \\((n,M,d)\\) con alfabeto A se denota por Aq (n, d).
Lemma
Dado A un alfabeto con q elementos, y n, d con d ≤ n, entonces q ≤ Aq (n, d).
Sea a0 ∈ A y sea C = {(a, . . . , a, a0 , . . . , a0 )} con d copias de a y n - d de a0 .
{: .d}

## Cota de Gilbert-Varshamov

Teorema
Sea A un alfabeto con q elementos y sean n, d tales que d ≤ n. Entonces existe un
\\((n,M,d)\\)-código q-ario tal que
Pd-1
i=0
qn
≤M
n
(q - 1)i
i
{: .t}

Corolario
: Pd-1
i=0
qn
≤ Aq (n, d)
n
(q - 1)i
i
{: .c}

Sea c1 un elemento de An y eliminamos todos los elementos de An que se encuentran a una distancia menor o igual que d - 1 de c1 .

Tomamos ahora c2 de entre los elementos restantes. Entonces d(c1,c2) ≥ d y procedemos como antes.

Del mismo modo, sea ahora c3 un elemento de entre los que quedan sin eliminar.

Entonces, d(c2 , c3 ) ≥ d y d(c1 , c3 ) ≥ d. Continuamos con el proceso tomando c4 , c5 , . . . hasta que no queden más elementos en An.
Como consecuencia de la demostración de la cota de Hamming, cada selección de un
P
n
elemento ck produce la eliminación de al menos d-1
(q - 1)i . De este modo, si
i=0
i
escogemos M elementos, entonces habremos eliminado, al menos,
P
n
M d-1
(q - 1)i .
i=0
i

Si continuamos el proceso hasta eliminar los q n elementos de An , se sigue que
P
n
podemos continuar hasta que q n ≤ M d-1
(q - 1)i .
i=0
i