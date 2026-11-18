---
modified: 2026-11-17T22:20:24Z
title: "Función Gamma"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Gamma de Euler
tags:
 - calculus
 - probability
cssclasses:
 - romana
---
El factorial $n! = 1 \cdot 2 \cdots n$ solo tiene sentido para $n$ natural. ¿Qué sería $\left( \frac{1}{2} \right)!$? La función gamma es la respuesta "correcta": una función definida en todos los reales positivos que pasa por los factoriales y conserva su propiedad clave, $(n+1)! = (n+1)\,n!$. Aparece en todos lados donde hay factoriales escondidos: las densidades [[Distribucion Gamma|gamma]], beta, ji-cuadrada, $t$ y $F$, el volumen de una bola en $\mathbb{R}^{n}$, la fórmula de Stirling.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> $\Gamma$ es el factorial que no necesita enteros.

> [!tip|idea]- **Idea Intuitiva.**
>
> $\int_{0}^{\infty} t^{n}e^{-t}\,dt = n!$, y la integral tiene sentido para cualquier exponente real $> -1$: así se extiende el factorial.

> [!theorem] **Definición.** (Función gamma)
>
> Para $\alpha > 0$, la **función gamma** es
> $$
> \Gamma(\alpha) = \int_{0}^{\infty} t^{\alpha-1}e^{-t} \, dt.
> $$

> [!observation]+ **Observación.**
>
> 1. La integral converge exactamente cuando $\alpha > 0$: cerca de $0$, $t^{\alpha-1}e^{-t}$ se comporta como $t^{\alpha-1}$, integrable en $(0,1]$ sii $\alpha - 1 > -1$; y en $[1,\infty)$ siempre converge porque $e^{-t}$ le gana a cualquier potencia (p. ej. $t^{\alpha-1}e^{-t} \leq C e^{-t/2}$ para $t \geq 1$).
> 2. En general no se puede evaluar en forma cerrada; los valores que sí se conocen salen de la siguiente proposición.

La propiedad que hace de $\Gamma$ un factorial es la recursión; de ella salen todos los valores exactos que vamos a usar.

> [!theorem] **Proposición.** (Propiedades)
>
> 1. $\Gamma(\alpha+1) = \alpha\,\Gamma(\alpha)$ para todo $\alpha > 0$.
> 2. $\Gamma(1) = 1$ y $\Gamma(2) = 1$.
> 3. $\Gamma(n+1) = n!$ para todo $n \in \mathbb{N}$.
> 4. $\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$.

> [!proof]- **Proof.**
>
> 1. Por partes con $u = t^{\alpha}$, $dv = e^{-t}\,dt$ (ent. $du = \alpha t^{\alpha-1}\,dt$, $v = -e^{-t}$):
> $$
> \begin{align}
> & \Gamma(\alpha+1) \\[0.5em]
> &= -t^{\alpha}e^{-t} \bigg|_{0}^{\infty} + \alpha \int_{0}^{\infty} t^{\alpha-1}e^{-t} \, dt \\[0.5em]
> &= 0 + \alpha\,\Gamma(\alpha) \tag{$\alpha > 0$}
> \end{align}
> $$
> El término de frontera es $0$ en $\infty$ porque $e^{-t}$ le gana a $t^{\alpha}$, y en $0$ porque $\alpha > 0$. $\blacksquare$
> 2. $\Gamma(1) = \int_{0}^{\infty} e^{-t}\,dt = 1$, y por 1, $\Gamma(2) = 1 \cdot \Gamma(1) = 1$. $\blacksquare$
> 3. Inducción sobre $n$. Para $n = 0$: $\Gamma(1) = 1 = 0!$. Sup. $\Gamma(n+1) = n!$ (H.I.). Ent. por 1, $\Gamma(n+2) = (n+1)\Gamma(n+1) = (n+1)\,n! = (n+1)!$. $\blacksquare$
> 4. Con el cambio $t = x^{2}$ ($dt = 2x\,dx$, y $t^{-1/2} = \frac{1}{x}$ para $x > 0$):
> $$
> \begin{align}
> & \Gamma\left( \tfrac{1}{2} \right) \\[0.5em]
> &= \int_{0}^{\infty} t^{-1/2}e^{-t} \, dt \\[0.5em]
> &= 2\int_{0}^{\infty} e^{-x^{2}} \, dx \tag{sust.} \\[0.5em]
> &= 2 \cdot \frac{\sqrt{ \pi }}{2} = \sqrt{ \pi }
> \end{align}
> $$
> por la [[Integral Gaussiana]] (la mitad positiva, por paridad). $\blacksquare$

Con 1 y 4 se calculan todos los valores en enteros y semienteros, que son los que aparecen en la [[Distribucion ji-cuadrada|ji-cuadrada]] (con $\frac{n}{2}$ grados de libertad):

> [!example]- **Ejemplo 1.** (Semienteros)
>
> $$
> \Gamma\left( \tfrac{3}{2} \right) = \tfrac{1}{2}\Gamma\left( \tfrac{1}{2} \right) = \frac{\sqrt{ \pi }}{2}, \qquad \Gamma\left( \tfrac{5}{2} \right) = \tfrac{3}{2}\Gamma\left( \tfrac{3}{2} \right) = \frac{3\sqrt{ \pi }}{4}.
> $$
> En general, "$\left( \frac{1}{2} \right)! = \Gamma\left( \frac{3}{2} \right) = \frac{\sqrt{ \pi }}{2}$".

Y al revés: muchas integrales que parecen difíciles son una gamma disfrazada. Basta reconocer $t^{\text{algo}}e^{-t}$ después de un cambio de variable.

> [!example]- **Ejemplo 2.** (Reconocer una gamma)
>
> 1. $\displaystyle \int_{0}^{\infty} x^{4}e^{-x} \, dx = \Gamma(5) = 4! = 24$, sin integrar por partes cuatro veces.
> 2. Con $t = \lambda x$, para $\alpha, \lambda > 0$,
> $$
> \int_{0}^{\infty} x^{\alpha-1}e^{-\lambda x} \, dx = \frac{\Gamma(\alpha)}{\lambda^{\alpha}}.
> $$
> Esta es la integral que normaliza la densidad [[Distribucion Gamma|gamma]] y que calcula todos sus momentos.

> [!Info]- **Nota!** (Dónde más aparece)
>
> - **Función beta:** $B(a,b) = \int_{0}^{1} x^{a-1}(1-x)^{b-1}\,dx = \frac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}$, la constante de la [[Distribucion Beta]].
> - **Volumen de la bola unitaria en $\mathbb{R}^{n}$:** $V_{n} = \frac{\pi^{n/2}}{\Gamma\left( \frac{n}{2} + 1 \right)}$ (da $2$, $\pi$ y $\frac{4}{3}\pi$ para $n = 1, 2, 3$).
> - **Stirling:** $\Gamma(x+1) \sim \sqrt{ 2\pi x }\left( \frac{x}{e} \right)^{x}$ cuando $x \to \infty$, la aproximación de $n!$ para $n$ grande.
>
> Ninguna de estas está probada aquí; son para saber hacia dónde conecta.

---
Se usa en: [[Distribucion Gamma]], [[Distribucion Beta]], [[Distribucion ji-cuadrada]], [[Distribucion t]], [[Distribucion F]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.10 (p. 258) y Ej. 394. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
