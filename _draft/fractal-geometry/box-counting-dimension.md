---
layout: page
title: Dimensión box-counting
menu: fractal-geometry
comments: true
mathjax: true
---

## Medida de Lebesgue

Definición
: El **volumen \\(n\\)-dimensional** de un cubo \\([a_1,b_1]\\times\\cdots\\times[a_n,b_n]\\)
*\\[ \\mathrm{vol}^n([a_1,b_1]\\times\\cdots\\times[a_n,b_n]):=\\prod_{i=1}^n(b_i-a_i).\\]*{: .eq}
{: .d}

Definición
: La **medida de Lebesgue \\(n\\)-dimensional** de un conjunto \\(A\\) en \\(\\mathbb{R}^n\\) como
*\\[\\mathrm{vol}^n(A):=\\mathrm{ínf}\\left\\{\\sum_{i=1}^{\\infty}\\mathrm{vol}^n(A_i):A\\subseteq\\bigcup_{i=1}^\\infty A_i\\right\\}.\\]*{: .eq}
donde el ínfimo se toma sobre todos los recubrimientos por abiertos de \\(A\\) por cubos de la forma \\(A_i=[a_1,b_1]\\times\\cdots\\times[a_n,b_n]\\).
{: .d}

## Dimensión box-counting

Definición
: El **límite superior** de una función \\(f:\\mathbb{R}^+\\to\\mathbb{R}\\) es
*\\[\\underset{x\\to 0}{\\overline{\\mathrm{lı́m}}}f(x):=\\underset{r\\to 0}{\\mathrm{lı́m}}\\sup\\{f(y):0 < y < r\\}.\\]*{: .eq}
{: .d}

Definición
: El **límite inferior** de una función \\(f:\\mathbb{R}^+\\to\\mathbb{R}\\) es
*\\[\\underset{x\\to 0}{\\underline{\\mathrm{lı́m}}}f(x):=\\underset{r\\to 0}{\\mathrm{lı́m}}\\operatorname{ínf}\\{f(y):0 < y < r\\}.\\]*{: .eq}
{: .d}

Dado un conjunto no vacío y acotado \\(F\\) en \\(\\mathbb{R}^n\\), denotaremos por \\(N_{\\delta}(F)\\) al menor número de conjuntos con diámetro a lo sumo \\(\\delta\\) que recubren a \\(F\\).

<!--box-counting dimension-->
Definición
: La **dimensión box-counting superior** de un conjunto no vacío y acotado \\(F\\) en \\(\\mathbb{R}^n\\) es
*\\[\\underline{\\overline{\\mathrm{dim}}}_BF:=\\underset{\\delta\\to 0}{\\overline{\\mathrm{lı́m}}}\\frac{\\log N_{\\delta}(F)}{-\\log\\delta}.\\]*{: .eq}
{: .d}

<!--box-counting dimension-->
Definición
: La **dimensión box-counting inferior** de un conjunto no vacío y acotado \\(F\\) en \\(\\mathbb{R}^n\\) es
*\\[\\underline{\\mathrm{dim}}_BF:=\\underset{\\delta\\to 0}{\\underline{\\mathrm{lı́m}}}\\frac{\\log N_{\\delta}(F)}{-\\log\\delta}.\\]*{: .eq}
{: .d}

<!--box-counting dimension-->
Definición
: La **dimensión box-counting** de un conjunto no vacío y acotado \\(F\\) en \\(\\mathbb{R}^n\\) existe si, y solo si, \\(\\overline{\\mathrm{dim}}_BF=\\underline{\\mathrm{dim}}\_BF\\). En tal caso, la dimensión box-counting de \\(F\\) es
    *\\[\\mathrm{dim}_BF:=\\underset{\\delta\\to 0}{\\mathrm{lı́m}}\\frac{\\log N\_{\\delta}(F)}{-\\log\\delta}.\\]*{: .eq}
{: .d}

## Definiciones alternativas

En los siguientes dos teoremas, se recogen definiciones alternativas para la dimensión box-counting.

Teorema
: Si \\(F\\) es un conjunto no vacío y acotado en \\(\\mathbb{R}^n\\), entonces 
*\\[\\overline{\\mathrm{dim}}_BF:=\\underset{\\delta\\to 0}{\\mathrm{lı́m}}\\frac{\\log N'_{\\delta}(F)}{-\\log\\delta},\\qquad\\underline{\\mathrm{dim}}_BF=\\underset{\\delta\\to 0}{\\mathrm{lı́m}}\\frac{\\log N'_{\\delta}(F)}{-\\log\\delta}.\\]*{: .eq}
donde \\(N'_{\\delta}(F)\\) indica alguno de los siguientes valores:
1. El menor número de bolas cerradas de radio \\(\\delta\\) que recubren a \\(F\\).
2. El menor número de cubos de lado \\(\\delta\\) que recubren a \\(F\\).
3. El número de cubos en una rejilla de cubos de lado \\(\\delta\\) que cortan a \\(F\\).
4. El menor número de conjuntos con diámetro a lo sumo \\(\\delta\\) que recubren a \\(F\\).
5. El mayor número de bolas disjuntas de diámetro \\(\\delta\\) cuyos centros pertenecen a \\(F\\).
{: .t}

Definición
: El **\\(\\delta\\)-cuerpo** de un conjunto \\(F\\) en \\(\\mathbb{R}^n\\) es
*\\[F_{\\delta}:=\\{y\\in\\mathbb{R}^n:(\\exists x\\in F)(d(x,y)\\leq\\delta)\\},\\]*{: .eq}
donde \\(d\\) es la distancia euclídea sobre \\(\\mathbb{R}^n\\).
{: .d}

Teorema
: Si \\(F\\) es un conjunto no vacío y acotado en \\(\\mathbb{R}^n\\), entonces
*\\[\\underline{\\mathrm{dim}}_BF=n-\\underset{\\delta\\to 0}{\\overline{\\mathrm{lı́m}}}\\frac{\\log(\\mathrm{vol}^n(F))}{\\log\\delta},
\\qquad\\overline{\\mathrm{dim}}_BF=n-\\underset{\\delta\\to 0}{\\underline{\\mathrm{lı́m}}}\\frac{\\log(\\mathrm{vol}^n(F))}{\\log\\delta}.\\]*{: .eq}
{: .t}

Ejemplo
: La dimension box-counting del conjunto de Cantor es \\(\\frac{\\log2}{\\log3}\\).
{: .e}

## Propiedades

Teorema
:   1. \\(\\underline{\\dim}_B\\) y \\(\\overline{\\dim}_B\\) son monótonas, es decir, si \\(A\\subseteq B\\), entonces \\(\\dim_BA\\leq\\dim_BB\\).
2. \\(\\overline{\\dim}_B\\) es finitamente estable, es decir, 
*\\[\\overline{\\mathrm{dim}}_B(A\\cup B)=\\mathrm{máx}\\{\\overline{\\dim}_B(A),\\overline{\\dim}_B(B)\\},\\]*{: .eq} 
pero \\(\\underline{\\dim}_B\\) no lo es.
3.  Si \\(f:F\\to\\mathbb{R}^m\\) es una aplicación de Lipschitz, entonces \\(\\overline{\\dim}_Bf(F)\\leq\\overline{\\dim}_BF\\) y \\(\\underline{\\dim}_Bf(F)\\leq\\underline{\\dim}_BF\\).
4.  \\(\\overline{\\dim}_B\\) y \\(\\underline{\\dim}_B\\) son bi-Lipschitz invariantes, es decir, si \\(f:\\mathbb{R}^n\\to\\mathbb{R}^n\\) es una aplicación bi-Lipschitz, entonces \\(\\overline{\\dim}_Bf(F)\\leq\\overline{\\dim}_BF\\) y \\(\\underline{\\dim}_Bf(F)\\leq\\underline{\\dim}_BF\\). En particular, son invariantes por aplicaciones bi-Lipschitz
5.  \\(\\overline{\\dim}_BF=\\overline{\\dim}_B\\bar{F}\\) y \\(\\underline{\\dim}_BF=\\underline{\\dim}_B\\bar{F}\\).
6.  Si \\(\\overline{\\dim}_B\\) o \\(\\underline{\\dim}_B\\) tiene una propiedad, entonces \\(\\dim_B\\) también la tiene.
{: .t}

Definición
: Una aplicación \\(f\\) es una **similaridad** si, y solo si, existe \\(c\\in\\mathbb{R}^+\\) satisfaciendo \\(d(f(x),f(y))=c\\,d(x,y)\\). En tal caso, se dice que \\(c\\) es la **constante de similaridad** de \\(f.\\)
{: .d}

Corolario
: La dimensión box-counting se conserva por similaridades.
{: .c}

Ejemplo
: Si \\(F:=\\{0\\}\\cup\\left\\{\\frac{1}{2^{n}}:n\\in\\mathbb{N}\\right\\} \\), entonces \\(\\dim_BF=\\frac{1}{2}.\\)
{: .e}