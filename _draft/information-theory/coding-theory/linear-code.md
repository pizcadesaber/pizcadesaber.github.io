---
layout: page
title: Código lineal
menu: coding-theory
index: 4
comments: true
mathjax: true
developing: true
---

## Motivación

Cada vez que se establece una comunicación, la información se codifica antes de enviarse, lo que produce un retraso.

En una conversación telefónica una acumulación de retrasos puede hacer inviable dicha comunicación.

El hecho de que la información pueda codificarse y decodificarse por medio de alguna estructura puede servir para hacer la comunicación más eficiente.

## Concepto de código lineal

Definición
: Un código lineal de dimensión k y longitud n sobre un cuerpo F (el alfabeto) es un subespacio vectorial de dimensión k de Fn . En tal caso hablamos de (n, k)-código. Si la distancia mínima del código es d, entonces el código se denomina un
(n, k, d)-código.
{: .d}

Ejemplo
: El código de repetición {(0, 0, 0), (1, 1, 1)} es un (3, 1, 3)-código lineal sobre Z2.
{: .e}

## Distancia mínima

Lema
: Sea C un código lineal. Entonces la distancia mínima de C es
d = min{w(u) : u ∈ C}
{: .l}

Demostración
: Como w(u) = d(u, 0) es la distancia Hamming entre u ∈ C y 0, entonces w(u) ≥ d
para todo u ∈ C. Por otro lado, d(u, v ) = w(u - v ) para cualesquiera u, v ∈ C. Sean
pues u, v ∈ C tales que d(u, v ) = d, con lo que, por ser C un espacio vectorial,
u - v ∈ C y así min{w(u) : u ∈ C} = d.
{: .p}

Observación
: Para calcular la distancia mínima de un (n, M)-código hay que realizar comparaciones. En un (n, M)-código lineal, símplemente M - 1.
{: .r}

Para describir un código lineal basta con indicar su base.


## Matriz generadora

Definición
: Una **matriz generadora** de un \\((n, k)\\)-código lineal \\(C\\) sobre \\(F\\) es una matriz con \\(k\\) filas y
\\(n\\) columnas en las que las filas representan una base de \\(C.\\)
{: .d}

Observación
: Sea \\(G\\) la matriz de un \\((n,k)\\)-código lineal \\(C\\) sobre \\(F.\\) Entonces \\(C\\) está formado por el
conjunto de vectores de la forma \\(vG,\\) donde \\(v\\in F\_k.\\)
{: .r}

## Códigos equivalentes

Teorema
: Sea \\(G\\) una matriz con \\(k\\) filas y \\(n\\) columnas tal que sus filas son linealmente independientes. Entonces dicha matriz es equivalente por filas a una matriz de la forma
*\\[(I\_k|A) \\]*{: .eq}
donde \\(I\_k\\) es la matriz identidad de orden \\(k\\) y \\(A\\) es una matriz con \\(k\\) filas y \\(n-k\\) columnas.
{: .t}

Definición
: Se dice que un \\((n,k)\\)-código lineal está en forma estándar o que es sistemático si su matriz generadora es de la forma
*\\[(I\_k|A) \\]*{: .eq}
En este caso, los \\(k\\) primeros bits de una palabra del código se denominan bits de información y los \\(n-k\\) restantes, bits de paridad.
{: .d}

Definición
: Dos códigos lineales se dicen equivalentes si se pueden obtener uno a partir del otro por medio de permutaciones de las posiciones de los símbolos de las palabras del código y multiplicaciones por un escalar no nulo.
{: .d}

## Codificación con códigos lineales

Sea \\(C\\) un \\((n,k)\\)-código lineal definido sobre el cuerpo finito \\(F\\) con \\(q=p^n\\) elementos y con matriz generadora \\(G.\\) Entonces, \\(C\\) contiene \\(q k\\) palabras y, por tanto, se pueden usar para transmitir \\(q k\\) mensajes. Si \\(u = (u\_1,\\ldots,u\_k)\\) un mensaje. Entonces, la palabra del código \\(C\\) correspondiente es \\(uG.\\)

Ejemplo
: 
1 0 2 1
la matriz generadora de un (4, 2)-código lineal definido
0 1 2 2
sobre Z3 . La siguiente tabla muestra las palabras del código y los correspondientes
mensajes que resultan en dichas palabras al ser codificados:


Sea G =
d0
0
1
2
0
0
1
2
1
2

d1
0
0
0
1
2
1
1
2
2

u0
0
1
2
0
0
1
2
1
2

u1
0
0
0
1
2
1
1
2
2

u2
0
2
1
2
1
1
0
0
2

u3
0
1
2
2
1
0
1
2
0

## Decodificación por clases

Sea \\(C\\) un \\((n,k)\\)-código lineal definido sobre \\(\\mathbb{F}.\\) Entonces \\(C\\) es un subespacio vectorial de \\(\\mathbb{F}^n.\\) Sea pues el espacio vectorial cociente \\(\\mathbb{F}^n/C.\\) Si \\(x\\in\\mathbb{F}^n,\\) entonces \\(x+C\\) tiene exactamente \\(q^k\\) elementos.

Algoritmo de decodificación
: 1. Formamos una tabla donde cada fila corresponde a una clase del espacio vectorial cociente \\(\\mathbb{F}^n/C,\\) tomando como representante de la clase, la palabra de menor peso Hamming.
1. Recibida una palabra y, encontramos su clase de equivalencia \\(y+C\\) y consideramos el representante de la clase \\(e,\\) como el error cometido.
2. Dado que \\(e+C=y+C,\\) se sigue que \\(y-e\\in C,\\) con lo que decodificamos por \\(x=y-e.\\)
{: .d}

Ejemplo
: Sea \\(C\\) el código definido sobre \\(\\mathbb{Z}\_2\\) dado por la matriz generadora
*\\[G=\\begin{pmatrix}1 & 0 & 1 & 1 \\\\ 0 & 1 & 0 & 1\\end{pmatrix}.\\]*{: .eq} 
Entonces, el array de decodificación es
*\\[\\begin{align}(0,0,0,0)+C&=(0,0,0,0)(1,0,1,1)(0,1,0,1)(1,1,1,0) \\\\(0,0,0,1)+C&=(0,0,0,1)(1,0,1,0)(0,1,0,0)(1,1,1,1) \\\\(0,0,1,0)+C&=(0,0,1,0)(1,0,0,1)(0,1,1,1)(1,1,0,0) \\\\(1,0,0,0)+C&=(1,0,0,0)(0,0,1,1)(1,1,0,1)(0,1,1,0)\\end{align}\\]*{: .eq}
>Si recibimos la palabra \\((1,1,0,0),\\) considerando su clase de equivalencia en \\(\\mathbb{Z}\_2/C,\\) se tiene que \\((1,1,0,0)+C=(0,0,1,0)+C,\\) de donde el mensaje original es
*\\[(1,1,0,0)+(0,0,1,0)=(1,1,1,0). \\]*{: .eq}
{: .e}

## Ejemplo de decodificación errónea

Sea \\(C\\) anterior y cuyo array de decodificación es el siguiente
(0,0,0,0)+C=(0,0,0,0)(1,0,1,1)(0,1,0,1)(1,1,1,0)
(0,0,0,1)+C=(0,0,0,1)(1,0,1,0)(0,1,0,0)(1,1,1,1)
(0,0,1,0)+C=(0,0,1,0)(1,0,0,1)(0,1,1,1)(1,1,0,0)
(1,0,0,0)+C=(1,0,0,0)(0,0,1,1)(1,1,0,1)(0,1,1 0)

Si recibimos la palabra \\((1,0,1,0),\\) considerando su clase de equivalencia en \\(\\mathbb{Z}\_2/C,\\) se tiene que \\((1,0,1,0)+C=(0,0,0,1)+C,\\) de donde el mensaje original es 
*\\[(1,0,1,0)+(0,0,0,1)=(1,0,1,1). \\]*{: .eq}

Pero hemos de observar que \\((0,0,0,1)\\) no es la única palabra de menor peso y, por tanto, no la única candidata a ser representante de la clase, pues \\((0,1,0,0)\\) está en la
misma clase.

De este modo, la decodificación habría sido 
*\\[(1,0,1,0)+(0,1,0,0)=(1,1,1,0). \\]*{: .eq}


## Ejemplos

<!--20210420-->
Ejemplo
: Por tanto, la distancia mínima del código \\(C\\) es \\(2\\) dado que el peso más pequeño de caulquier palabra de \\(C\\) es \\(2\\). Otra forma:
*\\[G=\\begin{pmatrix}1&0&2\\\\0&1&1\\end{pmatrix}\\Rightarrow H=\\begin{pmatrix}\\end{pmatrix}\\]*{: .eq}
*\\[\\begin{pmatrix}1&0&2\\end{pmatrix} \\]*{: .eq}
*\\[\\begin{pmatrix}1&0&2\\end{pmatrix} \\]*{: .eq}
Efectivamente, \\(H\\) es una matriz de paridad para \\(C\\).
>Por tanto, calculamos
*\\[\\begin{pmatrix}0&0&0\\end{pmatrix}+C=\\{\\begin{pmatrix}0&0&0\\end{pmatrix},\\begin{pmatrix}0&1&1\\end{pmatrix}\\} \\]*{: .eq}
*\\[\\begin{pmatrix}0&0&1\\end{pmatrix}+C=\\{\\begin{pmatrix}0&0&1\\end{pmatrix},\\begin{pmatrix}0&1&2\\end{pmatrix},\\begin{pmatrix}0&2&0\\end{pmatrix},\\begin{pmatrix}1&0&0\\end{pmatrix},\\begin{pmatrix}1&1&1\\end{pmatrix},\\begin{pmatrix}1&2&2\\end{pmatrix},\\begin{pmatrix}2&0&2\\end{pmatrix},\\begin{pmatrix}2&1&0\\end{pmatrix},\\begin{pmatrix}2&2&1\\end{pmatrix}\\} \\]*{: .eq}
*\\[\\begin{pmatrix}0&1&0\\end{pmatrix}+C=\\{\\begin{pmatrix}0&1&0\\end{pmatrix},\\begin{pmatrix}0&2&1\\end{pmatrix},\\begin{pmatrix}0&0&2\\end{pmatrix},\\begin{pmatrix}1&1&2\\end{pmatrix},\\begin{pmatrix}1&2&0\\end{pmatrix},\\begin{pmatrix}1&0&1\\end{pmatrix},\\begin{pmatrix}2&1&1\\end{pmatrix},\\begin{pmatrix}2&2&2\\end{pmatrix},\\begin{pmatrix}2&0&0\\end{pmatrix}\\} \\]*{: .eq}
>Si me envían \\(\\begin{pmatrix}1&1&0\\end{pmatrix}\\) y me llega \\(\\begin{pmatrix}1&1&2\\end{pmatrix},\\) entonces decodificamos por
*\\[\\begin{pmatrix}1&1&2\\end{pmatrix}-\\begin{pmatrix}0&1&0\\end{pmatrix}=\\begin{pmatrix}1&0&2\\end{pmatrix}. \\]*{: .eq}
>Se debe a que el representante d
>Tabla de síndromes:
>Si recibimos \\(\\begin{pmatrix}1&1&2\\end{pmatrix}\\), entonces
*\\[s\\begin{pmatrix}1&1&2\\end{pmatrix}=\\begin{pmatrix}1&1&2\\end{pmatrix} \\]*{: .eq}
>De aquí,
{: .e}

Ejemplo:
Sea el código \\(C\\) tal que su matriz de paridad viene dada por
*\\[s\\begin{pmatrix}1&1&2\\end{pmatrix}=\\begin{pmatrix}1&1&1&0&0\\\\0&1&0&1&0\\\\1&1&0&0&1\\end{pmatrix} \\]*{: .eq} con alfabeto en \\(\\mathbb{Z}\_2.\\)
>\\(\\operatorname{long}(C)=5,\;\\operatorname{dim}(C)=2,\;d(C)\\geq3\\) porque cualquier subconjunto de columnas de \\(H\\) es linealmente independiente. No puede ser \\(4\\) porque las columnas 1, 3 y 5 son dependientes. Por tanto, \\(d(C)=3\\).
>*\\[G=\\begin{pmatrix}I\_2&A\\end{pmatrix}=\\begin{pmatrix}1&0&1&0&1\\\\0&1&1&1&1\\end{pmatrix} \\]*
es la matriz generadora.
*\\[\\begin{align}\\begin{pmatrix}0&1\\end{pmatrix}\\end{align} \\]*{: .eq}
y como puede comprobarse  la palabra de peso mínimo tiene peso 3, es decir, \\
> para lo que calcularemos
*\\[s(x)=xH^t=x\\begin{pmatrix}1&0&1\\\\1&1&1\\\\1&0&0\\\\0&1&0\\\\0&0&1\\end{pmatrix}. \\]*{: .eq}
{: .e}