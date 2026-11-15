---
modified: 2026-11-15T04:47:33Z
title: "Límites Infinitos"
publish: true
type: zettel
date: 2026-09-12
status: seed
aliases:
tags:
  - calculus
cssclasses:
  - romana
---
> [!tip|idea]+ **Idea Intuitiva.**
>
> Como en la [[Sucesiones Divergentes|divergencia a $\infty$ de sucesiones]], el papel de $\varepsilon$ lo juega un "techo" $M$ tan alto como quieran: $f$ queda por encima de él cerca de $a$ (o para $x$ grande). Mientras más alto el techo, más angosta la franja $\delta$.
>
> <img src="/videos/techo-infinito.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** (Limite $x \to a$ es $\pm\infty$)
>
> Diremos que $\displaystyle \lim_{ x \to a } f(x) = \infty$ si
> $$
> \forall  M > 0 \ \exists \delta > 0 \ (0 < \lvert x - a \rvert < \delta \implies f(x) > M)
> $$
> y que $\displaystyle \lim_{ x \to a } f(x) = -\infty$ si $\displaystyle \lim_{ x \to a } (-f(x)) = \infty$.

> [!theorem] **Definición.** (Limite infinito por la derecha e izq.)
>
> Diremos que $\displaystyle \lim_{ x \to a^{+} } f(x) = \infty$ si
> $$
> \forall  M >0 \ \exists \delta >0 \text{ tal que } 0 < x -a < \delta \implies f(x) > M
> $$
> Diremos que $\displaystyle \lim_{ x \to a^{-} } f(x) = \infty$ si
> $$
> \forall  M >0 \ \exists \delta >0 \text{ tal que } 0 < a - x < \delta \implies f(x) > M
> $$
> Para $-\infty$ se cambia $f(x) > M$ por $f(x) < -M$.

> [!theorem] **Definición.** (Limite $x \to \pm\infty$ es $\infty$)
>
> Diremos que $\displaystyle\lim_{ x \to \infty } f(x) = \infty$ si
> $$
> \forall  M > 0 \ \exists  N \  (x > N \implies f(x ) > M)
> $$
> Además, $\displaystyle \lim_{ x \to -\infty } f(x) = \infty$ si
> $$
> \forall  M > 0 \ \exists  N \  (x < N \implies f(x ) > M)
> $$

> [!example]- Ejemplo. ($\frac{1}{x^{2}} \to \infty$ en $0$, y $\frac{1}{x}$ por los lados)
>
> 1. Sea $M > 0$ y $\delta = \frac{1}{\sqrt{ M }}$. Si $0 < \lvert x \rvert < \delta$, ent. $x^{2} < \frac{1}{M}$ y $\frac{1}{x^{2}} > M$. Así $\lim_{ x \to 0 } \frac{1}{x^{2}} = \infty$.
> 2. Con $\delta = \frac{1}{M}$: si $0 < x < \delta$, $\frac{1}{x} > M$; si $0 < -x < \delta$, $\frac{1}{x} < -M$. Así $\lim_{ x \to 0^{+} } \frac{1}{x} = \infty$ y $\lim_{ x \to 0^{-} } \frac{1}{x} = -\infty$ (y $\lim_{ x \to 0 } \frac{1}{x}$ no existe, ver [[Limites Laterales]]).

> [!observation]+ **Observación.**
>
> Igual que con sucesiones ([[Sucesiones Divergentes]]), $\infty$ **no** es un número: "$\lim f(x) = \infty$" significa que el límite **no** existe, de una forma particular.


> [!theorem] **Teorema.** (Operaciones con Límites Infinitos)
>
> Sean $f$ y $g$ funciones tales que $\displaystyle  \lim_{x \to a} f(x) = \infty$ y $\displaystyle \lim_{x \to a} g(x) = c$ donde $c \in  \mathbb{R}$, entonces
> 1. Suma con función convergente:
> $$
> \lim_{x \to a} \left[ f(x) + g(x)  \right] = \infty
> $$
> 2. Producto con función convergente: 
> Si $c >0$, entonces
> $$
> \lim_{x \to a} \left[f(x)  g(x)\right] = \infty
> $$
> Si $c < 0$, entonces
> $$
> \lim_{x \to a} \left[f(x)  g(x)\right] = -\infty
> $$
> Lo mismo vale para $x \to a^{\pm}$ y $x \to \pm\infty$.

> [!proof]- **Proof.**
>
> Sea $M > 0$.
> 1. Con $\varepsilon = 1$ existe $\delta_{1}$ tq. $0 < \lvert x - a \rvert < \delta_{1} \implies g(x) > c - 1$. Sea $M' = \max \{ M - c + 1, 1 \} > 0$; existe $\delta_{2}$ tq. $0 < \lvert x - a \rvert < \delta_{2} \implies f(x) > M' \geq M - c + 1$. Con $\delta = \min \{ \delta_{1}, \delta_{2} \}$, $f(x) + g(x) > M$.
> 2. Si $c > 0$, con $\varepsilon = \frac{c}{2}$ existe $\delta_{1}$ tq. $g(x) > \frac{c}{2} > 0$, y existe $\delta_{2}$ tq. $f(x) > \frac{2M}{c} > 0$. Con $\delta = \min \{ \delta_{1}, \delta_{2} \}$, $f(x)g(x) > \frac{2M}{c} \cdot \frac{c}{2} = M$. Si $c < 0$, aplicamos lo anterior a $-g \to -c > 0$: $f \cdot (-g) \to \infty$, i.e. $fg \to -\infty$.
> $$
> \tag*{$\blacksquare$}
> $$
> (Es la misma prueba que la Proposición ($c \cdot \infty$) de [[Limites de Sucesiones]].)


> [!observation]+ **Observación.** (Indeterminaciones)
>
> No se pueden utilizar los teoremas del álgebra de límites para las siguientes indeterminaciones, pues no se cumplen las hipótesis:
> - $\frac{0}{0}$ o $\frac{\infty}{\infty}$ : Se utiliza [[Regla de L'Hopital|L'Hôpital]].
> - $0 \cdot \infty$ : Falla el teorema del producto, se arregla pasando un factor al denominador ($fg = \frac{f}{1/g}$) y se pasa a la forma $\frac{0}{0}$.
> - $\infty - \infty$ : Falla el teorema de la suma, se arregla sumando fracciones o multiplicando por el conjugado.
> - $1^{\infty}$, $0^{0}$ y $\infty^{0}$ : Falla el teorema de la potencia continua, se arregla usando "trucos de logaritmos" ($f^{g} = e^{g \log f}$) y se pasa a la forma $0 \cdot \infty$.
