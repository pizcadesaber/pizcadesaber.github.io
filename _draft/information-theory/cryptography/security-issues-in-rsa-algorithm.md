---
layout: page
title: Problemas de seguridad del RSA # Security issues in RSA algorithm
menu: cryptography
index: 4
comments: true
mathjax: true
developing: true
---

## Selección de primos

Los primos escogidos han de ser aleatorios.
Si un atacante se dedicase a almacenar mensajes encriptados c e con las
correspondientes claves públicas usadas (n, e), podrı́a intentar calcular mcd(n1 , n2 )
con cada pareja de claves públicas guardadas. Si n1 y n2 tuviesen un factor común,
entonces ello permitirı́a encontrar las correspondientes claves privadas d1 y d2 y
obtener todos los mensajes cifrados con las claves (n1 , e1 ) y (n2 , e2 ).

Los primos deben estar suficientemente alejados
Si p − q no es suficientemente grande, entonces p, q ≈
√n.

## Ataque p − 1 de factorización de Pollard

Definition
Sean m y B enteros positivos. Se dice que m es B-suave (B-smooth) si todos los
factores primos de m son menores o iguales que B.
Example
48 es 3-suave pues 48 = 24 · 3.
Supongamos que n = pq y que p − 1 es B-suave (B pequeño), pero q − 1, no. Sea
Q E( log n )
k = r r log r , donde r ≤ B es primo. Por hipótesis, q − 1 no divide a k, pero p − 1,
sı́. Por el Pequeño Teorema de Fermat, ak ≡p 1 y ak 6≡q 1 para más de la mitad de los
elementos a (esto lo probaremos más adelante en los tests de primalidad). En este
caso, mcd(ak − 1, n) = p.
Example
Sea n = 511 y tomemos B = 4. Sea k = 29 · 35 = 62208.
Entonces,mcd(262208 − 1, 511) = 511, mientras que mcd(762208 − 1, 511) = 73.

## Primos seguros

Como consecuencia de los comentarios sobre la seguridad del RSA anteriores, la
elección de los primos suele hacerse del siguiente modo:
1. p y q han de verificar que p − q es un entero bastante grande (para evitar que √ ambos se encuentren en un entorno pequeño de pq.
2. p (y q) es tal que p − 1 tiene un factor primo grande, r (para evitar el ataque p − 1
de Pollard).
3. r es un número primo tal que r − 1 tiene un factor primo grande.
4. p (y q) es tal que p + 1 tiene un factor primo grande (para evitar un ataque similar
al anterior).

El hecho de usar este tipo de primos no significa que se aumente la seguridad, pero al
menos, se evitan los ataques anteriormente citados.

## El espacio de mensajes

En caso de que el espacio de mensajes sea pequeño o predecible, por ejemplo, un
PIN de 4 dı́gitos de una tarjeta, o el encriptado carácter a carácter de un texto,
entonces es posible encriptar todos los posibles mensajes y realizar una búsqueda
directa.
En el caso de encriptar carácter a carácter, dado que RSA siempre cifra m por el
mismo valor, podemos llevar a cabo un ataque por estadı́sticas del lenguaje.

## Exponente de encriptado pequeño

Mensajes cortos
Sea (n, e) la clave púlblica, con e tal que para m pequeño, c = me mod n = me ∈ N.
Entonces la raı́z e-ésima de c proporciona m. Por ejemplo, si n ≈ 21024 y e = 3,
entonces un mensaje m ≤ 2300 es cifrado por c ≤ 2900 y el cálculo de la raı́z cública
de c nos darı́a el mensaje cifrado.
Alternativa 1: si queremos usar tal exponente de encriptado hemos de usar “padding”.
Mensajes comunes
Otro peligro del uso de e pequeño es enviar un mismo mensaje m a, al menos, e
destinatarios, con módulos distintos (¡¡y coprimos!!). Entonces, el sistema x ≡ni ci ,
i = 1, . . . , e, nos produce como solución única (módulo el producto de los ni ), me . El
cálculo entonces de la raı́z e-ésima nos proporciona m.
Alternativa 2: no enviar el mismo mensaje a varios usuarios (usar “padding” distinto
para cada uno) o bien usar un exponente de cifrado muy grande con muchos ceros en
sus expresión binaria (para facilitar el proceso de encriptado), como por ejemplo
65537.

## Ataques con módulo común

Compromiso de una clave
Supongamos que se utiliza un módulo n = pq común para un sistema de parejas de
clave pública privada {(ei , di ) : i = 1, . . . , k}. El compromiso de una de las claves
privadas dj para algún j = 1, . . . , k permite la aplicación de un lema anterior que
afirmaba que es equivalente conocer la factorización de n a conocer di . De ese modo
quedarı́an comprometidas todas las claves di , i = 1, . . . , k, dado que se conocen
entonces Φ(n) y ei , i = 1, . . . , k.

Ataques internos
Como caso particular, un usuario del sistema anterior podrı́a comprometer las claves
privadas del resto de usuarios de dicho sistema.
Ataques con exponentes coprimos
Supongamos que (e1 , d1 ) y (e2 , d2 ) son dos parejas de exponentes de clave pública y
privada, que mcd(e1 , e2 ) = 1 y que se envı́a un mismo mensaje m usando ambas
claves, es decir, c1 ≡n me1 y c2 ≡n me2 . Sean ahora s, t ∈ Z tales que 1 = e1 s + e2 t.
Entonces c1s c2t ≡n (me1 )s (me2 )t = me1 s+e2 t = m.

## Propiedad homomórfica

Propiedad
f (m1 · m2 ) = (m1 · m2 )e ≡n m1e · m2e = f (m1 ) · f (m2 ).
Longitud del mensaje
Supongamos que enviamos un mensaje de longitud menor de 240 . Vamos a suponer
m = m1 · m2 , con m1 , m2 ≤ 222 . Entonces c ≡n me ≡n (m1 )e (m2 )e . Se puede
calcular una lista de valores c · (m1e )−1 para 1 ≤ m1 ≤ 222 y almacenamos únicamente
los últimos 50 bits. Ahora se calcula, para 1 ≤ m2 ≤ 222 , m2e y se comparan los
resultados con la lista almacenada para obtener una lista de candidatos m1 m2 = m.
Ataque con texto cifrado escogido
Supongamos que interceptamos c ≡n me y podemos acceder al descifrado de otro
mensaje distinto. Escogemos x ∈ U(Zn ) y proporcionamos el mensaje c 0 ≡n c · x e .
Obtendrı́amos entonces c 0d ≡n (cx e )d ≡n mx. Usando x −1 obtenemos m. Este tipo
de argumento fue usado contra una implementación del RSA en la que el servidor
devolvı́a el mensaje descifrado al emisor si el mensaje recibido por el emisor no tenı́a
la forma apropiada (ataque de Bleichenbacher 1998).