---
modified: 2026-11-15T04:17:25Z
title: "Acotación de Límites"
publish: true
type: zettel
date: "2026-06-30"
aliases:
 - Boundedness of Limits
tags: 
 - calculus
cssclasses: 
 - romana
---
Si $f$ tiene límite en $x_{0}$, no puede "explotar" cerca de $x_{0}$. Esto es lo que se usa en el producto y el cociente del álgebra de límites ([[Limite]]).

> [!theorem] **Teorema.** (Acotación de Limites)
>
> Supóngase
> $$
> \lim_{ x \to x_{0} } f(x) = L
> $$
> Entonces existe un intervalo $(x_{0}-c,x_{0}+c)$ y un número $M$ tal que
> $$
> \lvert f(x) \rvert \leq M
> $$
> para todo $x$ en el intervalo que está en el dominio de $f$.

> [!proof]- **Proof.** 
>
> Con $\varepsilon = 1$, existe $\delta>0$ tal que $\lvert f(x)-L \rvert<1$ siempre y cuando $x$ es un punto del dominio de $f$ diferente de $x_{0}$ el cual satisface $\lvert x-x_{0} \rvert<\delta$. Para esos $x$,
> $$
> \lvert f(x) \rvert = \lvert f(x)-L+L \rvert \leq \lvert f(x)-L \rvert +\lvert L \rvert < \lvert L \rvert +1 \tag{Des. triang.}
> $$
> Sea $c = \delta$.
> - Si $x_{0}$ no pertenece al dominio de $f$, tomamos $M = \lvert L \rvert+1$.
> - Si $x_{0} \in\text{dom}(f)$, falta el punto $x_{0}$, y tomamos $M = \lvert L \rvert +1+\lvert f(x_{0}) \rvert$.
>
> En ambos casos, $\forall x \in (x_{0}-\delta,x_{0}+\delta)$ en el dominio de $f$
> $$
> \lvert f(x) \rvert \leq M \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Si $f$ es [[Continuidad|continua]] en $x_{0}$, es el caso $L = f(x_{0})$: es la Acotación Local de [[Continuidad]].

> [!theorem] **Teorema.** (Acotación lejos de cero) (Boundedness Away from Zero)
>
> Si $\lim_{ x \to x_{0} } f(x) = L$ existe y es diferente de $0$, entonces existe un intervalo $(x_{0}-c,x_{0}+c)$ y un número $m>0$ tal que
> $$
> \lvert f(x) \rvert \geq m >0
> $$
> para todo $x\neq x_{0}$ en el intervalo y que pertenece al $\text{dom}(f)$.

> [!proof]- **Proof.**
>
> Con $\varepsilon = \frac{\lvert L \rvert}{2} > 0$ existe $\delta > 0$ tq. si $x \in \text{dom}(f)$ y $0 < \lvert x - x_{0} \rvert < \delta$, ent. $\lvert f(x) - L \rvert < \frac{\lvert L \rvert}{2}$. Para esos $x$,
> $$
> \lvert L \rvert \leq \lvert L - f(x) \rvert + \lvert f(x) \rvert < \frac{\lvert L \rvert}{2} + \lvert f(x) \rvert \tag{Des. triang.}
> $$
> i.e. $\lvert f(x) \rvert > \frac{\lvert L \rvert}{2}$. Tomamos $c = \delta$ y $m = \frac{\lvert L \rvert}{2}$.
> $$
> \tag*{$\blacksquare$}
> $$
> (Es la misma idea que el Lema de Acotación lejos de cero en [[Limites de Sucesiones]].)
