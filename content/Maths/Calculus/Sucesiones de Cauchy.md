---
modified: 2026-11-15T04:47:33Z
title: "Sucesiones de Cauchy"
publish: true
type: zettel
date: "2026-09-01"
status: undone
aliases:
tags:
 - calculus
cssclasses:
 - romana
---
Para usar la definición de convergencia necesitamos conocer el límite $L$. La idea de Cauchy es pedir que los términos se acerquen **entre sí**, sin mencionar a $L$.

> [!tip|idea]+ **Idea Intuitiva.** (La ventana $\varepsilon$)
>
> En lugar de una banda alrededor de $L$, pedimos que a partir de $N$ todos los términos quepan en una ventana de alto $\varepsilon$: cualesquiera dos están a menos de $\varepsilon$ entre sí. Al angostar la ventana, $N$ se recorre a la derecha.
>
> <img src="/videos/cauchy-ventana.avif" alt="center" width="720" loading="lazy">
>
> *Sucesión:* $a_{n} = 1 + \frac{1.5(-1)^{n}}{n+1}$.

> [!theorem] **Definición.** (Sucesión de Cauchy)
>
> Una sucesión $\{ x_{n} \}$ es **de Cauchy** si,
> $$
> \forall  \varepsilon  > 0 \ \exists N \in \mathbb{N} \text{ tal que } \forall n,m \geq N \ \left( \left| x_{n} - x_{m} \right| < \varepsilon \right)
> $$

> [!example]- Ejemplos.
>
> 1. $\left\{ \frac{1}{n} \right\}$ es de Cauchy. Sea $\varepsilon > 0$; por la Prop. Arquimediana existe $N \geq 1$ tq. $\frac{1}{N} < \varepsilon$. Si $n, m \geq N$, s.p.g. $n \leq m$, ent. $0 < \frac{1}{m} \leq \frac{1}{n}$ y
> $$
> \left\lvert \frac{1}{n} - \frac{1}{m} \right\rvert = \frac{1}{n} - \frac{1}{m} < \frac{1}{n} \leq \frac{1}{N} < \varepsilon
> $$
> 2. $\{ (-1)^{n} \}$ **no** es de Cauchy: para $\varepsilon = 1$ y cualquier $N$, $n = N$ y $m = N+1$ dan $\lvert x_{n} - x_{m} \rvert = 2 \geq 1$.

> [!theorem] **Proposición 1.**
>
> Toda sucesión de Cauchy está [[Sucesiones Acotadas|acotada]].

> [!proof]- **Proof.**
>
> Es como la prueba de que toda convergente está acotada ([[Sucesiones Convergentes]]), pero comparando con $x_{N}$ en lugar de $L$. Para $\varepsilon = 1$ existe $N$ tq. $\forall n,m \geq N$ $\lvert x_{n} - x_{m} \rvert < 1$. En particular, con $m = N$, $\forall n \geq N$
> $$
> \lvert x_{n} \rvert \leq \lvert x_{n} - x_{N} \rvert + \lvert x_{N} \rvert < 1 + \lvert x_{N} \rvert \tag{Des. triang.}
> $$
> Sea $k = \max \{ \lvert x_{0} \rvert, \dots, \lvert x_{N-1} \rvert, 1 + \lvert x_{N} \rvert \} > 0$. Ent. $\lvert x_{n} \rvert \leq k$ para todo $n \in \mathbb{N}$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Proposición 2.**
>
> Sea $\{ x_{n} \}$ sucesión de Cauchy. Si $\{ y_{k} \}$ es una subsucesión de $\left\{x_{n}  \right\}$ y $\{ y_{k} \}$ converge a $\alpha$, entonces $\{ x_{n} \}$ converge a $\alpha$.

> [!proof]- **Proof.**
>
> Sea $y_{k} = x_{n_{k}}$. Para $\varepsilon  > 0$ existen $N, K \in \mathbb{N}$ tales que
> $$
> \forall n,m \geq N \ \ \lvert x_{n} - x_{m} \rvert < \frac{\varepsilon}{2} \qquad \text{y} \qquad \forall k \geq K \ \ \lvert x_{n_{k}} - \alpha \rvert < \frac{\varepsilon}{2}
> $$
> Sea $n \geq N$ y tomemos $k = \max \{ N, K \}$. Como $n_{k} \geq k \geq N$ (Observación de [[Subsucesiones]]) y $k \geq K$,
> $$
> \lvert x_{n} - \alpha \rvert \leq \lvert x_{n} - x_{n_{k}} \rvert + \lvert x_{n_{k}} - \alpha \rvert < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon \tag{Des. triang.}
> $$
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Proposición 3.**
>
> Si $\{ x_{n} \}$ es una sucesión de Cauchy, entonces $\{ x_{n} \}$ tiene una subsucesión convergente.

> [!proof]- **Proof.**
>
> Por la Proposición 1 está acotada, y por el [[Teorema del Bolzano-Weierstrass]] tiene una subsucesión convergente.
> $$
> \tag*{$\blacksquare$}
> $$

Si aplicamos las proposiciones 2 y 3, tenemos el sig. teorema:

> [!theorem] **Teorema.** (Criterio de Cauchy)
>
> Una sucesión en $\mathbb{R}$ converge sii es de Cauchy.

> [!proof]- **Proof.**
>
> ($\implies$) Sup. que $\{ x_{n} \}$ converge a $\alpha\in \mathbb{R}$. Sea $\varepsilon >0$, existe $N \in \mathbb{N}$ tal que $\left| x_{n} - \alpha \right|< \frac{\varepsilon}{2}$ si $n \geq N$. Si $n,m\geq N$, entonces:
> $$
> \left| x_{n} - x_{m} \right| \leq \left| x_{n} - \alpha \right| + \left| -x_{m} + \alpha \right| < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
> $$
> $$
> \therefore \text{ es de Cauchy }
> $$
> $(\impliedby)$ Por la Proposición 3, $\{ x_{n} \}$ tiene una subsucesión que converge a algún $\alpha$, y aplicando la Proposición 2, $\{ x_{n} \}$ converge a $\alpha$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> El ($\impliedby$) usa Bolzano-Weierstrass, que a su vez usa el Axioma del Supremo. En $\mathbb{Q}$ falla: las aproximaciones decimales $1, 1.4, 1.41, 1.414, \dots$ de $\sqrt{ 2 }$ son de Cauchy, pero no convergen en $\mathbb{Q}$. Por eso se dice que $\mathbb{R}$ es **completo**.

Con Bolzano-Weierstrass y la continuidad por sucesiones ([[Limites de Sucesiones]]) se prueban los teoremas fuertes de continuidad: [[Teorema de Weierstrass y de Acotación]] y [[Continuidad Uniforme]].
