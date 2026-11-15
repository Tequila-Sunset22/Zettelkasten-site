---
modified: 2026-11-15T03:57:24Z
title: "Teorema de Weierstrass y de Acotación"
publish: true
type: zettel
date: "2026-09-07"
status: seed
aliases:
tags:
 - calculus
cssclasses: 
 - romana
---
Que $f$ sea continua en un punto solo da acotación **local**: cerca de ese punto (Acotación Local, en [[Continuidad]]). Aquí la acotación es **global**, en todo un intervalo cerrado, y para eso usamos sucesiones: el Corolario de [[Teorema del Bolzano-Weierstrass]] y la Continuidad por Sucesiones de [[Limites de Sucesiones]].

> [!theorem] **Teorema.** (Acotación de una Función Cont.)
>
> Sea $f: [a,b] \to \mathbb{R}$ continua en su intervalo compacto, entonces la función está acotada en su intervalo. Es decir
> $$
> \exists  C \geq 0 \ \text{ tal que } \ \left| f(x) \right| \leq C \quad \forall x \in [a,b]
> $$

> [!proof]- **Proof.**
>
> Sup. que $f([a,b])$ **no** es acotado, ent. para todo $n \in \mathbb{N}$ existe $x_{n} \in [a,b]$ tal que $\left| f(x_{n}) \right| > n$.
> Pero $\{ x_{n} \}$ tiene una subsucesión $\{ x_{n_{k}} \}$ que converge a un punto $\alpha \in [a,b]$ (Corolario de Bolzano-Weierstrass).
> Como $f$ es continua en $\alpha$, $f(x_{n_{k}}) \to f(\alpha)$ (Continuidad por Sucesiones), y así $\lvert f(x_{n_{k}}) \rvert \to \lvert f(\alpha) \rvert$ (Límite del Valor Absoluto). Entonces $\{ \lvert f(x_{n_{k}}) \rvert \}$ converge y por tanto está acotada ([[Sucesiones Convergentes]]).
> Pero $\left| f(x_{n_{k}}) \right| > n_{k} \geq k$ (Observación de [[Subsucesiones]]), así que no está acotada. Contradicción!
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Hace falta que el intervalo sea **cerrado**: $f(x) = \frac{1}{x}$ es continua en $(0,1]$ pero no está acotada.

> [!theorem] **Teorema.** (Teorema de los Valores Extremos) (Weierstrass)
>
> Si $f: [a,b] \to  \mathbb{R}$ es continua, entonces $f$ alcanza un máximo y un mínimo absoluto en $[a,b]$. Es decir, existen $c,d \in  [a,b]$ tales que $f(c) \leq  f(x) \leq  f(d)$ para todo $x \in  [a,b]$.

> [!proof]- **Proof.**
>
> Por el teorema de acotación, $f([a,b])$ está acotado (y no es vacío). Sea $M= \sup f([a,b])$, que existe por el Axioma del Supremo.
> Para cada $n \in \mathbb{N}$, $M - \frac{1}{n+1}$ no es cota superior, ent. existe $x_{n} \in [a,b]$ tal que
> $$
> M - \frac{1}{n+1} < f(x_{n}) \leq M
> $$
> y por Sándwich $\lim f(x_{n}) = M$.
> Por el Corolario de Bolzano-Weierstrass, $\{ x_{n} \}$ tiene una subsucesión $\{ x_{n_{k}} \}$ que converge a un punto $d \in [a,b]$. Por Continuidad por Sucesiones, $f(d) = \lim f(x_{n_{k}})$. Pero $\{ f(x_{n_{k}}) \}$ es subsucesión de $\{ f(x_{n}) \}$, que converge a $M$, ent. también converge a $M$ ([[Subsucesiones]]), y por Unicidad del Límite $f(d) = M$. Así $f(x) \leq M = f(d)$ para todo $x \in [a,b]$.
>
> Para el mínimo, aplicamos lo anterior a $-f$, que también es continua: existe $c$ con $-f(c) = \max(-f)$, i.e. $f(c) \leq f(x)$ para todo $x \in [a,b]$. Q.E.D.

> [!theorem] **Corolario.** (Imagen de una Función Continua)
>
> Si $f:[a,b] \to \mathbb{R}$ es una función continua en $[a,b]$ entonces $\operatorname{Im} \{f\} = [m,M]$ donde $m = \min \left\{f\right\}$ y $M = \max \left\{f\right\}$.

> [!proof]- **Proof.**
>
> Por el teorema, $m$ y $M$ existen: $m = f(c)$ y $M = f(d)$ con $c,d \in [a,b]$.
> $m\leq f(x) \leq M$ para $x \in [a,b] \implies  \operatorname{Im} \{f\} \subset [m,M]$
> Si $y = m$ o $y = M$, ya es imagen de $c$ o de $d$. Si ahora $m < y < M$ entonces $c \neq d$, y por T.V.I. ([[Teorema del Valor Intermedio]]) aplicado a $f$ en el intervalo cerrado entre $c$ y $d$, existe $x$ entre $c$ y $d$ (en particular $x \in [a,b]$) tal que $f(x) = y \implies  [m,M] \subset \operatorname{Im} \{f\}$
> $$
> \therefore  \operatorname{Im} \{f\} = [m,M] \tag*{$\blacksquare$}
> $$
