---
layout: page
title: Funciones hash
menu: cryptographic-protocols
index: 3
comments: true
mathjax: true
---

*Función hash* o *función resumen* es otra forma de llamar a la función de una vía.

Definición
: Una **función hash libre de colisiones débiles** es una función hash \\(h:X\\to Y\\) tal que para todo \\(x\\in X\\), resulta imposible calcular computacionalmente \\(x\_1\\in X\\setminus\\{x\\}\\) satisfaciendo \\(h(x\_1)=h(x).\\)
{: .d}

Definición
: Una **función hash libre de colisiones fuertes** es una función hash \\(h:X\\to Y\\) para la cual resulta imposible calcular computacionalmente \\(x\_1,x\_2\\in X\\) satisfaciendo \\(h(x\_1)=h(x\_2).\\)
{: .d}

Si \\(h\\) es libre de colisiones débiles y los valores están uniformemente distribuídos,
encontrar \\(x\_1\\) mediante una búsqueda aleatoria requiere \\(O(\|Y\|)\\) intentos.

Para el caso de funciones libres de colisiones fuertes, el número de intentos es \\(O(\\sqrt{\|Y\|}).\\)

## La función hash de Chaum-van Heijst-Pftizmann

Lema
: Sean \\(p\\) y \\(q\\) dos primos tales que \\(p=2q+1,\\) y \\(\\alpha\\) y \\(\\beta\\) dos generadores de \\(\\mathbb{Z}\_p.\\)
Identificando \\(\\mathbb{Z}\_q\\) con el conjunto \\(\\{0,1,\\ldots,q-1\\}\\subseteq\\mathbb{N},\\) la función \\(\\mathbb{Z}\_q\\times\\mathbb{Z}\_q\\to\\mathbb{Z}\_p^\\ast\\) definida por \\((x\_1,x\_2)\\mapsto\\alpha^{x\_1}\\beta^{x\_2}\\) es una función hash tal que encontrar una colisión es equivalente a resolver el logaritmo discreto \\(\\log\_{\\alpha}(\\beta).\\)
{: .l}

Demostración
: Sea \\(s = log\_{\\alpha}(\\beta).\\) Entonces, \\(\\alpha x\_1 \\beta x\_2=\\alpha^{x\_1}\\alpha^{sx\_2}\\) y
*\\[\\alpha^{x\_1+s}\\beta^{x\_2−1}=\\alpha^{x\_1}\\alpha^{s}\\alpha^{sx\_2}\\alpha^{-s}=\\alpha^{x\_1}\\alpha^ {sx\_2},\\]*{: .eq} 
por lo que \\((x\_1,x\_2)\\) tiene la misma imagen que \\((x\_1+s,x\_2-1).\\)
>Recíprocamente, sean \\((x\_1,x\_2)\\neq(x\_3,x\_4)\\) tales que \\(h(x\_1,x\_2)=h(x\_3,x\_4).\\) Luego, \\(\\alpha x\_1-x\_3=\\beta x\_4-x\_2.\\) Si \\(x\_2=x\_4,\\) entonces \\(x\_1=x\_3,\\) por identificar \\(\\mathbb{Z}\_q\\) con \\(\\{0,1,\\ldots,q-1\\}.\\) De aquí, \\(x\_1\\neq x\_3\\) y \\(x\_2\\neq x\_4.\\) Supongamos que \\(x\_4 > x\_2\\) y sea \\(d:=\\operatorname{mcd}(x\_4-x\_2,p-1).\\) Como \\(q > x\_4-x\_2\\leq 1\\) y \\(p-1=2q\\), entonces \\(d\\in\\{1,2\\}.\\)
>En caso de que \\(d = 1\\), para \\(y\\equiv_{p-1}(x\_4 − x\_2 )−1,\\) \\((\\beta^{x\_4-x\_2})^y=\\beta.\\) Además,
\\((\\beta^{x\_4-x\_2})^y=(\\alpha^{x\_1 −x\_3})^y\\), de donde \\((x\_1-x\_3)y=log\_{\\alpha}(\\beta).\\)
>Si \\(d=2\\), entonces \\(\\operatorname{mcd}(x\_4-x\_2,q)=1\\), dado que \\(p-1=2q.\\) Sea \\(y\\equiv\_q(x\_4-x\_2)-1.\\)
Si escribamos \\(y(x\_4-x\_2)=1+kq,\\) con \\(k\\in\\mathbb{Z},\\) entonces
*\\[ \\beta^{qk}\\beta\\equiv\_p\\beta^{qk+1}\\equiv\_p\\beta^{y(x\_4-x\_2)} \\]*{: .eq}
y \\(\\beta^{kq}\\equiv\_p\\pm1\\) (en realidad es \\((-1)^k\\)), ya que \\((\\beta^q)^2\\equiv_p \\beta^{p−1}\\equiv_p1.\\) De este modo, \\(log\_{\\alpha}(\\beta)\\in\\{(x\_4-x\_2)y,(x\_4-x\_2)y+q\\},\\) dependiendo de si \\(\\beta^{kq}\\equiv_p1\\) o \\(\\beta^{kq}\\equiv_{p}-1,\\) respectivamente.
{: .p}

## Construcciones de funciones hash

Construcción recursiva
: Sea \\(h:X\\to X\\) una función hash y sea \\(X^{\\ast}=\\bigcup\_{i=0}^{\\infty}X\\) y supongamos que \\(X\\) tiene definida una operación interna \\(\\ast.\\) Si se define la sucesión \\((h\_n(x\_1,\\ldots,x\_n))_{n\\in\\mathbb{N}}\\) como \\(h\_0(x\_1):=h(x\_1)\\) y \\(h\_{n+1}(x\_1,\\ldots,x\_n,x\_{n+1}):=h(x\_{n+1}\\ast h\_n(x\_1,\\ldots,x\_n ))\\) para todo \\(n\\in\\mathbb{N},\\) entonces \\(h^{\\ast}:X^{\\ast}\\to X\\) es una función hash.
{: .t}


Construcción basada en un criptosistema de clave simétrica
: Sean \\(\\mathcal{M}\\), \\(\\mathcal{C}\\) y \\(\\mathcal{K}\\) conjuntos biyectivos y sea \\(f:\\mathcal{M}\\times\\mathcal{K}\\to\\mathcal{C}\\) una función de encriptado. Entonces, la función \\(f\_m:K\\to\\mathcal{C}\\), dada por \\(f\_m(k):=f(m,k)\\), es una función de una vía. 
>Sea \\((k\_1,\\ldots,k\_n)\\in\\mathcal{K}^n.\\) Definimos la función \\(h\_n:\\mathcal{K}^n\\to\\mathcal{C}\\) como \\(h\_n(k\_1,\\ldots,k\_n):=y\_{n+1},\\) donde \\(y\_1:=m\\) y \\(y\_{i+1}:=f(y\_i,k\_i).\\) Entonces, \\(h^\\ast\\) es una función hash.
{: .t}

## Usos de la función hash

Message Authentication Code
: Sea \\(f:\\mathcal{M}\\times\\mathcal{K}\\to\\mathcal{C}\\) la función de encriptado de un criptosistema de clave simétrica y \\(h:\\mathcal{M}\\to\\mathcal{M}\\) una función hash. Entonces, \\(f\\circ h\\) produce, lo que se conoce como
un Message Authentication Code o MAC.
La verificación de un MAC se lleva a cabo exactamente de la misma forma que se
construye el mismo a partir del mensaje original.
{: .d}

Funcionamiento de firmas digitales
: Sea \\(f:X\\to Y\\) una función de una vía con puerta trasera y \\(h:X\\to Y\\) una función
hash. Entonces, \\(f^{-1}\\circ h\\) reproduce el verdadero funcionamiento de una firma digital.
Para verificar una firma digital, se calcula el valor hash del mensaje, \\(m\\) y este se
comprueba que \\((f\\circ f^{-1}\\circ h)(m)=h(m)\\).
{: .d}

## La paradoja del cumpleaños

Problema
: Encontrar el valor mínimo \\(k\\) para el que la probabilidad de que en un grupo de \\(k\\)
personas haya dos que tengan la misma fecha de cumpleaños.
{: .prob}

1. Para que no exista duplicidad, \\(k\\leq 365.\\)
2. Sea \\(N\\) el número de formas distintas en las que pueden obtenerse k\\) valores
distintos. Entonces \\(N=365\\cdot364\\cdots(365-k+1),\\) es decir,
\\(N=\\frac{365!}{(365-k)!.}\\)
3. Si hubiera duplicidades, entonces las posibilidades serían \\(365k.\\)
4. De este modo, la probabilidad de que en una reunión con \\(k\\) personas no existan
dos con el mismo cumpleaños es \\(N/365k,\\) es decir, que la probabilidad de que
haya dos personas con la misma fecha de cumpleaños es
*\\[ 1-\\frac{N}{365^k}=1-\\frac{365!}{(365-k)!\,365^k} \\]*{: .eq}
5. Para \\(k=23\\), dicha probabilidad es \\(0.5073.\\) Para \\(k=100\\) es de \\(0.9999997.\\)

Como podemos observar, entre una cantidad de 100 personas, se obtiene una probabilidad sorprendentemente alta.

Un ataque basado en la paradoja del cumpleaños
: 1. La fuente va a firmar un mensaje añadiendo un resumen de m bits.
2. El atacante genera \\(2^{\\frac{m}{2}}\\) variaciones del mensaje, todas ellas teniendo
esencialmente el mismo significado que el mensaje original. Prepara al mismo
tiempo un mismo número de mensajes, variaciones del fraudulento y que
sustituirá por el real.
3. Se comparan ambos conjuntos de mensajes para encontrar una pareja de
mensajes que produzcan el mismo hash.
4. El atacante ofrece la variación válida a la fuente para que la firme y se añade a la versión fraudulenta encontrada del mensaje.
{: .d.ol-number}