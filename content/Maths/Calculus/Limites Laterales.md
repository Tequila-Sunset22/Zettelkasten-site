---
modified: 2026-11-15T04:47:33Z
title: "Límites Laterales"
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
> [!tip|idea]+ **Idea Intuitiva.**
>
> Es el mismo [[Limite|límite]], pero solo nos acercamos a $x_{0}$ por un lado: con $x > x_{0}$ (por la derecha) o con $x < x_{0}$ (por la izquierda). Sirve, p. ej., para funciones por casos o en los extremos de un intervalo.
>
> <img src="/videos/limites-laterales.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** (Límite por la Derecha e Izquierda)
>
> Sea $A \subseteq \mathbb{R}$ y $f: A \to \mathbb{R}$. Se dice que $L \in  \mathbb{R}$ es **límite por la derecha de** $f$ **en** $x_{0}$ si,
> $$
> \forall \varepsilon >0 \ \exists \delta  >0  \ \forall x \in A \left(  0 < x- x_{0} < \delta  \implies  \left| f(x)  - L\right| < \varepsilon \right)
> $$
> y lo denotamos $\displaystyle \lim_{x \to x_{0}^{+}} f(x) =L$
> Se dice que $L$ es **límite por la izquierda de** $f$ **en** $x_{0}$ si,
> $$
> \forall \varepsilon >0 \ \exists \delta  >0 \ \forall x \in A \left( 0 < x_{0} - x < \delta  \implies  \left| f(x) - L \right| < \varepsilon   \right)
> $$
> y lo denotamos $\displaystyle \lim_{x \to x_{0}^{-}} f(x) = L$


> Relación del límite con sus límites laterales


> [!theorem] **Teorema.**
>
> $$
> \lim_{x \to x_{0}} f(x) = L \iff  \lim_{x \to x_{0}^{+}} f(x) = L = \lim_{x \to x_{0}^{-}} f(x)
> $$


> [!proof]- **Proof.**
>
> Observemos que $0 < \lvert x - x_{0} \rvert < \delta \iff \big( 0 < x - x_{0} < \delta \ \lor \ 0 < x_{0} - x < \delta \big)$.
>
> ($\implies$) Sea $\varepsilon > 0$ y $\delta$ el de la def. de límite. Si $0 < x - x_{0} < \delta$, o si $0 < x_{0} - x < \delta$, en ambos casos $0 < \lvert x - x_{0} \rvert < \delta$, ent. $\lvert f(x) - L \rvert < \varepsilon$. El mismo $\delta$ sirve para los dos laterales.
>
> ($\impliedby$) Sea $\varepsilon > 0$, y sean $\delta_{1}$ el de la derecha y $\delta_{2}$ el de la izquierda. Sea $\delta = \min \{ \delta_{1}, \delta_{2} \}$. Si $0 < \lvert x - x_{0} \rvert < \delta$, ent. $x$ está a la derecha (con $0 < x - x_{0} < \delta_{1}$) o a la izquierda (con $0 < x_{0} - x < \delta_{2}$), y en ambos casos $\lvert f(x) - L \rvert < \varepsilon$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!example]- Ejemplo.
>
> Sea $f(x) = \frac{\lvert x \rvert}{x}$ para $x \neq 0$. Si $x > 0$, $f(x) = 1$, y si $x < 0$, $f(x) = -1$. Ent. $\lim_{ x \to 0^{+} } f(x) = 1 \neq -1 = \lim_{ x \to 0^{-} } f(x)$, y por el teorema $\lim_{ x \to 0 } f(x)$ **no** existe.

Los límites laterales también pueden ser $\pm\infty$: ver [[Limites Infinitos]]. Y con ellos se define la continuidad en los extremos de un intervalo ([[Continuidad]]).
