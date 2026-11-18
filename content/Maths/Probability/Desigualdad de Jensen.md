---
modified: 2026-11-17T22:20:24Z
title: "Desigualdad de Jensen"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Jensen
tags:
 - probability
cssclasses:
 - romana
---
La [[Esperanza]] es lineal, así que pasa a través de funciones lineales: $\operatorname{E}(aX + b) = a\operatorname{E}(X) + b$. Con una función curva ya no: en general $\operatorname{E}(\varphi(X)) \neq \varphi(\operatorname{E}(X))$. Si $\varphi$ es **convexa**, al menos sabemos de qué lado queda la desigualdad, y eso basta para muchísimas cosas: que $\operatorname{E}(X^{2}) \geq \operatorname{E}^{2}(X)$, que la media geométrica es menor que la aritmética, y en estadística y ML, que la divergencia de Kullback–Leibler es $\geq 0$.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> $\varphi$ convexa $\implies$ $\varphi(\operatorname{E} X) \leq \operatorname{E}\,\varphi(X)$.

> [!theorem] **Definición.** (Función convexa)
>
> Sea $I$ un intervalo. $\varphi : I \to \mathbb{R}$ es **convexa** si para cualesquiera $x, y \in I$ y $\lambda \in [0,1]$,
> $$
> \varphi(\lambda x + (1-\lambda)y) \leq \lambda\varphi(x) + (1-\lambda)\varphi(y),
> $$
> i.e. la cuerda entre $(x, \varphi(x))$ y $(y, \varphi(y))$ queda por encima de la gráfica.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Con dos valores, $\operatorname{E}\,\varphi(X)$ está en la cuerda y $\varphi(\operatorname{E}X)$ en la curva, abajo. En general se usa la recta tangente en $\mu$, que queda debajo de toda la curva.
> ![[jensen-soporte.svg|center|550]]

La herramienta de la prueba es esa recta: una función convexa siempre tiene, en cada punto interior, una recta que la toca ahí y queda por debajo (si es derivable, la tangente).

> [!theorem] **Lema.** (Recta de soporte)
>
> Sea $\varphi$ convexa en un intervalo abierto $I$ y $\mu \in I$. Existe $c \in \mathbb{R}$ tal que
> $$
> \varphi(x) \geq \varphi(\mu) + c(x - \mu) \qquad \text{para todo } x \in I.
> $$

> [!proof]- **Proof.**
>
> **Borrador.** Las pendientes de las cuerdas que salen de $\mu$ crecen hacia la derecha (es la convexidad); cualquier $c$ entre la mayor pendiente por la izquierda y la menor por la derecha sirve.
>
> **Proof.** Para $s < \mu < t$ en $I$, escribiendo $\mu = \lambda s + (1-\lambda)t$ con $\lambda = \frac{t-\mu}{t-s}$, la convexidad da $\varphi(\mu) \leq \lambda\varphi(s) + (1-\lambda)\varphi(t)$, que reordenado es
> $$
> \frac{\varphi(\mu) - \varphi(s)}{\mu - s} \leq \frac{\varphi(t) - \varphi(\mu)}{t - \mu}.
> $$
> Ent. $c = \sup_{s < \mu} \frac{\varphi(\mu) - \varphi(s)}{\mu - s}$ es finito (acotado por cualquier pendiente derecha) y cumple $\frac{\varphi(\mu)-\varphi(s)}{\mu - s} \leq c \leq \frac{\varphi(t)-\varphi(\mu)}{t - \mu}$. Despejando, $\varphi(t) \geq \varphi(\mu) + c(t-\mu)$ para $t > \mu$ y $\varphi(s) \geq \varphi(\mu) + c(s - \mu)$ para $s < \mu$. $\blacksquare$

> [!theorem] **Teorema.** (Desigualdad de Jensen)
>
> Sea $X$ v.a. con valores en un intervalo abierto $I$ y esperanza finita $\mu$, y sea $\varphi : I \to \mathbb{R}$ convexa con $\varphi(X)$ de esperanza finita. Ent.
> $$
> \varphi(\operatorname{E} X) \leq \operatorname{E}\,\varphi(X).
> $$

> [!proof]- **Proof.**
>
> $\mu \in I$ (Propiedad 6 de [[Esperanza]], con $I$ abierto). Por el Lema con este $\mu$, $\varphi(X) \geq \varphi(\mu) + c(X - \mu)$, y tomando esperanza (monotonía y linealidad),
> $$
> \operatorname{E}\,\varphi(X) \geq \varphi(\mu) + c\left( \operatorname{E}(X) - \mu \right) = \varphi(\mu). \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Si $\varphi$ es **cóncava** ($-\varphi$ convexa), la desigualdad se voltea: $\operatorname{E}\,\varphi(X) \leq \varphi(\operatorname{E}X)$. Y si $\varphi$ es lineal, es igualdad: la linealidad de la esperanza.

> [!example]- **Ejemplo 1.** (Tres consecuencias)
>
> 1. $\varphi(x) = x^{2}$: $\operatorname{E}^{2}(X) \leq \operatorname{E}(X^{2})$, que es $\operatorname{Var}(X) \geq 0$ (ver [[Varianza]]).
> 2. $\varphi(x) = \frac{1}{x}$, convexa en $(0, \infty)$: si $X > 0$, $\frac{1}{\operatorname{E}(X)} \leq \operatorname{E}\left( \frac{1}{X} \right)$. Por ejemplo, si un viaje de $1$ km se hace a velocidad aleatoria $V$, el tiempo promedio $\operatorname{E}(1/V)$ es **mayor** que $1/\operatorname{E}(V)$.
> 3. $\varphi = \ln$, cóncava: $\operatorname{E}(\ln X) \leq \ln \operatorname{E}(X)$. Con $X$ uniforme en $\{ x_{1}, \dots, x_{n} \} \subseteq (0,\infty)$ y exponenciando, $\sqrt[n]{x_{1}\cdots x_{n}} \leq \frac{x_{1} + \dots + x_{n}}{n}$: la media geométrica no supera a la aritmética.

---
Se usa en: [[Esperanza]], [[Varianza]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 2, §2.6 (pp. 153–168), Ej. 225. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
