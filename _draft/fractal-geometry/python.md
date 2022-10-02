---
layout: page
title: Prácticas con Python
menu: fractal-geometry
comments: true
mathjax: true
---

## Introducción

Problema 1: Cambio de base
: Define una función que tenga como entrada un número real entre 0 y 1 y devuelva una lista (o un array de `numpy` o similar) con las primeras 20 coordenadas de la representación del número en la base indicada.
{: .prob}

~~~python
def convert(x, base, length = 20):
    """Devuelve un número decimal entre 0 y 1 en la base especificada."""
    output=[]
    remainder=x
    a=0
    for i in range(length):
        b = int(remainder * base)
        output.append(b)
        a = b
        remainder = remainder * base - a
    return output
~~~

## Dimmensión box-counting

Los objetivos básicos a perseguir en esta práctica son los siguientes:
- Calcular la dimensión box-counting de un conjunto de puntos.
- Calcular la dimensión box-counting de una imagen.

Para abrir un archivo se usa el comando `open` y para cerrarlo (lo cual es aconsejable una vez que hayamos finalizado las operaciones necesarias con él) `close`.

Pongamos en práctica estos comandos utilizando [este archivo](sierpinski.txt), llamado `sierpinski.txt`. Observemos que este archivo texto contiene una gran lista de puntos en el plano.

Vamos a almacenar todas las líneas que contiene dicho archivo en una variable como lista. Para ello, usaremos el siguiente código:
~~~python
f = open('sierpinski.txt')
lines = f.readlines()
f.close()
~~~

Ya que tenemos los datos de este archivo, sigamos trabajando con él. Si usamos el comando `lines[:5]`, nos mostrará las primeras cinco líneas.

Pongamos como objetivo extraer los puntos de cada línea. Comencemos con la primera línea.

Si escribimos `a=eval(lines[0])`, definiremos `a` como el primer punto del conjunto. Podemos comprobar que se trata de una tabla, ejecutando el comando `type(a)`.

Una vez que hemos visto como extraer el primer punto del conjunto, vamos a dar el siguiente paso. Obtengamos todos los puntos y los almacenaremos en una lista. Para ello, ejecutaremos lo siguiente:

~~~python
points=[eval(line) for line in lines]
~~~

Podemos comprobar el tamaño de la lista con `len(points)`

Para poder visualizar de manera gráfica este conjunto de puntos, usaremos el siguiente código:

~~~python
from matplotlib import pylab
pylab.plot([x[0] for x in points],[x[1] for x in points],'.')
pylab.grid()
~~~

Para guardar la gráfica generada como un archivo PNG, escribiremos lo siguiente:

~~~python
pylab.savefig('sierpinski.png')
~~~

~~~python
import matplotlib.image as mpimg
img=mpimg.imread('sierpinski.png')
pylab.imshow(img)
~~~

### Dimensión box-counting de un conjunto de puntos



### Dimensión box-counting de una imagen



## Sistemas de funciones iteradas

Objetivos:

- Generar un conjuntos autosimilares y atractores de sistemas de funciones iteradas.
- Utiliza el teorema del Collage para aproximar un conjunto.

### Sec1

Se usa el teorema del punto fijo de Banach.

Tener en cuenta el operador de Hutchinson. Es una contracción y se trabaja en un espacio métrico completo.

Conjunto compacto y acotado de \\(\\mathbb{R}^2\\).


### Sec2

Corolario
: Si \\(E\\in\\mathcal{K}\_0(\\mathbb{R}^n)\\) y \\(\\varepsilon\\in\\R^+\\), entonces existen similiaridades \\(S\_1,...S\_m\\) tales que \\(d\_H(E,K)<\\varepsilon,\\) donde \\(K\\) es el conjunto autosimilar asociado.
{: .c}