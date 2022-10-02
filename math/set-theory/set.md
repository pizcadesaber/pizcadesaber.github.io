---
layout: page
title: Conjunto
menu: set-theory
comments: true
mathjax: true
---

<!--Set-->
Definición
: Un **conjunto** es una colección de objetos bien definida. Los objetos de un conjunto son llamados **elementos**. Cuando \\(a\\) es un elemento de un conjunto \\(A\\), se dice que \\(a\\) **pertenece** a \\(A\\), y se escribe \\(a\\in A\\). Se dice que un conjunto **contiene** a sus elementos.
{: .d}

Bien definida quiere decir que no hay duda de si un elemento pertenece o no al conjunto.

Los elementos pueden ser cualquier cosa: números, letras, colores, otros conjuntos, etc.

Los conjuntos se suelen denotar por letras mayúsculas y no importa el orden de sus elementos. Se pueden definir de dos maneras:
- **Por enumeración.** Enumerando o listando todos sus elementos separándolos por comas y entre llaves.
- **Por compresión.** Declarando la propiedad o propiedades que deben tener todos sus elementos.

Ejemplo
: El conjunto de las vocales del alfabeto se puede escribir:
- Por enumeración: \\(\\{a,e,i,o,u\\}\\).
- Por compresión: \\(\\{x:x\\text{ es una vocal del alfabeto}\\}\\).
{: .e}

En la anterior, expresión los dos puntos, <<:>>, significan <<tal que>>.

<!--Equals-->
Definición
: Dos conjuntos \\(A\\) y \\(B\\) son **iguales** si, y solo si, cada elemento de \\(A\\) está en \\(B\\), y viceversa. En tal caso, se escribirá \\(A=B\\).
{: .d}

Ejemplo
: Los conjuntos \\(\\{1,3\\}\\) y \\(\\{x\\in\\mathbb{R}:x^2-4x+3=0\\}\\) son iguales.
{: .e}

Ejemplo
: Como las soluciones reales de la ecuación \\(x^2-4x+3\\) son \\(1\\) y \\(3\\), entonces 
*\\[\\{x\\in\\mathbb{R}:x^2-4x+3=0\\}=\\{1,3\\}. \\]*{: .eq}
{: .e}

Ejemplo
: Los conjuntos \\(\\{1,2\\}\\) y \\(\\{1,\\{2\\}\\}\\) no son iguales, ya que \\(2\\not\\in\\{1,\\{2\\}\\}\\) (y \\(\\{2\\}\\not\\in\\{1,2\\}\\)).
{: .e}

<!--Universal set-->
Definición
: El **conjunto universal**, denotado por \\(\mathbb{U}\\), es el conjunto que contiene todos los objetos considerados.
{: .d}

<!--Empty set-->
Definición
: El **conjunto vacío**, denotado por \\(\\varnothing\\), es el conjunto que no tiene elementos.
{: .d}

<!--Cardinality-->
Definición
: El **cardinal** de un conjunto \\(A\\), denotado por \\(\|A\|\\), es el número de elementos de \\(A\\).
{: .d}

Según el número de elementos de un conjunto, se puede clasificar en dos tipos.

<!--Finite set-->
Definición
: Un **conjunto finito** es un conjunto \\(A\\) que satisface \\(\|A\|<\\aleph\_0\\).
{: .d}

<!--Infinite set-->
Definición
: Un **conjunto infinito** es un conjunto que no es finito.
{: .d}