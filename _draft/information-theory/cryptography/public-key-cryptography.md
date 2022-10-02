---
layout: page
title: Criptografía de clave pública # Public-key cryptography
menu: cryptography
index: 2
comments: true
mathjax: true
developing: true
---

## El intercambio de clave de Diffie-Hellman
En 1976, Whitfield Diffie y Martin Hellman, publican su artı́culo fundacional <<New
Directions in Crytography>> en el que solucionan el problema del intercambio de clave a
través de un canal inseguro introduciendo el conocido como Intercambio de Clave de
Diffie-Hellman.

<!--Figure: W. Diffie y M. Hellman-->

Intercambio de Clave de Diffie-Hellman
: 1. Alice y Bob acuerdan un primo \\(p\\) y un generador \\(g\\) del grupo multiplicativo \\(\\mathbb{Z}\_p^{\\ast}.\\) Después, llevan a cabo las siguientes acciones:
2. Alice y Bob escogen, respectivamente, \\(a,b\\in\\mathbb{Z}\\) tales que \\(1 < a,b < p-1\\) y hacen públicos los valores \\(g^a\\) y \\(g^b,\\) manteniendo cada uno de ellos \\(a\\) y \\(b\\) en privado.
3. Alice calcula \\((g^b)^a\\in\\mathbb{Z}\_p\\) y Bob, \\((g^a)^b\\in\\mathbb{Z}\_p^{\\ast}.\\)
3. Al finalizar, ambos comparten el valor común \\(g^{ab}\\in\\mathbb{Z}\_p^{\\ast}.\\)
{: .d .ol-number}

Como curiosidad, los nombres Alice y Bob se suelen a menudo en criptografía.

## Funciones de una vı́a

Definición <!--One-way function-->
: Sean \\(X\\) e \\(Y\\) dos conjuntos no vacı́os. Una **función de una vía** es una función \\(f:X\\to Y\\) tal que \\(f(x)\\) se puede calcular efectivamente para cualquier \\(x\\in X,\\) mientras que el cálculo de \\(x\\in X\\), dado \\(y\\in\\operatorname{Im}(f)\\) tal que \\(f(x)=y,\\) es prácticamente imposible.
{: .d}


Ejemplo
: Consideremos el conjunto \\(\\mathbb{Z}\_p^{\\ast}\\) y g, un generador del grupo multiplicativo \\(\\mathbb{Z}\_p^{\\ast}\\) y
\\(f:\\mathbb{N}\\to\\mathbb{Z}\_p^{\\ast}\\) definida por \\(f(n)\\equiv_pg^n.\\) En caso de que \\(p\\) sea lo suficientemente grande (\\(p > 2^{1024}\\)), entonces \\(f\\) es una función de una vı́a.
>Dados \\(g,g^a\\in\\mathbb{Z}\_p^{\\ast},\\) el número natural \\(a,\\) se denomina logaritmo discreto de \\(g^a\\in\\mathbb{Z}\_p^{\\ast}.\\) El
cálculo del mismo, se considera, por ahora, un problema computacionalmente difícil.
{: .e}

<dl class="e">
    <dt>Ejemplo</dt>
    <dd>
        Sea el conjunto \(Z\_2^{64}\) y consideremos las siguientes multiplicaciones en dicho conjunto.
        <ol>
            <li>La multiplicación componente a componente, considerando el conjunto \(\mathbb{Z}_2^{64}\) como una suma de copias de \(\mathbb{Z}_2.\) Denotaremos dicha multiplicación por \(\otimes.\)</li>
            <li>Sea la aplicación biyectiva ϕ : Z64i ai · 22 → Z264 definida por ϕ((ai )) =64Podemos entonces identificar Z2 con \(\mathbb{Z}_2^{64}\) y definir una segunda multiplicación en Z642 como la multiplicación en \(\mathbb{Z}_2^{64},\) la cual denotaremos por ·.</li>
            <li>Sea una base de \(\mathbb{F}_{2^{64}}\) como Z2 -espacio vectorial y consideramos la aplicación biyectiva que envı́a un elemento de \(\mathbb{Z}_2^{64}\) al vector de F264 cuyas componentes son precisamente la 64-tupla definida por dicho elemento. Como antes, podemos identificar ambos conjuntos y definir una nueva multiplicación en \(\mathbb{Z}_2^{64}\) (la de \(\mathbb{F}_{2^{64}}\)) que denotamos por \(\times.\)</li>
            <li>Sea \(\theta:\mathbb{Z}_2^{64}\to\mathbb{Z}\_2^{64}\) la función dada por \[ \theta((a_1,\ldots,a_{64})):=\begin{pmatrix} a_1 & \cdots & a_8 \\ a_9 & \cdots & a_{15} \\ \vdots & \ddots & \vdots \\ a_{57} & \cdots & a_{64} \end{pmatrix}. \]Denotamos la nueva multiplicación por \(\circ.\)</li>
        </ol>
        Sea \(x\in\mathbb{Z}\_2^{64}\) y definimos x0 = x, xt+1 = xt · xt + (xt ◦ xt ) ⊗ xt + xt × xt ,64t = 0, . . . , 4. Definimos f : Z642 → Z2 dada por f (x) = x1 ◦ x5 + (x2 ⊗ x3 ) · x4 .
    </dd>
</dl>

## Criptosistemas de clave privada

Definición
: Sean \\(M\\), \\(C\\) y \\(K\\) tres conjuntos, a los que nos referiremos por el espacio de mensajes,
el espacio de mensajes cifrados y el espacio de claves respectivamente. Un **criptosistema de clave privada** está compuesto por dos aplicaciones \\(\\varphi:M\\times K\\to C\\) y \\(\\psi:C\\times K\\to M\\), llamadas función de encriptado y desencriptado respectivamente, tales que \\(\\psi(\\varphi(m,k),k)=m\\) para todo \\(m\\in M\\) y \\(k\\in K.\\)
Para \\(m\\in M\\) fijo, la función \\(\\varphi\_m:K\\to C\\) definida por \\(\\varphi\_m(k)=\\varphi(m,k)\\) es una función de una vı́a.
{: .d}

## Aplicaciones de las funciones de una vı́a

Criptosistemas simétricos o de clave privada
: La definición anterior es un claro ejemplo de aplicación de las funciones de una vı́a. El
64 ejemplo previo aplicado sobre Z64
2 × Z2 se aplica en la definición de la
implementación Rinjdael del estándar actual de clave privada conocido como AES.
{: .}

Almacenamiento de contraseñas
: En UNIX, el criptosistema de clave privada DES (anterior estándar de clave privada)
se aplica hasta en 25 ocasiones para el cifrado y almacenamiento de una contraseña
de usuario. Esto se hace transformando una cadena de 64 ceros mediante dicho
algoritmo, usando como clave la propia contraseña del usuario.
{: .}

Funciones hash
: Sea X un conjunto infinito e Y un conjunto finito. Se usan funciones de una vı́a
ϕ : X → Y para proteger la información x ∈ X contra cambios, mediante el cálculo del
valor hash ϕ(x). Si se altera la información, x, el correspondiente valor hash de dicho
nuevo x será, con alta probabilidad, distinto del primero.
{: .}

Ejemplo
: Sea (G, ∗) un grupo finito tal que |G| = n ≥ 21000 en el que el cálculo a ∗ b ∈ G para
a, b ∈ G sea eficiente y sea e ∈ N. Definimos la aplicación f : G → G dada por
f (g) = g e para todo g ∈ G. Por el teorema de Lagrange, sabemos que g n = 1G para
todo g ∈ G.
>Supongamos que n es conocido y que e y n son coprimos. Entonces, por la identidad
de Bezout (usando el algoritmo extendido de Euclides) es posible obtener u, v ∈ Z
tales que eu + nv = 1.
>De este modo se tiene que f (g)u = (g e )u = g eu = g 1−nv = g ∗ (g n )−v = g ∗ 1G = g.
Si mcd(n,e)6= 1, entonces, con el método anterior se puede recuperar g mcd(n,e) , pero
no g, dado que f no es inyectiva.
{: .e}

## Funciones con puerta trasera

Definición <!--One-way trapdoor function-->
: Una **función con puerta trasera** es una función de una vı́a \\(f:X\\to Y\\) satisfaciendo los siguientes axiomas:
1. La función \\(f\\) es inyectiva.
2. Existe una cierta información adicional, la puerta trasera, que permite calcular eficientemente \\(f^{-1}:\\operatorname{Im}(f)\\to X.\\)
{: .d}

## Aplicaciones de las funciones de una vı́a con puerta trasera

En su artículo de 1976, Diffie y Hellman señalan las grandes aplicaciones que se tendrían en caso de conseguir definir una función de una vı́a con puerta trasera:

Intercambios de una clave secreta
: Alice publica una función de una vı́a f : X → Y . Si Bob quiere enviar un secreto,
k ∈ X a Alice, y que pudiera servir como clave para un criptosistema de clave secreta,
calcula f (k). Alicia, usando la puerta trasera, será capaz de calcular f −1 (f (k)) = k.
Notemos que, al ser f una función de una vı́a, una persona que conozca f (k) no podrá
calcular k sin hacer uso de la puerta trasera.
{: .}

Firmas digitales
: Si Alicia publica f : X → Y , una función de una vı́a con puerta trasera (esta última solo
conocida por Alice) a través de una entidad de confianza, una firma de un valor
y ∈ Im(f ), será f −1 (y), la cual solo podrá solo ser calculada por Alice. Esta firma
puede verificarse mediante la comprobación f (f −1 (y)) = y.
{: .}

Ejemplo
: Sea \\((G,\\ast)\\) un grupo finito, tal que \\(|G|=n\\) pueda ser calculado solo por la entidad que
diseña el sistema que estamos introduciendo. Sea ahora e tal que mcd(e, n) = 1.
Entonces la aplicación f : G → G dada por f (g) = g e es una función de una vı́a con
puerta trasera.
>En primer lugar, como en el ejemplo previo, existen u, v ∈ Z tales que eu + nv = 1.
Definimos pues f −1 : G → G dada por f −1 (h) = hu.
>Si f (g) = f (g 0 ), entonces g e = g 0e y, como en el ejemplo anterior, (g e )u = g, se sigue
que g = g 0 , es decir, f es inyectiva. El hecho de que f ◦ f −1 = IG se sigue como en
dicho ejemplo.
{: .e}