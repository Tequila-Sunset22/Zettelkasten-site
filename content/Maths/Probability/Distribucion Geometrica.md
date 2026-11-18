---
modified: 2026-11-18T03:33:21Z
title: "Distribución Geométrica"
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
Repetimos un ensayo Bernoulli hasta el primer éxito: ¿cuántos fracasos hubo antes? Es el modelo de la espera **discreta**: volados hasta el primer sol, intentos hasta el primer acierto.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!tip|idea]- **Idea Intuitiva.**
>
> $X = x$ es "$x$ fracasos seguidos y luego un éxito", que por independencia tiene proba. $(1-p)^{x}p$.

Sup. que tenemos una sucesión infinita de ensayos indep. Bernoulli, cada uno con proba. de éxito $p$. Para cada una de estas sucesiones definimos la v.a. $X$ como el número de fracasos antes de obtener el primer éxito. Es decir,
$$
\begin{gather}
X(E F F \dots) = 0 \\[0.5em]
X(F E \dots) = 1 \\[0.5em]
X(F F E \dots) = 2, \quad \dots
\end{gather}
$$
de forma que $X$ toma valores $0,1,2,\dots$

> [!theorem] **Definición.** ($\operatorname{Geo}(p)$)
>
> Decimos que $X$ tiene una distribución geométrica con parámetro $p \in (0,1)$, i.e. $X \sim \operatorname{Geo} (p)$, cuando su función de proba. es:
> $$
> f(x) = \begin{cases}
>   p(1-p)^{x} & \text{ si } x = 0,1,2\dots \\[0.5em]
>   0 &   \text{ otro caso }
> \end{cases}
> $$

> [!Info]- **Nota!** (Otras notaciones)
>
> Muchos textos cuentan los **ensayos** hasta el primer éxito (incluyéndolo) en vez de los fracasos: $Y = X + 1$, con valores $1, 2, \dots$, $f(y) = p(1-p)^{y-1}$ y $\operatorname{E}(Y) = \frac{1}{p}$. Hay que fijarse cuál usa cada fuente.

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Geo} (p)$ y $q = 1 - p$.
> 1. $P(X \geq x) = q^{x}$ para $x = 0, 1, 2, \dots$
> 2. $G(t) = \dfrac{p}{1 - qt}$ para $\lvert t \rvert < \frac{1}{q}$.
> 3. $\displaystyle \operatorname{E} (X) = \frac{q}{p}$
> 4. $\displaystyle \operatorname{Var} (X) = \frac{q}{p^{2}}$

> [!proof]- **Proof.**
>
> 1. $X \geq x$ sii los primeros $x$ ensayos son fracasos: $q^{x}$. (O sumando la serie geométrica $\sum_{k \geq x} pq^{k} = \frac{pq^{x}}{1-q}$.) $\blacksquare$
> 2. $\sum_{x \geq 0} t^{x}pq^{x} = \frac{p}{1 - qt}$, serie geométrica. $\blacksquare$
> 3. $G'(t) = \frac{pq}{(1-qt)^{2}}$, ent. $\operatorname{E}(X) = G'(1) = \frac{pq}{p^{2}} = \frac{q}{p}$ ([[Funcion Generadora de Probabilidad]]). $\blacksquare$
> 4. $G''(1) = \frac{2pq^{2}}{p^{3}} = \frac{2q^{2}}{p^{2}}$, y
> $$
> \operatorname{Var}(X) = G''(1) + G'(1) - G'(1)^{2} = \frac{2q^{2}}{p^{2}} + \frac{q}{p} - \frac{q^{2}}{p^{2}} = \frac{q^{2} + pq}{p^{2}} = \frac{q}{p^{2}}. \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo 1.**
>
> Con un dado, ¿cuántos tiros fallamos antes del primer $6$? $X \sim \operatorname{Geo}(\frac{1}{6})$, $\operatorname{E}(X) = 5$, y $P(X \geq 10) = \left( \frac{5}{6} \right)^{10} \approx 0.16$: en una de cada seis rachas fallamos al menos diez veces.

### Pérdida de memoria

Si ya fallamos $x$ veces, ¿cambia algo hacia adelante? No: los ensayos son indep., así que la espera que falta es otra geométrica, como si empezáramos de cero.

> [!theorem] **Proposición.** (Pérdida de memoria)
>
> Sea $X \sim \operatorname{Geo}(p)$. Para todos $x, y \in \{ 0, 1, 2, \dots \}$,
> $$
> P(X \geq x + y \mid X \geq x) = P(X \geq y).
> $$

> [!proof]- **Proof.**
>
> Por la Propiedad 1, $\frac{P(X \geq x + y)}{P(X \geq x)} = \frac{q^{x+y}}{q^{x}} = q^{y}$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Es la **única** distribución con valores en $\{ 0, 1, \dots \}$ con esta propiedad: si $g(x) = P(X \geq x)$ cumple $g(x + y) = g(x)g(y)$ con $g(0) = 1$, ent. $g(x) = g(1)^{x}$. Su análogo continuo es la [[Distribucion Exponencial|exponencial]], y de hecho la parte entera de una exponencial es geométrica (ver esa nota).

La suma de $r$ geométricas indep. es la [[Distribucion Binomial Negativa|binomial negativa]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.4 (pp. 221–226). <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
