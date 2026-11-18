---
modified: 2026-11-18T16:58:57Z
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
> 3. Con $n = 1$ es $\operatorname{Ber}(\frac{K}{N})$.
> 4. ([[Moda]]) La moda es $\left\lfloor \frac{(n+1)(K+1)}{N+2} \right\rfloor$ (dos modas si ese número es entero).

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
> 3. $f(1) = \frac{K}{N}$ y $f(0) = \frac{N-K}{N}$. $\blacksquare$
> 4. Simplificando coeficientes binomiales, $\frac{f(x+1)}{f(x)} = \frac{(K-x)(n-x)}{(x+1)(N-K-n+x+1)}$, y $f(x+1) \geq f(x)$ sii $x + 1 \leq \frac{(n+1)(K+1)}{N+2}$ (despejando); se concluye como en la [[Distribucion Binomial|binomial]]. $\blacksquare$

> [!example]- **Ejemplo 2.** (Control de calidad)
>
> Un lote de $100$ artículos tiene $10$ defectuosos. Un comprador revisa $5$ al azar y compra si encuentra menos de $2$ defectuosos. Con $X \sim \operatorname{Hipergeo}(100, 10, 5)$,
> $$
> P(\text{compra}) = f(0) + f(1) = \frac{\binom{90}{5} + \binom{10}{1}\binom{90}{4}}{\binom{100}{5}} \approx 0.923.
> $$

La media coincide con la de una binomial y la varianza casi: cuando la caja es enorme, sacar sin reemplazo es casi lo mismo que con reemplazo.

> [!theorem] **Proposición.** (Aproximación binomial)
>
> Sea $X_{N} \sim \operatorname{Hipergeo}(N, K_{N}, n)$ con $n$ fijo y $\frac{K_{N}}{N} \to p \in (0,1)$ cuando $N \to \infty$. Ent. para $x = 0, \dots, n$,
> $$
> \lim_{ N \to \infty } P(X_{N} = x) = \binom{n}{x}p^{x}(1-p)^{n-x}.
> $$

> [!proof]- **Proof.**
>
> Escribiendo los coeficientes binomiales como productos,
> $$
> P(X_{N} = x) = \binom{n}{x}\frac{K_{N}(K_{N}-1)\cdots(K_{N}-x+1)\cdot(N-K_{N})\cdots(N-K_{N}-n+x+1)}{N(N-1)\cdots(N-n+1)}.
> $$
> Hay $n$ factores arriba y $n$ abajo. Emparejándolos, cada $\frac{K_{N} - j}{N - j} \to p$ y cada $\frac{N - K_{N} - j}{N - x - j} \to 1 - p$ (el $n$ es fijo y $N \to \infty$), así que el producto tiende a $p^{x}(1-p)^{n-x}$. $\blacksquare$

> [!observation]+ **Observación.** (Comparada con la binomial)
>
> La media es la de una $\operatorname{Bin}(n, \frac{K}{N})$, pero la varianza tiene el factor $\frac{N-n}{N-1} < 1$ (**corrección por población finita**): sin reemplazo hay menos variación, porque cada objeto sacado cambia la caja. Si $N$ es mucho más grande que $n$, el factor es casi $1$, en línea con la Proposición.

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.6 (pp. 234–237) y Ejs. 335–341. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
