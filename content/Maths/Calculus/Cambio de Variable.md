---
modified: 2026-11-15T17:19:02Z
title: "Cambio de Variable"
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
> [!theorem] **Teorema.** (Cambio de Variable)
>
> Sea $g: [a,b] \to  \mathbb{R}$ derivable con derivada continua, y sea $f$ continua en un intervalo $I$ que contiene a $g([a,b])$. Entonces
> $$
> \int_{a}^{b} f(g(x))g'(x) \, dx  = \int_{g(a)}^{g(b)} f(u) \, du 
> $$


> [!proof]- **Proof.**
>
> Como $f$ es continua en el intervalo $I$, por el [[Teorema Fundamental de Cálculo|T.F.C.]] tiene una antiderivada $F$ en $I$, y como $g(a), g(b) \in I$, $\displaystyle \int_{g(a)}^{g(b)} f(u) \, du = F(g(b)) - F(g(a))$
> Observamos ahora que, por la regla de la cadena: $\displaystyle \frac{d}{dx}F(g(x)) = F'(g(x))\cdot g'(x) = f(g(x)) \cdot g'(x)$
> Por esto, $F \circ g$ es una antiderivada de $f(g(x))\cdot g'(x)$, que es continua (producto y composición de continuas), lo que nos lleva por T.F.C. a
> $$
> \int_{a}^{b} f(g(x)) \cdot g'(x) \, dx  = (F \circ g)(b) - (F \circ g)(a)
> $$
> Así,
> $$
> \int_{a}^{b} f(g(x))g'(x) \, dx  = \int_{g(a)}^{g(b)} f(u) \, du \tag*{$\blacksquare$}
> $$


> [!observation]+ **Observación.**
>
> Si $f(x) = x$, ent. $\displaystyle \int_{a}^{b} g(x)g'(x) \, dx =\int_{g(a)}^{g(b)} u \, du =  \left. \frac{u^{2}}{2} \right|_{g(a)}^{g(b)}$

> [!example]- Ejemplo.
>
> 1. Con $u = \sin(x)$, $du = \cos(x)\,dx$: $\displaystyle \int_{a}^{b} \sin(x)\cos(x) \, dx = \int u \, du =  \left.  \frac{u^{2}}{2}\right| = \left. \frac{\sin^{2}(x)}{2} \right|_{a}^{b} = \frac{\sin^{2}(b)}{2} - \frac{\sin^{2}(a)}{2}$
>
> Si cambiamos los extremos de integración desde antes, podemos evaluar directamente en $u$; en el siguiente evaluamos de las dos formas para comprobar que da lo mismo:
>
> 2. Con $u = x^{3}+2$, $du = 3x^{2}\,dx$, $u(0) = 2$, $u(2) = 10$: $\displaystyle \int_{0}^{2} \frac{x^{2} \, dx}{(x^{3} + 2)^{2}} = \int_{2}^{10}  \frac{du}{3(u)^{2}} = 1/3 \int_{2}^{10} \frac{du}{u^{2}} = \frac{1}{3} \left. \left(-\frac{1}{u}\right)  \right|_{2}^{10} = \frac{1}{3}\left( \left. - \frac{1}{x^{3} + 2} \right|_{0}^{2}  \right) = \frac{1}{3} \left[ \frac{-1}{10} + \frac{1}{2}  \right] = \frac{1}{3} \left[ \frac{4}{10}  \right] = \frac{2}{15}$ 
> 
> Cuando integramos sin límites (integral indefinida, el concepto general de antiderivada), hay que poner la constante $+c$:
>
> 3. Con $u = 1+x^{2}$, $du = 2x\,dx$ y $x^{2} = u-1$: $\displaystyle \int \frac{x^{3}}{\sqrt{1 + x^{2}}} \, dx  = \int \frac{(u-1) \, du}{2\sqrt{u}} = \frac{1}{2}\left[ \int \frac{u \, du}{\sqrt{u}} - \int \frac{du}{\sqrt{u}} \right] = \frac{1}{2} \left[ \int u ^{\frac{1}{2}} \, du - \int u ^{- \frac{1}{2}} \, du  \right] = \frac{1}{2}\left[ \frac{2}{3} u^{\frac{3}{2}} - 2u^{\frac{1}{2}}  \right] = \frac{1}{2} \left[ \frac{2}{3} (1 + x^{2})^{\frac{3}{2}} - 2 (1 + x^{2})^{\frac{1}{2}}  \right] + c = \frac{(1+x^{2})^{\frac{3}{2}}}{3} - \sqrt{1+x^{2}} + c$
>
> ¡Puede haber múltiples cambios de variable!
>
> 4. Primero $u = \sqrt{x}$ ($x = u^{2}$, $dx = 2u\,du$) y luego $v = u^{2}-2u+2$ ($dv = 2(u-1)\,du$): $\displaystyle \int \frac{(\sqrt{x}- 1) \, dx}{\sqrt{x}(x - 2 \sqrt{x} + 2)^{2}} = \int \frac{ (u-1) 2u \, du}{u (u^{2} - 2u + 2)^{2}} = \int \frac{2 ( u-1) \, du}{(u^{2} - 2u + 2)^{2}} = \int \frac{dv}{v^{2}} = - \frac{1}{v} + c = -\frac{1}{x - 2\sqrt{x} + 2} + c$
>
