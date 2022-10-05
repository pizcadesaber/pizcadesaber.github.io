---
layout: page
title: Notación posicional
menu: arithmetic
index: 3
comments: true
mathjax: true
---

La <<notación posicional>> es un sistema de numeración en el cual cada dígito posee un valor que depende de su posición relativa, la cual está determinada por la base, que es el número de dígitos necesarios para escribir cualquier número.

Definición
: Sea \\(b\\in\\mathbb{N}\\) tal que \\(b>1\\). Un número natural \\(n\\) **está expresado en base** \\(b\\) si, y solo si, existe un número \\(a:=a\_r\\cdots a\_1a\_0,\\) donde \\(a\_i\\) es el dígito de \\(a\\) en la posición \\(i\\)-ésima, tal que
*\\[n=\\sum\_{i=1}^ra\_ib^i. \\]*{: .eq}
Se denota por \\((a)\_b.\\)
{: .d}

Teorema
: Para todo \\(a\\in\\mathbb{Z}\\) y todo \\(b\\in\\mathbb{Z}^\\ast\\), existe \\(q,r\\in\\mathbb{Z}\\) únicos satisfaciendo las siguientes propiedades:
1. \\(a=bq+r.\\)
2. \\(0\\leq r<\|b\|.\\)
{: .t}

<!--Demostración
: Esta demostración la dividiremos en dos partes. Por un lado, la existencia de los enteros \\(q\\) y \\(r,\\) y por otro, la unicidad.
- **Existencia.** Observemos que se puede reducir la demostración de la existencia al caso \\(a\\geq 0\\) y \\(b > 0,\\) teniendo en cuenta lo siguiente:
> - Si \\(b<0,\\) entonces al considerar \\(b'=-b\\) y \\(q'=-q\\), la ecuación \\(a=bq+r\\) se puede escribir como \\(a=b'q'+r\\) y la desigualdad \\(0\\leq r < \|b\|\\) como \\(0\\leq r < \|b'\|.\\) Esto reduce la existencia del caso \\(b<0\\) al caso \\(b>0.\\)
> - Si \\(a < 0\\) and \\(b > 0,\\) entonces al considerar \\(a' = -a,\\) \\(q' = -q-1,\\) and \\(r' = b-r,\\), la ecuación a = bq + r may be rewritten as a' = bq' + r′, and the inequality 0 ≤ r < \|b\| may be rewritten as 0 ≤ r' < \|b\|. Esto reduce la prueba de la existencia al caso a ≥ 0 and b > 0 — which will be considered in the remainder of the proof.
> {: }
>Let q1 = 0 and r1 = a, then these are non-negative numbers such that a = bq1 + r1. If r1 < b then the division is complete, so suppose r1 ≥ b. Then defining q2 = q1 + 1 and r2 = r1 – b, one has a = bq2 + r2 with 0 ≤ r2 < r1. As there are only r1 non-negative integers less than r1, one only needs to repeat this process at most r1 times to reach the final quotient and the remainder. That is, there exist a natural number k ≤ r1 such that a = bqk + rk and 0 ≤ rk < |b|.
>This proves the existence and also gives a simple division algorithm for computing the quotient and the remainder. However, this algorithm is not efficient, since its number of steps is of the order of a/b.
- **Unicidad.** The pair of integers r and q such that a = bq + r is unique, in the sense that there can't be other pair of integers that satisfies the same condition in the Euclidean division theorem. In other words, if we have another division of a by b, say a = bq' + r' with 0 ≤ r' < |b|, then we must have that \\(q'=q\\) and \\(r'=r.\\)
>To prove this statement, we first start with the assumptions that
0 ≤ r < |b|
0 ≤ r' < |b|
a = bq + r
a = bq' + r'
>Subtracting the two equations yields
b(q – q′) = r′ – r.
>So b is a divisor of r′ – r. As
|r′ – r| < |b|
>by the above inequalities, one gets
r′ – r = 0,
>and
b(q – q′) = 0.
>Since b ≠ 0, we get that r = r′ and q = q′, which proves the uniqueness part of the Euclidean division theorem.
{: .p}-->

Teorema
: Todo número natural se puede expresar en cualquier base \\(b\\) de manera única, es decir, para todo \\(n\\in\\mathbb{N}\\), existe \\(r\\in\\mathbb{N}\\) y \\(a\_1,\\ldots,a\_n\\in\\mathbb{N}\\) satisfaciendo \\(0\\leq a\_i< b\\) para todo \\(i\\in\\{0,1,\\ldots,n\\}\\) y
*\\[n=\\sum\_{i=1}^ra\_ib^i. \\]*{: .eq}
{: .t}