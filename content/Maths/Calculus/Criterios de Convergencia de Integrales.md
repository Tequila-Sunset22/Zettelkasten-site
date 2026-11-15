---
modified: 2026-11-15T17:20:37Z
title: "Criterios de Convergencia"
publish: true
type: zettel
date: "2026-09-01"
status: seed
aliases:
tags:
 - calculus
cssclasses:
 - romana
---
> $\displaystyle \square \ \int_{1}^{\infty} \frac{\cos(x^{3})}{x^{2}} \, dx$
> ¿Cómo podemos determinar que converge (o no)?

> [!theorem] **Teorema.** (Criterio 1)
>
> Supongamos que $f$ es no negativa e integrable en $[a,b]$ para todo $b > a$, sea $\displaystyle y_{n} := \int_{a}^{n} f(x) \, dx$ (para $n \geq a$). Entonces,
> $$
> \int_{a}^{\infty} f(x) \, dx \text{ converge } \iff \{ y_{n} \} \text{ está acotada sup.}
> $$


> [!proof]- **Proof.**
>
> $(\impliedby)$
> $y_{n}\leq y_{n+1}$ porque $f$ es no negativa $\left( \int_{a}^{b} f \geq  0  \right)$ y $\displaystyle y_{n} = \int_{a}^{n} f(x) \, dx \leq  \int_{a}^{n} f(x) \, dx + \int_{n}^{n+1} f(x) \, dx = y_{n+1}$
> Así, $\{ y_{n} \}$ es creciente acotada por arriba por lo que converge a su supremo $(\alpha)$.
> Falta pasar de $n$ entero a $b$ real. Sea $F(b) = \int_{a}^{b} f(x)\,dx$; por lo mismo ($f \geq 0$), $F$ es creciente. Dado $\varepsilon > 0$, existe $N$ con $\alpha - \varepsilon < y_{N} \leq \alpha$, y para todo $b \geq N$,
> $$
> \alpha - \varepsilon < y_{N} = F(N) \leq F(b) \leq F(\lceil b \rceil) = y_{\lceil b \rceil} \leq \alpha
> $$
> Por esto, $\displaystyle \int_{a}^{\infty} f(x) \, dx = \lim_{b \to \infty} F(b) = \alpha$
> $(\implies )$
> Si $\int_{a}^{\infty} f(x) \, dx$ converge es porque $\displaystyle  \lim_{b \to \infty} \int_{a}^{b} f(x) \, dx = \alpha$. Esto es,
> $$
> \forall \varepsilon > 0 \ \exists N \in  \mathbb{N} \left(n \geq N \implies \left| \int_{a}^{n} f(x) \, dx - \alpha  \right| < \varepsilon \right)
> $$
> Tomando $\varepsilon = 1$, $\left| y_{n} - \alpha \right| < 1$, ent.
> $$
> y_n = \int_{a}^{n} f(x) \, dx \leq 1 + \alpha  \quad \forall  n\geq N
> $$
> Para acotar los finitos términos $y_{n}$ con $n < N$ tome su máximo ($M$). De esta forma $\{ y_{n} \}$ está acotado por $\max \left\{M, 1+\alpha \right\}$ con lo que se tiene el resultado 
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Este criterio es solo para integrales impropias de 1ra clase; para las de 2da clase está el Criterio 4 (abajo).

> [!theorem] **Corolario.**
>
> Bajo las mismas hipótesis del Criterio 1,
> $$
> \int_{a}^{\infty} f(x) \, dx \text{ converge } \iff  \exists M \ \left( \int_{a}^{b} f(x) \, dx \leq M \quad \forall  b>a \right)
> $$

> [!proof]- **Proof.**
>
> $(\implies)$ En la prueba del Criterio 1 vimos que $F(b) = \int_{a}^{b} f$ es creciente y converge a $\alpha$, ent. $F(b) \leq \alpha =: M$ para todo $b$.
> $(\impliedby)$ En particular $y_{n} \leq M$ para todo $n$, y por el Criterio 1 converge. $\blacksquare$


> [!theorem] **Teorema.** (Criterio 2)
>
> Sean $f,g: [a,\infty) \to \mathbb{R}$ no negativas, integrables en $[a,b]$ para todo $b > a$, tales que $f\leq g$, entonces,
> 1. Si $\displaystyle \int_{a}^{\infty} g(x) \, dx$ converge, también $\displaystyle \int_{a}^{\infty} f(x) \, dx$ converge.
> 2. Si $\displaystyle \int_{a}^{\infty} f(x) \, dx$ diverge, también $\displaystyle \int_{a}^{\infty} g(x) \, dx$ diverge.


> [!proof]- **Proof.**
>
> Basta notar que $\displaystyle \int_{a}^{b} f(x) \, dx \leq  \int_{a}^{b} g(x) \, dx$ para todo $b>a$. 
> 1. Si $\displaystyle \int_{a}^{\infty} g(x) \, dx$ converge, por el corolario, $\displaystyle \int_{a}^{b} g(x) \, dx \leq M \quad \forall  b>a$
> Lo que implica, $\displaystyle \int_{a}^{b} f(x) \, dx \leq  M$, y por el Corolario, $\displaystyle \int_{a}^{\infty} f(x) \, dx$ converge. $\blacksquare$
> 2. Si $\displaystyle \int_{a}^{\infty} g(x) \, dx$ converge, por $(1)$ tendríamos que $\displaystyle \int_{a}^{\infty} f(x) \, dx$ converge, lo cual es una contradicción; por tanto diverge. $\blacksquare$


> [!theorem] **Teorema.** (Criterio 3)
>
> Sea $f$ integrable en $[a,b]$ para todo $b > a$. Si $\displaystyle\int_{a}^{\infty} \left| f(x) \right| \, dx$ converge, entonces $\displaystyle\int_{a}^{\infty} f(x) \, dx$ también converge.

> [!proof]- **Proof.**
>
> Nótese que $0\leq \left| f(x) \right| - f(x) \leq  2\left| f(x) \right|$. Definamos $F(x) = \left| f(x) \right| - f(x)$ y $G(x) = 2\left| f(x) \right|$
> Por el criterio 2 tenemos, $\int_{a}^{\infty} G(x) \, dx$ converge, ent. $\int_{a}^{\infty} F(x) \, dx$ converge.
> Además, para todo $b>a$ se cumple:
> $$
> \begin{align}
> \int_{a}^{b} f(x) \, dx &= \int_{a}^{b} f(x) -\left| f(x) \right| \, dx + \int_{a}^{b} \left| f(x) \right| \, dx \\[0.5em]
>  &= - \int_{a}^{b} F(x) \, dx + \int_{a}^{b} \left| f(x) \right| \, dx
> \end{align}
> $$
> Entonces al ser $\displaystyle \int_{a}^{\infty} F(x) \, dx$ y $\displaystyle \int_{a}^{\infty} \left| f(x) \right| \, dx$ convergentes, se concluye (límite de una resta) que $\displaystyle \int_{a}^{\infty} f(x) \, dx$ converge. $\blacksquare$


> [!example]- Ejemplo.
>
> $\square$ Pruébese que $\displaystyle \int_{1}^{\infty} \frac{\cos(x^{3})}{x^{2}} \, dx$ converge.
> **Demostración.**
> Observamos que $\displaystyle \left| \frac{\cos(x^{3})}{x^{2}} \right| \leq \frac{1}{x^{2}}$ para $x\geq 1$.
> Entonces, notamos que $\displaystyle \int_{1}^{\infty} \frac{1}{x^{2}} \, dx$ ¡sí converge! (vale $1$, ver el ejemplo de integrales $p$ en [[Integrales Impropias]]).
> Por el Criterio 2 $\displaystyle \int_{1}^{\infty} \left| \frac{\cos(x^{3})}{x^{2}} \right| \, dx$ converge. Y por el Criterio 3, $\int_{1}^{\infty} \frac{\cos(x^{3})}{x^{2}} \, dx$ converge. $\blacksquare$


> [!theorem] **Teorema.** (Criterio 4)
>
> Sea $f$ una función no negativa definida en $[a,b]$ excepto quizá en $b$. Supongamos que $f$ es integrable en $[a,c] \quad \forall  c\in  (a,b)$. Sea $\{ x_{n} \}$ sucesión tal que $\displaystyle \lim_{n \to \infty} x_{n} = b$ con $x_{n} \in [a,b)$ creciente, y además, $\displaystyle y_{n} = \int_{a}^{x_{n}} f(x) \, dx$. Así, se tiene
> $$
> \int_{a}^{b} f(x) \, dx \text{ existe } \iff  \{ y_{n} \} \text{ está acotada sup. }
> $$

> [!proof]- **Proof.**
>
> Es la misma idea que el Criterio 1, cambiando $n \to \infty$ por $x_{n} \to b$. Sea $F(c) = \int_{a}^{c} f$, creciente en $[a,b)$ porque $f \geq 0$.
> $(\implies)$ Si $\lim_{c \to b^{-}} F(c) = \alpha$, como $F$ es creciente, $F(c) \leq \alpha$ para todo $c$; en particular $y_{n} = F(x_{n}) \leq \alpha$.
> $(\impliedby)$ $\{ y_{n} \}$ es creciente y acotada, ent. converge a su supremo $\alpha$. Dado $\varepsilon > 0$ existe $N$ con $\alpha - \varepsilon < y_{N}$. Para $c \in [x_{N}, b)$, como $x_{n} \to b$ existe $m$ con $x_{m} \geq c$, y
> $$
> \alpha - \varepsilon < y_{N} = F(x_{N}) \leq F(c) \leq F(x_{m}) = y_{m} \leq \alpha
> $$
> Así $\lim_{c \to b^{-}} F(c) = \alpha$. $\blacksquare$

- Obsérvese que este criterio es para *integrales impropias de 2da clase*.
