---
layout: page
title: Código cíclico
menu: cyclic-code
index: 1
comments: true
mathjax: true
developing: true
---

## Definición

Definición
: Un código C es cı́clico si y solo si C es un código lineal y si además, para cualquier palabra (a0 , a1 , . . . , an−2 , an−1 ) ∈ C se tiene que (an−1 , a0 , . . . , an−2 ) ∈ C.
{: .d}

Ejemplo
: 1. C = {000, 101, 011, 110} es un código cı́clico.
2. C = {0000, 1001, 0110, 1111} es un código equivalente al código
C 0 = {0000, 1010, 0101, 1111}, que es un código cı́clico.
{: .e}

## Identificación en anillos de polinomios

Sea f (x) = x n − 1 en GF (q)[x] y consideremos el anillo cociente GF (q)[x]/(x n − 1). Entonces se tiene que x n ≡x n −1 1, de donde para reducir cualquier polinomio módulo x n − 1 nos basta reemplazar x n por 1, x n+1 por x, etc.

Entonces, dado un vector (a0 , a1 , . . . an−1 ) en GF (q)n , podemos identificarlo con el vector a(x) = a0 + a1 x + · · · + an−1 x n−1 ∈ GF (q)[x]/(x n − 1), lo que produce un isomorfismo de espacios vectoriales.

Pero además, si multiplicamos a(x) por el polinomio x, se tiene
xa(x) = a0 x + a1 x 2 + · · · + an−1 x n , el cual, es congruente módulo x n − 1 con el polinomio
an−1 + a0 x + · · · + an−2 x n−1.

De este modo, si a = (a0 , a1 , . . . an−1 ) es una palabra de un código cı́clico C, entonces (an−1 , a0 , . . . , an−2 ) vuelve a ser una palabra de dicho código C, lo que en términos de la identificación de a con
a(x) = a0 + a1 x + · · · + an−1 x n−1 ∈ GF (q)[x]/(x n − 1), 
equivale a decir que la palabra a0 se corresponde con el producto xa(x) en GF (q)[x]/(x n − 1).

## Caracterización códigos cı́clicos

Teorema
: Un subconjunto C ⊆ GF (q)[x]/(x n − 1) es un código cı́clico si y solo si es un ideal.
{: .t}

## Estructura códigos cı́clicos

Teorema
: Sea C un código cı́clico. Entonces:
1. Existe un único polinomio mónico g(x) de menor grado en C.
2. C = hg(x)i.
3. g(x) es un factor de x n − 1.
{: .t}

Demostración
: 1. Supongamos que existen dos polinomios mónicos en C de menor grado r , g1 (x)
y g2 (x). Entonces g1 (x) − g2 (x) es un polinomio de grado menor o igual que
r − 1, que multiplicado por el inverso del coeficiente lı́der del mismo produce un
polinomio de menor grado que r y mónico.
1. Sea g(x) el polinomio mónico de menor grado de C y sea r = deg(g(x)).
Consideremos ahora a(x) ∈ C. Entonces a(x) = g(x)q(x) + r (x), de donde
r (x) = a(x) − g(x)q(x) ∈ C
dado que a(x) ∈ C y g(x)q(x) ∈ C por ser C un ideal. De este modo, si multiplicamos r (x) por el inverso de su coeficiente lı́der,
se tiene que existe un polinomio mónico de grado menor que r , de donde se sigue que C = hg(x)i.
3. Sea x n − 1 = g(x)q(x) + r (x). Si reducimos módulo x n − 1, se sigue que
r (x) ≡x n −1 g(x)q(x) ∈ C, de donde por el mismo razonamiento anterior, existe
un polinomio mónico de menor grado que g(x) en C y ası́, se sigue que r (x) = 0.
{: .p}

## Polinomio generador

Definición
: Sea C un código cı́clico y sea C = hg(x)i. Entonces g(x) se denomina polinomio
generador de C.
{: .d}

Lema
: Sea g(x) = g0 + g1 x + · · · + gk x k un polinomio generador de un código cı́clico.
Entonces g0 6= 0.
{: .l}

Demostración
: Supongamos que g0 = 0. Entonces x n−1 g(x) = x −1 g(x) es un polinomio mónico de
grado k − 1, lo cual es absurdo.
{: .p}

## Ejemplo

Vamos a calcular todos los códigos binarios cı́clicos de longitud 3. Sea pues el polinomio x 3 − 1 ∈ GF (2)[x]. Entonces
x 3 − 1 = (x + 1)(x 2 + x + 1) De este modo, los divisores, son {1, x + 1, x 2 + x + 1, x 3 − 1}, con lo que los correspondientes códigos cı́clicos son
1. h1i = GF (2)[x]/(x 3 − 1) = {0, 1, x, 1 + x, x 2 , 1 + x 2 , x + x 2 , 1 + x + x 2 }, o lo que es lo mismo, {000, 100, 010, 110, 001, 101, 011, 111}.
1. h1 + xi = {0, 1 + x, x + x 2 , 1 + x 2 }, es decir, {000, 110, 011, 101}.
2. h1 + x + x 2 i = {0, 1 + x + x 2 }, o equivalentemente {000, 111}.
3. hx 3 − 1i = 0, que es el código {000}.