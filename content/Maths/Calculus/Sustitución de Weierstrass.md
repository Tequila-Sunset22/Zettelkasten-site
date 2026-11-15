---
modified: 2026-11-15T17:19:37Z
title: "Sustitución de Weierstrass"
publish: true
type: zettel
date: "2026-10-02"
status: seed
aliases:
tags:
 - calculus
cssclasses: 
 - romana
---
> [!tip|idea]- **Idea Intuitiva.**
>
> Este tipo de sustitución es muy frecuente al buscar integrales de varias funciones trigonométricas compuestas. La mayoría de casos se reducen a integrales sencillas de resolver o a fracciones parciales.

> [!theorem] **Teorema.**
>
> Sea $x \in (-\pi, \pi)$ y $z = \tan(\frac{x}{2})$, se cumple:
> $$
> \sin(x) = \frac{2z}{1 + z^{2}} \quad \text{ , } \quad \cos(x) = \frac{1-z^{2}}{1+z^{2}} \quad \text{ y } \quad dx = \frac{2dz}{1 + z^{2}}
> $$

> [!proof]- **Proof.**
>
> Como $\frac{x}{2} \in \left( -\frac{\pi}{2}, \frac{\pi}{2} \right)$, $\cos\left( \frac{x}{2} \right) > 0$ y $\displaystyle \cos^{2}\left( \frac{x}{2} \right) = \frac{1}{\sec^{2}\left( \frac{x}{2} \right)} = \frac{1}{1 + \tan^{2}\left( \frac{x}{2} \right)} = \frac{1}{1+z^{2}}$.
> $$
> \begin{align}
> \sin(x) &= 2\sin\left( \tfrac{x}{2} \right)\cos\left( \tfrac{x}{2} \right) = 2\tan\left( \tfrac{x}{2} \right)\cos^{2}\left( \tfrac{x}{2} \right) = \frac{2z}{1+z^{2}} \tag{ángulo doble} \\[0.5em]
> \cos(x) &= \cos^{2}\left( \tfrac{x}{2} \right) - \sin^{2}\left( \tfrac{x}{2} \right) = \cos^{2}\left( \tfrac{x}{2} \right)\left( 1 - z^{2} \right) = \frac{1-z^{2}}{1+z^{2}} \tag{ángulo doble}
> \end{align}
> $$
> Por último, $x = 2\tan^{-1}(z)$, así que $\displaystyle dx = \frac{2\,dz}{1+z^{2}}$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Con esto, cualquier cociente de polinomios en $\sin(x)$ y $\cos(x)$ se vuelve un cociente de polinomios en $z$, que se integra con [[Fracciones Parciales]].

> [!example]- Ejemplo.
>
> $\displaystyle \int \frac{dx}{1+\cos(x)}$. Como $\displaystyle 1 + \cos(x) = 1 + \frac{1-z^{2}}{1+z^{2}} = \frac{2}{1+z^{2}}$,
> $$
> \int \frac{dx}{1+\cos(x)} = \int \frac{1+z^{2}}{2}\cdot \frac{2\,dz}{1+z^{2}} = \int dz = z + C = \tan\left( \frac{x}{2} \right) + C
> $$
