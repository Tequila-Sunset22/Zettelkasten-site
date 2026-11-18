---
modified: 2026-11-17T22:20:24Z
title: "Moda"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Unimodal
 - Multimodal
tags:
 - probability
cssclasses:
 - romana
---
Ya tenemos dos formas de decir dónde está "el centro" de una v.a.: la [[Esperanza]] (el promedio ponderado) y la mediana (el punto que deja la mitad de la probabilidad de cada lado, ver [[Cuantiles]]). La moda es la tercera y la más ingenua: el valor **más probable**. Es la única de las tres que no necesita sumar ni acumular nada, solo mirar dónde está el pico.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> La moda es donde la función de probabilidad (o de densidad) alcanza su máximo.

> [!tip|idea]- **Idea Intuitiva.**
>
> Discreta: el valor que más sale. Continua: donde la densidad es más alta, i.e. donde se amontona la probabilidad.

> [!theorem] **Definición.** (Moda)
>
> Sea $X$ v.a. con función de probabilidad (o de densidad) $f$. Una **moda** de $X$ (o de su distribución) es un número $x^{*}$ tal que
> $$
> f(x^{*}) = \max_{x \in \mathbb{R}} f(x).
> $$
> Si $x^{*}$ es único, decimos que $X$ es **unimodal**; si hay dos o más, que es **multimodal** (o bimodal, si son dos). En general la moda es un **conjunto** de puntos, que puede ser vacío.

> [!Info]- **Nota!** (Otras notaciones)
>
> No hay símbolo estándar: se usa $x^{*}$, $\operatorname{Moda}(X)$ o $x_{m}$.

Que sea un conjunto no es un tecnicismo: aparece con distribuciones muy sencillas.

> [!example]- **Ejemplo 1.** (Bernoulli)
>
> Sea $X \sim \operatorname{Ber}(p)$, con $f(0) = 1-p$ y $f(1) = p$. Ent. la moda es $0$ si $p < \frac{1}{2}$, es $1$ si $p > \frac{1}{2}$, y si $p = \frac{1}{2}$ las dos son modas: $X$ es bimodal.

> [!example]- **Ejemplo 2.** (Binomial bimodal)
>
> Sea $X \sim \operatorname{Bin}(5, \frac{1}{2})$. Ent. $f(x) = \binom{5}{x}\frac{1}{32}$:
> $$
> f(0) = f(5) = \tfrac{1}{32}, \qquad f(1) = f(4) = \tfrac{5}{32}, \qquad f(2) = f(3) = \tfrac{10}{32}.
> $$
> El máximo se alcanza en $2$ y en $3$: la moda es $\{ 2, 3 \}$.

> [!example]- **Ejemplo 3.** (Densidad con joroba)
>
> Sea $f(x) = xe^{-x}$ para $x > 0$ ($0$ en otro caso). Derivando,
> $$
> f'(x) = (1-x)e^{-x},
> $$
> que es positiva en $(0,1)$ y negativa en $(1,\infty)$. Ent. la moda es única: $x^{*} = 1$. (Es la $\operatorname{Gamma}(2,1)$; ver [[Distribucion Gamma]].)

> [!example]- **Ejemplo 4.** (Todo el intervalo)
>
> Si $X \sim \operatorname{Unif}(0,1)$, $f(x) = 1$ en $(0,1)$ y todos esos puntos son modas: la moda es un intervalo entero. La moda no dice nada útil aquí, y eso también es información: la distribución no tiene un pico.

### ¿Siempre existe?

En el caso discreto sí, aunque la v.a. tome una infinidad de valores. La razón es que las probabilidades suman $1$: no puede haber muchos valores con probabilidad "grande".

> [!theorem] **Proposición.** (Existencia en el caso discreto)
>
> Si $X$ es discreta con función de probabilidad $f$, ent. $X$ tiene al menos una moda.

> [!proof]- **Proof.**
>
> **Borrador.** Tomamos un valor cualquiera con probabilidad $a > 0$. Solo hay finitos valores con probabilidad $\geq a$ (a lo más $\frac{1}{a}$), y el máximo de un conjunto finito existe. Todos los demás valores tienen probabilidad $< a$, así que no le pueden ganar.
>
> **Proof.** Sea $x_{0}$ un valor con $a = f(x_{0}) > 0$ (existe porque las probabilidades suman $1$). Sea $A = \{ x \mid f(x) \geq a \}$. Si $A$ tuviera $k$ elementos, ent.
> $$
> 1 \geq \sum_{x \in A} f(x) \geq k a,
> $$
> i.e. $k \leq \frac{1}{a}$: $A$ es finito, y no vacío ($x_{0} \in A$). Sea $x^{*} \in A$ con $f(x^{*}) = \max_{x \in A} f(x)$. Si $x \in A$, $f(x) \leq f(x^{*})$ por def. de máximo; si $x \notin A$, $f(x) < a \leq f(x^{*})$. $\therefore$ $x^{*}$ es moda. $\blacksquare$

En el caso continuo **no**: la densidad puede crecer sin alcanzar nunca su supremo.

> [!example]- **Ejemplo 5.** (Exponencial sin moda)
>
> Sea $X \sim \operatorname{Exp}(\lambda)$ con densidad $f(x) = \lambda e^{-\lambda x}$ para $x > 0$ (y $0$ en otro caso). $f$ es estrictamente decreciente en $(0,\infty)$, su supremo es $\lambda$ y "se alcanzaría" en $x = 0$, pero ahí $f(0) = 0$. Ent. no hay ningún $x^{*}$ con $f(x^{*}) = \max f$: **no hay moda**.

> [!observation]+ **Observación.** (La moda depende de la densidad que escojamos)
>
> En el Ejemplo 5, si escribimos la densidad con $\mathbb{1}_{[0,\infty)}(x)$ (como en [[Distribucion Exponencial]]), ent. $f(0) = \lambda$ y la moda **sí** existe: es $0$. Las dos son densidades de la misma v.a., porque cambiar $f$ en un punto no cambia ninguna integral, i.e. ninguna probabilidad.
>
> Esto pasa porque la densidad de una v.a. continua **no es única**, y la moda es la única de nuestras medidas de centro que depende del valor de $f$ en puntos aislados (la esperanza y la mediana no). En la práctica se escoge la versión "natural" de $f$ (continua donde se pueda), y conviene decir cuál se está usando.

### Moda, mediana y media

Ya tenemos tres respuestas a "¿dónde está el centro?": la moda (el pico), la mediana $c_{0.5}$ (el punto que parte la probabilidad a la mitad, ver [[Cuantiles]]) y la media $\operatorname{E}(X)$ (el punto de equilibrio, ver [[Esperanza]]). Miden cosas distintas, y comparar las tres dice algo de la **forma** de la distribución.

> [!tip|idea]- **Idea Intuitiva.**
>
> Con la densidad como una tabla de madera: la moda es el punto más alto, la mediana el corte que la parte a la mitad y la media el punto de equilibrio. Una cola larga casi no mueve la moda y mueve mucho la media.

Si la distribución es simétrica y tiene un solo pico, la simetría obliga a que las tres coincidan en el centro de simetría:

> [!example]- **Ejemplo 6.** (Simétrica: coinciden)
>
> Para $X \sim \operatorname{N}(\mu, \sigma^{2})$, la moda, la mediana y la media valen $\mu$ (Propiedades de [[Distribucion Normal]]). Lo mismo para $t(n)$ con $n > 1$: las tres valen $0$ (ver [[Distribucion t]]); con $n = 1$ (la Cauchy) la moda y la mediana son $0$, pero la media **no existe**.

Con una cola larga a la derecha se separan, y casi siempre en el mismo orden, el de la "palanca": moda, luego mediana, luego media.

> [!example]- **Ejemplo 7.** (Cola a la derecha)
>
> 1. $X \sim \operatorname{Exp}(\lambda)$, con la densidad en $[0,\infty)$:
> $$
> \underbrace{0}_{\text{moda}} < \underbrace{\frac{\ln 2}{\lambda}}_{\text{mediana}} < \underbrace{\frac{1}{\lambda}}_{\text{media}}
> $$
> (la mediana es el Ejemplo 3 de [[Cuantiles]]).
> 2. $X \sim \operatorname{Gamma}(2, 1)$, la densidad $xe^{-x}$ del Ejemplo 3: moda $1$, mediana $\approx 1.678$ (numérica: la gamma no tiene $F$ en forma cerrada) y media $2$ (ver [[Distribucion Gamma]]).
> 3. Con $\operatorname{Gamma}(5,1)$ las tres son $4$, $\approx 4.671$ y $5$: con más forma la distribución es menos asimétrica, y las tres se acercan en proporción.

> [!example]- **Ejemplo 8.** (Cola a la izquierda)
>
> Al revés, con la cola a la izquierda el orden se invierte. Para $X \sim \operatorname{Beta}(5,2)$: media $\frac{5}{7} \approx 0.714$, mediana $\approx 0.736$ y moda $\frac{4}{5} = 0.8$ (ver [[Distribucion Beta]]). Y como $1 - X \sim \operatorname{Beta}(2,5)$, para esa son $0.2 < 0.264 < 0.286$: el espejo.

> [!observation]+ **Observación.**
>
> El orden moda $<$ mediana $<$ media es una **tendencia** de las distribuciones con una sola joroba y cola a la derecha, no un teorema: se pueden construir contraejemplos. Lo que sí es cierto siempre es lo de la Idea Intuitiva: la media es la única de las tres que puede no existir o irse a donde sea con poca probabilidad muy lejos, y por eso en datos con colas largas (ingresos, tiempos de espera) se reporta la mediana.

---
Siguiente: [[Funcion Generadora de Probabilidad]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 2, §2.10 (p. 186) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
