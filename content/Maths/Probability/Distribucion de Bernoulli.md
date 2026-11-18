---
modified: 2026-11-18T03:30:30Z
title: "Distribución de Bernoulli"
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
Un **ensayo Bernoulli** es aquel experimento aleatorio con únicamente dos posibles resultados: *éxito* o *fracaso*. Es el ladrillo con el que se construyen la [[Distribucion Binomial|binomial]], la [[Distribucion Geometrica|geométrica]] y la [[Distribucion Binomial Negativa|binomial negativa]].<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!tip|idea]- **Idea Intuitiva.**
>
> Cualquier pregunta de sí o no sobre un experimento es una Bernoulli: $X = \mathbb{1}_{A}$ (ver [[Variable Aleatoria]]), con $p = P(A)$.

Se define la v.a.
$$
X(\omega) = \begin{cases}
  1 & \text{ éxito } \\[0.5em]
  0 & \text{ fracaso }
\end{cases}
$$
y sean $p$ y $1-p$ las probabilidades de éxito y fracaso, respectivamente.

> [!theorem] **Definición.** ($\operatorname{Ber} (p)$)
>
> Sea $p \in (0,1)$. Decimos que $X \sim \operatorname{Ber} (p)$ si su función de probabilidad está dada por
> $$
> f(x) = \begin{cases}
>   1-p & x = 0 \\[0.5em]
>   p & x = 1 \\[0.5em]
>   0 &  \text{otro caso }
> \end{cases}
> $$
> De forma equivalente, $f(x) = p^{x}(1-p)^{1-x}$ si $x \in \{ 0,1 \}$.

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Ber}(p)$
> 1. $\operatorname{E}(X^{n}) = p$ para todo $n \geq 1$; en particular $\operatorname{E}(X) = p$.
> 2. $\operatorname{Var}(X) = p(1-p)$
> 3. $M(t) = 1 - p + pe^{t}$ y $G(t) = 1 - p + pt$.

> [!proof]- **Proof.**
>
> 1. $X^{n} = X$ porque $0^{n} = 0$ y $1^{n} = 1$, y $\operatorname{E}(X) = 0\cdot(1-p) + 1\cdot p$. $\blacksquare$
> 2. $\operatorname{Var}(X) = \operatorname{E}(X^{2}) - \operatorname{E}^{2}(X) = p - p^{2}$. $\blacksquare$
> 3. $\operatorname{E}(e^{tX}) = (1-p)e^{0} + pe^{t}$, y lo mismo con $t^{X}$. $\blacksquare$

> [!observation]+ **Observación.**
>
> $\operatorname{Var}(X) = p(1-p)$ es máxima en $p = \frac{1}{2}$ (la moneda más impredecible) y vale $0$ en los extremos, donde el resultado ya es seguro. Es el caso de igualdad de la cota $\operatorname{Var} \leq \frac{(b-a)^{2}}{4}$ de [[Varianza]].

Es un caso particular de la [[Distribucion Binomial|binomial]]: $\operatorname{Ber}(p) = \operatorname{Bin}(1,p)$.

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.2 (pp. 208–212). <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
