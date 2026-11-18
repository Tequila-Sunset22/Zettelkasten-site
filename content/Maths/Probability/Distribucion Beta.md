---
modified: 2026-11-17T22:20:24Z
title: "Distribución Beta"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Variable Aleatoria Beta
tags:
 - probability
cssclasses:
 - romana
---
Muchas cantidades aleatorias viven en $(0,1)$: una proporción, un porcentaje, o la misma proba. de éxito de una moneda que no conocemos. La [[Distribucion Uniforme Continua|uniforme]] es el modelo más simple ahí, pero dice que todos los valores son igual de creíbles. La familia beta es la forma natural de modelar cantidades en $(0,1)$ con **cualquier forma**: cargada a la izquierda, a la derecha, concentrada en el centro o en los extremos. La uniforme es solo uno de sus miembros.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> La beta es la distribución de una proporción.

> [!tip|idea]+ **Idea Intuitiva.**
>
> $a$ empuja la masa hacia $1$ y $b$ hacia $0$. Con $a = b$ es simétrica; con $a, b > 1$ tiene joroba; con $a, b < 1$ tiene forma de U; con $a = b = 1$ es la uniforme.
> ![[densidad-beta.svg|center|600]]

> [!theorem] **Definición.** ($\operatorname{Beta}(a, b)$)
>
> Sean $a > 0$ y $b > 0$. Decimos que la v.a. continua $X$ tiene **distribución beta** con parámetros $a$ y $b$, y escribimos $X \sim \operatorname{Beta}(a,b)$, si su función de densidad es
> $$
> f_{X}(x) = \frac{1}{B(a,b)}\, x^{a-1}(1-x)^{b-1} \cdot \mathbb{1}_{(0,1)}(x),
> $$
> donde $B(a,b) = \int_{0}^{1} x^{a-1}(1-x)^{b-1}\,dx$ es la [[Funcion Beta]].

La constante $B(a,b)$ está ahí exactamente para que $f_{X}$ integre $1$, por definición de la función beta. Y como $B(a,b) = \frac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}$, los momentos salen igual que en la [[Distribucion Gamma|gamma]]: subir el exponente de $x$ es cambiar $a$ por $a + n$.

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Beta}(a,b)$.
> 1. $\displaystyle \operatorname{E}(X^{n}) = \frac{B(a+n,b)}{B(a,b)} = \frac{a(a+1)\cdots(a+n-1)}{(a+b)(a+b+1)\cdots(a+b+n-1)}$ para $n \in \mathbb{N}$.
> 2. $\displaystyle \operatorname{E}(X) = \frac{a}{a+b}$ y $\displaystyle \operatorname{Var}(X) = \frac{ab}{(a+b)^{2}(a+b+1)}$.
> 3. ([[Moda]]) Si $a > 1$ y $b > 1$, la moda es única: $x^{*} = \frac{a-1}{a+b-2}$.
> 4. $1 - X \sim \operatorname{Beta}(b, a)$.
> 5. Para $x \in (0,1)$: si $b = 1$, $F(x) = x^{a}$; si $a = 1$, $F(x) = 1 - (1-x)^{b}$. En general $F$ no tiene forma cerrada.
> 6. $\operatorname{Beta}(1,1) = \operatorname{Unif}(0,1)$.

> [!proof]- **Proof.**
>
> 1. $\displaystyle \operatorname{E}(X^{n}) = \frac{1}{B(a,b)}\int_{0}^{1} x^{a+n-1}(1-x)^{b-1}\,dx = \frac{B(a+n,b)}{B(a,b)}$, y aplicando $n$ veces $B(c+1,b) = \frac{c}{c+b}B(c,b)$ (Propiedades de la [[Funcion Beta]]) con $c = a, a+1, \dots, a+n-1$ se obtiene el producto. $\blacksquare$
> 2. Con $n = 1$, $\operatorname{E}(X) = \frac{a}{a+b}$. Con $n = 2$,
> $$
> \begin{align}
> & \operatorname{Var}(X) \\[0.5em]
> &= \frac{a(a+1)}{(a+b)(a+b+1)} - \frac{a^{2}}{(a+b)^{2}} \\[0.5em]
> &= \frac{a(a+1)(a+b) - a^{2}(a+b+1)}{(a+b)^{2}(a+b+1)} \tag{común denom.} \\[0.5em]
> &= \frac{ab}{(a+b)^{2}(a+b+1)}
> \end{align}
> $$
> pues el numerador es $a\left[ (a+1)(a+b) - a(a+b+1) \right] = a\,b$. $\blacksquare$
> 3. En $(0,1)$, $\frac{d}{dx}\ln f_{X}(x) = \frac{a-1}{x} - \frac{b-1}{1-x}$, que se anula sii $(a-1)(1-x) = (b-1)x$, i.e. $x = \frac{a-1}{a+b-2}$, un punto de $(0,1)$ porque $a, b > 1$. Como $\frac{a-1}{x}$ decrece y $\frac{b-1}{1-x}$ crece, la derivada pasa de positiva a negativa ahí: máximo único. $\blacksquare$
> 4. $\varphi(x) = 1 - x$ es decreciente con $\lvert (\varphi^{-1})' \rvert = 1$, así que por [[Cambio de Variable Aleatoria|cambio de v.a.]], para $y \in (0,1)$, $f_{1-X}(y) = f_{X}(1-y) = \frac{1}{B(a,b)}(1-y)^{a-1}y^{b-1}$, que es la densidad $\operatorname{Beta}(b,a)$ porque $B(a,b) = B(b,a)$. $\blacksquare$
> 5. Si $b = 1$, $B(a,1) = \frac{1}{a}$ y $F(x) = a\int_{0}^{x} u^{a-1}\,du = x^{a}$. Si $a = 1$, por 4, $1 - X \sim \operatorname{Beta}(b,1)$, ent. $F(x) = P(1 - X \geq 1 - x) = 1 - (1-x)^{b}$. $\blacksquare$
> 6. Con $a = b = 1$, $B(1,1) = 1$ y $f_{X} = \mathbb{1}_{(0,1)}$. $\blacksquare$

> [!example]- **Ejemplo 1.** (Leer los parámetros)
>
> Si $X \sim \operatorname{Beta}(2,5)$, ent. $\operatorname{E}(X) = \frac{2}{7} \approx 0.286$, la moda es $\frac{1}{5}$ y $\operatorname{Var}(X) = \frac{10}{49 \cdot 8} \approx 0.0255$. La masa está cargada a la izquierda (hay "más fracasos que éxitos"), y la moda queda a la izquierda de la media por la cola derecha.
>
> Si en cambio $X \sim \operatorname{Beta}(2,1)$, $F(x) = x^{2}$ y $P(X \leq \frac{1}{2}) = \frac{1}{4}$: solo un cuarto de la probabilidad está en la mitad izquierda.

> [!observation]+ **Observación.** (La media no fija la forma)
>
> $\operatorname{Beta}(1,1)$, $\operatorname{Beta}(2,2)$ y $\operatorname{Beta}(\frac{1}{2},\frac{1}{2})$ tienen las tres media $\frac{1}{2}$, pero la primera es plana, la segunda tiene una joroba en $\frac{1}{2}$ y la tercera tiene forma de U, con la mayor parte de la probabilidad **lejos** de $\frac{1}{2}$. Lo que las distingue es $a + b$: entre más grande, más concentrada (la varianza decrece como $\frac{1}{a+b+1}$ con la media fija).

### De dónde sale

Si $X$ es el tiempo hasta $a$ eventos y $Y$ el tiempo hasta otros $b$ eventos independientes, al mismo ritmo, ¿qué fracción del tiempo total se llevó la primera espera? La respuesta es una beta, y explica por qué la constante de la beta se escribe con gammas.

> [!theorem] **Proposición.**
>
> Sean $X \sim \operatorname{Gamma}(a,\lambda)$ y $Y \sim \operatorname{Gamma}(b,\lambda)$ [[Independencia de Variables Aleatorias|independientes]]. Ent.
> $$
> \frac{X}{X+Y} \sim \operatorname{Beta}(a,b).
> $$

> [!proof]- **Proof.**
>
> %% Pendiente: prueba cuando esté la nota de vectores aleatorios (densidad conjunta y cambio de variable en R^2). %%
> Es el mismo cambio $u = x + y$, $v = \frac{x}{x+y}$ de la prueba de $B(a,b) = \frac{\Gamma(a)\Gamma(b)}{\Gamma(a+b)}$ en [[Funcion Beta]], ahora aplicado a la densidad conjunta $f_{X}(x)f_{Y}(y)$: la parte en $u$ es una $\operatorname{Gamma}(a+b,\lambda)$ y la parte en $v$ una $\operatorname{Beta}(a,b)$. Hace falta el cambio de variable para vectores aleatorios, que todavía no vemos.

> [!Info]- **Nota!** (Dónde más aparece)
>
> - **Estadística bayesiana:** si la proba. de éxito $p$ de una moneda se modela como $\operatorname{Beta}(a,b)$ y observamos $k$ éxitos en $n$ lanzamientos, la distribución actualizada de $p$ es $\operatorname{Beta}(a+k, b+n-k)$: los parámetros literalmente cuentan éxitos y fracasos.
> - **Estadísticos de orden:** si $U_{1}, \dots, U_{n}$ son uniformes indep. en $(0,1)$, el $k$-ésimo más chico es $\operatorname{Beta}(k, n-k+1)$.
>
> Ninguna está probada aquí; necesitan distribuciones condicionales y vectores aleatorios.

---
Siguiente: [[Distribucion Weibull]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.11 (pp. 263–265) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
