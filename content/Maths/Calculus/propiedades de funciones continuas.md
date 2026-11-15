---
modified: 2026-11-15T04:19:31Z
title: "Propiedades de Funciones Continuas"
publish: true
---
> [!theorem] **Teorema.** (Algebra)
>
> Sea $f,g : A \to \mathbb{R}$ y $c \in \mathbb{R}$. Supongamos $f$ y $g$ son **continuas** en $x_{0} \in A$. Entonces $cf$, $f+g$, $f-g$ y $fg$ son continuas en $x_{0}$. Además, si $g(x_{0})\neq 0$, entonces $f / g$ es continua en $x_{0}$.

> [!proof]- **Proof.** 
>
> Inmediata a partir de la definición de continuidad ($\lim_{ x \to x_{0} } f(x) = f(x_{0})$, ver [[Continuidad]]) y el álgebra de límites ([[Limite]]). P. ej., $\lim_{ x \to x_{0} } (f+g)(x) = f(x_{0}) + g(x_{0}) = (f+g)(x_{0})$. Para el cociente, como $g(x_{0}) \neq 0$, por la Acotación lejos de cero ([[Acotacion de Limites]]) $g \neq 0$ cerca de $x_{0}$, así que $\frac{f}{g}$ está definida ahí.
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Corolario.** 
>
> Todo polinomio es continuo en $\mathbb{R}$

> [!proof]- **Proof.** 
>
> Las funciones $f(x) = 1$ y $g(x) = x$ son continuas en $\mathbb{R}$. El corolario sigue del teorema anterior (por inducción, sumas y productos de una cantidad finita de continuas son continuas).
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Corolario** 
>
> Toda función racional es continua en cada punto de su dominio. (i.e., $\forall x \in \mathbb{R}$ donde el denominador no se hace cero).

> [!proof]- **Proof.**
>
> Es un cociente de polinomios, que son continuos, y el teorema aplica donde el denominador no es cero.
> $$
> \tag*{$\blacksquare$}
> $$

---


> [!theorem] **Teorema.** (Composición)
>
> Sea $f: A\to \mathbb{R}$, $g: B \to \mathbb{R}$ y supongamos $f(A)\subset B$. Supongamos que $f$ es continua en $x_{0} \in A$ y $g$ continua en $y_{0} = f(x_{0}) \in B$. Entonces la composición
> $$
> g \circ f : A \to \mathbb{R}
> $$
> es continua en $x_{0}$.

> [!proof]- **Proof.**
>
> La demostración sigue del Teorema (Límite de la Composición) de [[Limite]]: como $f$ es continua en $x_{0}$, $\lim_{ x \to x_{0} } f(x) = f(x_{0}) = y_{0}$, y como $g$ es continua en $y_{0}$,
> $$
> \lim_{ x \to x_{0} } g(f(x)) = g(y_{0}) = (g \circ f)(x_{0}) \tag*{$\blacksquare$}
> $$

Un forma global como corolario:
> [!theorem] **Corolario.** 
>
> Sea $f: A\to \mathbb{R}$, $g: B \to \mathbb{R}$ y supongamos $f(A)\subset B$. Si $f$ es **continua** en $A$ y $g$ es **continua** en $B$, entonces la composición
> $$
> g \circ f : A \to \mathbb{R}
> $$
> es continua en $A$.

> [!proof]- **Proof.**
>
> Aplicamos el teorema en cada $x_{0} \in A$ (ver [[continuidad en un conjunto]]).
> $$
> \tag*{$\blacksquare$}
> $$

Otra propiedad importante: si $f$ es continua en $x_{0}$ y $x_{n} \to x_{0}$, ent. $f(x_{n}) \to f(x_{0})$ (Continuidad por Sucesiones, en [[Limites de Sucesiones]]).
