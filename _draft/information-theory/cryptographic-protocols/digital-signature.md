---
layout: page
title: Firmas digitales
menu: cryptographic-protocols
index: 2
comments: true
mathjax: true
developing: true
---

## Idea de firma digital

La solución al problema de la existencia de impostores o información falsificada puede
tenerse a partir de las firmas digitales. Para ello, una firma digital ha de verificar las
siguientes propiedades:
1. Ha de ser fácilmente obtenible.
2. Solo puede ser generada por la persona autorizada.
3. Ha de ser verificable por cualquiera.

## Problemas

Los problemas que resuelve la firma digital son los siguientes:
1. Autentificación de la información. Será posible determinar sin género de duda la
procedencia o autoría de una información, con lo que el problema de la existencia
de impostores quedará solucionado.

2. Integridad de la información. Una vez firmado un mensaje, si se altera el
contenido del mismo, entonces la firma decretará que este ha sido falseado.

3. No repudio de la información. El hecho de firmar un mensaje y que esto sea
posible solo por medio de la entidad autorizada, implicará además que dicha
entidad no podrá negar posteriormente la autoría de la misma.

## Concepto de firma digital

Definition
Sean M y S dos conjuntos, que serán los conjuntos de posibles mensajes y las
posibles firmas, respectivamente. Un esquema de firma digital consiste en una pareja
de aplicaciones:
f :M→S
y
v : M × S → {1, 0}
siendo f secreta, mientras que v es pública y tales que v (m, s) = 1 si y solo si
f (m) = s y v (m, s) = 0 en caso contrario, para m ∈ M y s ∈ S.
{: .d}

## Ejemplo de firma digital: la firma RSA

Ejemplo
: La firma RSA se basa precisamente en la construcción del criptosistema del mismo
nombre. En este caso, Si (n, e) es la clave pública de un esquema RSA y d es la
correspondiente clave privada, la función secreta que permite la construcción de la
firma es f : Zn → Zn dada por f (m) ≡n md , para cualquier m ∈ Zn .
La función pública que permite la verificación de una firma f (m) es
v : Zn × Zn → {1, 0} dada por v (m, s) = 1 si y solo si se ≡n m y v (m, s) = 0 en caso
contrario.
Recordemos, en este punto que si s ≡n md , entonces, se ≡n mde ≡n m.
{: .e}

Observación
: El primer problema que se plantea con el esquema anterior es que si alguien conoce
s, entonces es posible obtener m inmediatamente, con lo que sería imposible tener
confidencialidad a la vez que se usa el esquema.
Un segundo problema que tiene este esquema es que cualquiera podría obtener
firmas falsificadas de algunos mensajes: si s1 y s2 son dos firmas de los mensajes m1
y m2 respectivamente, entonces s1 s2 es la firma correspondiente al mensaje m1 m2 .
{: .r}

## La firma ElGamal (1985)

Sea p un número primo (la recomendación actual del NIST es de p ≈ 23072 ) y sea
g ∈ Z∗p un generador. Sea a ∈ Zp−1 , conocido únicamente por el firmante y sea
h = g a ∈ Zp . La función firma es:


s : Zp → Zp × Zp−1 , m 7→ (s1 , s2 ) = g k , (m − ag k )k −1
siendo k un número aleatorio.

Notemos, en primer lugar, que g k se calcula en Zp , mientras que el resto de valores de
la firma (en la segunda parte de la misma) se calculan en Zp−1 .
Los valores públicos de la firma (custodiados por una entidad de confianza) serán
(p, g, g a ). Para verificar la firma hemos de tener en cuenta la siguiente condición
necesaria:
s
k
hs1 s12 ≡p g ag g k (m−ag
k
)k −1
≡p g ag

De este modo, vamos a definir v (m, (s1 , s2 )) = 1 si
en caso contrario.
k
+m−ag k
s
hs1 s12
≡p g m
≡p g m y v (m, (s1 , s2 )) = 0

Observación
: Si un tercero quiere falsificar una firma (s1 , s2 ) de m y toma s1 ∈ Zp al azar, entonces
s
s
ha de encontrar s2 tal que hs1 s12 ≡p g m o, equivalentemente, s12 ≡p g m h−s1 , es
m
−s
decir, encontrar el logaritmo discreto en base s1 de g h 1 .
Un punto a favor respecto de este esquema es que la firma de un mensaje m no se
repite cada vez que se calcula.
El principal inconveniente es que si p ≈ 23072 , entonces la firma de un mensaje de
3072 bits requerirá 9216 bits.
{: .r}

## La firma ElGamal con curvas elípticas

Sea E una curva elíptica definida sobre Zp , y sea A ∈ E. Se toma a un número entero
que sirve como clave privada y se calcula B = aA. Los parámetros públicos de la firma
son E, p, A y B. A continuación vamos a calcular la firma de un entero m tal que es
menor que el número de puntos de E, n.
1. Se escoge k aleatorio tal que mcd(k , n) = 1 y se calcula R = kA = (x, y), tal que
n no divide a x.
2. Se calcula s ≡n k −1 (m − ax).
3. La firma del mensaje m es el par (R, s).
Para autentificar la firma se comprueba que xB + sR = mA dado que
xB + sR = xaA + k −1 (m − ax)(kA) = xaA + (m − ax)A = mA

## Error en la seguridad de la firma

Sean E, p, A, B los parámetros públicos de un esquema de firma digital con curvas
elípticas y sean m y m0 dos mensajes distintos cuyas firmas son, respectivamente,
(R, s) y (R, s0 ). En ambos casos se ha construido la firma usando el mismo entero
aleatorio k . Entonces las igualdades
ks ≡n m − ax
y
ks0 ≡n m0 − ax
determinan un sistema de ecuaciones, en caso de conocer los mensajes m y m0 , con
incógnitas k y a, el parámetro aleatorio y la clave privada, respectivamente.