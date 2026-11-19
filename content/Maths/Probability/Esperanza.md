---
modified: 2026-11-18T22:38:38Z
title: "Esperanza"
publish: true
type: zettel
date: "2026-09-01"
status: seed
aliases:
tags:
 - probability
cssclasses:
 - romana
---
Una v.a. toma muchos valores, cada uno con su probabilidad. Para resumirla en un solo número, el más natural es el **promedio ponderado** de sus valores, pesando cada uno por qué tan probable es. Uno de los conceptos más importantes de toda la probabilidad.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!tip|idea]+ **Idea Intuitiva.**
>
> $\operatorname{E}(X)$ es el valor en el que se estabiliza el promedio de muchas observaciones de $X$. En la animación $X$ tiene densidad $f(x) = 2x$ en $(0,1)$ (Ejemplo 1.2): cada punto es una observación, cae al azar bajo la curva (más donde $f$ es alta) y su coordenada $x$ es el valor observado; $\bar{x}_{n}$ es el promedio de las primeras $n$ y el segmento rojo lo que le falta para llegar a $\operatorname{E}(X) = \frac{2}{3}$.
>
> <img src="/videos/esperanza-promedio.avif" alt="center" width="720" loading="lazy">
>
> Como fórmula es un centro de masa (con $f$ como densidad de masa total $1$, ver [[Centros de Masa para Actuarios]]); lo probabilístico es que ese número es al que tienden los promedios.

> [!Info]- **Nota!** (Esperanza, media y promedio)
>
> - $\operatorname{E}(X)$, la **media**, el **valor esperado** y $\mu$ son **lo mismo**: un número fijo que depende solo de la distribución de $X$. Por eso se dice indistintamente "la esperanza de $X$" o "la media de la exponencial", y en las notas se usan como sinónimos.
> - Lo que **no** es lo mismo es la **media muestral** (o promedio) de unos datos, $\bar{X} = \frac{1}{n}\sum_{i=1}^{n} X_{i}$: se calcula con observaciones, y es en sí misma una v.a. (cambia de una muestra a otra). La conexión entre las dos es la ley de los grandes números: $\bar{X}$ se acerca a $\operatorname{E}(X)$ conforme $n$ crece.
> - "Valor esperado" no quiere decir "el valor que esperamos que salga": $\operatorname{E}(X)$ puede no ser un valor posible de $X$. Con un dado, $\operatorname{E}(X) = 3.5$.
> - Tampoco es la única medida de "centro": la mediana y la moda son otras, y en general dan números distintos (ver [[Moda]] y [[Cuantiles]]).

> [!theorem] **Definición.** (Esperanza)
>
> Sea $X$ v.a. **discreta** con función de probabilidad $f(x)$. La **esperanza** de $X$ se define como
> $$
>\operatorname{E} (X) = \sum_{x} xf(x),
> $$
> suponiendo que esta suma es **absolutamente convergente**, i.e. la suma de los valores absolutos es convergente.
>
> Por otro lado, si $X$ es **continua** con función de densidad $f(x)$, entonces la esperanza es
> $$
> \operatorname{E} (X) = \int_{-\infty}^{\infty} xf(x) \, dx,
> $$
> suponiendo que esta integral es absolutamente convergente.
>
> Si para los dos casos no se cumple la condición de convergencia absoluta, ent. se dice que $\operatorname{E} (X)$ no existe, o que $X$ no tiene esperanza finita.
> Generalmente, suele denotarse $\operatorname{E} (X) = \mu$.

> [!example]- **Ejemplo 1.**
>
> 1. Un dado justo: $\operatorname{E}(X) = \frac{1}{6}(1 + 2 + \dots + 6) = \frac{21}{6} = 3.5$.
> 2. $X$ continua con $f(x) = 2x$ en $(0,1)$: $\operatorname{E}(X) = \int_{0}^{1} 2x^{2}\,dx = \frac{2}{3}$. La densidad pesa más cerca de $1$, y la media se recorre hacia allá.

> [!observation]+ **Observación.** (¿Por qué convergencia absoluta?)
>
> 1. Los valores de una v.a. discreta no traen un orden natural, y una serie que converge pero no absolutamente puede dar cualquier resultado si se reordena (teorema de Riemann). Pedir convergencia absoluta hace que $\operatorname{E}(X)$ no dependa del orden.
> 2. Hay v.a.s sin esperanza. Con $f(x) = \frac{1}{x(x+1)}$ para $x = 1, 2, \dots$ (es función de probabilidad: la suma es telescópica, $\frac{1}{x} - \frac{1}{x+1}$), $\sum x f(x) = \sum \frac{1}{x+1} = \infty$. En el caso continuo, la Cauchy (ver [[Distribucion t]]).

Muchas veces queremos la esperanza de $Y = \varphi(X)$. Por def. tendríamos $\operatorname{E}(Y) = \sum_{y} y\,f_{Y}(y)$, para lo cual necesitamos encontrar $f_{Y}(y)$, que en general no es fácil (ver [[Cambio de Variable Aleatoria]]). El siguiente resultado dice que no hace falta: basta conocer $f_{X}$.

> [!theorem] **Teorema.** (Teorema del Estadístico Inconsciente)
>
> Sea $X$ v.a. y sea $\varphi$ función tal que $\varphi(X)$ es una v.a. con esperanza finita. Entonces
> 1. si $X$ es discreta, $\displaystyle \operatorname{E} [\varphi (X)] = \sum_{x} \varphi (x)\,f_{X}(x)$;
> 2. si $X$ es continua, $\displaystyle \operatorname{E} [\varphi (X)] =  \int_{-\infty}^{\infty} \varphi(x) f_{X}(x) \, dx$.

> [!proof]- **Proof.**
>
> **Borrador.** En el caso discreto, cada valor $y$ de $Y$ junta la probabilidad de todos los $x$ con $\varphi(x) = y$; se reagrupa la suma por $x$.
>
> **Proof.** 1. Por el cambio de v.a. discreta, $\displaystyle f_{Y}(y) = \sum_{x \in \varphi^{-1}(y)} f_{X}(x)$. Ent.
> $$
> \begin{align}
> \operatorname{E}(Y) &= \sum_{y} y \sum_{x \in \varphi^{-1}(y)} f_{X}(x) = \sum_{y} \sum_{x \in \varphi^{-1}(y)} \varphi(x) f_{X}(x) \\[0.5em]
> &= \sum_{x} \varphi(x) f_{X}(x) \tag{reagrupando}
> \end{align}
> $$
> pues cada $x$ está en exactamente un $\varphi^{-1}(y)$. Reagrupar es válido porque la serie converge absolutamente. $\blacksquare$
>
> 2. Para $\varphi$ estrictamente monótona y diferenciable sale del cambio de v.a. continua con la sustitución $y = \varphi(x)$; la prueba general necesita teoría de la medida y la omitimos. $\blacksquare$

> [!example]- **Ejemplo 2.**
>
> Con el dado, $\operatorname{E}(X^{2}) = \frac{1}{6}(1 + 4 + \dots + 36) = \frac{91}{6}$, sin calcular la distribución de $X^{2}$. Con $f(x) = 2x$ en $(0,1)$, $\operatorname{E}(X^{2}) = \int_{0}^{1} 2x^{3}\,dx = \frac{1}{2}$.

Los resultados anteriores se pueden extender para el caso de $2$ o más v.a.s:

> [!theorem] **Proposición.**
>
> Sean $X,Y$ v.a.s definidas sobre un mismo esp. de prob. y sea $\varphi :\mathbb{R}^{2} \to  \mathbb{R}$ una función tq. $\varphi (X,Y)$ es una v.a. con esperanza finita. Si son continuas con función de densidad conjunta $f(x,y)$,
> $$
> \operatorname{E} [\varphi (X,Y)] = \int_{-\infty}^{\infty}\int_{-\infty}^{\infty} \varphi (x,y) f(x,y) \, dy \, dx,
> $$
> y si son discretas, el resultado es análogo,
> $$
> \operatorname{E} [\varphi (X,Y)] = \sum _{x} \sum_{y} \varphi (x,y) f(x,y).
> $$
> Su dem. es similar al caso con una sola variable (en el discreto, reagrupar por pares $(x,y)$).

Ahora, propiedades generales de la esperanza.

> [!theorem] **Teorema.** (Propiedades)
>
> Sean $X,Y$ v.a.s con esperanza finita y sean $a, b, c$ constantes. Entonces
> 1. $\operatorname{E} (c) = c$
> 2. $\operatorname{E} (cX) = c \operatorname{E} (X)$
> 3. $X\geq 0 \implies \operatorname{E} (X)\geq 0$
> 4. $\operatorname{E} (X+Y) = \operatorname{E} (X) + \operatorname{E} (Y)$
> 5. Monotonía: $X \leq Y \implies \operatorname{E}(X) \leq \operatorname{E}(Y)$
> 6. Si $a \leq X \leq b$, ent. $a \leq \operatorname{E}(X) \leq b$

> [!proof]- **Proof.**
>
> 1. La v.a. constante toma el valor $c$ con proba. $1$: $\operatorname{E}(c) = c \cdot 1$. $\blacksquare$
> 2. Por el estadístico inconsciente con $\varphi(x) = cx$, $\operatorname{E}(cX) = \sum_{x} cx\,f(x) = c\operatorname{E}(X)$ (igual con integrales). $\blacksquare$
> 3. Todos los términos $x f(x)$ (o el integrando $xf(x)$) son $\geq 0$. $\blacksquare$
> 4. Por la Proposición con $\varphi(x,y) = x + y$ (caso discreto; el continuo es igual con integrales),
> $$
> \operatorname{E}(X + Y) = \sum_{x}\sum_{y} (x + y) f(x,y) = \sum_{x} x f_{X}(x) + \sum_{y} y f_{Y}(y),
> $$
> usando que las marginales son $f_{X}(x) = \sum_{y} f(x,y)$ y $f_{Y}(y) = \sum_{x} f(x,y)$ ([[Independencia de Variables Aleatorias]]). $\blacksquare$
> 5. $Y - X \geq 0$, y por 3, 2 y 4, $0 \leq \operatorname{E}(Y - X) = \operatorname{E}(Y) - \operatorname{E}(X)$. $\blacksquare$
> 6. Es 5 con las constantes $a$ y $b$, y 1. $\blacksquare$

> [!observation]+ **Observación.**
>
> Por 2 y 4 la esperanza es **lineal**: $\operatorname{E}(aX + bY) = a\operatorname{E}(X) + b\operatorname{E}(Y)$, separa sumas y saca constantes. Pero **no** respeta productos ni funciones: en general $\operatorname{E}(XY) \neq \operatorname{E}(X)\operatorname{E}(Y)$ y $\operatorname{E}(\varphi(X)) \neq \varphi(\operatorname{E}(X))$ (p. ej. $\operatorname{E}(1/X) \neq 1/\operatorname{E}(X)$; ver [[Desigualdad de Jensen]]).

Veamos ahora una aplicación del concepto de indep. en el cálculo de la esperanza: para v.a.s independientes, la esperanza **sí** respeta productos.

> [!theorem] **Proposición.**
>
> Sean $X,Y$ v.a.s indep. y sean $g(x)$ y $h(y)$ funciones tq. $g(X)$, $h(Y)$ y $g(X)h(Y)$ son v.a.s con esperanza finita. Entonces,
> $$
> \operatorname{E} [g(X)h(Y)]= \operatorname{E} [g(X)] \cdot \operatorname{E} [h(Y)]
> $$
> En particular, con $g(x) = x$, $h(y) = y$: $\operatorname{E}(XY) = \operatorname{E}(X)\operatorname{E}(Y)$.

> [!proof]- **Proof.**
>
> Caso discreto. Por la Proposición y la independencia, $f(x,y) = f_{X}(x)f_{Y}(y)$, ent.
> $$
> \operatorname{E}[g(X)h(Y)] = \sum_{x}\sum_{y} g(x)h(y)f_{X}(x)f_{Y}(y) = \sum_{x} g(x)f_{X}(x) \sum_{y} h(y)f_{Y}(y).
> $$
> El caso continuo es igual con la densidad conjunta $f_{X}(x)f_{Y}(y)$ y Fubini. $\blacksquare$

> [!example]- **Ejemplo 3.** (El recíproco es falso)
>
> Sea $X$ uniforme en $\{ -1, 0, 1 \}$ y $Y = X^{2}$. Ent. $\operatorname{E}(X) = 0$ y $\operatorname{E}(XY) = \operatorname{E}(X^{3}) = 0$, así que $\operatorname{E}(XY) = \operatorname{E}(X)\operatorname{E}(Y)$. Pero no son independientes: $P(X = 0, Y = 1) = 0 \neq \frac{1}{3}\cdot\frac{2}{3}$. $Y$ está completamente determinada por $X$.

### Esperanza como área

Para v.a.s no negativas hay una fórmula que solo usa la función de distribución, y que muchas veces es más rápida que la definición: la esperanza es el área entre $F$ y la recta $y = 1$.

> [!tip|idea]+ **Idea Intuitiva.**
>
> $1 - F(x) = P(X > x)$; sumarlo sobre $x \geq 0$ cuenta cada valor $k$ de $X$ exactamente $k$ veces.
> ![[esperanza-area.svg|center|550]]

> [!theorem] **Proposición.** (Fórmula alternativa)
>
> 1. Si $X$ es discreta con valores en $\mathbb{N}$, ent. $\displaystyle \operatorname{E}(X) = \sum_{x=0}^{\infty} \left( 1 - F(x) \right) = \sum_{x=0}^{\infty} P(X > x)$.
> 2. Si $X \geq 0$ es continua, ent. $\displaystyle \operatorname{E}(X) = \int_{0}^{\infty} \left( 1 - F(x) \right) dx$.

> [!proof]- **Proof.**
>
> **Borrador.** Se escribe $P(X > x)$ como suma (o integral) de $f$ y se intercambia el orden; todo es $\geq 0$, así que se puede (Tonelli/Fubini).
>
> **Proof.** 1. Cambiando el orden de la suma doble (términos $\geq 0$),
> $$
> \sum_{x=0}^{\infty} P(X > x) = \sum_{x=0}^{\infty} \sum_{k=x+1}^{\infty} f(k) = \sum_{k=1}^{\infty} \sum_{x=0}^{k-1} f(k) = \sum_{k=1}^{\infty} k f(k) = \operatorname{E}(X). \tag*{$\blacksquare$}
> $$
> 2. Igual, con integrales y Fubini sobre la región $0 \leq x < u$:
> $$
> \int_{0}^{\infty} \int_{x}^{\infty} f(u) \, du \, dx = \int_{0}^{\infty} \int_{0}^{u} dx \, f(u) \, du = \int_{0}^{\infty} u f(u) \, du = \operatorname{E}(X). \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo 4.**
>
> 1. Si $F(x) = 1 - e^{-x}$ para $x > 0$ ([[Distribucion Exponencial]]), $\operatorname{E}(X) = \int_{0}^{\infty} e^{-x}\,dx = 1$, sin integrar por partes.
> 2. Si $X \in \{ 0,1,2,3 \}$ con $F(0) = \frac{1}{5}$, $F(1) = \frac{3}{5}$, $F(2) = \frac{4}{5}$, $F(3) = 1$: $\operatorname{E}(X) = \frac{4}{5} + \frac{2}{5} + \frac{1}{5} = \frac{7}{5}$.

> [!observation]+ **Observación.**
>
> Si $X$ también toma valores negativos, se resta el área de $F$ a la izquierda de $0$: $\operatorname{E}(X) = \int_{0}^{\infty} (1 - F(x))\,dx - \int_{-\infty}^{0} F(x)\,dx$.

---
Siguiente: [[Varianza]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 2, §2.6 (pp. 153–168) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
