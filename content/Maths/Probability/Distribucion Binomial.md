---
modified: 2026-11-18T16:57:55Z
title: "Distribución Binomial"
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
Supongamos que realizamos una serie de $n$ ensayos independientes Bernoulli en donde la probabilidad de éxito de cada ensayo es $p$, y contamos cuántos éxitos hubo. Ese conteo es la binomial: el modelo de cualquier "¿cuántos de $n$ cumplen?" con casos indep. e iguales.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!tip|idea]- **Idea Intuitiva.**
>
> Cada sucesión con $x$ éxitos y $n - x$ fracasos tiene proba. $p^{x}(1-p)^{n-x}$, y hay $\binom{n}{x}$ sucesiones así (las posiciones de los éxitos).

Denotemos $E = \text{éxito}$ y $F = \text{fracaso}$; el espacio muestral consiste de $OR_{n}^{2} = 2^{n}$ sucesiones. Definamos $X$ como la v.a. que indica el número de $E$ en cada sucesión, ent. $X$ toma valores $0,1,2,\dots,n$. La probabilidad de obtener $x$ éxitos y $n-x$ fracasos **en un orden fijo** es, por independencia,
$$
\underbrace{p\cdots p}_{x\text{-veces}} \underbrace{(1-p)\cdots (1-p)}_{n-x\text{-veces}} = p^{x}(1-p)^{n-x},
$$
y las diferentes formas en que los $x$ éxitos pueden distribuirse en los $n$ ensayos están dadas por el coef. binomial $\binom{n}{x}$.

> [!theorem] **Definición.** ($\operatorname{Bin} (n,p)$)
>
> Decimos que $X$ tiene una distribución binomial con parámetros $n$ y $p$, i.e. $X \sim \operatorname{Bin} (n,p)$, si
> $$
> f(x) = \begin{cases}
>   \binom{ n}{ x}p^{x}(1-p)^{n-x} & x \in \{ 0,\dots,n \} \\[0.5em]
>  0 & \text{otro caso }
> \end{cases}
> $$

> [!observation]+ **Observación.**
>
> Suma $1$ por el binomio de Newton: $\sum_{x=0}^{n}\binom{n}{x}p^{x}(1-p)^{n-x} = (p + (1-p))^{n} = 1$. De ahí el nombre.

> [!example]- **Ejemplo 1.**
>
> En $10$ volados justos, $P(X = 5) = \binom{10}{5}\frac{1}{2^{10}} = \frac{252}{1024} \approx 0.246$: el resultado más probable sale menos de una de cada cuatro veces. (Que $5$ es la moda lo dice la Propiedad 6: $\lfloor 11 \cdot \frac{1}{2} \rfloor = 5$. Con $9$ volados, $(n+1)p = 5$ es entero y hay dos modas, $4$ y $5$.)

La construcción dice exactamente que una binomial es una suma de Bernoullis, y esa es la forma más cómoda de trabajar con ella:

> [!theorem] **Proposición.**
>
> Sean $X_{1},\dots,X_{n}$ v.a.s independientes cada una con distribución $\operatorname{Ber} (p)$. Entonces,
> $$
> X_{1}+\dots+X_{n} \sim \operatorname{Bin} (n,p)
> $$
> Recíprocamente, toda variable aleatoria con distrib. $\operatorname{Bin} (n,p)$ tiene la misma distribución que una suma de la forma anterior.

> [!proof]- **Proof.**
>
> Por la f.g.p. ([[Funcion Generadora de Probabilidad]]): cada $X_{i}$ tiene $G(t) = 1 - p + pt$, así que la suma tiene $(1 - p + pt)^{n}$, cuyo coeficiente de $t^{x}$ es, por el binomio de Newton, $\binom{n}{x}p^{x}(1-p)^{n-x}$. El recíproco es lo mismo leído al revés. $\blacksquare$

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Bin} (n,p)$
> 1. $\operatorname{E} (X) = np$
> 2. $\operatorname{Var} (X) = np(1-p)$
> 3. $M(t) = (1 - p + pe^{t})^{n}$
> 4. Si $Y \sim \operatorname{Bin}(m, p)$ es indep. de $X$, ent. $X + Y \sim \operatorname{Bin}(n + m, p)$.
> 5. $n - X \sim \operatorname{Bin}(n, 1-p)$ (contar fracasos en vez de éxitos).
> 6. ([[Moda]]) $\frac{f(x+1)}{f(x)} = \frac{p}{1-p}\cdot\frac{n-x}{x+1}$, así que la moda es $\lfloor (n+1)p \rfloor$; si $(n+1)p$ es entero, hay dos modas, $(n+1)p - 1$ y $(n+1)p$.

> [!proof]- **Proof.**
>
> Con $X = X_{1} + \dots + X_{n}$ como en la Proposición:
> 1. Linealidad: $\operatorname{E}(X) = np$. $\blacksquare$
> 2. Las $X_{i}$ son indep., así que las varianzas se suman ([[Varianza]]): $np(1-p)$. $\blacksquare$
> 3. Producto de f.g.m. de indep.: $(1-p+pe^{t})^{n}$. $\blacksquare$
> 4. $X + Y$ es suma de $n + m$ Bernoullis indep. con el mismo $p$. $\blacksquare$
> 5. $f_{n-X}(y) = f_{X}(n-y) = \binom{n}{n-y}p^{n-y}(1-p)^{y} = \binom{n}{y}(1-p)^{y}p^{n-y}$. $\blacksquare$
> 6. El cociente sale de $\binom{n}{x+1} = \binom{n}{x}\frac{n-x}{x+1}$. Ent. $f(x+1) \geq f(x)$ sii $p(n-x) \geq (1-p)(x+1)$ sii $x \leq (n+1)p - 1$: $f$ crece mientras $x + 1 \leq (n+1)p$ y luego decrece, así que el máximo está en el mayor entero $\leq (n+1)p$, con empate si $(n+1)p$ es entero. $\blacksquare$

> [!observation]+ **Observación.**
>
> En 4 hace falta el **mismo** $p$: $\operatorname{Bin}(1, \frac{1}{2}) + \operatorname{Bin}(1, \frac{1}{4})$ toma el valor $2$ con proba. $\frac{1}{8}$, y ninguna binomial con $n = 2$ y media $\frac{3}{4}$ (i.e. $p = \frac{3}{8}$) da eso: $\left( \frac{3}{8} \right)^{2} = \frac{9}{64} \neq \frac{1}{8}$.

Cuando $n$ es grande y $p$ chico, la binomial se parece a una [[Distribucion de Poisson|Poisson]] con $\lambda = np$ (el resultado y la animación están en esa nota).

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.3 (pp. 213–220) y Ejs. 293–302. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
