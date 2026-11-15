---
modified: 2026-11-15T04:20:52Z
title: "Regla de L'Hôpital"
publish: true
type: zettel
status: 
links: 
tags: []
date: "2026-03-30"
aliases: [ "" ]
cssclasses: romana
materia: 
---
> [!tip|idea]- **Idea Intuitiva.**
>
> Cerca de $a$, si $f(a) = g(a) = 0$, las funciones se parecen a sus rectas tangentes: $f(x) \approx f'(a)(x-a)$ y $g(x) \approx g'(a)(x-a)$. El cociente de las rectas es $\frac{f'(a)}{g'(a)}$: lo que importa es qué tan rápido se van a $0$ (o a $\infty$), y eso lo mide la derivada.

Para probarla necesitamos una versión del [[Teorema del Valor Medio|T.V.M.]] con dos funciones.

> [!theorem] **Lema.** (Teorema del Valor Medio de Cauchy)
>
> Sean $f, g$ continuas en $[a,b]$ y derivables en $(a,b)$. Ent. existe $c \in (a,b)$ tq.
> $$
> (f(b) - f(a))\,g'(c) = (g(b) - g(a))\,f'(c)
> $$

> [!proof]- **Proof.**
>
> Sea $h(x) = (f(b) - f(a))g(x) - (g(b) - g(a))f(x)$, continua en $[a,b]$ y derivable en $(a,b)$. Desarrollando,
> $$
> h(a) = f(b)g(a) - g(b)f(a) = h(b)
> $$
> Por el [[Teorema de Rolle]] existe $c \in (a,b)$ con $h'(c) = (f(b) - f(a))g'(c) - (g(b) - g(a))f'(c) = 0$.
> $$
> \tag*{$\blacksquare$}
> $$
> Con $g(x) = x$ es el T.V.M.

> [!theorem] **Teorema.** (Regla de L'Hôpital)
>
> Sean $f$ y $g$ funciones derivables en un intervalo abierto que contiene a $a$ (excepto posiblemente en $a$).
> Si $\displaystyle \lim_{x \to a} f(x)= 0$ y $\displaystyle \lim_{x \to a} g(x) = 0$, o si $\displaystyle \lim_{x \to a} \lvert g(x) \rvert = \infty$ (p. ej. si los dos límites son $\pm\infty$), y si $g'(x) \neq  0$ cerca de $a$, y si **existe** $\displaystyle \lim_{x \to a} \frac{f'(x)}{g'(x)}$ (en $\mathbb{R}$ o $\pm\infty$), entonces
> $$
> \lim_{x \to a} \frac{f(x)}{g(x)} = \lim_{x \to a} \frac{f'(x)}{g'(x)}
> $$
> Lo mismo vale para $x \to a^{\pm}$ y $x \to \pm\infty$.

> [!proof]- **Proof.**
>
> Sea $\ell = \lim \frac{f'}{g'}$; hacemos el caso $\ell \in \mathbb{R}$ y $x \to a^{+}$ ($\ell = \pm\infty$ es igual cambiando la banda por un "techo" $M$; $x \to a^{-}$ es simétrico, y con los dos laterales sale $x \to a$ por [[Limites Laterales]]). Sea $\varepsilon > 0$ y $\delta > 0$ tq. en $(a, a + \delta)$, $g' \neq 0$ y $\left\lvert \frac{f'(t)}{g'(t)} - \ell \right\rvert < \varepsilon$.
>
> *Caso $\frac{0}{0}$.* Definimos $f(a) = g(a) = 0$, así $f, g$ son continuas en $[a, x]$ para $x \in (a, a+\delta)$. Además $g(x) \neq 0$: si $g(x) = 0 = g(a)$, por Rolle $g'$ se anularía en $(a,x)$. Por el Lema existe $c_{x} \in (a, x)$ con
> $$
> \frac{f(x)}{g(x)} = \frac{f(x) - f(a)}{g(x) - g(a)} = \frac{f'(c_{x})}{g'(c_{x})}
> $$
> y como $c_{x} \in (a, a+\delta)$, $\left\lvert \frac{f(x)}{g(x)} - \ell \right\rvert < \varepsilon$.
>
> *Caso $\lvert g \rvert \to \infty$.* Fijemos $y \in (a, a+\delta)$. Para $x \in (a, y)$, por el Lema en $[x,y]$ existe $c \in (x,y)$ con $Q(x) := \frac{f(x) - f(y)}{g(x) - g(y)} = \frac{f'(c)}{g'(c)}$, así $\lvert Q(x) - \ell \rvert < \varepsilon$ (y $g(x) \neq g(y)$ por Rolle). Despejando,
> $$
> \frac{f(x)}{g(x)} = Q(x)\left( 1 - \frac{g(y)}{g(x)} \right) + \frac{f(y)}{g(x)}
> $$
> Como $\lvert g(x) \rvert \to \infty$ y $y$ está fijo, $\frac{g(y)}{g(x)} \to 0$ y $\frac{f(y)}{g(x)} \to 0$ ([[Limites Infinitos]]), y $\lvert Q(x) \rvert < \lvert \ell \rvert + \varepsilon$. Ent. para $x$ suficientemente cerca de $a$,
> $$
> \left\lvert \frac{f(x)}{g(x)} - \ell \right\rvert \leq \lvert Q(x) - \ell \rvert + \lvert Q(x) \rvert \left\lvert \frac{g(y)}{g(x)} \right\rvert + \left\lvert \frac{f(y)}{g(x)} \right\rvert < 2\varepsilon
> $$
> *Caso $x \to \infty$.* Con $t = \frac{1}{x}$, aplicamos lo anterior a $F(t) = f\left( \frac{1}{t} \right)$, $G(t) = g\left( \frac{1}{t} \right)$ cuando $t \to 0^{+}$: $\frac{F'(t)}{G'(t)} = \frac{-f'(1/t)/t^{2}}{-g'(1/t)/t^{2}} = \frac{f'(1/t)}{g'(1/t)}$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> 1. Hace falta que $\lim \frac{f'}{g'}$ **exista**: con $f(x) = x + \sin x$ y $g(x) = x$, $\frac{f(x)}{g(x)} = 1 + \frac{\sin x}{x} \to 1$ cuando $x \to \infty$, pero $\frac{f'(x)}{g'(x)} = 1 + \cos x$ no tiene límite.
> 2. Solo sirve para $\frac{0}{0}$ y $\frac{\infty}{\infty}$; las otras indeterminaciones se pasan a estas (ver [[Limites Infinitos]]).

> [!example]- Ejemplos.
>
> 1. $\displaystyle \lim_{ x \to 0 } \frac{1 - \cos x}{x^{2}} = \lim_{ x \to 0 } \frac{\sin x}{2x} = \lim_{ x \to 0 } \frac{\cos x}{2} = \frac{1}{2}$ (L'Hôpital dos veces, $\frac{0}{0}$).
> 2. $\displaystyle \lim_{ x \to \infty } \frac{\log x}{x} = \lim_{ x \to \infty } \frac{1/x}{1} = 0$ ($\frac{\infty}{\infty}$).
> 3. $\displaystyle \lim_{ x \to \infty } x\log\left( 1 + \frac{y}{x} \right) = y$ ($0 \cdot \infty$): con $t = \frac{1}{x}$, es $\displaystyle \lim_{ t \to 0^{+} } \frac{\log(1 + yt)}{t} = \lim_{ t \to 0^{+} } \frac{\frac{y}{1 + yt}}{1} = y$. Por continuidad de $\exp$, $\left( 1 + \frac{y}{x} \right)^{x} \to e^{y}$ (se usa en [[Limites de Sucesiones]]).
