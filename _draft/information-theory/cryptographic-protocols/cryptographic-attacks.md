---
layout: page
title: Ataques criptográficos
menu: cryptographic-protocols
index: 1
comments: true
mathjax: true
developing: true
---

## Ataques sobre un encriptado

Ataque con solo texto cifrado
: Ataque en el que tan solo se dispone de un texto cifrado y se trata de obtener, bien el texto original, bien la clave de descrifrado mediante la única observación del texto cifrado. Un esquema vulnerable a este tipo de ataque es completamente inseguro.
{: .d}

Ataque con texto claro conocido
: Ataque en el que se dispone de varias parejas de texto cifrado y sus correspondientes texto sin cifrar.
{: .d}

Ataque con texto claro escogido
: Ataque en el que el adversario puede escoger un texto en claro y acceder a su correspondiente texto cifrado.
{: .d}

Ataque con texto claro escogido adaptado
: Ataque con texto en claro escogido en el que la elección del texto en claro puede depender del texto cifrado recibido en previas peticiones.
{: .d}

Ataque con texto cifrado escogido
: Ataque en el que el adversario escoge el texto cifrado para obtener a continuación el correspondiente texto en claro. Una forma de montar este ataque es el de obtener acceso al algoritmo de descifrado, pero no a la clave. El objetivo es el de obtener el descifrado de algún texto a partir de la información obtenida de un descifrado distinto.
{: .d}

Ataque con texto cifrado escogido adaptado
: es análogo al correspondiente con texto en claro, pero la elección se realiza sobre el texto cifrado.
{: .d}

## Ataques sobre protocolos

Ataque con clave conocida
: El adversario, a partir de una clave usada anteriormente, trata de obtener información sobre claves nuevas.
{: .d}

Ataque por repetición
: El adversario graba una sesión de comunicación y la repite, completamente o en parte, en un momento posterior en el tiempo.
{: .d}

Ataque por impersonación
: El adversario asume la identidad de una parte legı́tima
en una comunicación.
{: .d}

Ataque con diccionarios
: Se trata, usualmente, de un ataque contra contraseñas. Una contaseña se suele almacenar encriptada de algún modo. El atacante toma una lista de posibles contraseñas, calcula sus encriptados y los compara con el valor almacenado.
{: .d}

Búsqueda hacia adelante
: Similar al anterior, pero con el objetivo de descifrar mensajes.
{: .d}

Ataques de inserción
: Consiste en la inserción de información en una comunicación con objeto de impersonar una identidad.
{: .d}

## Protocolo de Diffie-Hellman

1. Alice y Bob se ponen de acuerdo en un grupo G y un elemento g ∈ G de orden finito.
2. Alice escoge \\(a\in\mathbb{N}\\) y calcula \\(g^a\\).
3. Bob escoge \\(b\in\mathbb{N}\\) y calcula \\(g^b\\).
4. Alice y Bob intercambian \\(g^a\\) y \\(g^b\\).
5. Alice y Bob calculan \\(g^{ab}=(g^a)^b=(g^b)^a\\).

## Ataque man-in-the-middle

Eve es un adversario poderoso que es capaz de interceptar la comunicación entre Alice y Bob, que se han puesto de acuerdo en un grupo \\(G\\) y un elemento \\(g\in G\\) de orden finito.
1. Alice escoge \\(a\in\mathbb{N}\\), calcula \\(g^a\\) y se lo envı́a a Bob.
2. Eve escoge intercepta el mensaje y lo sustituye por \\(g^e\\), para algún \\(e\in\mathbb{N}\\), que es lo que Bob recibe.
3. Bob escoge \\(b\in\mathbb{N}\\), calcula \\(g^b\\) y se lo envı́a a Alice.
4. Eve intercepta el mensaje y lo sustituye por \\(g^e\\), que es lo que Alice recibe.
5. Alice calcula \\((g^e)^a\\).
6. Bob calcula \\((g^e)^b\\).
7. Eve calcula \\((g^a)^e\\) y \\((g^b)^e\\).

Alice y Eve comparten \\(k_1=g^{ae}\\), y Bob y Eve comparten \\(k_2=g^{be}.\\) Cuando Alice envía un mensaje a Bob, usa \\(k_1.\\) Eve lo intercepta, lo descifra, lo lee y/o lo transforma, y se
lo envía a Bob encriptado usando \\(k_2\\) y viceversa.

## Ataque por impersonación

Cuando se quiere usar una función de una vı́a con puerta trasera para enviar un secreto a través de un canal público inseguro, se hace necesario el hacer pública cierta información, que denominamos la clave pública.

¿Qué impide a un atacante suplantar la personalidad de alguien que dice que está publicando una función de una vı́a y publicar en realidad una función de clave pública cuya puerta trasera esté controlada por él mismo?

## Protocolo de Diffie-Hellman para más de 2 usuarios: CLIQUES I

1.  Un conjunto de n usuarios {Ui }ni=1 se ponen de acuerdo en un grupo G y un
elemento \\(g\in G\\) de orden finito.
2.  Cada usuario escoge una clave privada \\(x_i\in\mathbb{N}\\), \\(i\in\{1,\ldots,n\}\\).
3.  El usuario \\(U_1\\) envı́a \\(g^{x_1}\\) a \\(U_2\\).
4.  El usuario U2 envı́a \\(\{g^{x_2},g^{x_1},(g^{x_1})^{x_2}\}\\) a \\(U_3\\).
5.  El usuario \\(U_3\\) envı́a \\(\\\{(g^{x_2})^{x_3},(g^{x^1})^{x^3},g^{x_1x_2},((g^{x_1})^{x_2})^{x_3}\\\}\\) a \\(U_4\\).
6.  El usuario \\(U_i\\) envı́a a Ui+1 {hj }ij=1 para i2 ≤ i ≤ n, donde hj = g
Qn−1
k =1,k6=j
xk
.
xk xn
) .
7.  El usuario Un calcula (g
8.  El usuario Un envı́a al resto de usuarios
n Qn
on
x
g k =1,k 6=j k
k=1,k6=j
Qi
j=1
9.  El usuario Ui calcula (g
Qn
k=1,k6=i xk )xi .

## Protocolo de Diffie-Hellman para más de 2 usuarios: CLIQUES II

1.  Un conjunto de n usuarios {Ui }ni=1 se ponen de acuerdo en un grupo G y un
elemento g ∈ G de orden finito.
2.  Cada usuario escoge una clave privada xi ∈ N, i = 1, . . . , n.
3.  El usuario U1 envı́a g x1 a U2 .
4.  El usuario Ui envı́a a Ui+1 g
5.  El usuario Un−1 envı́a al resto de usuarios (incluyendo Un ) g
Qn
k=1 xk
Qi
k =1 xk
para 2 ≤ i ≤ n − 2.
6.  Un calcula g
7.  Cada usuario Ui , i = 1, . . . , n − 1, calcula y envı́a a Un (g
8.  El usuario Un envı́a al resto de usuarios
n Qn
on
x
g k =1,k 6=j k
Qn−1
k =1
xk
.
.
Qn−1
k =1
xk −xi
) .
j=1
1
El usuario Ui calcula (g
Qn
k=1,k6=i
xk xi
) .

## Un ataque a CLIQUES II

1.  Los pasos 1 y 2 transcurren sin ser alterados.
2.  El atacante \\(\mathcal{M}\\) intercepta \\(g^{\\prod_{k=1}^{n-1}.\\)
3.  \\(U_{n-1}\\) envı́a a \\(U_{n-1} \\left( g^{\\prod_{k=1}^{n-1}x_k}\\right)^{-x_{n-1}} = g^{\\prod_{k=1}^{n-2}x_k}.\\) \\(\mathcal{M}\\) intercept también este mensaje.
4.  \\(\mathcal{M}\\) envı́a a Un (g
k =1
xk
Qn−1
x
k =1 k )−xn−1
Qn−1
k =1
Qn−1
Qn−1
.
=g
Qn−2
k =1
xk
. M intercepta también este
xk m
) .
xk m xn
) ) .
5.  Un calcula ((g
6.  \\(\mathcal{M}\\) envı́a, haciéndose pasar por todo el resto de usuarios,
    *\\[ \\left\\{ g \\right\\} \\]*{: .eq}
7.  Un envı́a a todo el resto de usuarios
n
o
Qn−2
Qn−1
(g r1 )xn , (g r2 )xn , . . . , (g rn−3 )xn , (g k =1 xk )xn , (g k=1 xk )xn
    pero \\(\mathcal{M}\\) vuelve a interceptar este mensaje.
8.  \\(\mathcal{M}\\) calcula ((g
Qn−1
k =1
xk xn m
) ) .
9.  Hasta ahora U1 , . . . , Un−2 están esperando el mensaje de Un−1 , pero M,
haciéndose pasar por este, les envı́a (g
Qn−1
xk xn
) .
k =1
10. Ahora \\(U_i\\), \\(i\\in\\{1,\ldots,n-2\\}\\) devuelve a \\(U_{n-1}((g^{\\prod_{k=1}^{n-1}x_k})^{x_n})^{-x_i},\\) pero \\(\mathcal{M}\\) los intercepta.
11. \\(\mathcal{M}\\) envı́a a \\(U_i\\), \\(i\\in\\{1,\ldots,n-2\\}\\)
    *\\[ \\left\\{ (((g^{\\prod_{k=1}^{n-1}x_k})^{x_n})^{-x_i})^m \\right\\}_{i=1}^{n-1} \cup \\left\\{ (g^{\\prod_{k=1}^{n-1}x_k})^{x_n} \\right\\} \\]*{: .eq}
    y a \\(U_n\\) el mismo mensaje, pero sustituye \\( \\left\\{ (g^{\\prod_{k=1}^{n-1}x_k})^{x_n} \\right\\} \\) por \\( \\left\\{ g^{\\prod_{k=1}^{n-1}x_k} \\right\\} \\)
12. \\(U_i\\), usando \\(x_i\\), \\(i\\in\\{1,\ldots,n-1\\}\\) calcula \\(((g^{\\prod_{k=1}^{n-1}x_k})^m)^{x_n}.\\)

La diferencia con el ataque man-in-the-middle clásico es que ¡todos los usuarios comparten la misma clave!

La consecuencia, como puede observarse, es que debemos tener un método que
permita autentificar la procedencia de la información.