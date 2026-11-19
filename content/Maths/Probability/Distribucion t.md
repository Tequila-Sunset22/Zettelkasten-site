---
modified: 2026-11-18T22:36:04Z
title: "Distribución t"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Distribucion t de Student
 - t de Student
tags:
 - probability
cssclasses:
 - romana
---
Si $X_{1}, \dots, X_{n}$ son normales con media $\mu$ y conocemos $\sigma$, estandarizar el promedio da exactamente una normal estándar: $\frac{\bar{X}-\mu}{\sigma/\sqrt{ n }} \sim \operatorname{N}(0,1)$ (ver [[Distribucion Normal]]). Pero en la vida real **no** conocemos $\sigma$, y lo sustituimos por la desviación muestral $S$. Esa sustitución agrega incertidumbre: a veces $S$ sale chica y el cociente se dispara. La distribución que resulta ya no es normal; la encontró W. S. Gosset (que firmaba "Student") y es la distribución $t$.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> La $t$ es una normal con colas más pesadas, el precio de no conocer $\sigma$.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Campana como la normal estándar, pero con colas más pesadas: estimar $\sigma$ con $S$ agrega incertidumbre. Con $n$ grande $S \approx \sigma$ y la $t$ se pega a la normal. Abajo, $t(n)$ en rojo para $n = 1, 2, 4, 8, 30$ contra $\operatorname{N}(0,1)$ punteada.
>
> <img src="/videos/t-a-normal.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** ($t(n)$)
>
> Sea $n > 0$. Decimos que la v.a. continua $X$ tiene **distribución $t$ (de Student) con $n$ grados de libertad**, y escribimos $X \sim t(n)$, si su función de densidad es
> $$
> f_{X}(x) = \frac{\Gamma\left( \frac{n+1}{2} \right)}{\sqrt{ n\pi }\,\Gamma\left( \frac{n}{2} \right)}\left( 1 + \frac{x^{2}}{n} \right)^{-(n+1)/2}, \qquad x \in \mathbb{R}.
> $$

La constante se ve rara, pero sale de una sola integral, que además da todos los momentos. Es una [[Funcion Beta]] disfrazada:

> [!theorem] **Lema.**
>
> Para $n > 0$ y $m \geq 0$,
> $$
> \int_{-\infty}^{\infty} \lvert x \rvert^{m}\left( 1 + \frac{x^{2}}{n} \right)^{-(n+1)/2} \, dx = \begin{cases}
> n^{(m+1)/2}B\left( \frac{m+1}{2}, \frac{n-m}{2} \right) & \text{ si } m < n \\[0.5em]
> \infty & \text{ si } m \geq n
> \end{cases}
> $$

> [!proof]- **Proof.**
>
> **Borrador.** Para $\lvert x \rvert$ grande el integrando es como $\lvert x \rvert^{m}\cdot\lvert x \rvert^{-(n+1)}$, que es integrable sii $m - n - 1 < -1$, i.e. $m < n$. Para calcularla, el cambio $u = \left( 1 + \frac{x^{2}}{n} \right)^{-1} \in (0,1]$ la convierte en una beta.
>
> **Proof.** El integrando es par, así que la integral es $2\int_{0}^{\infty}$. Con $u = \left( 1 + \frac{x^{2}}{n} \right)^{-1}$ se tiene $x = \sqrt{ n }\left( \frac{1-u}{u} \right)^{1/2}$ y $\lvert dx \rvert = \frac{\sqrt{ n }}{2}u^{-3/2}(1-u)^{-1/2}\,du$. Ent.
> $$
> \begin{align}
> & 2\int_{0}^{\infty} x^{m}\left( 1 + \frac{x^{2}}{n} \right)^{-(n+1)/2} \, dx \\[0.5em]
> &= 2\int_{0}^{1} n^{m/2}\left( \frac{1-u}{u} \right)^{m/2} u^{(n+1)/2}\,\frac{\sqrt{ n }}{2}u^{-3/2}(1-u)^{-1/2} \, du \\[0.5em]
> &= n^{(m+1)/2}\int_{0}^{1} u^{\frac{n-m}{2}-1}(1-u)^{\frac{m+1}{2}-1} \, du
> \end{align}
> $$
> que es $n^{(m+1)/2}B\left( \frac{n-m}{2}, \frac{m+1}{2} \right)$ si $\frac{n-m}{2} > 0$, y diverge si $m \geq n$ (el exponente de $u$ cerca de $0$ es $\leq -1$). Por la simetría de $B$ queda el enunciado. $\blacksquare$

> [!theorem] **Corolario.**
>
> $f_{X}$ es una función de densidad.

> [!proof]- **Proof.**
>
> Con $m = 0$ y $B\left( \frac{1}{2}, \frac{n}{2} \right) = \frac{\Gamma(1/2)\Gamma(n/2)}{\Gamma((n+1)/2)} = \frac{\sqrt{ \pi }\,\Gamma(n/2)}{\Gamma((n+1)/2)}$,
> $$
> \int_{-\infty}^{\infty} f_{X}(x) \, dx = \frac{\Gamma\left( \frac{n+1}{2} \right)}{\sqrt{ n\pi }\,\Gamma\left( \frac{n}{2} \right)} \cdot \sqrt{ n } \cdot \frac{\sqrt{ \pi }\,\Gamma\left( \frac{n}{2} \right)}{\Gamma\left( \frac{n+1}{2} \right)} = 1. \tag*{$\blacksquare$}
> $$

El Lema dice algo muy distinto a lo que pasa con la normal: el momento $m$ **solo existe si $m < n$**. Con pocos grados de libertad, la $t$ ni siquiera tiene media.

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim t(n)$.
> 1. $f_{X}$ es par; la [[Moda]] y la mediana son $0$.
> 2. $\operatorname{E}\lvert X \rvert^{m} < \infty$ sii $m < n$.
> 3. $\operatorname{E}(X) = 0$ si $n > 1$.
> 4. $\operatorname{Var}(X) = \operatorname{E}(X^{2}) = \dfrac{n}{n-2}$ si $n > 2$.
> 5. La f.g.m. **no existe**: $\operatorname{E}(e^{tX}) = \infty$ para todo $t \neq 0$.

> [!proof]- **Proof.**
>
> 1. $f_{X}$ depende de $x$ solo por $x^{2}$, y es estrictamente decreciente en $\lvert x \rvert$: máximo único en $0$. Por simetría $P(X \leq 0) = \frac{1}{2}$, y $F_{X}$ es continua y estrictamente creciente, así que la mediana es $0$. $\blacksquare$
> 2. Es el Lema. $\blacksquare$
> 3. Si $n > 1$, por 2 la esperanza existe, y $xf_{X}(x)$ es impar: $\operatorname{E}(X) = 0$. $\blacksquare$
> 4. Por el Lema con $m = 2$ y el Corolario,
> $$
> \operatorname{E}(X^{2}) = n\,\frac{B\left( \frac{3}{2}, \frac{n-2}{2} \right)}{B\left( \frac{1}{2}, \frac{n}{2} \right)} = n\,\frac{\Gamma(3/2)}{\Gamma(1/2)}\cdot\frac{\Gamma\left( \frac{n-2}{2} \right)}{\Gamma\left( \frac{n}{2} \right)} = n \cdot \frac{1}{2} \cdot \frac{2}{n-2},
> $$
> usando $\Gamma(\beta+1) = \beta\,\Gamma(\beta)$ dos veces. Como $\operatorname{E}(X) = 0$, $\operatorname{Var}(X) = \frac{n}{n-2}$. $\blacksquare$
> 5. Sea $t > 0$ (para $t < 0$ es igual por simetría) y $k \geq n$ entero. Para $x > 0$, $e^{tx} \geq \frac{(tx)^{k}}{k!}$, así que $\operatorname{E}(e^{tX}) \geq \frac{t^{k}}{k!}\int_{0}^{\infty} x^{k}f_{X}(x)\,dx = \infty$ por 2. $\blacksquare$

> [!example]- **Ejemplo 1.** ($n = 1$: la Cauchy)
>
> Con $n = 1$, $\Gamma(1) = 1$ y $\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$, la densidad queda
> $$
> f_{X}(x) = \frac{1}{\pi(1 + x^{2})},
> $$
> la **distribución de Cauchy**. Es simétrica alrededor de $0$, su mediana es $0$, y sin embargo **no tiene esperanza**: $\int \lvert x \rvert f_{X} = \infty$. El "centro" existe en el sentido de la mediana, pero no en el de la [[Esperanza]].

> [!example]- **Ejemplo 2.** (Qué tan pesadas son las colas)
>
> $P(\lvert X \rvert > 2)$ para $X \sim t(n)$ contra $Z \sim \operatorname{N}(0,1)$:
>
> | $n$ | $1$ | $3$ | $5$ | $30$ | normal |
> |---|---|---|---|---|---|
> | $P(\lvert X \rvert > 2)$ | $0.295$ | $0.139$ | $0.102$ | $0.055$ | $0.046$ |
>
> En la práctica: el valor que deja $2.5\%$ en cada cola es $1.96$ para la normal, pero $2.262$ para $t(9)$. Con $10$ datos, un intervalo de confianza al $95\%$ es un $15\%$ más ancho que si conociéramos $\sigma$.

### De dónde sale

> [!theorem] **Proposición.**
>
> Si $Z \sim \operatorname{N}(0,1)$ y $Y \sim \chi^{2}(n)$ son [[Independencia de Variables Aleatorias|independientes]], ent.
> $$
> \frac{Z}{\sqrt{ Y/n }} \sim t(n).
> $$

> [!proof]- **Proof.**
>
> %% Pendiente: prueba cuando esté la nota de vectores aleatorios (densidad de un cociente). %%
> Se calcula la densidad del cociente a partir de la densidad conjunta $\phi(z)f_{Y}(y)$, cambiando a $(t, y)$ con $t = \frac{z}{\sqrt{ y/n }}$ e integrando $y$; la integral en $y$ es una gamma. Necesita vectores aleatorios.

$\frac{Y}{n}$ es un promedio de $n$ cuadrados de normales estándar (ver [[Distribucion ji-cuadrada]]), así que $\sqrt{ Y/n }$ es una "desviación estándar estimada" que tiende a $1$. Dividir entre ella es exactamente lo que se hace al estandarizar con $S$ en vez de $\sigma$:

> [!theorem] **Corolario.**
>
> Sean $X_{1}, \dots, X_{n}$ indep., cada una $\operatorname{N}(\mu, \sigma^{2})$, con $\bar{X}$ y $S^{2}$ el promedio y la varianza muestral. Ent.
> $$
> \frac{\bar{X} - \mu}{S/\sqrt{ n }} \sim t(n-1).
> $$

> [!proof]- **Proof.**
>
> %% Pendiente: usa la independencia de X̄ y S² (vectores aleatorios). %%
> Se escribe
> $$
> \frac{\bar{X} - \mu}{S/\sqrt{ n }} = \frac{\frac{\bar{X} - \mu}{\sigma/\sqrt{ n }}}{\sqrt{ \frac{(n-1)S^{2}}{\sigma^{2}} \big/ (n-1) }},
> $$
> donde el numerador es $\operatorname{N}(0,1)$ y la cantidad dentro de la raíz es $\chi^{2}(n-1)$ entre $n-1$ (Varianza muestral, en [[Distribucion ji-cuadrada]]). Si son independientes (lo son, pero hace falta probarlo), es la Proposición con $n - 1$. $\blacksquare$

### Convergencia a la normal

Lo que muestra la animación se puede probar: la densidad $t(n)$ converge, punto a punto, a la normal estándar.

> [!theorem] **Proposición.**
>
> Para todo $x \in \mathbb{R}$,
> $$
> \lim_{n \to \infty} f_{t(n)}(x) = \frac{1}{\sqrt{ 2\pi }}e^{-x^{2}/2}.
> $$

> [!proof]- **Proof.**
>
> **Borrador.** La parte que depende de $x$ es casi $\left( 1 + \frac{x^{2}}{n} \right)^{n}$ elevada a $-\frac{1}{2}$, que tiende a $e^{-x^{2}/2}$. La constante tiende a $\frac{1}{\sqrt{ 2\pi }}$ por cómo crece $\Gamma$.
>
> **Proof.** *(La parte en $x$)* Como $\ln(1+y) = y + o(y)$ cuando $y \to 0$,
> $$
> \ln\left( 1 + \frac{x^{2}}{n} \right)^{-(n+1)/2} = -\frac{n+1}{2}\left( \frac{x^{2}}{n} + o\left( \tfrac{1}{n} \right) \right) \xrightarrow[n \to \infty]{} -\frac{x^{2}}{2}.
> $$
> *(La constante)* Por la fórmula de Stirling (ver [[Funcion Gamma]]), $\frac{\Gamma(y + 1/2)}{\Gamma(y)\sqrt{ y }} \to 1$ cuando $y \to \infty$. Con $y = \frac{n}{2}$,
> $$
> \frac{\Gamma\left( \frac{n+1}{2} \right)}{\sqrt{ n\pi }\,\Gamma\left( \frac{n}{2} \right)} = \frac{\Gamma\left( \frac{n}{2} + \frac{1}{2} \right)}{\Gamma\left( \frac{n}{2} \right)\sqrt{ \frac{n}{2} }}\cdot\frac{1}{\sqrt{ 2\pi }} \xrightarrow[n \to \infty]{} \frac{1}{\sqrt{ 2\pi }}.
> $$
> El producto de los dos límites es la densidad normal estándar. $\blacksquare$

> [!observation]+ **Observación.**
>
> Esto justifica la regla práctica de usar la normal en vez de la $t$ cuando hay muchos datos ($n \gtrsim 30$): en la tabla del Ejemplo 2, con $n = 30$ la proba. de las colas ya casi coincide con la de la normal. Con pocos datos, usar la normal subestima la incertidumbre.

---
Siguiente: [[Distribucion F]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.15 (pp. 283–286) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
