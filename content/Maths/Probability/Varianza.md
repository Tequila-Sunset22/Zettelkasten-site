---
modified: 2026-11-17T22:18:12Z
title: "Varianza"
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
La [[Esperanza]] dice dónde está el centro de una v.a., pero no qué tan **dispersa** está alrededor de él: una v.a. constante $3$ y otra que vale $0$ o $6$ con proba. $\frac{1}{2}$ tienen la misma media. La varianza mide esa dispersión.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!tip|idea]- **Idea Intuitiva.**
>
> $\operatorname{Var}(X)$ es el promedio de la distancia de $X$ a su media, al cuadrado.

> [!theorem] **Definición.** (Varianza)
>
> Sea $X$ v.a. discreta con función de masa de probabilidad $f(x)$ y esperanza $\mu$ finita. La **varianza** de $X$ se define como el número
> $$
> \operatorname{Var} (X) = \sum_{x} (x-\mu)^{2}f(x),
> $$
> cuando esta suma es convergente.
>
> Para $X$ v.a. continua, se define
> $$
> \operatorname{Var} (X) = \int_{-\infty}^{\infty} (x-\mu)^{2}f(x) \, dx,
> $$
> cuando esta integral es convergente.
>
> En el caso de que la integral o la suma no converjan, ent. se dice que la varianza no existe o que $X$ no tiene varianza finita.
>
> A la varianza, generalmente, se le denota $\sigma ^{2}$.

> [!observation]+ **Observación.**
>
> También podemos expresar la varianza en una sola expresión como, donde $\mu$ es $\operatorname{E} (X)$ (bajo la misma v.a.):
> $$
> \operatorname{Var} (X) = \operatorname{E}(X - \mu)^{2}
> $$
> ¡Sí! La varianza es un caso particular de la esperanza, en donde estamos calculando la esperanza de $g(x)= ( x - \mu )^{2}$ aplicada a una v.a. $X$ con esperanza $\mu$ (teorema del estadístico inconsciente). Entonces, podemos hacer uso de la teoría que desarrollamos sobre la esperanza<sup><a href="#user-content-fn-inline-2" id="user-content-fnref-inline-2" data-footnote-ref class="internal">2</a></sup>.

> [!theorem] **Definición.** (Desviación Estándar)
>
> A la raíz cuadrada de $\sigma ^{2}$ se le llama **desviación estándar**, denotada $\sigma$.

> [!observation]+ **Observación.**
>
> La varianza tiene las unidades de $X$ **al cuadrado** (si $X$ son metros, $\operatorname{Var}(X)$ son metros cuadrados). La desviación estándar regresa a las unidades de $X$, y por eso es la que se compara con la media.

> [!theorem] **Teorema.** (Propiedades)
>
> Sean $X$ y $Y$ v.a. con varianza finita y $c$ una constante, entonces
> 1. $\displaystyle \operatorname{Var} (X) \geq 0$.
> 2. $\operatorname{Var} (c) = 0$.
> 3. $\operatorname{Var} (cX) = c^{2} \operatorname{Var} (X)$.
> 4. $\operatorname{Var} (X + c) = \operatorname{Var} (X)$.
> 5. $\operatorname{Var} (X) = \operatorname{E} (X^{2}) - \operatorname{E}^{2} (X)$.
> 6. $\operatorname{Var}(X + Y) = \operatorname{Var}(X) + \operatorname{Var}(Y) + 2\left[ \operatorname{E}(XY) - \operatorname{E}(X)\operatorname{E}(Y) \right]$; en general, $\operatorname{Var} (X + Y) \neq  \operatorname{Var} (X) + \operatorname{Var} (Y)$.

> [!proof]- **Proof.**
>
> Sea $\mu = \operatorname{E}(X)$. Todo sale de la linealidad de la esperanza.
> 1. $(X - \mu)^{2} \geq 0$, ent. su esperanza es $\geq 0$. $\blacksquare$
> 2. $\operatorname{E}(c) = c$, ent. $\operatorname{Var}(c) = \operatorname{E}(c - c)^{2} = 0$. $\blacksquare$
> 3. $\operatorname{E}(cX) = c\mu$, ent. $\operatorname{Var}(cX) = \operatorname{E}(cX - c\mu)^{2} = c^{2}\operatorname{E}(X - \mu)^{2}$. $\blacksquare$
> 4. $\operatorname{E}(X + c) = \mu + c$, ent. $(X + c) - (\mu + c) = X - \mu$. $\blacksquare$
> 5. Desarrollando el cuadrado,
> $$
> \operatorname{E}(X - \mu)^{2} = \operatorname{E}(X^{2}) - 2\mu\operatorname{E}(X) + \mu^{2} = \operatorname{E}(X^{2}) - \mu^{2}. \tag*{$\blacksquare$}
> $$
> 6. Por 5 y la linealidad, con $\nu = \operatorname{E}(Y)$,
> $$
> \begin{align}
> & \operatorname{Var}(X + Y) \\[0.5em]
> &= \operatorname{E}(X^{2}) + 2\operatorname{E}(XY) + \operatorname{E}(Y^{2}) - (\mu + \nu)^{2} \\[0.5em]
> &= \operatorname{Var}(X) + \operatorname{Var}(Y) + 2\left[ \operatorname{E}(XY) - \mu\nu \right] \tag*{$\blacksquare$}
> \end{align}
> $$

> [!example]- **Ejemplo 1.**
>
> 1. Un dado: $\operatorname{E}(X) = \frac{7}{2}$ y $\operatorname{E}(X^{2}) = \frac{91}{6}$, ent. $\operatorname{Var}(X) = \frac{91}{6} - \frac{49}{4} = \frac{35}{12}$.
> 2. $f(x) = 2x$ en $(0,1)$: $\operatorname{E}(X) = \frac{2}{3}$, $\operatorname{E}(X^{2}) = \frac{1}{2}$, ent. $\operatorname{Var}(X) = \frac{1}{2} - \frac{4}{9} = \frac{1}{18}$.

Por 6, la varianza de una suma es la suma de las varianzas justo cuando el término cruzado se anula, y con [[Independencia de Variables Aleatorias|independencia]] se anula:

> [!theorem] **Proposición.**
>
> Sean $X$ y $Y$ v.a.s con varianza finita. Ent.
> $$
> \operatorname{Var}(X + Y) = \operatorname{Var}(X) + \operatorname{Var}(Y) \iff \operatorname{E}(XY) = \operatorname{E}(X)\operatorname{E}(Y).
> $$
> En particular, si $X$ y $Y$ son **independientes**, $\operatorname{Var} (X + Y) = \operatorname{Var} (X) + \operatorname{Var} (Y)$.

> [!proof]- **Proof.**
>
> La equivalencia es la Propiedad 6. Si son independientes, $\operatorname{E}(XY) = \operatorname{E}(X)\operatorname{E}(Y)$ (ver [[Esperanza]]). $\blacksquare$

Su consecuencia más importante es lo que le pasa al promedio de $n$ mediciones independientes:

> [!theorem] **Corolario.** (Media muestral)
>
> Sean $X_{1}, \dots, X_{n}$ v.a.s indep. con media $\mu$ y varianza $\sigma^{2}$, y $\bar{X} = \frac{1}{n}\sum_{k=1}^{n} X_{k}$. Ent.
> $$
> \operatorname{E}(\bar{X}) = \mu, \qquad \operatorname{Var}(\bar{X}) = \frac{\sigma^{2}}{n}.
> $$

> [!proof]- **Proof.**
>
> Por linealidad, $\operatorname{E}(\bar{X}) = \frac{1}{n}\cdot n\mu$. Por la Propiedad 3 y la Proposición (aplicada $n - 1$ veces; cada $X_{k}$ es indep. de la suma de las anteriores),
> $$
> \operatorname{Var}(\bar{X}) = \frac{1}{n^{2}}\sum_{k=1}^{n} \operatorname{Var}(X_{k}) = \frac{\sigma^{2}}{n}. \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> El promedio tiene la misma media que cada medición, pero su desviación estándar es $\frac{\sigma}{\sqrt{ n }}$: promediar $100$ mediciones reduce el error típico a la décima parte. Es la razón de fondo de la ley de los grandes números.

### La media como mejor predicción

¿Por qué medir la dispersión alrededor de $\mu$ y no de otro punto? Porque $\mu$ es justo el número que hace más chico el error cuadrático promedio, y ese mínimo es la varianza.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Si hay que adivinar $X$ con un solo número $c$ y se paga $(X - c)^{2}$, lo mejor es $c = \mu$, y lo que se paga en promedio es $\operatorname{Var}(X)$.
> ![[varianza-minimo.svg|center|500]]

> [!theorem] **Proposición.**
>
> Sea $X$ con varianza finita y $g(c) = \operatorname{E}(X - c)^{2}$. Ent.
> $$
> g(c) = \operatorname{Var}(X) + (c - \mu)^{2},
> $$
> así que $g$ tiene un único mínimo en $c = \mu$, y su valor mínimo es $\operatorname{Var}(X)$.

> [!proof]- **Proof.**
>
> Sumando y restando $\mu$, $(X - c)^{2} = (X - \mu)^{2} + 2(X - \mu)(\mu - c) + (\mu - c)^{2}$. Tomando esperanza, el término de en medio se va porque $\operatorname{E}(X - \mu) = 0$. $\blacksquare$

Con este resultado sale gratis una cota para v.a.s acotadas: la varianza no puede ser más que un cuarto del cuadrado del rango.

> [!theorem] **Corolario.**
>
> Si $a \leq X \leq b$, ent. $\operatorname{Var}(X) \leq \frac{(b-a)^{2}}{4}$, con igualdad si $X$ vale $a$ o $b$ con proba. $\frac{1}{2}$ cada uno.

> [!proof]- **Proof.**
>
> Por la Proposición con $c = \frac{a+b}{2}$, y como $\lvert X - c \rvert \leq \frac{b-a}{2}$,
> $$
> \operatorname{Var}(X) \leq \operatorname{E}\left( X - \frac{a+b}{2} \right)^{2} \leq \frac{(b-a)^{2}}{4}.
> $$
> Si $X$ vale $a$ o $b$ con proba. $\frac{1}{2}$, ent. $\mu = \frac{a+b}{2}$ y $(X - \mu)^{2} = \frac{(b-a)^{2}}{4}$ siempre. $\blacksquare$

> [!observation]+ **Observación.**
>
> Si $X$ es discreta y $\operatorname{Var}(X) = 0$, ent. $X$ es constante: cada término $(x - \mu)^{2}f(x) \geq 0$ de la suma tiene que ser $0$, así que $f(x) = 0$ para todo $x \neq \mu$, i.e. $P(X = \mu) = 1$.

---
Siguiente: [[Momentos]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 2, §2.7 (pp. 169–177) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
<li id="user-content-fn-inline-2">

[[Esperanza]] <a href="#user-content-fnref-inline-2" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
