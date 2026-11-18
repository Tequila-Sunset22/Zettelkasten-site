---
modified: 2026-11-17T22:20:24Z
title: "Método de la Transformada Inversa"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Transformada Inversa
 - Transformada Integral de Probabilidad
tags:
 - probability
cssclasses:
 - romana
---
Una computadora sabe generar números "al azar" uniformes en $(0,1)$, y nada más. ¿Cómo simula entonces una exponencial, una normal o una binomial? Con los [[Cuantiles]]: si leemos una altura uniforme al revés en la gráfica de $F$, obtenemos una v.a. con distribución exactamente $F$. Es la base de toda la simulación (Monte Carlo), y su recíproco, que $F(X)$ es uniforme, es de donde salen los p-valores en estadística.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> Con una sola uniforme se fabrica cualquier distribución.

Recordemos de [[Cuantiles]] que $c_{p} = \min \{ x \mid F(x) \geq p \}$ existe para $p \in (0,1)$ y que
$$
F(x) \geq p \iff x \geq c_{p}.
$$
Esa equivalencia es todo lo que hace falta.

> [!tip|idea]- **Idea Intuitiva.**
>
> Donde $F$ sube rápido hay mucha probabilidad, y ahí cae $c_{U}$ más seguido; en un tramo plano no cae nunca.

> [!theorem] **Teorema.** (Transformada inversa)
>
> Sea $F$ una función de distribución y sea $U \sim \operatorname{Unif}(0,1)$ (ver [[Distribucion Uniforme Continua]]). Ent. la v.a. $X = c_{U}$ tiene función de distribución $F$.

> [!proof]- **Proof.**
>
> **Borrador.** La equivalencia $c_{u} \leq x \iff u \leq F(x)$ convierte el evento sobre $X$ en un evento sobre $U$, cuya probabilidad es su longitud.
>
> **Proof.** Con probabilidad $1$, $U \in (0,1)$, y ahí $c_{U}$ existe. Sea $x \in \mathbb{R}$. Para $u \in (0,1)$ se tiene $c_{u} \leq x \iff F(x) \geq u$. Ent.
> $$
> \begin{align}
> & P(X \leq x) \\[0.5em]
> &= P(c_{U} \leq x) \\[0.5em]
> &= P(U \leq F(x)) \tag{equivalencia} \\[0.5em]
> &= F(x) \tag{$U$ uniforme}
> \end{align}
> $$
> donde la última igualdad usa que $P(U \leq u) = u$ para $u \in [0,1]$. $\blacksquare$

Para usarlo hay que poder despejar $c_{p}$. Cuando $F$ es continua y estrictamente creciente, $c_{p} = F^{-1}(p)$ y basta resolver $F(x) = p$:

> [!example]- **Ejemplo 1.** (Exponencial)
>
> Para $X \sim \operatorname{Exp}(\lambda)$, $F(x) = 1 - e^{-\lambda x} = p$ da $c_{p} = -\frac{1}{\lambda}\ln(1-p)$. Ent.
> $$
> -\frac{1}{\lambda}\ln(1-U) \sim \operatorname{Exp}(\lambda).
> $$
> Como $1 - U$ también es uniforme en $(0,1)$, es común usar $-\frac{1}{\lambda}\ln U$, que tiene la misma distribución.

> [!example]- **Ejemplo 2.** (Weibull)
>
> Para $X \sim \operatorname{Weibull}(\alpha, \lambda)$, $F(x) = 1 - e^{-(\lambda x)^{\alpha}}$ para $x > 0$. Despejando $1 - e^{-(\lambda c_{p})^{\alpha}} = p$,
> $$
> c_{p} = \frac{1}{\lambda}\left( -\ln(1-p) \right)^{1/\alpha}, \qquad \text{así que} \qquad \frac{1}{\lambda}\left( -\ln(1-U) \right)^{1/\alpha} \sim \operatorname{Weibull}(\alpha, \lambda).
> $$
> Con $\alpha = 1$ se recupera el Ejemplo 1 (ver [[Distribucion Weibull]]).

El teorema no pide que $F$ sea continua: para una v.a. discreta, $c_{U}$ es una función escalonada de $U$, y el método se vuelve "partir $(0,1)$ en pedazos de longitud $f(x)$":

> [!example]- **Ejemplo 3.** (Bernoulli y cualquier discreta)
>
> Para $X \sim \operatorname{Bernoulli}(p)$, $F(0) = 1-p$ y $F(1) = 1$, así que para $u \in (0,1)$
> $$
> c_{u} = \begin{cases}
> 0 & \text{ si } u \leq 1-p \\[0.5em]
> 1 & \text{ si } u > 1-p
> \end{cases}
> $$
> i.e. "si $U > 1-p$, éxito". En general, si $X$ toma los valores $x_{0} < x_{1} < \dots$, se parte $(0,1)$ en intervalos consecutivos de longitudes $f(x_{0}), f(x_{1}), \dots$ y $c_{U} = x_{k}$ cuando $U$ cae en el $k$-ésimo.

Como consecuencia, los cuantiles guardan **toda** la información de la distribución:

> [!theorem] **Corolario.**
>
> Si dos v.a.s $X$ y $Y$ tienen los mismos cuantiles ($c_{p}^{X} = c_{p}^{Y}$ para todo $p \in (0,1)$), ent. tienen la misma distribución.

> [!proof]- **Proof.**
>
> Por el Teorema, $F_{X}(x) = P(c_{U}^{X} \leq x) = P(c_{U}^{Y} \leq x) = F_{Y}(x)$ para todo $x$. $\blacksquare$

### El recíproco: $F(X)$ es uniforme

Si leer al revés convierte una uniforme en $X$, leer al derecho debería convertir a $X$ en una uniforme. Es cierto, pero solo si $F$ no tiene saltos:

> [!theorem] **Proposición.** (Transformada integral de probabilidad)
>
> Sea $X$ v.a. con función de distribución $F$ **continua**. Ent.
> $$
> F(X) \sim \operatorname{Unif}(0,1).
> $$

> [!proof]- **Proof.**
>
> **Borrador.** Negando la equivalencia de los cuantiles, $F(x) < u \iff x < c_{u}$. Así $P(F(X) < u) = P(X < c_{u})$, y por continuidad eso es $F(c_{u}) = u$.
>
> **Proof.** Sea $u \in (0,1)$. Negando ambos lados de $F(x) \geq u \iff x \geq c_{u}$,
> $$
> F(x) < u \iff x < c_{u}.
> $$
> Ent.
> $$
> \begin{align}
> & P(F(X) < u) \\[0.5em]
> &= P(X < c_{u}) = F(c_{u}^{-}) \\[0.5em]
> &= F(c_{u}) = u \tag{$F$ continua}
> \end{align}
> $$
> donde $F(c_{u}) = u$ es el caso continuo de [[Cuantiles]]. Por continuidad de la probabilidad, $P(F(X) \leq u) = \lim_{h \to 0^{+}} P(F(X) < u + h) = \lim_{h \to 0^{+}} (u+h) = u$. Como además $0 \leq F(X) \leq 1$, la función de distribución de $F(X)$ es la de $\operatorname{Unif}(0,1)$. $\blacksquare$

La hipótesis de continuidad no se puede quitar:

> [!example]- **Ejemplo 4.** (Contraejemplo discreto)
>
> Si $X \sim \operatorname{Bernoulli}(0.3)$, ent. $F(0) = 0.7$ y $F(1) = 1$, así que $F(X)$ solo toma los valores $0.7$ y $1$: no es uniforme. En general, para una v.a. discreta $F(X)$ es discreta.

> [!observation]+ **Observación.**
>
> El Teorema y la Proposición juntos dicen que, para $F$ continua, "$X$" y "$U$" son intercambiables a través de $F$ y de su función cuantil. En estadística, la Proposición es la razón por la que un p-valor (que es $1 - F(T)$ para un estadístico $T$ con distribución continua) es uniforme cuando la hipótesis nula es cierta.

---
Se usa en: [[Cuantiles]], [[Distribucion Exponencial]], [[Distribucion Weibull]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

La idea aparece para la Weibull en Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.12 (p. 266), Ej. 407. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
