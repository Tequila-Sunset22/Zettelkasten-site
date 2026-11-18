---
modified: 2026-11-17T21:59:52Z
title: "Límites en el Infinito"
publish: true
type: zettel
date: 2026-08-18
status: seed
aliases:
tags:
  - calculus
cssclasses:
  - romana
---
#### Convergencia

>*"Si me das un margen de error diminuto $\varepsilon$ alrededor de la recta $y=L$, siempre puedo encontrar un punto $N$ en el eje $X$ a partir del cual toda la gráfica queda atrapada dentro de ese tubo horizontal para siempre"*

> [!tip|idea]+ **Idea Intuitiva.**
>
> Es la banda $\varepsilon$ de las [[Sucesiones Convergentes|sucesiones convergentes]], pero ahora $x$ recorre todos los reales: al angostar el tubo, el $N$ a partir del cual la gráfica ya no se sale se recorre a la derecha.
>
> <img src="/videos/tubo-infinito.avif" alt="center" width="720" loading="lazy">
>
> *Función:* $f(x) = 1 + \frac{2\sin(x)}{x}$, con $L = 1$.

> [!theorem] **Definición.** (Límite $x \to \pm \infty$ es $L$)
>
> Sea $f: (a, \infty) \to  \mathbb{R}$. Decimos que $\displaystyle \lim_{x \to \infty} f(x) = L$ si
> $$
> \forall  \varepsilon  > 0 \ \exists N > 0 \ (x > N \implies  \left| f(x) - L \right| < \varepsilon )
> $$
> Igualmente, si $f: (-\infty, a) \to \mathbb{R}$, decimos que $\displaystyle \lim_{x \to -\infty} f(x) = L$ si
> $$
> \forall  \varepsilon  > 0 \ \exists N < 0 \ (x < N \implies  \left| f(x) - L \right| < \varepsilon )
> $$

Es la misma idea que la [[Sucesiones Convergentes|convergencia de sucesiones]], pero con $x \in \mathbb{R}$ en lugar de $n \in \mathbb{N}$.

Además, este límite al infinito es **único**: la prueba es la de [[Limite]], tomando $x > \max \{ N_{1}, N_{2} \}$ en lugar de $0 < \lvert x - a \rvert < \min \{ \delta_{1}, \delta_{2} \}$. Por lo mismo, el álgebra de límites, la conservación de desigualdades y el sándwich valen igual para $x \to \pm\infty$.

> [!example]- Ejemplo. ($\frac{1}{x} \to 0$)
>
> Sea $\varepsilon > 0$ y $N = \frac{1}{\varepsilon}$. Si $x > N$, ent. $0 < \frac{1}{x} < \frac{1}{N} = \varepsilon$.
> $$
> \therefore \ \lim_{ x \to \infty } \frac{1}{x} = 0 \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Si $\displaystyle \lim_{ x \to \infty } f(x) = L$ y $x_{n} \to \infty$, ent. $f(x_{n}) \to L$; en particular $f(n) \to L$ (Teorema de "Sucesiones y funciones" en [[Limites de Sucesiones]]). El recíproco es falso: $\sin(\pi n) = 0 \to 0$, pero $\lim_{ x \to \infty } \sin(\pi x)$ no existe.

Cuando no es $L$ sino que $f$ crece sin cota, $\displaystyle \lim_{ x \to \infty } f(x) = \infty$, ver [[Limites Infinitos]].
