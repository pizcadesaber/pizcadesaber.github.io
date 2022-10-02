---
layout: page
title: Código de Hamming
menu: coding-theory
index: 6
comments: true
mathjax: true
developing: true
---

## Caso binario

Los códigos Hamming son una clase de códigos lineales capaces de corregir un error y con algoritmos de codificación y decodificación muy sencillos. Fueron utilizados originalmente en llamadas telefónicas.

Definición
: Un código de Hamming binario es un código lineal tal que su matriz de paridad tiene m filas y 2m − 1 columnas, que son todos los vectores no nulos de Zm2. Dicho código de Hamming se denota usualmente por Ham(m, 2).
{: .d}

Lema
: Los parámetros del código Ham(m, 2) son:
Longitud del código n = 2m − 1.
Dimensión del código k = 2m − m − 1.
Distancia mínima d = 3.
{: .l}

## Ejemplos

Ejemplo
: El código Ham(2, 2) tiene como matriz de paridad H =
generadora de dicho código es, por tanto, G =
de repetición de longitud 3.
1
1

1 1 0
. La matriz
1 0 1

1 , es decir, es un código.
{: .e}

Ejemplo
: El código Ham(3, 2) es un (7, 4, 3)-código lineal con matriz de paridad


0 0 0 1 1 1 1

0 1 1 0 0 1 1 
H=
1 0 1 0 1 0 1
{: .e}

## Códigos Hamming y cota de Hamming

Teorema
: Todo código de Hamming, es perfecto, es decir, alcanza la cota de Hamming:
M·
t  
X
n
i=0
i
(2 − i)i

= 2n
{: .t}

Demostración
: En primer lugar, se tiene que dado que la distancia mínima es 3, se tiene que t = 1.
Por otro lado, n = 2m − 1 y, como la dimensión del código es 2m − m − 1, se sigue que
m
M = 22 −m−1 .


m
m
De este modo, 22 −m−1 ( n0 (2 − 0)0 + n1 (2 − 1)1 ) = 22 −m−1 (1 + n) =
m
22
−m−1 (1
+ 2m − 1) = 22
m
−m−1 2m
m
= 22
−1 .
{: .p}

## Decodificación de Ham(m, 2)

Supongamos que recibimos la palabra y = x + e con w(e) = 1 y supongamos que la posición de e distinta de cero es j. Entonces:
S(y) = yH t = (x + e)H t = xH t + eH t = eH t = hj
donde hj es la j-ésima columna de H. Si se ordenan las columnas de H de menor a mayor, hj será la representación de j en binario. Así

Algoritmo de decodificación
1. Recibida y, se calcula el síndrome S(y).
2. Si S(y) = 0, entonces no se ha producido ningún error.
3. Si S(y) 6= 0, entonces el síndrome indica la posición, en binario, en la que ha tenido lugar el error.

## Ejemplo

Ejemplo
: Sea el código Ham(3, 2), con matriz de paridad

0 0 0 1 1
H= 0 1 1 0 0
1 0 1 0 1
1
1
0

1
1 
1
>Supongamos que se envía x = (1, 1, 0, 1, 0, 0, 1) y se recibe y = (1, 1, 0, 1, 0, 1, 1). Si
calculamos S(y) = (1, 1, 0), es decir, detectamos que se ha producido un error en la
posición 6 y, por tanto, se decodifica por x = (1, 1, 0, 1, 0, 0, 1)
En caso de que se reciba y = (1, 1, 1, 1, 0, 0, 0), es decir, dos errores, en las
posiciones 2 y 7, al calcular S(y) = (1, 0, 0) (que es la suma (0, 1, 1) + (1, 1, 1)), con
lo que se decodifica, erróneamente, por x = (1, 1, 1, 0, 0, 0, 0).
{: .e}

## Códigos Hamming no binarios

Sea GF (q) un cuerpo finito cualquiera, y consideremos GF (q)r con r ≥ 2.

Definición
: Llamaremos código de Hamming y lo denotaremos por Ham(r , q) a todo aquel código
cuya matriz de paridad, se construye de la siguiente forma:
q r −1
).
q−1
1 Sean todos los subespacios de dimensión 1 de GF (q)r (en total hay
2 De cada uno de los subespacios se toma un vector no nulo y se incluye como
columna de la matriz de paridad.
{: .d}

Ejemplo
: El código Ham(3, 3) es el código cuya matriz de paridad es

0 0 0 0 1 1 1 1 1 1 1
H= 0 1 1 1 0 0 0 1 1 1 2
1 0 1 2 0 1 2 0 1 2 0
1
2
1

1
2 
2
{: .e}

## Parámetros de los códigos Ham(r , q)

Teorema
:  r
−1
Un qq−1
,
q r −1
q−1

− r , 3 -código lineal sobre GF (q) es un código de Hamming.
{: .t}

Demostración
: En primer lugar, hemos de poner de manifiesto que un código de Hamming se define
por su matriz de paridad, compuesta por n vectores de GF (q)r de modo que dos
cualesquiera son siempre linealmente independientes y n es lo más grande posible, de
donde se tiene que, como hemos indicado antes, hay un total de q r − 1 subespacios
unidimensionales que dividimos por los posibles múltiplos, es decir, q − 1, con lo que
r
−1
su longitud es precisamente qq−1
. Así mismo, la matriz de paridad de un código
r
−1
Hamming tiene rango r , de donde la dimensión ha de ser qq−1
− r (recordemos que la
matriz H representa las ecuaciones cartesianas). Finalmente, como H tiene siempre 3
columnas linealmente independientes y no existe un subconjunto de 2 filas linealmente
independiente, entonces la distancia mínima es 3.
El recíproco es inmediato dado que la distancia mínima es 3 (lo que nos da la
propiedad sobre la dependencia lineal de las columnas) y la matriz de paridad tiene r
r
−1
filas y qq−1
columnas.
{: .p}

## Decodificación con códigos Ham(r , q)

Supongamos que recibimos la palabra y = x + e con w(e) = 1. Supongamos que la
posición de e distinta de cero es j. En este caso, e = (0, . . . , 0, b, 0, . . . , 0),
b ∈ GF (q). Entonces:
S(y) = yH t = (x + e)H t = xH t + eH t = eH t = b · hj

Algoritmo de decodificación
1. Recibida y, se calcula el síndrome S(y).
2. Si S(y) = 0, entonces no se ha producido ningún error.
3. Si S(y) 6= 0, entonces S(y) = bhj y el el error cometido es
e = (0, . . . , 0, b, 0, . . . , 0)
y decodificamos por y − e.

## Ejemplo

Ejemplo
: Sea Ham(2, 5) definido por

H=
0
1
1
0
1
1
1
2
1
3
1
4

{: .e}
>Supongamos que recibimos y = (2, 0, 3, 0, 3, 1). Entonces S(y) = (2, 3) = 2(1, 4) y
como 4 es la sexta columna de H, entonces e = (0, 0, 0, 0, 0, 2), con lo que
decodificamos por x = y − e = (2, 0, 3, 0, 3, 4).
{: .e}

## Códigos simplex

Definición
: Un código simplex es el código dual de un código Hamming.
{: .d}

Teorema
: Cualquier palabra de un código simplex tiene peso q r −1.
{: .t}

Demostración
: La matriz generadora de un código simplex es la matriz de paridad H de un código
r
−1
Hamming, con lo que tiene r filas y qq−1
columnas y además sabemos que el rango
de dicha matriz es r . De este modo, el código es hHi = {xH : x ∈ GF (q)r }.
Nótese que w(xH) = n-(columnas de H, y, tales que xy = 0). Sabemos que
r −1
dimx ⊥ = r − 1, luego tiene q q−1−1 subespacios de dimensión 1 y todos ellos están
representados en las columnas de H. Por tanto,
qr − 1
q r −1 − 1
−
= q r −1
q−1
q−1
 r

−1
Podemos concluir que un código simplex es un qq−1
, r , q r −1 -código lineal.
w(xH) =
{: .p}