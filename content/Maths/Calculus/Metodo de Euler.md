---
modified: 2026-11-15T18:06:56Z
title: "Método de Euler"
publish: true
type: zettel
date: "2026-09-29"
status: seed
aliases:
tags:
 - calculus
cssclasses: 
 - romana
---
> Útil para resolver integrales que contienen una función racional de $x$ y una raíz cuadrada de un trinomio de segundo grado, $\sqrt{ax^{2} + bx + c}$.

> [!tip|idea]- **Idea Intuitiva.**
>
> Estaría bueno que $\sqrt{ax^{2}+bx + c} = \sqrt{a}x + t$. Al elevar al cuadrado, el término $ax^{2}$ aparece en ambos lados y se cancela, así que lo que queda es **lineal** en $x$ y podemos despejar $x$ como función racional de $t$. ¿Cómo nos deshacemos de los demás términos del polinomio? Justo así:
> $$
> \begin{align}
> \sqrt{ax^{2}+bx + c} &= \sqrt{a}x + t \\[0.5em]
> ax^{2}+ bx + c &= ax^{2} + 2\sqrt{a}xt + t^{2}
> \end{align}
> $$

> [!theorem] **Teorema.** (Sustitución de Euler, $a > 0$)
>
> Sea $a > 0$. Con la sustitución $\sqrt{ax^{2}+bx+c} = \sqrt{a}\,x + t$ se tiene
> $$
> x = \frac{t^{2}-c}{b - 2\sqrt{a}\,t}, \qquad \sqrt{ax^{2}+bx+c} = \sqrt{a}\,x + t,
> $$
> y tanto $x$, $dx$ como la raíz quedan como funciones racionales de $t$. Así, la integral se vuelve la de un cociente de polinomios en $t$, que se resuelve con [[Fracciones Parciales]]. Al final se regresa con $t = \sqrt{ax^{2}+bx+c} - \sqrt{a}\,x$.

> [!proof]- **Proof.**
>
> Elevando al cuadrado, $ax^{2} + bx + c = ax^{2} + 2\sqrt{a}\,xt + t^{2}$, ent. $bx - 2\sqrt{a}\,xt = t^{2} - c$ y despejando $x = \frac{t^{2}-c}{b-2\sqrt{a}\,t}$, que es racional en $t$. Su derivada $\frac{dx}{dt}$ es racional (cociente de polinomios), y la raíz es $\sqrt{a}\,x + t$, también racional. $\blacksquare$

> [!example]- Ejemplo 1.
>
> $\displaystyle \int \frac{dx}{\sqrt{x^{2} + 3}}$. Llamemos $\sqrt{x^{2}+3} = \sqrt{1}x + t$
> Ent. $x^{2} + 3 = x^{2} + 2xt + t^{2}$
> $$
> \begin{align}
>   \implies 3 &= 2xt + t^{2} \\[0.5em]
>   \implies x &= \frac{3-t^{2}}{2t} \\[0.5em]
>   \implies \frac{dx}{dt} &= \frac{(-2t)(2t)- 2(3-t^{2})}{(2t)^{2}} \tag{cociente} \\[0.5em]
>    &= \frac{-4t^{2} - 6 + 2t^{2}}{4t^{2}} = \frac{-2t^{2} - 6}{4t^{2}} = -\frac{t^{2}+3}{2t^{2}}
> \end{align}
> $$
> Y la raíz: $\displaystyle \sqrt{x^{2}+3} = x + t = \frac{3-t^{2}}{2t} + t = \frac{t^{2}+3}{2t}$. Sustituyendo,
> $$
> \begin{align}
> \int \frac{dx}{\sqrt{x^{2}+3}} &= \int \frac{2t}{t^{2}+3}\cdot \left( -\frac{t^{2}+3}{2t^{2}} \right) dt = -\int \frac{dt}{t} = -\log\left| t \right| + C \\[0.5em]
> &= -\log\left| \sqrt{x^{2}+3} - x \right| + C = \log\left| x + \sqrt{x^{2}+3} \right| + C \tag{$\star$}
> \end{align}
> $$
> $(\star)$: como $\left( \sqrt{x^{2}+3}-x \right)\left( \sqrt{x^{2}+3}+x \right) = 3$, $\ -\log\left| \sqrt{x^{2}+3}-x \right| = \log\left| \sqrt{x^{2}+3}+x \right| - \log(3)$, y la constante se absorbe en $C$. Coincide con la fórmula de [[Fomulasos de Derivadas y Antiderivadas]].

> [!example]- Ejemplo 2.
>
> $\displaystyle \int \frac{dx}{\sqrt{x^{2} - 3x + 2}}$
> Lo sustituimos con $\sqrt{x^{2} - 3x + 2} = \sqrt{1}x  +t \implies  x(-3 - 2t) = t^{2}-2$
> Y encontramos $\displaystyle x = \frac{t^{2} -2}{-3-2t} \implies  \frac{dx}{dt} = \frac{2t(-3-2t)-(-2)(t^{2}-2)}{(-3-2t)^{2}}$
> $$
> \begin{align}
>   \frac{dx}{dt} &= \frac{-6t - 4t^{2} + 2t^{2} -4}{(2t+3)^{2}} = \frac{-2t^{2} - 6t -4}{(2t+3)^{2}}
> \end{align}
> $$
> Sustituyendo en la integral,
> $$
> \begin{align}
> & \int \frac{dx}{\sqrt{x^{2}-3x + 2}} \\[0.5em]
> &= \int \frac{\frac{-2t^{2} -6t-4}{(2t+3)^{2}}}{\frac{t^{2}-2}{-3-2t} +t} \, dt \\[0.5em]
> &= \int \frac{\frac{-2t^{2}-6t -4}{(2t+3)^{2}}}{\frac{t^{2}-2-3t-2t^{2}}{-3-2t}} \, dt \\[0.5em]
> &= \int \frac{(-2t^{2}-6t-4)(-3-2t)}{(2t+3)^{2}(-t^{2}-3t -2)} \, dt \\[0.5em]
> &= \int \frac{-2}{2t+3} \, dt \tag{$-2t^{2}-6t-4 = 2(-t^{2}-3t-2)$} \\[0.5em]
> &= -2 \frac{\log \left|2t+3\right|}{2} + C \\[0.5em]
> &= -\log \left|2t+3\right| + C \tag{$t = \sqrt{x^{2}-3x+2} - x$} \\[0.5em]
> &= -\log \left|2\sqrt{x^{2}-3x+2} - 2x + 3\right| + C
> \end{align}
> $$
