---
layout: page
title: Protocolos criptográficos
menu: cryptographic-protocols
index: 4
comments: true
mathjax: true
developing: true
---

## El problema de la distribución de claves públicas

Problema
¿Cómo podemos hacer pública una función de una vía con puerta trasera de modo
que podamos asegurar que no pertenece realmente a un impostor?

## Concepto de protocolo

Definition
Un protocolo es un sistema de reglas que permiten llevar a cabo el desarrollo de un
algoritmo de forma apropiada.
En el caso de los protocolos criptográficos, el sistema de reglas afecta a la
representación de la información, la estructura de datos y una serie de pasos que
describan de forma clara el modo en que el algoritmo criptográfico correspondiente ha
de ser ejectuado para que consiga los objetivos perseguidos.

## Certificado de clave pública

Un certificado de clave pública es un protocolo que permite distribuir una función de
una vía de modo autentificado.

Las partes que componen un certificado son las siguientes:
1. Una autoridad certificadora, confiable por parte de los usuarios y que emite los
certificados de clave pública.
2. Una función de una vía con puerta trasera propiedad de la autoridad certificadora.
3. Un conjunto de mensajes, creados por la autoridad certificadora, que contiene
información sobre la función de una vía propiedad de su legítimo poseedor, así
como otra información relativa al mismo y una información que permite
autentificar el certificado mediante la función de una vía de la autoridad emisora.

## Protocolo de distribución de clave pública

1. Alice se autentica (verifica su identidad) con la autoridad certificadora y obtiene
una función de una vía (con puerta trasera) publicada por la autoridad.
2. La autoridad certificadora emite un certificado que contiene, básicamente:
Identidad de Alice.
Validez del certificado.
Función de una vía correspondiente a Alice.
Firma digital del certificado realizada por la autoridad certificadora.
3. Alice envía a Bob su certificado.
4. Bob utiliza la función de una vía de la autoridad certificadora para verificar la
autenticidad del certificado y comprueba su validez.
5. Bob utiliza la función de una vía contenida en el certificado para enviar un
mensaje a Alice.

## El problema del almacenamiento de clave

Problema: ¿Es posible almacenar una clave de forma confidencial y que no se corra peligro de
perderla o que se nos impida el acceso a la misma?

## Interpolación de Lagrange

Lema
: Sea \\(F\\) un cuerpo y sean (xi , yi ) ∈ F2 , i = 1, . . . , n + 1con xi 6= xj , j 6= i. Entonces
existe un único \\(f\\in F[x ]\\) de grado n tal que f (xi ) = yi , para todo i = 1, . . . , n.
{: .l}

Demostración
: Sea fi =
x−xj
j6=i xi −xj
Q
∈ F[x]. Es claro que fi tiene grado n y que fi (xj ) = δi,j para todo
Pn+1
i=1 yi fi .
i = 1, . . . , n + 1. Sea pues f =
Supongamos que f 0 ∈ F[x] es un segundo polinomio tal que f 0 (xi ) = yi para todo
i = 1, . . . , n + 1. Entonces f − f 0 ∈ F[x] es un polinomio de grado n y tal que
(f − f 0 )(xi ) = 0 para todo i = 1, . . . , n + 1. Por tanto f − f 0 = 0 y, de este modo, f es
único.
{: .p}

## Esquema umbral de Shamir

Sea S ∈ F un secreto que quiere almacenarse de forma segura. El esquema “divide”
S en N participaciones, k de las cuales son requeridas para la recuperación de S.
Pk−1
1 Se escogen k ∈ F, i = 1, . . . , k − 1 y se considera f = S +
k x i ∈ F[x].
i
i=1 i
2

Se escogen xi ∈ F, i = 1, . . . , N y se calculan las participaciones yi = f (xi ) ∈ F,
i = 1, . . . , N.

3

Se reparten las participaciones yi , i = 1, . . . , N y se destruye el polinomio f .

4

Cuando se desea recuperar el secreto S, se reúnen k de las N participaciones,
(xi1 , yi1 ), . . . , (xik , yik ) y se calcula
ik
X

yj

j=i1

ik
Y
j=i1

xj
xj − xi

Nota
El esquema funciona dado que f (0) = S.

## Distribución de clave común en grupo

Problema
Distribuir un secreto común a un grupo de usuarios en un único mensaje.

El siguiente protocolo se conoce como “Secure Lock”:
1. El servidor comparte con con cada usuario un par (fki , mi ), i = 1, . . . , n, donde fki
es una función de una vía (correspondiente a un criptosistema de clave simétrica)
y mi es un entero positivo grande (del tamaño determinado por el criptosistema)
i = 1, . . . , n tales que mcd(mi , mj ) = 1 para i 6= j.
2
Si s es el secreto a distribuir, el servidor calcula ri = fki (s), para todo i = 1, . . . , n.
3
El servidor calcula una solución del sistema de congruencias x ≡mi ri ,
i = 1, . . . , n, L.
Q
El servidor envía L mod ni=1 mi .
4
5. Cada usuario calcula L ≡mi ri = fki (m).
6. Cada usuario calcula fk−1 (ri ) = d.i