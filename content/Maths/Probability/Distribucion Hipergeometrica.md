---
modified: 2026-11-18T03:32:08Z
title: "Distribución Hipergeométrica"
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
Esta distrib. surge cuando tomamos una muestra **sin reemplazo** de un conjunto de objetos de dos tipos: piezas buenas y defectuosas, bolas de dos colores, los números de una lotería que sí salieron. Es la versión "sin reemplazo" de la [[Distribucion Binomial|binomial]].<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!tip|idea]- **Idea Intuitiva.**
>
> Se cuentan las muestras con exactamente $x$ objetos del primer tipo: se escogen $x$ de los $K$ y $n - x$ de los otros $N - K$, entre todas las $\binom{N}{n}$ muestras posibles.

Sup. que tenemos $N$ objetos dentro de una caja, de los cuales $K$ son de un primer tipo y $N-K$ de otro. De esta caja tomamos al azar una muestra de tamaño $n$, sin reemplazo y sin importar el orden, así que el espacio muestral tiene cardinalidad $\binom{N}{n}$ y todas las muestras son igual de probables ([[Medida de Probabilidad Clasica]]). Sea $X$ el núm. de objetos de la muestra que son del primer tipo.

> [!theorem] **Definición.** ($\operatorname{Hipergeo} (N,K,n)$)
>
> $X$ tiene una distrib. hipergeométrica con parámetros $N,K, n$ ($K \leq N$, $n \leq N$), i.e. $X \sim \operatorname{Hipergeo} (N,K, n)$, si
> $$
> f(x) = \frac{\binom{K}{x} \binom{N-K}{n-x}}{\binom{N}{n}}, \qquad x = 0,1,\dots,n,
> $$
> con la convención $\binom{a}{b} = 0$ si $b > a$.

> [!observation]+ **Observación.**
>
> 1. Por la convención, $f(x) > 0$ solo si $\max\{ 0, n - (N-K) \} \leq x \leq \min\{ n, K \}$: no se pueden sacar más objetos de un tipo de los que hay.
> 2. Que $f$ sume $1$ es la **identidad de Vandermonde**, $\sum_{x}\binom{K}{x}\binom{N-K}{n-x} = \binom{N}{n}$, que dice lo mismo contado de dos formas: escoger $n$ de $N$ objetos es escoger cuántos ($x$) y cuáles son del primer tipo.

> [!example]- **Ejemplo 1.** (Lotería)
>
> En una lotería se escogen $6$ números de $49$; tú marcaste $6$. El núm. de aciertos es $\operatorname{Hipergeo}(49, 6, 6)$ ($K = 6$ "buenos": los que marcaste), y
> $$
> P(X = 3) = \frac{\binom{6}{3}\binom{43}{3}}{\binom{49}{6}} \approx 0.0177.
> $$

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Hipergeo}(N,K,n)$
> 1. $\displaystyle \operatorname{E} (X) = n \frac{K}{N}$
> 2. $\displaystyle \operatorname{Var} (X) = n \frac{K}{N}\frac{N-K}{N}\frac{N-n}{N-1}$

> [!proof]- **Proof.**
>
> **Borrador.** Se escribe $X$ como suma de indicadoras, una por extracción (ordenando las extracciones). Cada una vale $1$ con proba. $\frac{K}{N}$, pero **no** son independientes: hay que calcular las covarianzas.
>
> **Proof.** Sea $I_{j} = 1$ si la $j$-ésima extracción es del primer tipo, ent. $X = I_{1} + \dots + I_{n}$. Por simetría, cada extracción es un objeto al azar de los $N$, así que $\operatorname{E}(I_{j}) = \frac{K}{N}$, y para $j \neq k$, $\operatorname{E}(I_{j}I_{k}) = \frac{K}{N}\cdot\frac{K-1}{N-1}$.
> 1. Linealidad: $\operatorname{E}(X) = n\frac{K}{N}$. $\blacksquare$
> 2. Con $p = \frac{K}{N}$, $\operatorname{Var}(I_{j}) = p(1-p)$, y desarrollando $\operatorname{E}(X^{2}) = \sum_{j}\operatorname{E}(I_{j}^{2}) + \sum_{j \neq k}\operatorname{E}(I_{j}I_{k})$,
> $$
> \begin{align}
> & \operatorname{Var}(X) \\[0.5em]
> &= np + n(n-1)\,p\,\frac{K-1}{N-1} - n^{2}p^{2} \\[0.5em]
> &= np(1-p)\,\frac{N-n}{N-1} \tag{álgebra}
> \end{align}
> $$
> El último paso es factorizar $np$ y simplificar $1 + (n-1)\frac{K-1}{N-1} - np = (1-p)\frac{N-n}{N-1}$. $\blacksquare$

> [!observation]+ **Observación.** (Comparada con la binomial)
>
> La media es la de una $\operatorname{Bin}(n, \frac{K}{N})$, pero la varianza tiene el factor $\frac{N-n}{N-1} < 1$ (**corrección por población finita**): sin reemplazo hay menos variación, porque cada objeto sacado cambia la caja. Si $N$ es mucho más grande que $n$, el factor es casi $1$ y la hipergeométrica se puede aproximar por la binomial: sacar sin reemplazo de una caja enorme es casi lo mismo que con reemplazo.

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.6 (pp. 234–237). <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
