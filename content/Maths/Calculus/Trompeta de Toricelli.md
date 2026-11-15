---
modified: 2026-11-15T17:23:16Z
title: "Trompeta de Torricelli"
publish: true
type: zettel
date: "2026-10-28"
status: seed
aliases:
tags:
 - calculus
cssclasses:
 - romana
---
![[Pasted image 20261028112246.png|center|300]]

> Considera la región $R = \{ (x,y) \mid x \geq 1 , 0 \leq y \leq  \frac{1}{x} \}$. Al rotar esta región alrededor del eje $X$, justo obtenemos la Trompeta de Torricelli. Observamos estas propiedades:

> [!theorem] **Proposición.** (Volumen y Área)
>
> 1. El volumen de la Trompeta de Torricelli es finito, y es igual a $\pi$.
> 2. Su área o superficie es infinita.
>

> [!proof]- **Proof.**
>
> 1. Es una integral impropia de 1ra clase (ver [[Integrales Impropias]]): $\displaystyle V = \pi \int_{1}^{\infty} \left(\frac{1}{x}\right)^{2} \, dx = \pi \lim_{b \to \infty} \left(\frac{x^{-1}}{-1}  \right)\bigg|_{1}^{b} = -\pi \lim_{b \to \infty} \left[ \frac{1}{b} - 1  \right] = \pi$
> Por lo tanto, $V = \pi$.
>
> 2. $\displaystyle A = 2\pi \int_{a}^{b} \left| f(x) \right| \sqrt{1+f'(x)^{2}} \, dx = 2\pi\int_{1}^{\infty} \left(\frac{1}{x}  \right) \sqrt{1 + \left(- \frac{1}{x^{2}}  \right)^{2}} \, dx = 2\pi \int_{1}^{\infty} \frac{1}{x} \frac{\sqrt{x^{4} + 1}}{\sqrt{x^{4}}} \, dx = 2\pi \int_{1}^{\infty} \frac{\sqrt{x^{4}+1}}{x^{3}} \, dx$
> Recordando las propiedades de monotonía de la integral, y el Criterio 2 de [[Criterios de Convergencia de Integrales]].
> Notese que $\sqrt{x^{4} + 1} > \sqrt{x^{4}} = x^{2}$.
> $$
> \implies \frac{\sqrt{x^{4}+1}}{x^{3}} > \frac{x^{2}}{x^{3}} = \frac{1}{x}
> $$
> Ent. $\displaystyle \int_{1}^{b} \frac{\sqrt{x^{4}+1}}{x^{3}} \, dx > \int_{1}^{b} \frac{1}{x} \, dx$ para todo $b > 1$.
> Y sabemos que $\displaystyle \int_{1}^{b} \frac{1}{x} \, dx = \log \left(b\right) \overset{b \to \infty}{\longrightarrow} \infty$ (integrales $p$ con $p = 1$).
> $$
> \therefore A > 2\pi\int_{1}^{\infty} \frac{1}{x} \, dx \longrightarrow \infty \tag*{$\blacksquare$}
> $$


