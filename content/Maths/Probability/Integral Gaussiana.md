---
modified: 2026-11-17T22:20:24Z
title: "Integral Gaussiana"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Integral de Gauss
tags:
 - calculus
 - probability
cssclasses:
 - romana
---
La función $e^{-x^{2}}$ es de las más importantes de las matemáticas (es la forma de la campana de la [[Distribucion Normal|normal]]), y sin embargo **no tiene antiderivada elemental**: no hay combinación finita de polinomios, exponenciales, logaritmos y funciones trigonométricas cuya derivada sea $e^{-x^{2}}$. Aun así, su integral sobre toda la recta se puede calcular exactamente, con un truco que vale la pena conocer: elevarla al cuadrado.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> No sabemos integrar $e^{-x^{2}}$ en una dimensión, pero sí en dos.

> [!tip|idea]- **Idea Intuitiva.**
>
> El cuadrado de la integral es una integral doble; en polares aparece el factor $r$, y $r e^{-r^{2}}$ sí tiene antiderivada.

> [!theorem] **Teorema.** (Integral gaussiana)
>
> $$
> \int_{-\infty}^{\infty} e^{-x^{2}} \, dx = \sqrt{ \pi }.
> $$

> [!proof]- **Proof.**
>
> **Borrador.** La integral converge (para $\lvert x \rvert \geq 1$, $e^{-x^{2}} \leq e^{-\lvert x \rvert}$). Se eleva al cuadrado, se escribe como integral doble (Fubini, válido porque el integrando es positivo) y se pasa a polares.
>
> **Proof.** Sea $I = \int_{-\infty}^{\infty} e^{-x^{2}}\,dx > 0$. Ent.
> $$
> \begin{align}
> & I^{2} \\[0.5em]
> &= \int_{-\infty}^{\infty} \int_{-\infty}^{\infty} e^{-(x^{2}+y^{2})} \, dx \, dy \tag{Fubini} \\[0.5em]
> &= \int_{0}^{2\pi} \int_{0}^{\infty} e^{-r^{2}}\, r \, dr \, d\theta \tag{polares} \\[0.5em]
> &= 2\pi \left[ -\frac{1}{2}e^{-r^{2}} \right]_{0}^{\infty} = \pi
> \end{align}
> $$
> $\therefore$ $I = \sqrt{ \pi }$. $\blacksquare$

Con un cambio de variable lineal sale la versión con cualquier "ancho", que es la que se usa en la práctica:

> [!theorem] **Corolario.**
>
> Para todo $a > 0$,
> $$
> \int_{-\infty}^{\infty} e^{-ax^{2}} \, dx = \sqrt{ \frac{\pi}{a} }.
> $$
> En particular, con $a = \frac{1}{2}$,
> $$
> \int_{-\infty}^{\infty} e^{-x^{2}/2} \, dx = \sqrt{ 2\pi }.
> $$

> [!proof]- **Proof.**
>
> Con $u = \sqrt{ a }\,x$ ($du = \sqrt{ a }\,dx$),
> $$
> \int_{-\infty}^{\infty} e^{-ax^{2}} \, dx = \frac{1}{\sqrt{ a }} \int_{-\infty}^{\infty} e^{-u^{2}} \, du = \sqrt{ \frac{\pi}{a} }. \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo 1.** (La constante de la normal)
>
> La densidad de la normal estándar es $\frac{1}{\sqrt{ 2\pi }}e^{-x^{2}/2}$: el $\sqrt{ 2\pi }$ está ahí exactamente para que integre $1$, por el Corolario. Con $\mu$ y $\sigma$, el cambio $u = \frac{x-\mu}{\sigma}$ reduce todo a este caso (ver [[Distribucion Normal]]).

> [!example]- **Ejemplo 2.** (Media campana)
>
> Como $e^{-x^{2}}$ es par,
> $$
> \int_{0}^{\infty} e^{-x^{2}} \, dx = \frac{\sqrt{ \pi }}{2}.
> $$
> Esta es la forma que aparece al calcular $\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$ (ver [[Funcion Gamma]]).

> [!observation]+ **Observación.**
>
> 1. El truco **solo** funciona sobre toda la recta (o media recta): $\int_{0}^{b} e^{-x^{2}}\,dx$ no tiene forma cerrada para $b$ finito. Por eso la función de distribución de la normal, $\Phi$, se calcula con tablas o numéricamente.
> 2. El cambio a polares de la prueba es un cambio de variable en $\mathbb{R}^{2}$ con jacobiano $r$; es la versión en dos dimensiones de "sust." en una integral.

---
Se usa en: [[Distribucion Normal]], [[Funcion Gamma]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

El cálculo por polares aparece en Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.13 (p. 269), Ej. 408 y su solución. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
