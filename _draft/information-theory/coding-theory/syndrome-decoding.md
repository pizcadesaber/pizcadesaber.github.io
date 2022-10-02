---
layout: page
title: Decodificación de síndromes
menu: syndrome-decoding
index: 5
comments: true
mathjax: true
developing: true
---

## Motivación

En un código con muchas palabras, usando la decodificación por clases, encontrar la clase de una palabra recibida puede ser algo bastante costoso, lo que llevaría a retrasos en la comunicación.

## Matriz de paridad

Definición
: Sea C un (n, k)-código lineal sobre F. Se dice que una matriz H es una matriz de paridad (o de comprobación de la paridad) para C si H verifica que v ∈ Fn es una palabra del código C si y solo si vH t = 0, donde H t denota la transpuesta de la matriz H.
{: .d}

## Cálculo de la matriz de paridad

Teorema
: Si G = [Ik |A] es la matriz generadora de un código C, entonces [−At |In−k ] es una
matriz de paridad para C.
{: .t}

Demostración.
Consideremos la i-ésima fila de la matriz G
vi = (0, . . . 0, 1, 0, . . . , 0, ai,1 , . . . , ai,n−k )
que es un vector de una base de C. El j-ésimo vector de la matriz H t es el vector
(−a1,j , . . . , −an−k ,j , 0, . . . , 0, 1, 0, . . . , 0)
donde el 1 se encuentra en la posición (n − k + j). Si multiplicamos ambos vectores, entonces el producto es 1 · (−ai,j ) + ai,j · 1 = 0. De este modo, si v ∈ C, entonces vH t = 0.
{: .p}

## Síndrome

Definición
: Sea C un (n, k)-código lineal definido sobre F y sea u ∈ Fn . Se define el síndrome de
u como S(u) = uH t .
{: .d}

Lema
: Sea C un (n, k)-código lineal definido sobre F y sean u, v ∈ Fn tales que
u + C = v + C. Entonces S(u) = S(v ).
{: .l}

Demostración
: Dado que u + C = v + C, se sigue que u = v + c, con c ∈ C. De este modo, 
S(u) = S(v + c) = (v + c)H t = vH t + cH t,
donde H es la matriz de paridad de C. El resultado se sigue del hecho de que cH t = 0.
{: .p}

## Decodificación por síndromes

Algoritmo
1. Calcular una tabla de síndromes, almacenando, para cada representante r + C, su correspondiente síndrome S(r).
2. Sea u la palabra recibida. Se calcula S(u).
3. Se localiza la clase u+C encontrando r + C tal que S(u)=S(r).
4. Se decodifica por v = u − r.

Ejemplo
: Sea C
 el código definido
 sobre Z2 dado por la matriz generadora

1 0 1 1
1 0 1 0
G=
. Entonces la matriz de paridad es H =
.
0 1 0 1
1 1 0 1
Los representantes de las clases, junto con sus correspondientes síndromes son:
(0,0,0,0)+C=(0,0)
(0,0,0,1)+C=(0,1)
(0,0,1,0)+C=(1,0)
(1,0,0,0)+C=(1,1)
1 0 1 1
= (1, 1, 1, 0).
0 1 0 1

Supongamos que se envía y y que se produce un error en el tercer bit, es decir, se recibe la palabra u = (1, 1, 0, 0).



1 1
 0 1 


Calculamos el síndrome de u: (1, 1, 0, 0) 
 1 0  = (1, 0), que es el síndrome de
0 1
(0, 0, 1, 0), con lo que decodificamos por c = y − u = (1, 1, 1, 0).

Codificamos el mensaje (1, 1): y = (1, 1)

Pero, ¿qué sucede si el error tiene lugar en el segundo bit, en lugar del tercero?

## Distancia mínima y matriz de paridad

Lema
: Sea C un código lineal. Si existe una palabra c ∈ C de peso d, entonces d columnas
de la matriz de paridad de H son linealmente dependientes.
{: .p}

Demostración
: Sea (c1 , . . . , cn ) ∈ C tal que w(c) = d. Entonces uH t = 0, es decir,
c1 h1 + · · · + cn hn = 0,
donde hi , i = 1, . . . , son las columnas de H. Como d coeficientes de la combinación lineal son distintos de cero, se sigue que d columnas de H son linealmente dependientes.
{: .p}

Lema
: Un código lineal C tiene distancia mínima mayor o igual que d si y solo si cualquier
subconjunto de columnas de la matriz de paridad H de C formado por a lo sumo d − 1
elementos es linealmente independiente.
{: .l}

Demostración
: Supongamos que la distancia mínima de C es d. Si existiesen d − 1 o menos columnas linealmente dependientes, entonces existiría una palabra de peso d − 1 o menos, lo que es una contradicción. Supongamos ahora que cualquier conjunto de d − 1 o menos columnas es linealmente independiente. Entonces, no puede existir una palabra del código de peso d − 1 o menos, es decir, la distancia mínima es ≥ d.
{: .p}

## Códigos duales

Definición
: Sea C un (n, k) código lineal definido sobre F. Se define el código dual de C como
C ⊥ = {u ∈ Fn : u · c = 0 para todo c ∈ C}.
Se dice que C es auto-dual si C = C ⊥.
{: .d}

## Caracterización de los códigos duales

Teorema
: Si C es un (n, k)-código lineal con matriz generadora [Ik |A], entonces C ⊥ es un (n, n − k)-código lineal con matriz generadora [−At |In−k ]. Además G es una matriz de paridad para C ⊥ .
{: .t}

Demostración
: En primer lugar, si dim(C) = k, entonces dim(C ⊥ ) = n − k. Por otro lado, como las filas de G constituyen una base de C, u ∈ C ⊥ si y solo si uGt = 0, con lo que G es una matriz de paridad para C ⊥ .
>Por otro lado, como (HGt )t = GH t = 0, entonces las filas de H son vectores de C ⊥.
>Como H tiene rango n − k, se tiene que las filas de H constituyen una base de C ⊥ y, de este modo, H es una matriz generadora para C ⊥.
{: .p}