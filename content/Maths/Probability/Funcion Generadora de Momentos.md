---
modified: 2026-11-17T22:19:10Z
title: "Función Generadora de Momentos"
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
Calcular momentos uno por uno ($\operatorname{E}(X)$, $\operatorname{E}(X^{2})$, …) es una integral distinta cada vez. La función generadora de momentos los guarda **todos** en una sola función, de donde salen derivando. Y tiene dos propiedades que la vuelven la herramienta estándar para sumas de v.a.s independientes: convierte sumas en productos y determina la distribución.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!tip|idea]+ **Idea Intuitiva.**
>
> $e^{tX} = 1 + tX + \frac{t^{2}X^{2}}{2!} + \cdots$, así que $M(t) = \operatorname{E}(e^{tX})$ es una serie de potencias cuyos coeficientes son los momentos: $M(0) = 1$, la pendiente en $0$ es $\operatorname{E}(X)$, la segunda derivada en $0$ es $\operatorname{E}(X^{2})$, etc.
> ![[fgm-pendiente.svg|center|500]]

> [!theorem] **Definición.** (f.g.m.)
>
> Sea $X$ v.a. (discreta o continua). La **función generadora de momentos** de $X$ es la función
> $$
> M(t) = \operatorname{E} (e^{tX})
> $$
> para valores reales de $t$ en donde esta esperanza existe. Se escribe $M_{X}(t)$ si hay que decir de qué v.a. es.
>
> Por el teorema del estadístico inconsciente se calcula, en el caso discreto,
> $$
> M(t) = \sum_{x} e^{tx}f_{X}(x)
> $$
> y en el caso continuo,
> $$
> M(t) = \int_{-\infty}^{\infty} e^{tx} f(x) \, dx
> $$

> [!observation]+ **Observación.**
>
> $M(0) = 1$ siempre, pero puede ser que $M(t) = \infty$ para todo $t \neq 0$: entonces decimos que la f.g.m. **no existe**. Pasa cuando las colas son pesadas, como en la Cauchy o la $t$ (ver [[Distribucion t]]). Todos los resultados de abajo piden que $M$ sea finita en un intervalo $(-s, s)$ alrededor de $0$.

> [!example]- **Ejemplo 1.** (Laplace)
>
> Sea $f(x) = \frac{1}{2}e^{-\lvert x \rvert}$. Partiendo la integral en $x < 0$ y $x > 0$, para $-1 < t < 1$,
> $$
> M(t) = \frac{1}{2}\int_{0}^{\infty} e^{(t-1)x} \, dx + \frac{1}{2}\int_{-\infty}^{0} e^{(t+1)x} \, dx = \frac{1}{2}\cdot\frac{1}{1-t} + \frac{1}{2}\cdot\frac{1}{1+t} = \frac{1}{1-t^{2}},
> $$
> y $M(t) = \infty$ si $\lvert t \rvert \geq 1$: el dominio de $M$ no tiene por qué ser todo $\mathbb{R}$.

### Los momentos salen derivando

> [!theorem] **Proposición.**
>
> Sea $X$ con f.g.m. finita en $(-s, s)$, $s > 0$. Ent. todos los momentos de $X$ existen,
> $$
> M(t) = \sum_{n=0}^{\infty} \frac{t^{n}}{n!}\operatorname{E}(X^{n}) \qquad \text{para } t \in (-s,s),
> $$
> y $M^{(n)}(0) = \operatorname{E}(X^{n})$ para todo $n \in \mathbb{N}$.

> [!proof]- **Proof.**
>
> **Borrador.** Tomar esperanza en la serie de Taylor de $e^{tX}$ término a término, y derivar la serie de potencias en $0$.
>
> **Proof.** Para cada $\omega$, $e^{tX} = \sum_{n} \frac{(tX)^{n}}{n!}$. Intercambiando esperanza y suma (es válido aquí porque $\sum_{n} \frac{\lvert tX \rvert^{n}}{n!} = e^{\lvert tX \rvert} \leq e^{tX} + e^{-tX}$, que tiene esperanza finita para $\lvert t \rvert < s$; lo aceptamos sin entrar en el teorema de convergencia),
> $$
> M(t) = \sum_{n=0}^{\infty} \frac{t^{n}}{n!}\operatorname{E}(X^{n}),
> $$
> y esa misma cota da $\operatorname{E}\lvert X \rvert^{n} < \infty$. Una serie de potencias se deriva término a término dentro de su intervalo de convergencia, y su $n$-ésima derivada en $0$ es $n!$ veces su coeficiente $n$-ésimo: $M^{(n)}(0) = \operatorname{E}(X^{n})$. $\blacksquare$

> [!example]- **Ejemplo 2.**
>
> 1. Exponencial: $M(t) = \frac{1}{1-t} = \sum_{n} t^{n}$ para $\lvert t \rvert < 1$, ent. $\frac{\operatorname{E}(X^{n})}{n!} = 1$, i.e. $\operatorname{E}(X^{n}) = n!$ (lo mismo que con la [[Funcion Gamma]], sin integrar).
> 2. Laplace (Ejemplo 1): $M(t) = \frac{1}{1 - t^{2}} = \sum_{k} t^{2k}$, ent. los momentos impares son $0$ y $\operatorname{E}(X^{2k}) = (2k)!$. En particular $\operatorname{E}(X) = 0$ y $\operatorname{Var}(X) = 2$.

### Sumas, cambios de escala y caracterización

Lo que hace a la f.g.m. tan útil es cómo se comporta con las operaciones:

> [!theorem] **Teorema.** (Propiedades)
>
> Sean $X, Y$ v.a.s con f.g.m. finitas cerca de $0$, y $a, b$ constantes.
> 1. $M_{aX + b}(t) = e^{bt}M_{X}(at)$.
> 2. Si $X$ y $Y$ son [[Independencia de Variables Aleatorias|independientes]], $M_{X+Y}(t) = M_{X}(t)\,M_{Y}(t)$.
> 3. (Caracterización) Si $M_{X}(t) = M_{Y}(t)$ para todo $t$ en un intervalo $(-s, s)$, ent. $X$ y $Y$ tienen la misma distribución.

> [!proof]- **Proof.**
>
> 1. $\operatorname{E}(e^{t(aX + b)}) = e^{bt}\operatorname{E}(e^{(at)X})$. $\blacksquare$
> 2. $e^{tX}$ y $e^{tY}$ son indep. (funciones de v.a.s indep.), y la esperanza de un producto de indep. es el producto de las esperanzas ([[Esperanza]]):
> $$
> M_{X+Y}(t) = \operatorname{E}(e^{tX}e^{tY}) = \operatorname{E}(e^{tX})\operatorname{E}(e^{tY}). \tag*{$\blacksquare$}
> $$
> 3. La prueba no es sencilla (usa transformadas de Laplace o de Fourier) y la omitimos. Para v.a.s con valores en $\mathbb{N}$ es la caracterización de la [[Funcion Generadora de Probabilidad]], pues $M(t) = G(e^{t})$. $\blacksquare$

La receta para la suma de v.a.s independientes es entonces: multiplicar las f.g.m. y **reconocer** el resultado.

> [!example]- **Ejemplo 3.**
>
> Si $X_{1}, X_{2}$ son indep. $\operatorname{Exp}(\lambda)$, $M_{X_{1} + X_{2}}(t) = \left( \frac{\lambda}{\lambda - t} \right)^{2}$, que es la f.g.m. de $\operatorname{Gamma}(2, \lambda)$ ([[Distribucion Gamma]]). Por la caracterización, $X_{1} + X_{2} \sim \operatorname{Gamma}(2, \lambda)$, sin calcular ninguna convolución. Igual se prueba que la suma de normales indep. es normal ([[Distribucion Normal]]).

> [!Info]- **Nota!** (Continuidad de la f.g.m.)
>
> Hay un resultado más fuerte, que se usa para los teoremas límite: si $M_{X_{n}}(t) \to M_{X}(t)$ para todo $t$ en un intervalo alrededor de $0$, ent. $F_{X_{n}}(x) \to F_{X}(x)$ en cada punto donde $F_{X}$ es continua (**convergencia en distribución**). Así se prueba, por ejemplo, el teorema central del límite. Su prueba queda fuera del curso.

---
Siguiente: [[Distribuciones de Probabilidad]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 2, §2.12 (p. 195 y ss.) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
