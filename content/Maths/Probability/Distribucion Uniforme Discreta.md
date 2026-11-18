---
modified: 2026-11-18T16:57:55Z
title: "Distribución Uniforme Discreta"
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
Es el modelo de "todos los resultados son igual de probables" con un número finito de ellos: un dado justo, una carta al azar, un número de lotería. Es la [[Medida de Probabilidad Clasica|medida clásica]] vista como v.a.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!theorem] **Definición.** ($\operatorname{Unif}\{ x_{1}, \dots, x_{n} \}$)
>
> Sean $x_{1}, \dots, x_{n}$ números distintos. $X$ tiene distribución **uniforme discreta** en ellos si
> $$
>  f(x) = \begin{cases} 
>  \displaystyle  \frac{1}{n} & x \in \{ x_{1},\dots,x_{n} \} \\[0.5em]
>   0 & \text{ otro caso }
> \end{cases}
> $$
> El caso más usado es $\{ 1, \dots, n \}$, que escribimos $X \sim \operatorname{Unif}(n)$.

> [!theorem] **Teorema.** (Propiedades)
>
> 1. En general, $\operatorname{E}(X) = \frac{1}{n}\sum_{i} x_{i}$ (el promedio de los valores) y $\operatorname{Var}(X) = \frac{1}{n}\sum_{i} (x_{i} - \operatorname{E}(X))^{2}$.
>
> Sea $X \sim \operatorname{Unif} (n)$, con valores $1, \dots, n$:
> 2. $\displaystyle \operatorname{E} (X) = \frac{n+1}{2}$
> 3. $\displaystyle \operatorname{E} (X^{2}) = \frac{(n+1)(2n+1)}{6}$
> 4. $\displaystyle \operatorname{Var} (X) = \frac{n^{2}-1}{12}$
> 5. $G(t) = \dfrac{t(1-t^{n})}{n(1-t)}$ y $M(t) = \dfrac{e^{t}(1-e^{nt})}{n(1-e^{t})}$ ($t \neq 0$, resp. $t \neq 1$).

> [!proof]- **Proof.**
>
> 1. Es la definición de [[Esperanza]] y [[Varianza]] con $f(x_{i}) = \frac{1}{n}$. $\blacksquare$
> 2. $\frac{1}{n}\sum_{k=1}^{n} k = \frac{1}{n}\cdot\frac{n(n+1)}{2}$. $\blacksquare$
> 3. $\frac{1}{n}\sum_{k=1}^{n} k^{2} = \frac{1}{n}\cdot\frac{n(n+1)(2n+1)}{6}$. $\blacksquare$
> 4. Por 2 y 3,
> $$
> \begin{align}
> & \operatorname{Var}(X) = \dots \\[0.5em]
> \dots &= \frac{(n+1)(2n+1)}{6} - \frac{(n+1)^{2}}{4} \\[0.5em]
> &= \frac{(n+1)\left[ 2(2n+1) - 3(n+1) \right]}{12} \tag{factor.} \\[0.5em]
> &= \frac{(n+1)(n-1)}{12} \tag*{$\blacksquare$}
> \end{align}
> $$
> 5. Son sumas geométricas finitas: $\frac{1}{n}\sum_{k=1}^{n} t^{k} = \frac{t}{n}\cdot\frac{1-t^{n}}{1-t}$, y $M(t) = G(e^{t})$. $\blacksquare$

> [!example]- **Ejemplo 1.** (Dado)
>
> Con $n = 6$: $\operatorname{E}(X) = \frac{7}{2}$ y $\operatorname{Var}(X) = \frac{35}{12}$, lo mismo que se calculó a mano en [[Varianza]].

> [!observation]+ **Observación.**
>
> La fórmula 4 solo vale para valores **consecutivos** que empiezan en $1$. Para $\{ a, a+1, \dots, a+n-1 \}$ la varianza es la misma (recorrer no cambia la varianza) y la media se recorre a $\frac{n+1}{2} + a - 1$; para valores cualesquiera hay que usar 1. Su [[Funcion Generadora de Probabilidad|f.g.p.]] (valores $0, \dots, n-1$) es $\frac{1 - t^{n}}{n(1-t)}$.

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.1 (pp. 204–207) y Ejs. 271–278. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
