---
modified: 2026-11-18T16:57:55Z
title: "Método de Monte Carlo"
publish: true
type: zettel
date: "2026-11-18"
status: seed
aliases:
 - Monte Carlo
tags:
 - probability
cssclasses:
 - romana
---
Muchas cantidades son difíciles de calcular exactamente pero fáciles de **simular**: una probabilidad con un evento complicado, una integral sin antiderivada, un área rara. La idea de Monte Carlo es escribir la cantidad como una probabilidad o una esperanza, repetir el experimento muchas veces en la computadora, y promediar. Con la [[Varianza]] se puede decir además qué tan bueno es el resultado.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> Para calcular una probabilidad, simula el experimento muchas veces y cuenta.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Puntos uniformes en el cuadrado unitario caen bajo el cuarto de círculo con proba. igual a su área, $\frac{\pi}{4}$; la fracción que cae ahí, por $4$, aproxima $\pi$.
> ![[monte-carlo-pi.svg|center|550]]

> [!theorem] **Proposición.** (Estimador de Monte Carlo)
>
> Sean $X_{1}, \dots, X_{n}$ v.a.s indep. con la misma distribución que $X$, con media $\mu$ y varianza $\sigma^{2}$ finitas, y $\bar{X}_{n} = \frac{1}{n}\sum_{k=1}^{n} X_{k}$. Ent.
> $$
> \operatorname{E}(\bar{X}_{n}) = \mu, \qquad \sqrt{ \operatorname{Var}(\bar{X}_{n}) } = \frac{\sigma}{\sqrt{ n }}.
> $$
> En particular, si $X = \mathbb{1}_{A}$ (vale $1$ si ocurre $A$), $\bar{X}_{n}$ es la **frecuencia relativa** de $A$, su media es $P(A)$ y su desviación estándar $\sqrt{ \frac{P(A)(1-P(A))}{n} }$.

> [!proof]- **Proof.**
>
> Es el Corolario de la media muestral de [[Varianza]], con $\mu = \operatorname{E}(\mathbb{1}_{A}) = P(A)$ y $\sigma^{2} = P(A)(1 - P(A))$ en el caso de la indicadora ([[Distribucion de Bernoulli]]). $\blacksquare$

> [!observation]+ **Observación.**
>
> 1. El estimador no tiene sesgo (en promedio da el valor correcto) y su error típico baja como $\frac{1}{\sqrt{ n }}$: para ganar **un dígito** de precisión hay que multiplicar $n$ por $100$. Es lento, pero no depende de la dimensión del problema, y por eso es la herramienta estándar en integrales de muchas variables.
> 2. Que $\bar{X}_{n}$ de verdad se acerque a $\mu$ (no solo en promedio) es la ley de los grandes números, que veremos más adelante.

> [!example]- **Ejemplo 1.** (Aproximar $\pi$)
>
> Sean $U, V$ indep. $\operatorname{Unif}(0,1)$ ([[Distribucion Uniforme Continua]]). El punto $(U, V)$ es uniforme en el cuadrado, así que $P(U^{2} + V^{2} \leq 1) = \frac{\pi}{4}$ (el área del cuarto de círculo). Con $n = 1000$ puntos, en la figura cayeron $789$ adentro: $4\cdot\frac{789}{1000} = 3.156$. El error típico de $4\bar{X}_{n}$ es
> $$
> 4\sqrt{ \frac{\frac{\pi}{4}\left( 1 - \frac{\pi}{4} \right)}{1000} } \approx 0.052,
> $$
> así que errores de $\pm 0.05$ son lo normal con mil puntos.

Lo mismo sirve para integrales: por el teorema del estadístico inconsciente, una integral en $[0,1]$ es una esperanza.

> [!theorem] **Proposición.** (Integración de Monte Carlo)
>
> Si $U \sim \operatorname{Unif}(0,1)$ y $g$ es integrable en $[0,1]$, ent. $\displaystyle \int_{0}^{1} g(x)\,dx = \operatorname{E}(g(U))$, y $\frac{1}{n}\sum_{k=1}^{n} g(U_{k})$, con $U_{k}$ uniformes indep., es un estimador de la integral con error típico $\frac{\sigma_{g}}{\sqrt{ n }}$, donde $\sigma_{g}^{2} = \operatorname{Var}(g(U))$.

> [!proof]- **Proof.**
>
> La densidad de $U$ es $1$ en $(0,1)$, así que $\operatorname{E}(g(U)) = \int_{0}^{1} g(x) \cdot 1 \, dx$ ([[Esperanza]]). Lo demás es la Proposición anterior con $X = g(U)$. $\blacksquare$

> [!example]- **Ejemplo 2.**
>
> $\int_{0}^{1} e^{-x^{2}}\,dx$ no tiene antiderivada elemental (ver [[Integral Gaussiana]]), pero promediando $e^{-U_{k}^{2}}$ sobre muchos uniformes se aproxima su valor, $\approx 0.7468$.

Para simular distribuciones que no son uniformes se usa el [[Metodo de la Transformada Inversa]].

---
Volver a [[Distribucion Uniforme Continua]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.3, Ej. 304, y §3.8, Ej. 370 (pp. 213–253). <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
