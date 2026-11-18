---
modified: 2026-11-17T22:20:24Z
title: "Distribución F"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Distribucion F de Fisher-Snedecor
 - F de Fisher
tags:
 - probability
cssclasses:
 - romana
---
La [[Distribucion t|$t$]] responde "¿esta media es distinta de $\mu$?" usando una normal entre una desviación estimada. La distribución $F$ responde la pregunta siguiente: **¿estas dos varianzas son iguales?** Para compararlas se divide una entre la otra, y cada varianza muestral es una [[Distribucion ji-cuadrada|ji-cuadrada]] reescalada, así que la $F$ es la distribución de un cociente de dos ji-cuadradas independientes, cada una dividida entre sus grados de libertad. Es la base del análisis de varianza (ANOVA) y de las pruebas en regresión.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> $F(a,b)$ es el cociente de dos varianzas estimadas, con $a$ y $b$ grados de libertad.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Si las dos varianzas son iguales, el cociente anda cerca de $1$. Con pocos grados de libertad las estimaciones varían mucho, y la $F$ tiene cola larga a la derecha.
> ![[densidad-f.svg|center|600]]

> [!theorem] **Definición.** ($F(a,b)$)
>
> Sean $a > 0$ y $b > 0$. Decimos que la v.a. continua $X$ tiene **distribución $F$** (de Fisher–Snedecor) con $a$ y $b$ grados de libertad, y escribimos $X \sim F(a,b)$, si su función de densidad es
> $$
> f_{X}(x) = \frac{\Gamma\left( \frac{a+b}{2} \right)}{\Gamma\left( \frac{a}{2} \right)\Gamma\left( \frac{b}{2} \right)}\left( \frac{a}{b} \right)^{a/2}x^{a/2-1}\left( 1 + \frac{a}{b}x \right)^{-(a+b)/2} \cdot \mathbb{1}_{(0,\infty)}(x).
> $$
> El orden importa: $a$ son los grados de libertad del **numerador** y $b$ los del **denominador**.

Como en la $t$, la constante y todos los momentos salen de una sola integral que es una [[Funcion Beta]] disfrazada:

> [!theorem] **Lema.**
>
> Para $p, q > 0$,
> $$
> \int_{0}^{\infty} \frac{s^{p-1}}{(1+s)^{p+q}} \, ds = B(p,q).
> $$

> [!proof]- **Proof.**
>
> Con $u = \frac{1}{1+s} \in (0,1)$: $s = \frac{1-u}{u}$, $\lvert ds \rvert = \frac{du}{u^{2}}$ y $1 + s = \frac{1}{u}$. Ent.
> $$
> \int_{0}^{\infty} \frac{s^{p-1}}{(1+s)^{p+q}} \, ds = \int_{0}^{1} \frac{(1-u)^{p-1}}{u^{p-1}}\,u^{p+q}\,\frac{du}{u^{2}} = \int_{0}^{1} u^{q-1}(1-u)^{p-1} \, du = B(q,p),
> $$
> y $B(q,p) = B(p,q)$. $\blacksquare$

> [!theorem] **Proposición.** (Momentos)
>
> Sea $X \sim F(a,b)$. Para $k \geq 0$ con $2k < b$,
> $$
> \operatorname{E}(X^{k}) = \left( \frac{b}{a} \right)^{k}\frac{B\left( \frac{a}{2}+k, \frac{b}{2}-k \right)}{B\left( \frac{a}{2}, \frac{b}{2} \right)} = \left( \frac{b}{a} \right)^{k}\frac{\Gamma\left( \frac{a}{2}+k \right)\Gamma\left( \frac{b}{2}-k \right)}{\Gamma\left( \frac{a}{2} \right)\Gamma\left( \frac{b}{2} \right)},
> $$
> y si $2k \geq b$, $\operatorname{E}(X^{k}) = \infty$. Con $k = 0$: $f_{X}$ es una función de densidad.

> [!proof]- **Proof.**
>
> Con $s = \frac{a}{b}x$ ($dx = \frac{b}{a}\,ds$), y $c = \frac{(a/b)^{a/2}}{B(a/2, b/2)}$ la constante de la densidad (pues $\frac{\Gamma(\frac{a+b}{2})}{\Gamma(\frac{a}{2})\Gamma(\frac{b}{2})} = \frac{1}{B(a/2,b/2)}$),
> $$
> \begin{align}
> & \operatorname{E}(X^{k}) \\[0.5em]
> &= c\int_{0}^{\infty} x^{a/2+k-1}\left( 1 + \frac{a}{b}x \right)^{-(a+b)/2} \, dx \\[0.5em]
> &= c\left( \frac{b}{a} \right)^{a/2+k}\int_{0}^{\infty} \frac{s^{a/2+k-1}}{(1+s)^{(a/2+k)+(b/2-k)}} \, ds \tag{sust.} \\[0.5em]
> &= \left( \frac{b}{a} \right)^{k}\frac{B\left( \frac{a}{2}+k, \frac{b}{2}-k \right)}{B\left( \frac{a}{2}, \frac{b}{2} \right)} \tag{Lema}
> \end{align}
> $$
> si $\frac{b}{2} - k > 0$. Si $\frac{b}{2} - k \leq 0$, para $s$ grande el integrando es como $s^{-1-(b/2-k)}$ con exponente $\geq -1$, y la integral diverge. La forma con $\Gamma$ es $B = \frac{\Gamma\Gamma}{\Gamma}$, donde $\Gamma\left( \frac{a+b}{2} \right)$ se cancela. $\blacksquare$

Igual que en la $t$, los momentos solo existen hasta cierto orden, ahora controlado por los grados de libertad del **denominador**:

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim F(a,b)$.
> 1. $\operatorname{E}(X) = \dfrac{b}{b-2}$ si $b > 2$.
> 2. $\operatorname{Var}(X) = \dfrac{2b^{2}(a+b-2)}{a(b-2)^{2}(b-4)}$ si $b > 4$.
> 3. ([[Moda]]) Si $a > 2$, la moda es única: $x^{*} = \dfrac{b(a-2)}{a(b+2)}$.
> 4. La f.g.m. no existe: $\operatorname{E}(e^{tX}) = \infty$ para todo $t > 0$.

> [!proof]- **Proof.**
>
> 1. Proposición con $k = 1$ y $\Gamma(\beta+1) = \beta\,\Gamma(\beta)$: $\frac{b}{a}\cdot\frac{a/2}{b/2-1} = \frac{b}{b-2}$. $\blacksquare$
> 2. Con $k = 2$, $\operatorname{E}(X^{2}) = \frac{b^{2}}{a^{2}}\cdot\frac{\frac{a}{2}\left( \frac{a}{2}+1 \right)}{\left( \frac{b}{2}-1 \right)\left( \frac{b}{2}-2 \right)} = \frac{b^{2}(a+2)}{a(b-2)(b-4)}$, y restando $\operatorname{E}^{2}(X) = \frac{b^{2}}{(b-2)^{2}}$ con común denominador $a(b-2)^{2}(b-4)$ el numerador queda $b^{2}\left[ (a+2)(b-2) - a(b-4) \right] = 2b^{2}(a+b-2)$. $\blacksquare$
> 3. En $(0,\infty)$, $\frac{d}{dx}\ln f_{X}(x) = \frac{a/2 - 1}{x} - \frac{a+b}{2}\cdot\frac{a/b}{1 + \frac{a}{b}x}$. Igualando a $0$: $(a-2)(b + ax) = a(a+b)x$, i.e. $x = \frac{b(a-2)}{a(b+2)}$, positivo sii $a > 2$; la derivada pasa de positiva a negativa ahí. $\blacksquare$
> 4. Para $t > 0$ y $k$ entero con $2k \geq b$, $e^{tx} \geq \frac{(tx)^{k}}{k!}$ en $x > 0$, y $\operatorname{E}(X^{k}) = \infty$ por la Proposición. $\blacksquare$

> [!example]- **Ejemplo 1.**
>
> Si $X \sim F(4, 10)$: $\operatorname{E}(X) = \frac{10}{8} = 1.25$, $\operatorname{Var}(X) = \frac{2 \cdot 100 \cdot 12}{4 \cdot 64 \cdot 6} = 1.5625$ y la moda es $\frac{10 \cdot 2}{4 \cdot 12} \approx 0.417$. La media es mayor que $1$ aunque la $F$ "compare varianzas iguales": la cola derecha la jala.

### De dónde sale

> [!theorem] **Proposición.**
>
> Si $X \sim \chi^{2}(a)$ y $Y \sim \chi^{2}(b)$ son [[Independencia de Variables Aleatorias|independientes]], ent.
> $$
> \frac{X/a}{Y/b} \sim F(a,b).
> $$

> [!proof]- **Proof.**
>
> %% Pendiente: prueba cuando esté la nota de vectores aleatorios (densidad de un cociente). %%
> Como en la $t$: densidad conjunta $f_{X}(x)f_{Y}(y)$, cambio a $(w, y)$ con $w = \frac{x/a}{y/b}$, e integrar $y$ (sale una gamma). Necesita vectores aleatorios.

> [!observation]+ **Observación.** (Comparar varianzas)
>
> Con dos muestras normales independientes, de tamaños $n_{1}$ y $n_{2}$ y la **misma** varianza $\sigma^{2}$, cada $\frac{(n_{i}-1)S_{i}^{2}}{\sigma^{2}}$ es $\chi^{2}(n_{i}-1)$ (ver [[Distribucion ji-cuadrada]]), y por la Proposición
> $$
> \frac{S_{1}^{2}}{S_{2}^{2}} \sim F(n_{1}-1, n_{2}-1).
> $$
> La $\sigma^{2}$ desconocida se cancela: por eso la $F$ sirve para probar si dos varianzas son iguales.

Dos relaciones con las que se lee cualquier tabla de la $F$. La primera dice que voltear el cociente intercambia los grados de libertad:

> [!theorem] **Proposición.** (Recíproco)
>
> Si $X \sim F(a,b)$, ent. $\frac{1}{X} \sim F(b,a)$.

> [!proof]- **Proof.**
>
> $\varphi(x) = \frac{1}{x}$ es estrictamente decreciente en $(0,\infty)$, con $\lvert (\varphi^{-1})'(y) \rvert = \frac{1}{y^{2}}$. Por [[Cambio de Variable Aleatoria|cambio de v.a.]], para $y > 0$, con $K = \frac{\Gamma(\frac{a+b}{2})}{\Gamma(\frac{a}{2})\Gamma(\frac{b}{2})}$,
> $$
> \begin{align}
> & f_{1/X}(y) \\[0.5em]
> &= f_{X}\left( \frac{1}{y} \right)\frac{1}{y^{2}} = K\left( \frac{a}{b} \right)^{a/2}y^{1-a/2}\left( \frac{by + a}{by} \right)^{-(a+b)/2}\frac{1}{y^{2}} \\[0.5em]
> &= K\left( \frac{b}{a} \right)^{b/2}y^{b/2-1}\left( 1 + \frac{b}{a}y \right)^{-(a+b)/2}
> \end{align}
> $$
> sacando $a^{-(a+b)/2}$ del paréntesis y juntando potencias de $y$ y de $\frac{a}{b}$. Es la densidad $F(b,a)$. $\blacksquare$

> [!theorem] **Corolario.** ([[Cuantiles]])
>
> Sea $c_{p}(a,b)$ el cuantil $p$ de $F(a,b)$. Ent. $c_{p}(a,b) = \dfrac{1}{c_{1-p}(b,a)}$.

> [!proof]- **Proof.**
>
> Para $x > 0$, $P(X \leq x) = P\left( \frac{1}{X} \geq \frac{1}{x} \right) = 1 - P\left( \frac{1}{X} \leq \frac{1}{x} \right)$. Las dos funciones de distribución son continuas y estrictamente crecientes en $(0,\infty)$, así que $P(X \leq x) = p$ sii $P\left( \frac{1}{X} \leq \frac{1}{x} \right) = 1-p$, i.e. $x = c_{p}(a,b)$ sii $\frac{1}{x} = c_{1-p}(b,a)$. $\blacksquare$

> [!example]- **Ejemplo 2.** (Tablas)
>
> Las tablas solo traen las colas derechas ($p = 0.95, 0.99, \dots$). Para la izquierda: $c_{0.05}(4,10) = \frac{1}{c_{0.95}(10,4)} \approx \frac{1}{5.964} \approx 0.168$.

La segunda conecta con la $t$: el cuadrado de una $t$ es una $F$ con un grado de libertad en el numerador.

> [!theorem] **Proposición.** ($t^{2}$)
>
> Si $T \sim t(n)$, ent. $T^{2} \sim F(1, n)$.

> [!proof]- **Proof.**
>
> Para $y > 0$, $F_{T^{2}}(y) = F_{T}(\sqrt{ y }) - F_{T}(-\sqrt{ y })$, y derivando (la densidad $t$ es par),
> $$
> f_{T^{2}}(y) = \frac{f_{T}(\sqrt{ y })}{\sqrt{ y }} = \frac{\Gamma\left( \frac{n+1}{2} \right)}{\sqrt{ n\pi }\,\Gamma\left( \frac{n}{2} \right)}\,y^{-1/2}\left( 1 + \frac{y}{n} \right)^{-(n+1)/2}.
> $$
> La densidad $F(1,n)$ es $\frac{\Gamma(\frac{n+1}{2})}{\Gamma(\frac{1}{2})\Gamma(\frac{n}{2})}\left( \frac{1}{n} \right)^{1/2}y^{-1/2}\left( 1 + \frac{y}{n} \right)^{-(n+1)/2}$, la misma porque $\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Es lo esperable: si $T = \frac{Z}{\sqrt{ Y/n }}$, ent. $T^{2} = \frac{Z^{2}/1}{Y/n}$ con $Z^{2} \sim \chi^{2}(1)$. Por eso una prueba $t$ de dos colas y una prueba $F$ con $(1, n)$ grados de libertad son la misma prueba: $P(\lvert T \rvert > c) = P(T^{2} > c^{2})$.

---
Con esto terminan las distribuciones continuas de [[Probabilidad]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.16 (pp. 287–289) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
