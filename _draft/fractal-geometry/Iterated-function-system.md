---
layout: page
title: Sistemas iterativos de funciones
menu: fractal-geometry
next: next-page
previous: previous-page
comments: true
mathjax: true
developing: true
---

## Hiperespacio

En lo sucesivo, dado un espacio métrico \\((X,d)\\), \\(A\\subseteq X\\) y \\(\\varepsilon\\in\\mathbb{R}^+\\), consideraremos la siguiente notación:
- \\(\\mathcal{P}\_0(X)\\) es la familia formada por todos los subconjuntos no vacíos de \\(X.\\)
- \\(\\mathcal{C}\_0(X)\\) es la familia formada por todos los subconjuntos cerrados no vacíos de \\(X.\\)
- \\(\\mathcal{K}\_0(X)\\) todos los subconjuntos compactos no vacíos de \\(X.\\)
- \\(d(x,A):=\\operatorname{ı́nf}\\{d(x,y):y\\in A\\}.\\)
- \\(B\_{\\varepsilon}(A):=\\{x\\in X:d(x,A)<\\varepsilon\\}.\\)
- \\(\\overline{B}\_{\\varepsilon}(A):=\\{x\\in X:d(x,A)\\leq\\varepsilon\\}.\\)

Definición
: Sea \\((X,d)\\) un espacio métrico y \\(A,B\\in\\mathcal{P}_0(X)\\). Definimos la función \\(D:\\mathcal{P}_0(X)\\times\\mathcal{P}_0(X)\\to\\mathbb{R}\_0^+\\) 
*\\[D(A,B):=\\sup\\{d(x,B):x\\in A\\}.\\]*{: .eq} Una pseudométrica
D(A, B) = sup{d(x, B) : x ∈ A}. (casi-pseudo-métrica de
Hausdorff)
dH (A, B) = máx{D(A, B), D(B, a)} (pseudo-métrica de
Hausdorff).
{: .d}

Lema
: Sea \\((X,d)\\) un espacio métrico y \\(A,B,C\\in\\mathcal{P}_0(X)\\).
Si \\(A\\subseteq B\\) entonces \\(D(A,B)=0\\)
D(A, B) = D(A, B).
Si \\(D(A,B)=0\\), entonces \\(A\\subseteq B.\\)
\\(D(A,B)\\leq D(A,C)+D(C,B).\\)
{: .l}

Lema
: Sea \\((X,d)\\) un espacio métrico, \\(A,B,C\\in\\mathcal{P}_0(X)\\) y \\(\\varepsilon,\\delta\\in\\mathbb{R}^+.
Si \\(A\\subseteq B\_{\\varepsilon}(C)\\) y \\(C\\subseteq B\_{\\delta}(B) entonces \\(A\\subseteq B\_{\\varepsilon+\\delta}(B).
- \\(d\_H(A,B) ≤ ε\\) si y sólo si A ⊆ B[B, ε]\\) y \\(B ⊆ B[A, ε]\\).
- \\(d\_H(A,B)=\\operatorname{ı́nf}\\{\\varepsilon>0:A\\subseteq B\_\\varepilon(B),\\;B\\subseteq\\overline B\_\\varepilon(A)\\}\\).
- \\(d\_H(A,B)=d\_H(A,B)\\).
- \\(d\_H(A,B)=0\\) si y solo si \\(A = B\\).
- \\(d\_H(A,B)≤d\_H(A,C)+d\_H(C,B)\\).
{: .l}

Teorema
: dH es una métrica en C0 (X ) y en K0 (X ) y una pseudo-métrica en
P0 (X ).

Definición:
(K0 (X ), dH ): hiperespacio de X .
{: .t}

Lema
: Sea K ∈ K0 (X ) y x ∈ X . Entonces existe y ∈ K tal que
d(x, K ) = d(x, y ).
Sea (xn ) una sucesión de Cauchy. Entonces existe una
1
subsucesión σ tal que d(xσ(n) , xσ(n−1) ) < 2n−1
para todo
n ∈ N.
1
Sea (yn ) una sucesión tal que d(yn , yn−1 ) < 2n−1
para todo
1
n ∈ N. Entonces d(yn , yn+h ) < 2n−1 , para todo h ∈ N.
{: .l}

Teorema de Zeron-Morita
: Si \\((X,d)\\) un espacio métrico completo, entonces \\((\\mathcal{K}_{0}(X ),d_H)\\) es un espacio métrico completo.
{: .t}

## Conjuntos autosimilares

Recordatorio
Definición (aplicación contractiva)
Sean (X , d) e (Y , ρ) dos espacios métricos y f : X → Y una
aplicación. Se dice que f es contractiva o que f es una contracción
si existe un número (el factor de contracción) 0 ≤ c < 1 tal que
ρ(f (x), f (y )) ≤ cd(x, y ), para todo x, y ∈ X.

Definición (punto fijo)
Sean (X , d) un espacio métrico y f : X → X una aplicación. Se
dice que x es un punto fijo de f si f (x) = x.
Teorema (del punto fijo de Banach)
Sean (X , d) un espacio métrico completo y f : X → X una
contracción. Entonces f tiene un único punto fijo x0 ∈ X . Además,
si x ∈ X entonces f n (x) → x0 .

Definición (operador de Hutchinson)
Sea {f1 , . . . , fm } un conjunto finito de contracciones en un espacio
métric (X , d). Se llama operador de Hutchinson
a la aplicación
S
f : K0 (X ) → K0 (X ) dada por f (A) = m
f
(A).
i=1 i

Proposición
El operador de Hutchinson es una contracción en el hiperespacio
(K0 (X ), dH ).

Definición (sistema de funciones iteradas)
Sea {f1 , . . . , fm } un conjunto finito de contracciones en un espacio
métrico completo (X , d). El par (X , {f1 , . . . , fm }) se llama sistema
de funciones iteradas (IFS).
Sea (X , {f1 , . . . , fm }) un sistema de funciones iteradas, entonces el
operador de Hutchinson es una contracción en el hiperespacio
(K0 (X ), dH ). Por el Teorema de Zenor-Morita, el hiperespacio es
completo, por lo que aplicando el Teorema del
S punto fijo de Banach
existe un único K ∈ K0 (X ) tal que f (K ) = m
i=1 fi (K ) = K .

Definición (atractor de un sistema de funciones iteradas)
K se llama atractor del sistema de funciones iteradas. Cuando las
aplicaciones fi son similaridades (d(fi (x), fi (y )) = ci d(x, y )), se
dice que K es un conjunto autosimilar.

Observación. Por el Teorema del punto fijo de Banach, sabemos que si \\(E\\) es cualquier compacto no vacı́o, entonces \\(f^n(E)\\) converge al atractor \\(K\\).

## Dimensión de conjuntos autosimilares

Definición
: Sea {(X , {f1 , . . . , fm }) un sistema de funciones iteradas. Se dice
que el sistema de funciones iteradas verifica la condición de
conjunto abierto (OSC) si existe un abierto V de X tal quei:
fi (V ) ∩ fj (V ) = ∅ para todo i 6= j.
S
f (V ) = m
i=1 fi (V ) ⊆ V .
Se dice que {(X , {f1 , . . . , fm }) verifica la propiedad fuerte de
conjunto abierto (SOSC) si además V ∩ K 6= ∅.
{: .d}

Teorema de Moran
: Sea \\(\\left(\\mathbb{R}^n,\\left\\{f_i\\right\\}_{i=1}^m\\right)\\) un sistema de funciones iteradas, donde las \\(f_i\\) son similaridades con factor de similaridad \\(c_i\\). Si \\(K\\) es el conjunto autosimilar asociado, entonces
*\\[\\mathrm{dim}_H(K)=\\mathrm{dim}_B(K)=s, \\]*{: .eq}
donde \\(s\\) es la solución de la ecuación \\(\\sum_{i=1}^mc_i^s=1\\). Además, \\( 0 < H^s(K) < +\\infty \\).
{: .t}

Teorema del collage
: Sea \\(\\left(\\mathbb{R}^n,\\left\\{f_i\\right\\}_{i=1}^m\\right)\\) un sistema de funciones iteradas. Si \\(c\\) es el máximo de los factores de contracción de las funciones \\(\\{f_i\\}_{i=1}^m\\), entonces para todo \\(E\\in\\mathcal{K}_0(X)\\),
*\\[d_H(E,K)\\leq\\frac{d_H(E,f(E))}{1-c}, \\]*{: .eq}
donde \\(K\\) es el atractor del sistema de funciones iteradas.
{: .t}

Corolario
: Sea \\(E\\in\\mathcal{K}_0(\\mathbb{R}^n)\\) y \\(\\varepsilon\\in]0,+\\infty[\\). Entonces, existen unas similaridades \\(S_1,\\ldots,S_m\\) satisfaciendo \\(d_H(E,K)<\\varepsilon\\), donde \\(K\\) es el conjunto autosimilar asociado.
{: .c}
