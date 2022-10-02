---
layout: page
title: RSA # Public-key cryptography
menu: cryptography
index: 3
comments: true
mathjax: true
developing: true
---

## Primer criptosistema de clave pública

En 1978, los matemáticos Ron Rivest, Adi Shamir y Len Addleman publican su artículo <<A method for Obtaining Digital Signatures and Public Key Cryptosystems>> en el que introducen el primer criptosistema de clave pública basado en la conjetura publicada dos años antes por Whitfield Diffie y Martin Hellman.

La función de una vía con puerta trasera viene definida por una aplicación \\(f:\\mathbb{Z}\_n\\to\\mathbb{Z}\_n,\\) con \\(n=p\\cdot q,\\) para \\(p\\) y \\(q\\) números primos, definida por \\(f(g)=g^e,\\) siendo \\(g\\) un elemento invertible en \\(\\mathbb{Z}\_n\\) y \\(\\operatorname{mcd}(e,(p-1)(q-1))=1.\\)

<!--Figure: R. Rivest, A. Shamir y L. Addleman-->

## Función indicatriz de Euler

Definición
: La **función indicatriz de Euler** o **función \\(\\  varphi\\) de Euler** es la función \\(\\varphi:\\mathbb{N}^{\\ast}\\to\\mathbb{N}\\), dada por
*\\[ \\varphi(n):=|\\mathbb{Z}\_n^{\\times}|, \\]*{: .eq}
donde \\(\\mathbb{Z}\_n^{\\times}\\) es el grupo multiplicativo de las unidades de \\(\\mathbb{Z}\_n.\\)
{: .d}

El siguiente teorema de teoría de números nos servirá para obtener una fórmula que nos permita el cálculo de la función indicatriz de Euler.

Teorema chino del resto
: Si \\(n\_1,\\ldots,n\_k\\in\\mathbb{Z}\\) tales que \\(n\_1,\\ldots,n\_k>2\\) y son primos relativos dos a dos, entonces
*\\[ \\mathbb{Z}\_{n\_1\\cdots n\_k}\\cong\\mathbb{Z}\_{n\_1}\\times\\cdots\\times\\mathbb{Z}\_{n\_k}.\\]*{: .eq}
{: .t}

Demostración
: Sean \\(n\_1,\\ldots,n\_k\\in\\mathbb{Z}\\) tales que \\(n\_1,\\ldots,n\_k>2\\) y son primos relativos dos a dos. Definamos \\(n:=n\_1\\cdots n\_k\\) y la función \\(f:\\mathbb{Z}\\to\\mathbb{Z}\_{n\_1}\\times\\cdots\\times\\mathbb{Z}\_{n\_k} \\) dada por
*\\[ f(a):=(a+n\_1\\mathbb{Z},\\ldots,a+n\_k\\mathbb{Z}) \\]*{: .eq}
Observemos que \\(f\\) es un homomorfismo de anillos y
*\\[ \\ker(f)=\\bigcap\_{i=1}^{k}\\ker(f\_i)=\\bigcap\_{i=1}^kn\_i\\mathbb{Z}=n\\mathbb{Z}, \\]*{: .eq}
donde \\(f\_i\\) es la componente \\(i\\)-ésima de \\(f\\). Aplicando el primer teorema de isomorfía, 
*\\[ \\mathbb{Z}\_n=\\frac{\\mathbb{Z}}{n\\mathbb{Z}}=\\frac{\\mathbb{Z}}{\\ker(f)}\\cong\\operatorname{Im}(f). \\]*{: .eq}
Luego, \\(|\\operatorname{Im}(f)|=n\\). Por otro lado, 
\\(|\\mathbb{Z}\_{n\_1}\\times\\cdots\\times\\mathbb{Z}\_{n\_k}|=\\prod\_{i=1}^kn\_i=n.\\)
Como \\(n\\) es finito, \\(\\operatorname{Im}(f)\\subseteq\\mathbb{Z}\_{n\_1}\\times\\cdots\\times\\mathbb{Z}\_{n\_k}\\) y ambos conjuntos tienen cardinal \\(n\\), entonces \\(\\operatorname{Im}(f)=\\mathbb{Z}\_{n\_1}\\times\\cdots\\times\\mathbb{Z}\_{n\_k},\\) lo que completa la prueba.
{: .p}

Teorema
: Sea \\(k\\in\\mathbb{Z}^+,\\) \\(p\_1,\\ldots,p\_k\\in\\mathbb{P}\\) distintos y \\(e\_1,\\ldots,e\_k\\in\\mathbb{Z}^+.\\) Si \\(n:=\\prod_{i=1}^kp\_i,\\) entonces
*\\[ \\varphi(n)=n\\prod\_{i=1}^k\\frac{p\_i-1}{p\_i} \\]*{: .eq}
{: .t}

Demostración
: Por el teorema del resto chino,
*\\[ \\mathbb{Z}\_n\\cong\\mathbb{Z}\_{n\_1}\\times\\cdots\\times\\mathbb{Z}\_{n\_k}, \\]*{: .eq}
donde \\(n\_i=p\_i^{e\_i}\\) para cada \\(i\\in\\{1,\\ldots,k\\}.\\) De aquí, se deduce
*\\[ \\mathbb{Z}\_n^{\\times}\\cong\\mathbb{Z}\_{n\_1}^{\\times}\\times\\cdots\\times\\mathbb{Z}\_{n\_k}^{\\times}. \\]*{: .eq}
Luego,
*\\[ \\varphi(n)=\\prod\_{i=1}^n\\varphi(p\_i^{e\_i}). \\]*{: .eq}
Como \\(\\operatorname{mcd}(a,p\_i^{e\_i})=1\\) si y solo si \\(\\operatorname{mcd}(a,p\_i)=1,\\) entonces
*\\[ \\left|\\mathbb{Z}\_{p\_i^{e\_i}}^{\\times}\\right|=p\_i^{e\_i}-p\_i^{e\_i-1}=p\_i^{e\_i}\\frac{p\_i-1}{p\_i}.\\]*{: .eq}
{: .p}

## Criptosistema RSA

El criptosistema de clave pública RSA se construye del siguiente modo:
1. Alicia elige dos números primos distintos y muy grandes p, q ≥ 21024.
2. Alicia calcula n = pq y Φ(n) = (p - 1)(q - 1).
3. Alicia escoge e < Φ(n) y tal que mcd(e, Φ(n)) = 1 y calcula d ∈ N, d < Φ(n) tal
que ed + v Φ(n) = 1 para algún v ∈ Z.
4. Alicia publica la función de una vía con puerta trasera f : Zn → Zn dada por m 7→ me , manteniendo p, q, Φ(n) y d en secreto.

Nota
: Si Bob envía a Alice el número m ∈ U(Zn ) usando f , entonces, Alice recupera el
mensaje recibido usando la puerta trasera d ya que:
(me )d = med (mod n) = m1-Φ(n)v (mod n) = m · (mΦ(n) )-v (mod n) = m (mod n)
Teniendo en cuenta que, dado que m ∈ U(Zn ) y |U(Zn )| = Φ(n), entonces
mΦ(n) = 1 (mod n) .
{: .}

Ejemplo
: Sea \\((n,e):=(91,12)\\) una clave pública. We are given $N$ and that will give us the prime factors $p$ and $q$ as:
*\\[N = 91 =  p \times q = 7 \times 13\\]*{: .eq}
We need the Euler Totient Function of the modulus, hence we get:
*\\[\varphi(N) = \varphi(91) = (p-1)(q-1) = 6 \times 12 = 72\\]*{: .eq}
Now, we choose an encryption exponent $1 \lt e \lt \varphi(N) = 72$. We were told to pick an an $e \lt 6$, so lets choose $e = 5$ and see if that works, where it should be coprime with $\varphi(N)$.
*\\[(5, 72) = 1 \\rightarrow e = 5\\]*{: .eq}
To find the decryption exponent , we just find the modular inverse of the encryption exponent using the totient result, hence:
*\\[d\\equiv\_{\\varphi(n)} e^{-1} \\equiv\_{72} 5^{-1}\\equiv\_{72} 29\\]*{: .eq}
Encryption:
*\\[\displaystyle c\\equiv\_{n} m^{e} \\rightarrow 9^5\\equiv\_{91} 81\\]*{: .eq}
Decryption:
*\\[\displaystyle m\\equiv\_{n} c^{d} \\rightarrow 81^{29}\\equiv\_{91} 9\\]*{: .eq}
Where:
>- \\(m\\) es el mensaje a encriptar.
- \\(c\\) es el mensaje encriptado.
- \\(e\\) es el exponente de encriptación.
- \\(d\\) es el exponente de desencriptación.
- \\(n\\) es el módulo que es formado por los dos primos p y q.
- \\(\varphi\\) es la función indicatriz de Euler.

## Preguntas

1. Si Bob envía un valor m, que no es una unidad de Zn , ¿puede Alice recuperar m?
2. ¿Cómo de difícil es calcular me y (me )d ?
3. ¿Cómo es de difícil encontar números primos como los requeridos para construir
el criptosistema?
4. ¿Cómo es de difícil encontrar los números primos p y q a partir de la información
pública? ¿Cómo es de difícil factorizar n?
5. ¿Conocer p y q es equivalente a conocer Φ(n)?

## Funcionalidad del RSA

Respuesta 1
: El teorema del resto chino permite recuperar el valor enviado por Bob, m, en el caso
de que m no sea coprimo con n.
{: .d}

Respuesta 2
: Sea e un número natural y sea k la longitud de la representación binaria de e.
Entonces me (mod n) puede calcularse en, a lo sumo, 2k multiplicaciones en Zn .
P
Para ello, sea e = ki=1 ei 2i la representación binaria de e. Entonces
me =
k
Y
i=0
i
m ei 2 =
k
Y
m2
i
i=0,ei 6=0
{: .d}

Ejemplo
: Sea e = 25. Dado que 25 = 20 + 23 + 24 , se tiene entonces
m25 = m2
0
+23 +24
3
4
= m · m2 · m2 = m · ((m2 )2 )2 · (((m2 )2 )2 )2
es decir, un total de 9 productos, siempre y cuando no se almacenen en alguna
variable aquellos que puedan ser reutilizados, en cuyo caso se tienen, exactamente 6
productos.
{: .e}

## Complejidad algorítmica

Definición
: Sean \\(f,g:\\mathbb{Z}\\to\\mathbb{R}^+\\) dos funciones. Se dice que \\(f\\) es:
* más compleja que \\(g\\) si, y solo si, *\\[ \\underset{n\\to\\infty}{\\operatorname{lím}}\\frac{f(n)}{g(n)}=+\\infty. \\]*{: .eq}
* menos compleja que \\(g\\) si, y solo si, *\\[ \\underset{n\\to\\infty}{\\operatorname{lím}}\\frac{f(n)}{g(n)}=0. \\]*{: .eq}
* equivalente a \\(g\\) en complejidad si, y solo si, existe \\(k\\in\\mathbb{R}^+\\) satisfaciendo *\\[ \\underset{n\\to\\infty}{\\operatorname{lím}}\\frac{f(n)}{g(n)}=k. \\]*{: .eq}
{: .d}

## Funciones de complejidad

Las funciones de complejidad más usuales viene dadas por el siguiente cuadro:

| ---                           | ---                       |
| \\(f(n)\\)                    |                           |
| ---                           | ---                       |
| \\(1\\)                       | constante                 |
| \\(\\operatorname{log}(n)\\)  | logaritmo                 |
| \\(n\\)                       | lineal                    |
| \\(n\\operatorname{log}(n)\\) |                           |
| \\(n^2\\)                     | cuadrática                |
| \\(n^k\\)                     | polinomial (\\(k > 2\\))  |
| \\(a^n\\)                     | exponencial (\\(a > 1\\)) |
| \\(n!\\)                      | factorial                 |

## Orden de complejidad

Definición
: El **conjunto de las funciones de orden \\(f(n)\\)** es el conjunto
*\\[O(f(n))=\\left\\{g\\in(\\mathbb{R}^+)^{\\mathbb{Z}}:\\underset{n\\to\\infty}{\\operatorname{lím}}\\frac{g(n)}{f(n)} < \\infty\\right\\}\\]*{: .eq}
{: .d}

Los órdenes de complejidad más habituales son los siguientes:

| \\(O(1)\\) | orden constante |
| \\(O(log(n))\\) | orden logarítmico |
| \\(O(n)\\) | orden lineal |
| \\(O(n\\operatorname{log}(n))\\) | |
| \\(O(n^2)\\) | orden cuadrático |
| \\(O(n^k)\\) | orden polinomial (\\(k > 2\\)) |
| \\(O(a^n)\\) | orden exponencial (\\(a > 1\\)) |
| \\(O(n!)\\) | orden factorial |

## Cuadro de ejemplo de complejidad

La siguiente tabla muestra el comportamiento en tiempo aproximado (\\(1\\mu\\text{s}=10^{-6}\,\\text{s},\\) \\(1\\,\\text{ms}=10^{-3}\\,s\\)) de los distintos órdenes de magnitud para ciertos valores de \\(n.\\)

| \\(n\\) | \\(O(1)\\)             | \\(O(log(n))\\)        | \\(O(n)\\)               | \\(O(n log(n))\\)        | \\(O(n^2)\\)             | \\(O(n^5)\\)                             | \\(O(5^n)\\) | \\(O(n!)\\) |
| 10      | \\(1\\,\\mu\\text{s}\\) | \\(2\\,\\mu\\text{s}\\) | \\(10\\,\\mu\\text{s}\\)  | \\(23\\,\\mu\\text{s}\\) | \\(100\\,\\mu\\text{s}\\) | \\(100\\,\\text{ms}\\)                    | \\(10\\,\\text{s}\\) | \\(4\\,\\text{s}\\) |
| 20      | \\(1\\,\\mu\\text{s}\\) | \\(3\\,\\mu\\text{s}\\) | \\(20\\,\\mu\\text{s}\\)  | \\(60\\,\\mu\\text{s}\\)  | \\(400\\,\\mu\\text{s}\\) | \\(3\\,\\text{s}\\)                       | \\(5\\,\\text{a}\\) | \\(63000\\,\\text{a}\\)
| 30      | \\(1\\,\\mu\\text{s}\\) | \\(3\\,\\mu\\text{s}\\) | \\(20\\,\\mu\\text{s}\\)  | \\(102\\,\\mu\\text{s}\\) | \\(900\\,\\mu\\text{s}\\) | \\(20\\,\\text{s}\\)                      | \\(28\\cdot 10^6\\,\\text{a}\\)
| 50      | \\(1\\,\\mu\\text{s}\\) | \\(4\\,\\mu\\text{s}\\) | \\(50\\,\\mu\\text{s}\\)  | \\(196\\,\\mu\\text{s}\\) | \\(2.5\\,\\text{ms}\\)   | \\(300\\,\\text{s}\\)                      |
| 100     | \\(1\\,\\mu\\text{s}\\) | \\(5\\,\\mu\\text{s}\\) | \\(100\\,\\mu\\text{s}\\) | \\(461\\,\\mu\\text{s}\\) | \\(10\\,\\text{ms}\\)    | \\(2\\,\\text{h}\\,46\\,\\text{min}\\)       | |
{: .eq}

## Problemas de clase P

Definición
: Un **problema de tiempo polinomial** o **de clase P** es un problema para el cual existe un algoritmo de orden polinomial que lo resuelva.
{: .d}

Ejemplo
: 1. El problema de encontrar el producto de dos elementos de Zn es un problema de
clase P.
1. M. Agrawal, N. Kayal y N. Saxena probaron en 2004 que determinar si un número
es o no primo es un problema de clase P.
{: .e}

## Problemas de clase NP

Definición
: Un **problema de clase NP** es un problema que puede ser resuelto con infinita potencia de cálculo y la respuesta puede verificarse en tiempo polinomial.
{: .d}

Ejemplo
: Encontrar la factorización de un entero es un problema de clase NP, dado que una vez
obtenidos los factores, la comprobación de la solución se puede obtener en tiempo
polinomial.
{: .e}

Problema abierto
: Una cuestión aún por resolver es si P=NP o si existe un problema de clase NP, que no
sea de clase P.
{: .}

## Seguridad del RSA

Lema
: Conocer los primos p y q de la factorización de la clave pública del RSA es equivalente
computacionalmente a conocer n y Φ(n).
{: .l}

Demostración
: Supongamos que conocemos n y Φ(n). Entonces n = pq y Φ(n) = (p - 1)(q - 1),
sistema de ecuaciones que puede resolverse en tiempo polinomial. El recíproco es
trivial.
{: .p}

## El problema RSA

Teorema
: Conocer la clave privada d que permite descifrar es computacionalmente equivalente
a factorizar.
{: .t}

Demostración
: Si p, q y e son conocidos, entonces es obvio que d se calcula muy fácilmente.
Sea ahora d la clave privada. De este modo, med-1 ≡n 1 (med ≡n m), para todo m tal
que mcd(m, n) = 1, de donde se tiene que Φ(n) divide a ed - 1. Sea pues
k = ed - 1 y escribamos k = 2t r , con r impar. Como p y q son impares,
Φ(n) = (p - 1)(q - 1) es divisible por 4 (al menos) y, de este modo, t ≥ 2. Sea ahora
g aleatorio tal que mcd(g, n) = 1 aleatorio y consideremos la sucesión:
t
g, g 2r , . . . g 2 r
i
i-1
Sea ahora i el menor entero tal que g 2 r ≡n 1, con lo que g 2 r 6≡n 1 si i ≥ 1.
i-1
Por el Teorema del resto chino, se tiene que Zn ∼
= Zp × Zq y dado que g 2 r es la raíz
i
i-1
cuadrada de g 2 r , entonces la imagen de g 2
(1, 1) ∈ Zp × Zq , es decir, (±1, ±1).
r
es una de las cuatro raíces de
i-1
En primer lugar (1, 1) no puede ser, porque se tiene que g 2 r 6≡n 1. En caso de que
i-1
i-1
sea (-1, -1), entonces mcd(g 2 r + 1, n) = n, ya que g 2 r ≡n -1. Finalmente, en
i-1
2
r
el caso de ser (-1, 1), se tendría que mcd(g+1, n) = p.
{: .p}




Ejercicio
: Determina \\(u,v\\in\\mathbb{Z}\\) que satisfacen la identidad \\(3120u+251v=\\operatorname{mcd}(3120,251).\\)
{: .ex}

Solución
: *\\[\\begin{align}3120&=251\\cdot12+108\\Rightarrow108=3120+251\\cdot(-12)\\\\ 251&=108\\cdot2+35\\Rightarrow35=251+108\\cdot(-2)\\\\ 108&=35\\cdot3+3\\Rightarrow3=108+35\\cdot(-3)\\\\ 35&=3\\cdot11+2\\Rightarrow2=35+3\\cdot(-11)\\\\ 3&=2\\cdot1+1\\Rightarrow1=3+2\\cdot(-1)\\end{align}\\]*{: .eq}
*\\[\\begin{align}1&=(3\\cdot 1+2\\cdot (-1))=(3\\cdot 1+(35+3\\cdot (-11))\\cdot (-1))=(3\\cdot 1+(35\\cdot (-1)+3\\cdot 11))\\\\&=(35\\cdot (-1)+3\\cdot 12)=(35\\cdot (-1)+(108+35\\cdot (-3))\\cdot 12)=(35\\cdot (-1)+(108\\cdot 12+35\\cdot (-36)))\\\\&=(108\\cdot 12+35\\cdot (-37))=(108\\cdot 12+(251+108\\cdot (-2))\\cdot (-37))=(108\\cdot 12+(251\\cdot (-37)+108\\cdot 74))\\\\&=(251\\cdot (-37)+108\\cdot 86)=(251\\cdot (-37)+(3120+251\\cdot (-12))\\cdot 86)=(251\\cdot (-37)+(3120\\cdot 86+251\\cdot (-1032)))\\\\&=(3120\\cdot 86+251\\cdot (-1069))\\end{align}\\]*{: .eq}
{: .s}



**Atención. Los siguientes dos ejemplos están pendientes de ser colocados en su correspondiente sección.**

Ejemplo sobre otro tema
: Sean \\(u\_1\\), \\(u\_2\\) y \\(u\_3\\) tres usuarios que comparten los siguientes parámetros con un servidor \\(s\\).
>Utilizaremos el teorema chino del resto. 
>Crearemos un criptosistema que para cifrar sea multiplicar por un número y describrar multiplicar por el inverso de dicho número.
>Supongamos que para cada \\(i\\in\\{1,2,3\\}\\), \\(u\_i\\) comparte con \\(s\\) un mensaje \\(m\_i\\in\\mathbb{Z}\\), \\(m\_i\\geq2\\), y una función \\(E\_i:\\mathbb{Z}\_{m\_i}\\to\\mathbb{Z}\_{m\_i}\\) dada por
*\\[ E(x)\\equiv\_{m\_i}a\_ix. \\]*{: .eq}
>Vamos a definir un esquema de envío de mensajes del tipo Secure Locker
>- \\(U\_1\\) comparte con \\(S\\): \\(m\_1=11,\\) \\(a\_1=6.\\)
- \\(U\_2\\) comparte con \\(S\\): \\(m\_2=13,\\) \\(a\_2=8.\\)
- \\(U\_3\\) comparte con \\(S\\): \\(m\_3=10,\\) \\(a\_3=7.\\)
>Supongamos que \\(s\\) quiere enviar un mensaje \\(c=4\\) a \\(u\_1\\), \\(u\_2\\) y \\(u\_3\\) de forma confidencial.
>\\(s\\) calcula:
>- \\(E\_1(4)\\equiv\_{11}6\\cdot4\\equiv\_{13}6\\equiv\_{11}2\\)
- \\(E\_2(4)\\equiv\_{13}8\\cdot4\\equiv\_{13}6\\equiv\_{13}6\\)
- \\(E\_3(4)\\equiv\_{10}7\\cdot4\\equiv\_{10}8\\)
*\\[\\left\\{\\begin{align} x&\\equiv\_{11}2 \\\\ x&\\equiv\_{13}6 \\\\ x&\\equiv\_{10}8 \\end{align}\\right.\\]*{: .eq}
*\\[\\begin{align} x\\end{align}\\]*{: .eq}
>Entonces, \\(s\\)
>- \\(u\_1\\) calcula \\(838\\equiv\_{11}\\)
- \\(u\_2\\) calcula \\(838\\equiv\_{13}6\\) y descifra \\(6\\), calculando
*\\[ 6\\cdot8^{-1}\\equiv\_{13}6\\cdot5\\equiv\_{13}4 \\]*
{: .e}

Ejemplo curva elíptica con CrypTool
: ECC Demonstration 1.1.1: Point addition on elliptic curves over discrete groups of prime numbers
>`a=11`, `p=20`, `p=71`
>`29*P`
>(28,46)  27  27*P
>~~~
>P=(28/46)
>11P=(41/5)
>R=11*P=(38/70)
>~~~
{: .e}
