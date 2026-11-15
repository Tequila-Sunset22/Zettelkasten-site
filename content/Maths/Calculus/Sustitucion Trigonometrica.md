---
modified: 2026-11-15T18:06:56Z
title: "Integración por Sustitución Trigonométrica"
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
Sirve para integrales con términos de la forma (con $a > 0$):
$$
\sqrt{a^{2} - x^{2}} \quad \sqrt{x^{2}+a^{2}} \quad \sqrt{x^{2}-a^{2}}
$$

> [!tip|idea]- **Idea Intuitiva.**
>
> Las tres raíces se parecen a una identidad pitagórica: $1 - \sin^{2} = \cos^{2}$, $\ 1 + \tan^{2} = \sec^{2}$, $\ \sec^{2} - 1 = \tan^{2}$. Si escribimos $x$ como $a$ por la función trigonométrica adecuada, lo de adentro de la raíz se vuelve un cuadrado perfecto y la raíz desaparece. Para regresar a $x$ dibujamos el triángulo rectángulo que cumple la sustitución y leemos de ahí las demás razones.

> [!observation]+ **Observación.** (Por qué es un cambio de variable)
>
> Es el [[Cambio de Variable]] leído al revés: en lugar de $u = g(x)$ ponemos $x = g(\theta)$ con $g$ **inyectiva** en el intervalo indicado, y
> $$
> \int f(x) \, dx = \int f(g(\theta))\, g'(\theta) \, d\theta, \qquad \text{y al final } \theta = g^{-1}(x).
> $$
> Por eso cada caso fija un intervalo para $\theta$: ahí $g$ es invertible y además sabemos el signo de la raíz.

> [!theorem] **Caso 1.** ($\sqrt{a^{2}-x^{2}}$)
>
> Para $x \in [-a,a]$, sea $x = a\sin(\theta)$ con $\theta \in \left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$. Entonces
> $$
> dx = a\cos(\theta)\, d\theta \qquad \text{y} \qquad \sqrt{a^{2}-x^{2}} = a\cos(\theta).
> $$

> [!proof]- **Proof.**
>
> $\sqrt{a^{2}-a^{2}\sin^{2}(\theta)} = a\sqrt{\cos^{2}(\theta)} = a\left| \cos(\theta) \right| = a\cos(\theta)$, pues $\cos(\theta) \geq 0$ en $\left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$. Además $\sin$ es inyectiva ahí, con inversa $\theta = \sin^{-1}\left( \frac{x}{a} \right)$. $\blacksquare$

> [!example]+ Ejemplo 1.
>
> ![[Pasted image 20260918112859.png|center|190]]
> $\displaystyle \int \frac{\sqrt{a^{2}-x^{2}}}{x^{2}} \, dx$. Observamos que $\displaystyle \sin(\theta )  = \frac{x}{a} \implies  x = a \sin(\theta )$ y con derivada $dx = a\cos(\theta )d\theta$.
> Además, $\displaystyle \cos(\theta ) = \frac{\sqrt{a^{2}-x^{2}}}{a} \implies  \sqrt{a^{2}-x^{2}} = a \cos(\theta )$, y del triángulo $\displaystyle \cot(\theta) = \frac{\sqrt{a^{2}-x^{2}}}{x}$.
> Por lo que nos queda en la integral
> $$
> \begin{align}
> \int \frac{a\cos(\theta )}{a^{2}\sin^{2}(\theta )} \cdot  a \cos(\theta )  \, d\theta  &= \int \cot^{2}(\theta) \, d\theta = \int (\csc^{2}(\theta) - 1) \, d\theta \tag{$1 + \cot^{2} = \csc^{2}$} \\[0.5em]
> &= -\cot(\theta) - \theta + c \\[0.5em]
> &= -\frac{\sqrt{a^{2}-x^{2}}}{x} - \sin^{-1}\left(\frac{x}{a}\right)+c \tag{triángulo}
> \end{align}
> $$

> [!theorem] **Caso 2.** ($\sqrt{x^{2}+a^{2}}$)
>
> Sea $x = a\tan(\theta)$ con $\theta \in \left( -\frac{\pi}{2}, \frac{\pi}{2} \right)$. Entonces
> $$
> dx = a\sec^{2}(\theta)\, d\theta \qquad \text{y} \qquad \sqrt{x^{2}+a^{2}} = a\sec(\theta).
> $$
> (También funciona $x = a\cot(\theta)$ con $\theta \in (0,\pi)$, que es tomar el otro ángulo agudo del triángulo; entonces $\sqrt{x^{2}+a^{2}} = a\csc(\theta)$.)

> [!proof]- **Proof.**
>
> $\sqrt{a^{2}\tan^{2}(\theta) + a^{2}} = a\sqrt{\sec^{2}(\theta)} = a\left| \sec(\theta) \right| = a\sec(\theta)$, pues $\cos(\theta) > 0$ en $\left( -\frac{\pi}{2}, \frac{\pi}{2} \right)$. Además $\tan$ es biyectiva de ese intervalo en $\mathbb{R}$, con inversa $\theta = \tan^{-1}\left( \frac{x}{a} \right)$. $\blacksquare$

> [!example]+ Ejemplo 2.
>
> ![[Pasted image 20260918120236.png|center|194]]
> $\displaystyle \int x\sqrt{a^{2} + x^{2}} \, dx$
> Observamos que $\displaystyle \sin(\theta ) = \frac{a}{\sqrt{a^{2}+x^{2}}} \implies \sqrt{a^{2}+x^{2}} = \frac{a}{\sin(\theta )} = a \csc(\theta)$.
> Igual, $\displaystyle \tan(\theta ) = \frac{a}{x} \implies  x = \frac{a}{\tan(\theta )} = a\cot(\theta)$, ent. $dx = -a\csc^{2}(\theta)\,d\theta$. Sustituyo en la integral:
> $$
> \begin{align}
> & \int a\cot(\theta)\cdot a\csc(\theta)\cdot \left(-a\csc^{2}(\theta)\right) \, d\theta \\[0.5em]
> &= -a^{3}\int \frac{\cos(\theta )}{\sin(\theta )} \cdot  \frac{1}{\sin^{3}(\theta )} \, d\theta \\[0.5em]
> &= -a^{3} \int \frac{\cos(\theta ) \, d\theta }{\sin^{4}(\theta )} \tag{$u = \sin(\theta)$} \\[0.5em]
> &= -a^{3} \int \frac{du}{u^{4}} \\[0.5em]
> &= -a^{3} \left( \frac{u^{-3}}{-3}  \right) \\[0.5em]
> &= \frac{a^{3}}{3\sin^{3}(\theta )} \\[0.5em]
> &= \frac{a^{3}}{3\left( \frac{a^{3}}{\sqrt{a^{2}+x^{2}}^{3}}  \right)} \tag{triángulo} \\[0.5em]
> &= \frac{\sqrt{a^{2}+x^{2}}^{3}}{3} + c
> \end{align}
> $$
> **Obs.** Aquí era más rápido $u = a^{2}+x^{2}$, $du = 2x\,dx$: $\displaystyle \int x\sqrt{a^{2}+x^{2}}\,dx = \frac{1}{2}\int \sqrt{u}\,du = \frac{u^{3/2}}{3} + c$. La sustitución trigonométrica conviene cuando no está el factor $x$ que "completa" el $du$.

> [!theorem] **Caso 3.** ($\sqrt{x^{2}-a^{2}}$)
>
> Para $x \geq a$, sea $x = a\sec(\theta)$ con $\theta \in \left[ 0, \frac{\pi}{2} \right)$. Entonces
> $$
> dx = a\sec(\theta)\tan(\theta)\, d\theta \qquad \text{y} \qquad \sqrt{x^{2}-a^{2}} = a\tan(\theta).
> $$

> [!proof]- **Proof.**
>
> $\sqrt{a^{2}\sec^{2}(\theta) - a^{2}} = a\sqrt{\tan^{2}(\theta)} = a\left| \tan(\theta) \right| = a\tan(\theta)$, pues $\tan(\theta) \geq 0$ en $\left[ 0, \frac{\pi}{2} \right)$. Además $\sec$ es inyectiva ahí (es creciente) y toma todos los valores de $[1,\infty)$, con inversa $\theta = \sec^{-1}\left( \frac{x}{a} \right)$. $\blacksquare$

> [!example]- Ejemplo 3.
>
> $\displaystyle \int \frac{dx}{x^{2}\sqrt{x^{2}-a^{2}}}$ con $x > a$. Sea $x = a\sec(\theta)$, ent. $dx = a\sec(\theta)\tan(\theta)\,d\theta$ y $\sqrt{x^{2}-a^{2}} = a\tan(\theta)$. Del triángulo (hipotenusa $x$, cateto adyacente $a$, opuesto $\sqrt{x^{2}-a^{2}}$), $\displaystyle \sin(\theta) = \frac{\sqrt{x^{2}-a^{2}}}{x}$.
> $$
> \begin{align}
> \int \frac{a\sec(\theta)\tan(\theta)}{a^{2}\sec^{2}(\theta)\cdot a\tan(\theta)} \, d\theta &= \frac{1}{a^{2}} \int \cos(\theta) \, d\theta \tag{$\frac{1}{\sec} = \cos$} \\[0.5em]
> &= \frac{\sin(\theta)}{a^{2}} + c = \frac{\sqrt{x^{2}-a^{2}}}{a^{2}x} + c \tag{triángulo}
> \end{align}
> $$

> [!example]- Ejemplo 4. (Integral definida)
>
> Calcula $\displaystyle \int_{0}^{2\sqrt{3}} \frac{x^{3}}{\sqrt{16 - x^{2}}} \, dx$.
> Caso 1 con $a = 4$: $x = 4\sin(\theta)$, $dx = 4\cos(\theta)\,d\theta$. Cambiamos los límites: $x = 0 \implies \theta = 0$ y $x = 2\sqrt{3} \implies \sin(\theta) = \frac{\sqrt{3}}{2} \implies \theta = \frac{\pi}{3}$.
> Como $\theta \in \left[ 0, \frac{\pi}{3} \right] \subseteq \left[ -\frac{\pi}{2}, \frac{\pi}{2} \right]$, $\cos(\theta) \geq 0$ y $\sqrt{16-x^{2}} = 4\cos(\theta)$ sin valor absoluto (de eso se trataba lo del dominio de $\cos$).
> $$
> \begin{align}
> & \int_{0}^{\frac{\pi}{3}} \frac{64\sin^{3}(\theta)}{4\cos(\theta)}\, 4\cos(\theta) \, d\theta \\[0.5em]
> &= 64\int_{0}^{\frac{\pi}{3}} \sin^{3}(\theta) \, d\theta \\[0.5em]
> &= 64\left[ -\cos(\theta) + \frac{\cos^{3}(\theta)}{3} \right]_{0}^{\frac{\pi}{3}} \tag{ver [[Integrales Trigonometricas]]} \\[0.5em]
> &= 64\left[ \left( -\frac{1}{2} + \frac{1}{24} \right) - \left( -1 + \frac{1}{3} \right) \right] \\[0.5em]
> &= 64 \cdot \frac{5}{24} \\[0.5em]
> &= \boxed{\frac{40}{3}}
> \end{align}
> $$

Al sustituir casi siempre quedan potencias de funciones trigonométricas ($\sin^{3}$, $\sec^{3}$, $\cot^{2}$, ...). Sus integrales, con prueba, están en [[Integrales Trigonometricas]].

---

###### Referencias
- https://blog.nekomath.com/tag/sustitucion-trigonometrica/
