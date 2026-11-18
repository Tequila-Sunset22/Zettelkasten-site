---
modified: 2026-11-17T22:19:20Z
title: "Momentos"
publish: true
type: zettel
date: "2026-09-01"
status: undone
aliases:
tags:
 - probability
cssclasses:
 - romana
---
La [[Esperanza]] es el promedio de $X$; la [[Varianza]] usa el promedio de $X^{2}$. Siguiendo así, los promedios de todas las potencias $X^{n}$ forman una colección de números que describe cada vez más detalles de la forma de la distribución.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!theorem] **Definición.** (Momentos)
>
> Los momentos de una variable aleatoria $X$ o de su distribución son la colección de números:
> $$
> \operatorname{E}(X), \operatorname{E}(X^{2}), \operatorname{E}(X^{3}),\dots
> $$
> llamados **primer momento**, segundo momento, tercer momento, etc., cuando tales cantidades existen.
>
> Para v.a.d. el $n$-ésimo momento se calcula mediante
> $$
> \operatorname{E}(X^{n}) = \sum_{x} x^{n}f(x),
> $$
> mientras que para v.a.c. la fórmula es:
> $$
> \operatorname{E}(X^{n}) = \int_{-\infty}^{\infty} x^{n}f(x) \, dx
> $$

> [!observation]+ **Observación.**
>
> Cada uno de estos momentos representa una característica de la v.a. o de su distribución:
> - El primer momento es el valor promedio o esperanza.
> - El segundo está relacionado con la dispersión de los valores que toma la variable aleatoria, esto recordando: $\displaystyle \operatorname{Var}(X)= \operatorname{E}(X^{2}) - \operatorname{E}^{2}(X)$
> - El tercero está relacionado con la simetría de la correspondiente distribución de proba.
>
> En general, no se conoce una interpretación para cada uno de los momentos de una v.a. cualquiera, en el sentido de que no se conoce una interpretación para cada una de las derivadas de una función infinitamente diferenciable.

> [!example]- **Ejemplo 1.**
>
> Si $X \sim \operatorname{Unif}(0,1)$, $\operatorname{E}(X^{n}) = \int_{0}^{1} x^{n}\,dx = \frac{1}{n+1}$. Si $X \sim \operatorname{Exp}(1)$, $\operatorname{E}(X^{n}) = \int_{0}^{\infty} x^{n}e^{-x}\,dx = n!$ ([[Funcion Gamma]]).

Además de los momentos "a secas", se usan versiones recorridas o con valor absoluto:

> [!theorem] **Definición.** (Otros momentos)
>
> Sea $X$ con media finita $\mu$, $n \geq 1$ y $c$ constante.
>
> | Nombre | Expresión |
> |---|---|
> | $n$-ésimo momento central | $\operatorname{E}(X - \mu)^{n}$ |
> | $n$-ésimo momento absoluto | $\operatorname{E}\lvert X \rvert^{n}$ |
> | $n$-ésimo momento absoluto central | $\operatorname{E}\lvert X - \mu \rvert^{n}$ |
> | $n$-ésimo momento generalizado | $\operatorname{E}(X - c)^{n}$ |
>
> La varianza es el segundo momento central.

### ¿Cuándo existen?

No toda v.a. tiene momentos de todos los órdenes (la [[Distribucion t]] con $n$ grados de libertad solo tiene los de orden $< n$, y la Cauchy ninguno). Pero los que existen se heredan hacia abajo: si existe uno, existen todos los anteriores.

> [!theorem] **Proposición.**
>
> 1. Si $\operatorname{E}\lvert X \rvert^{n} < \infty$ y $0 \leq m \leq n$, ent. $\operatorname{E}\lvert X \rvert^{m} < \infty$.
> 2. Si $X$ es acotada ($\lvert X \rvert \leq K$), todos sus momentos existen.
> 3. Si el segundo momento existe, $\operatorname{E}^{2}(X) \leq \operatorname{E}(X^{2})$.

> [!proof]- **Proof.**
>
> 1. Para todo real $x$, $\lvert x \rvert^{m} \leq 1 + \lvert x \rvert^{n}$ (si $\lvert x \rvert \leq 1$ el lado izquierdo es $\leq 1$; si no, $\lvert x \rvert^{m} \leq \lvert x \rvert^{n}$). Ent. $\operatorname{E}\lvert X \rvert^{m} \leq 1 + \operatorname{E}\lvert X \rvert^{n} < \infty$ (monotonía). $\blacksquare$
> 2. $\lvert X \rvert^{n} \leq K^{n}$, ent. $\operatorname{E}\lvert X \rvert^{n} \leq K^{n}$. $\blacksquare$
> 3. Es $\operatorname{Var}(X) = \operatorname{E}(X^{2}) - \operatorname{E}^{2}(X) \geq 0$. $\blacksquare$

> [!observation]+ **Observación.**
>
> **No** es cierto en general que $\operatorname{E}(X) \leq \operatorname{E}(X^{2})$: si $X = \frac{1}{2}$ constante, $\operatorname{E}(X) = \frac{1}{2} > \frac{1}{4} = \operatorname{E}(X^{2})$. Lo que siempre vale es 3, con el primer momento **al cuadrado**.

### Simetría y momentos impares

Lo de que "el tercer momento mide la simetría" se puede hacer preciso para las distribuciones simétricas: todos sus momentos centrales impares valen $0$.

> [!theorem] **Proposición.**
>
> Sea $X$ con densidad (o función de probabilidad) simétrica respecto de $a$, i.e. $f(a + x) = f(a - x)$ para todo $x$, y con $n$-ésimo momento finito. Ent. $\operatorname{E}(X) = a$ (si existe) y $\operatorname{E}(X - a)^{n} = 0$ para todo $n$ impar.

> [!proof]- **Proof.**
>
> $X - a$ y $a - X$ tienen la misma distribución (la densidad de $X - a$ en $u$ es $f(a+u)$, y la de $a - X$ es $f(a - u)$, que son iguales). Para $n$ impar, $(a - X)^{n} = -(X - a)^{n}$, ent. $\operatorname{E}(X-a)^{n} = \operatorname{E}(a - X)^{n} = -\operatorname{E}(X - a)^{n}$, así que es $0$. Con $n = 1$ sale $\operatorname{E}(X) = a$. $\blacksquare$

> [!Info]- **Nota!** (Asimetría y curtosis)
>
> Por eso se define el **coeficiente de asimetría** $\frac{\operatorname{E}(X - \mu)^{3}}{\sigma^{3}}$: es $0$ para distribuciones simétricas, positivo con cola larga a la derecha (como la exponencial, donde vale $2$) y negativo con cola a la izquierda. El cuarto momento central normalizado, $\frac{\operatorname{E}(X-\mu)^{4}}{\sigma^{4}}$, se llama **curtosis** y mide qué tan pesadas son las colas (vale $3$ para la normal).

En ocasiones no podremos encontrar una expresión compacta de alguno de los momentos; como alternativa, se pueden calcular todos a la vez con la [[Funcion Generadora de Momentos]].

---
Siguiente: [[Cuantiles]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 2, §2.8 (pp. 178–181) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
