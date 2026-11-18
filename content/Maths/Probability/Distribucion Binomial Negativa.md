---
modified: 2026-11-18T16:58:57Z
title: "Distribución Binomial Negativa"
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
La [[Distribucion Geometrica|geométrica]] cuenta los fracasos antes del **primer** éxito; la binomial negativa, los fracasos antes del $r$-ésimo. Por ejemplo: cuántos tiros fallamos antes de encestar $3$ veces.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!tip|idea]- **Idea Intuitiva.**
>
> $X = x$ es: en los primeros $r + x - 1$ ensayos hubo $r - 1$ éxitos (en cualquier orden) y el ensayo $r + x$ es éxito. Eso da $\binom{r+x-1}{x}p^{r-1}(1-p)^{x}\cdot p$.

Sup. que tenemos una sucesión infinita de ensayos indep. Bernoulli, en cada uno de los cuales la proba. de éxito es $p$. Sea $r\geq 1$ núm. entero; definamos $X$ como el número de fracasos antes de obtener el $r$-ésimo éxito. $X$ puede tomar valores $0,1,2,\dots$

> [!theorem] **Definición.** ($\operatorname{BinNeg}(r,p)$)
>
> Decimos que $X$ tiene una distrib. binomial negativa con parámetros $r$ y $p$, i.e. $X \sim \operatorname{BinNeg} (r,p)$, si su función de probabilidad es:
> $$
> f(x) = \begin{cases}
> \binom{r+x-1}{x} p^{r} (1-p)^{x} & x = 0,1,2\dots\\[0.5em]
> 0 & \text{en otro caso } 
> \end{cases}
> $$

> [!Info]- **Nota!** (Otras notaciones)
>
> Cuando se cuenta el núm. **total de ensayos** necesarios para obtener $r$ éxitos, $Y = X + r$, la función cambia a $f(y) = \binom{y-1}{r-1} p^{r} (1-p)^{y-r}$ con $\operatorname{supp}(Y) = \{ r,r+1,r+2 \dots\}$. Con $r = 1$ es la geométrica.

> [!observation]+ **Observación.** (¿Por qué "negativa"?)
>
> $\binom{r+x-1}{x} = (-1)^{x}\binom{-r}{x}$, así que $f(x) = \binom{-r}{x}p^{r}(-q)^{x}$ con $q = 1-p$, y que sumen $1$ es el binomio de Newton con exponente **negativo**: $\sum_{x} \binom{-r}{x}(-q)^{x} = (1 - q)^{-r} = p^{-r}$.

Igual que la binomial es una suma de Bernoullis, esperar $r$ éxitos es esperar uno, luego otro, … : una suma de geométricas.

> [!theorem] **Proposición.**
>
> Sean $X_{1},\dots,X_{r}$ v.a.s independientes, cada una con distrib. $\operatorname{Geo} (p)$. Entonces,
> $$
> X_{1}+\dots+X_{r} \sim \operatorname{BinNeg} (r,p) .
> $$
> Recíprocamente, toda v.a. con distrib. $\operatorname{BinNeg} (r,p)$ tiene la misma distribución que una suma de la forma anterior.

> [!proof]- **Proof.**
>
> Por la [[Funcion Generadora de Probabilidad|f.g.p.]]: cada $X_{i}$ tiene $\frac{p}{1 - qt}$, así que la suma tiene $\left( \frac{p}{1-qt} \right)^{r} = p^{r}(1 - qt)^{-r}$. Por el binomio de Newton con exponente negativo (Observación), $(1 - qt)^{-r} = \sum_{x \geq 0} \binom{r+x-1}{x}q^{x}t^{x}$, y el coeficiente de $t^{x}$ es $\binom{r+x-1}{x}p^{r}q^{x} = f(x)$. Por la caracterización de la f.g.p., la suma es $\operatorname{BinNeg}(r,p)$. $\blacksquare$

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{BinNeg}(r,p)$ y $q = 1-p$.
> 1. $\displaystyle \operatorname{E} (X) = r \frac{q}{p}$
> 2. $\displaystyle \operatorname{Var} (X) = r \frac{q}{p^{2}}$
> 3. $P(X \leq x) = P(Y \geq r)$ con $Y \sim \operatorname{Bin}(r + x, p)$.
> 4. $G(t) = \left( \dfrac{p}{1 - qt} \right)^{r}$ y $M(t) = \left( \dfrac{p}{1 - qe^{t}} \right)^{r}$ para $t < -\ln q$.
> 5. Si $W \sim \operatorname{BinNeg}(s, p)$ es indep. de $X$, ent. $X + W \sim \operatorname{BinNeg}(r + s, p)$.
> 6. ([[Moda]]) $\frac{f(x+1)}{f(x)} = q\,\frac{x + r}{x+1}$, así que la moda es $\left\lfloor \frac{(r-1)q}{p} \right\rfloor$ (dos modas si ese número es entero y positivo).

> [!proof]- **Proof.**
>
> 1. y 2. Por la Proposición y las Propiedades de la geométrica: la media se suma siempre, y la varianza se suma por independencia. $\blacksquare$
> 3. A lo más $x$ fracasos antes del $r$-ésimo éxito sii en los primeros $r + x$ ensayos hubo al menos $r$ éxitos, y el núm. de éxitos en $r + x$ ensayos es $\operatorname{Bin}(r+x, p)$. $\blacksquare$
> 4. Está en la prueba de la Proposición; $M(t) = G(e^{t})$. $\blacksquare$
> 5. Producto de f.g.p.: $\left( \frac{p}{1-qt} \right)^{r}\left( \frac{p}{1-qt} \right)^{s}$, y caracterización. (O: son $r + s$ geométricas indep.) $\blacksquare$
> 6. El cociente sale de $\binom{r+x}{x+1} = \binom{r+x-1}{x}\frac{r+x}{x+1}$. $f(x+1) \geq f(x)$ sii $q(x+r) \geq x+1$ sii $x + 1 \leq \frac{(r-1)q}{p}$, y se concluye como en la [[Distribucion Binomial|binomial]]. Con $r = 1$ la moda es $0$, como en la geométrica. $\blacksquare$

> [!example]- **Ejemplo 1.**
>
> Un jugador encesta con proba. $0.4$. ¿Cuál es la proba. de que falle a lo más $2$ tiros antes de su tercer enceste? Por 3, con $Y \sim \operatorname{Bin}(5, 0.4)$: $P(Y \geq 3) \approx 0.317$. En promedio falla $3\cdot\frac{0.6}{0.4} = 4.5$ tiros.

> [!example]- **Ejemplo 2.** (Muestreo)
>
> Se buscan $20$ personas con cierta característica que tiene el $1\%$ de la población, preguntando al azar. El núm. total de personas consultadas es $Y = X + 20$ con $X \sim \operatorname{BinNeg}(20, 0.01)$, y en promedio
> $$
> \operatorname{E}(Y) = 20 + 20\cdot\frac{0.99}{0.01} = \frac{20}{0.01} = 2000.
> $$

> [!observation]+ **Observación.**
>
> La relación 3 es la versión discreta de la de [[Distribucion Gamma|Erlang y Poisson]]: "el $r$-ésimo éxito llegó a tiempo" es lo mismo que "hubo al menos $r$ éxitos en ese tiempo".

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.5 (pp. 227–233) y Ejs. 322–332. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
