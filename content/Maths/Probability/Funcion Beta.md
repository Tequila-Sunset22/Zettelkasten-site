---
modified: 2026-11-17T22:20:24Z
title: "Función Beta"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Integral de Euler de primera especie
tags:
 - calculus
 - probability
cssclasses:
 - romana
---
La [[Funcion Gamma]] generaliza al factorial; la función beta hace lo mismo con el **inverso de un coeficiente binomial**. Es la integral de $x^{a-1}(1-x)^{b-1}$ en $[0,1]$, que aparece cada vez que hay una proporción $x$ y su complemento $1-x$ elevados a alguna potencia: la [[Distribucion Beta]], la normalización de la [[Distribucion t|t]] y de la [[Distribucion F|F]], o integrales de polinomios de Bernstein.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> $B$ mide cuánto pesa, en total, "$a$ éxitos y $b$ fracasos" cuando la proba. de éxito recorre $[0,1]$.

> [!theorem] **Definición.** (Función beta)
>
> Para $a > 0$ y $b > 0$, la **función beta** es
> $$
> B(a,b) = \int_{0}^{1} x^{a-1}(1-x)^{b-1} \, dx.
> $$

> [!observation]+ **Observación.**
>
> La integral converge exactamente cuando $a > 0$ y $b > 0$: cerca de $0$ el integrando se comporta como $x^{a-1}$ y cerca de $1$ como $(1-x)^{b-1}$, integrables sii los exponentes son $> -1$.

Calcular $B(a,b)$ directo es difícil, pero no hace falta: se escribe con la gamma, y de ahí sale todo lo demás.

> [!tip|idea]- **Idea Intuitiva.**
>
> En la integral doble de $\Gamma(a)\Gamma(b)$, con $u = s + t$ (tamaño total) y $v = \frac{s}{s+t}$ (proporción) la integral se separa: $u$ da $\Gamma(a+b)$ y $v$ da $B(a,b)$.

> [!theorem] **Teorema.** (Relación con la gamma)
>
> Para $a, b > 0$,
> $$
> B(a,b) = \frac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}.
> $$

> [!proof]- **Proof.**
>
> **Borrador.** Es el cambio de la Idea Intuitiva: $s = uv$, $t = u(1-v)$ con $u > 0$, $v \in (0,1)$, cuyo jacobiano es $u$. Usa Fubini (integrando positivo) y cambio de variable en $\mathbb{R}^{2}$.
>
> **Proof.** Por Fubini,
> $$
> \Gamma(a)\Gamma(b) = \int_{0}^{\infty} \int_{0}^{\infty} s^{a-1}t^{b-1}e^{-(s+t)} \, ds \, dt.
> $$
> Con $s = uv$, $t = u(1-v)$, la transformación $(u,v) \mapsto (s,t)$ es una biyección de $(0,\infty) \times (0,1)$ en $(0,\infty)^{2}$ con jacobiano
> $$
> \left\lvert \det \begin{pmatrix} v & u \\ 1-v & -u \end{pmatrix} \right\rvert = \lvert -uv - u(1-v) \rvert = u.
> $$
> Ent., como $s + t = u$,
> $$
> \begin{align}
> & \Gamma(a)\Gamma(b) \\[0.5em]
> &= \int_{0}^{1} \int_{0}^{\infty} (uv)^{a-1}(u(1-v))^{b-1}e^{-u}\, u \, du \, dv \\[0.5em]
> &= \int_{0}^{\infty} u^{a+b-1}e^{-u} \, du \cdot \int_{0}^{1} v^{a-1}(1-v)^{b-1} \, dv \\[0.5em]
> &= \Gamma(a+b)\,B(a,b)
> \end{align}
> $$
> y se despeja $B(a,b)$. $\blacksquare$

Con esto, todas las propiedades de $B$ son propiedades de $\Gamma$ en una línea:

> [!theorem] **Proposición.** (Propiedades)
>
> Para $a, b > 0$:
> 1. $B(a,b) = B(b,a)$.
> 2. $B(a,1) = \frac{1}{a}$ y $B(1,b) = \frac{1}{b}$.
> 3. $B(a+1,b) = \frac{a}{a+b}B(a,b)$ y $B(a,b+1) = \frac{b}{a+b}B(a,b)$.
> 4. $B(a+1,b) = \frac{a}{b}B(a,b+1)$.
> 5. $B\left( \frac{1}{2}, \frac{1}{2} \right) = \pi$.

> [!proof]- **Proof.**
>
> 1. La fórmula con $\Gamma$ es simétrica en $a$ y $b$. (También sale directo con $u = 1-x$ en la integral.) $\blacksquare$
> 2. $B(a,1) = \int_{0}^{1} x^{a-1}\,dx = \frac{1}{a}$, y por 1, $B(1,b) = B(b,1) = \frac{1}{b}$. $\blacksquare$
> 3. Usando $\Gamma(a+1) = a\,\Gamma(a)$ y $\Gamma(a+b+1) = (a+b)\Gamma(a+b)$,
> $$
> B(a+1,b) = \frac{a\,\Gamma(a)\Gamma(b)}{(a+b)\Gamma(a+b)} = \frac{a}{a+b}B(a,b),
> $$
> y la otra es la misma con los papeles de $a$ y $b$ cambiados (por 1). $\blacksquare$
> 4. Dividiendo las dos igualdades de 3. $\blacksquare$
> 5. $B\left( \frac{1}{2}, \frac{1}{2} \right) = \frac{\Gamma(1/2)^{2}}{\Gamma(1)} = (\sqrt{ \pi })^{2} = \pi$. $\blacksquare$

> [!example]- **Ejemplo 1.** (Enteros y coeficientes binomiales)
>
> Si $a = k+1$ y $b = n-k+1$ con $k, n \in \mathbb{N}$, $k \leq n$, ent. por la relación con la gamma,
> $$
> \int_{0}^{1} x^{k}(1-x)^{n-k} \, dx = \frac{k!\,(n-k)!}{(n+1)!} = \frac{1}{(n+1)\binom{n}{k}}.
> $$
> Por ejemplo, $\int_{0}^{1} x^{2}(1-x)^{3}\,dx = \frac{1}{6 \cdot 10} = \frac{1}{60}$, sin desarrollar el polinomio. Aquí se ve por qué $B$ es "el inverso de un binomial": si la proba. de éxito $p$ fuera uniforme en $[0,1]$, la proba. de obtener exactamente $k$ éxitos en $n$ ensayos sería $\binom{n}{k}\int_{0}^{1} p^{k}(1-p)^{n-k}\,dp = \frac{1}{n+1}$, la misma para todo $k$.

> [!example]- **Ejemplo 2.** (Una integral trigonométrica)
>
> Con $x = \sin^{2}\theta$ ($dx = 2\sin\theta\cos\theta\,d\theta$),
> $$
> B(a,b) = 2\int_{0}^{\pi/2} \sin^{2a-1}\theta \, \cos^{2b-1}\theta \, d\theta.
> $$
> Con $a = b = \frac{1}{2}$ queda $2 \cdot \frac{\pi}{2} = \pi$, otra prueba del inciso 5 (y de que $\Gamma(\frac{1}{2}) = \sqrt{ \pi }$, al revés).

---
Se usa en: [[Distribucion Beta]], [[Distribucion t]], [[Distribucion F]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.11 (pp. 263–265) y Ej. 395. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
