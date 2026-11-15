---
modified: 2026-11-15T19:42:33Z
title: "Trigonométricas Hiperbólicas"
publish: true
type: zettel
date: "2026-08-19"
status: seed
aliases:
 - 
tags:
 - calculus
cssclasses: 
 - romana
---
Después de construir $\exp \left(x\right)$, definimos sus partes: par e impar. 
> Recordamos que toda función real puede escribirse como la suma de una función par y una impar, las hiperbólicas son justo esto para $e^{x}$ .

> [!observation]+ **Observación.** (Parte par y parte impar)
>
> Si $f: \mathbb{R} \to \mathbb{R}$, entonces
> $$
> f(x) = \underbrace{\frac{f(x) + f(-x)}{2}}_{\text{par}} + \underbrace{\frac{f(x) - f(-x)}{2}}_{\text{impar}}
> $$
> (sumando se cancelan los $f(-x)$; y cambiando $x$ por $-x$ el primer sumando no cambia y el segundo cambia de signo, ver [[Paridad]]). Con $f(x) = e^{x}$, la parte par es $\cosh(x)$ y la impar es $\sinh(x)$: $e^{x} = \cosh(x) + \sinh(x)$.

> [!theorem] **Definición.** (Funciones Hiperbólicas)
>
> Sea $x \in  \mathbb{R}$, definimos:
> - $\displaystyle \sinh(x) = \frac{e^{x}- e^{-x}}{2}$
> - $\displaystyle \cosh(x) = \frac{e^{x}+ e^{-x}}{2}$
> - $\displaystyle \tanh(x ) = \frac{\sinh(x)}{\cosh(x)} =  \frac{e^{x}-e^{-x}}{e^{x}+e^{-x}}$
>
> Al igual que las trig. normales (las tres primeras para $x \neq 0$):
> - $\displaystyle \coth(x) = \frac{\cosh(x)}{\sinh(x)} = \frac{e^{x} + e^{-x}}{e^{x} - e^{-x}}$
> - $\displaystyle \operatorname{csch} (x) = \frac{1}{\sinh(x)} = \frac{2}{e^{x}- e^{-x}}$
> - $\displaystyle \operatorname{sech}(x) = \frac{1}{\cosh(x)} = \frac{2}{e^{x}+ e^{-x}}$

### Identidades

A partir de las propiedades de $\exp \left(x\right)$ (*leyes de exponentes*), demostramos el casi análogo del Teorema de Pitágoras y las demás identidades. Son las de las trigonométricas, salvo algunos signos.

> [!theorem] **Teorema.** (Propiedades de Funciones Hiperbólicas)
>
> - Identidades Fundamentales:
> $$
> \begin{align}
> \cosh^{2}(x) - \sinh^{2}(x) &= 1 \\[0.5em]
> \tanh^{2}(x) + \operatorname{sech}^{2} (x) &= 1 \\[0.5em]
> \coth^{2}(x) - \operatorname{csch}^{2}(x) &=  1 \quad (x \neq 0)
> \end{align}
> $$
> - Paridad
> $$
> \begin{align}
> \sinh(-x) &= -\sinh(x) \\[0.5em]
> \cosh(-x) &= \cosh(x) \\[0.5em]
> \tanh(-x) &= -\tanh(x)
> \end{align}
> $$
> - Suma y Doble ángulo
> $$
> \begin{align}
> \sinh(x\pm y) &= \sinh(x)\cosh(y) \pm \cosh(x)\sinh(y) \\[0.5em]
> \cosh(x\pm y) &= \cosh(x)\cosh(y) \pm \sinh(x)\sinh(y)
> \end{align}
> $$
> $$
> \begin{align}
> \sinh(2x) &= 2 \sinh(x) \cosh(x) \\[0.5em]
> \cosh(2x) &= \cosh^{2}(x) + \sinh^{2}(x) = 2 \sinh^{2}(x)  + 1
> \end{align}
> $$

> [!proof]- **Proof.**
>
> *Identidades fundamentales.* Usando $e^{x}e^{-x} = 1$:
> $$
> \begin{align}
> & \cosh^{2}(x) - \sinh^{2}(x) \\[0.5em]
> &= \frac{(e^{2x} + 2 + e^{-2x}) - (e^{2x} - 2 + e^{-2x})}{4} \tag{binomio} \\[0.5em]
> &= \frac{4}{4} = 1
> \end{align}
> $$
> Dividiendo esta identidad entre $\cosh^{2}(x)$ (que nunca es $0$) queda $1 - \tanh^{2}(x) = \operatorname{sech}^{2}(x)$; dividiendo entre $\sinh^{2}(x)$ (si $x \neq 0$) queda $\coth^{2}(x) - 1 = \operatorname{csch}^{2}(x)$.
>
> *Paridad.* $\sinh(-x) = \frac{e^{-x} - e^{x}}{2} = -\sinh(x)$ y $\cosh(-x) = \frac{e^{-x} + e^{x}}{2} = \cosh(x)$; el cociente de una impar entre una par es impar.
>
> *Suma.* Desarrollando los productos, los términos cruzados se cancelan:
> $$
> \begin{align}
> & \sinh(x)\cosh(y) + \cosh(x)\sinh(y) \\[0.5em]
> &= \frac{(e^{x}-e^{-x})(e^{y}+e^{-y}) + (e^{x}+e^{-x})(e^{y}-e^{-y})}{4} \\[0.5em]
> &= \frac{2e^{x+y} - 2e^{-(x+y)}}{4} = \sinh(x+y)
> \end{align}
> $$
> Igual, $\cosh(x)\cosh(y) + \sinh(x)\sinh(y) = \frac{2e^{x+y} + 2e^{-(x+y)}}{4} = \cosh(x+y)$. Los casos con $-$ salen cambiando $y$ por $-y$ y usando la paridad.
>
> *Doble ángulo.* Con $y = x$ en las de suma: $\sinh(2x) = 2\sinh(x)\cosh(x)$ y $\cosh(2x) = \cosh^{2}(x) + \sinh^{2}(x)$, y por la identidad fundamental $\cosh^{2} = 1 + \sinh^{2}$, queda $2\sinh^{2}(x) + 1$. $\blacksquare$

> [!observation]+ **Observación.** (¿Por qué "hiperbólicas"?)
>
> Dado que $e^{x} > 0$ y $e^{-x} > 0$, $\cosh(x) > 0$ para todo $x$, lo que significa que por el teorema anterior
> $(\cosh(x), \sinh(x))\in \{ (u,v) \mid u^{2} - v^{2} = 1, u > 0 \}$, esto representa a la "rama positiva de la hipérbola $u^{2} - v^{2} = 1$". Así como $(\cos t, \sin t)$ recorre la circunferencia $u^{2} + v^{2} = 1$, $(\cosh t, \sinh t)$ recorre la hipérbola.

##### Gráficas

Para graficar, necesitamos sacar la derivada (abajo), evaluar crecimientos y decrecimientos, concavidades, ver si es simétrica (ejes y puntos de simetría), si es par o impar:
- $\sinh$ es impar y estrictamente creciente ($\sinh' = \cosh > 0$), cóncava en $(-\infty,0)$ y convexa en $(0,\infty)$ ($\sinh'' = \sinh$), y va de $-\infty$ a $\infty$.
- $\cosh$ es par, decrece en $(-\infty,0)$ y crece en $(0,\infty)$ ($\cosh' = \sinh$), con mínimo $\cosh(0) = 1$, y es convexa ($\cosh'' = \cosh > 0$). Veremos que es una **catenaria**: la forma de un cable colgando.
- $\tanh$ es impar, estrictamente creciente ($\tanh' = \operatorname{sech}^{2} > 0$) y acotada: $\tanh(x) \to \pm 1$ cuando $x \to \pm\infty$, pues $\tanh(x) = \frac{1 - e^{-2x}}{1 + e^{-2x}}$.

![[Pasted image 20261002115947.png|center]]

### Derivadas

> [!theorem] **Teorema.** (Derivadas)
>
> $$
> \begin{align}
> \sinh' (x) &= \cosh(x) \\[0.5em]
> \cosh' (x) &= \sinh(x) \\[0.5em]
> \tanh'(x) &= \operatorname{sech}^{2}(x) \\[.5em]
> \coth'(x) &= -\operatorname{csch}^{2}(x)\\[0.5em]
> \operatorname{sech}' (x) &= - \operatorname{sech} (x)\tanh (x) \\[0.5em]
> \operatorname{csch}' (x) &= -\operatorname{csch}(x)\coth(x) 
> \end{align}
> $$

> [!proof]- **Proof.**
>
> Como $(e^{-x})' = -e^{-x}$: $\sinh'(x) = \frac{e^{x} + e^{-x}}{2} = \cosh(x)$ y $\cosh'(x) = \frac{e^{x} - e^{-x}}{2} = \sinh(x)$. Las demás, por la regla del cociente y la identidad fundamental:
> $$
> \begin{align}
> \tanh'(x) &= \frac{\cosh^{2}(x) - \sinh^{2}(x)}{\cosh^{2}(x)} = \frac{1}{\cosh^{2}(x)} = \operatorname{sech}^{2}(x) \\[0.5em]
> \coth'(x) &= \frac{\sinh^{2}(x) - \cosh^{2}(x)}{\sinh^{2}(x)} = -\frac{1}{\sinh^{2}(x)} = -\operatorname{csch}^{2}(x) \\[0.5em]
> \operatorname{sech}'(x) &= -\frac{\sinh(x)}{\cosh^{2}(x)} = -\operatorname{sech}(x)\tanh(x) \\[0.5em]
> \operatorname{csch}'(x) &= -\frac{\cosh(x)}{\sinh^{2}(x)} = -\operatorname{csch}(x)\coth(x) \tag*{$\blacksquare$}
> \end{align}
> $$

### Funciones Inversas Hiperbólicas

$\sinh$, $\tanh$, $\coth$ y $\operatorname{csch}$ son inyectivas en todo su dominio. $\cosh$ y $\operatorname{sech}$ no (son pares), así que las restringimos a $[0,\infty)$. Como todas están hechas de $e^{x}$, sus inversas se pueden escribir con $\log$.

![[Pasted image 20261002120356.png|center|607]]

> [!theorem] **Teorema.** (Funciones Inversas)
>
> - $\displaystyle \sinh^{-1}(x) = \log \left(x+ \sqrt{x^{2}+1}\right) \quad x \in \mathbb{R}$
> - $\displaystyle \cosh^{-1}(x) = \log \left(x + \sqrt{x^{2} -1}\right) \quad x \geq 1$
> - $\displaystyle  \tanh^{-1}(x) = \frac{1}{2}\log \left(\frac{1+x}{1-x}\right) \quad \left| x \right| < 1$ 
> - $\displaystyle  \coth^{-1}(x) = \frac{1}{2}\log \left(\frac{x+1}{x-1}\right) \quad \left| x \right| >1$
> - $\displaystyle \operatorname{sech}^{-1}(x) = \log \left(\frac{1+ \sqrt{1 - x^{2}}}{x}\right) \quad 0 < x \leq 1$
> - $\displaystyle \operatorname{csch}^{-1}(x) = \log \left(\frac{1}{x} + \frac{\sqrt{1 + x^{2}}}{\left| x \right|}\right) \quad x \neq 0$

> [!proof]- **Proof.**
>
> *$\sinh^{-1}$.* Sea $y = \sinh(x) = \frac{e^{x} - e^{-x}}{2}$. Multiplicando por $2e^{x}$: $e^{2x} - 2ye^{x} - 1 = 0$, una cuadrática en $u = e^{x}$. Sus raíces son $u = y \pm \sqrt{y^{2}+1}$, pero $u = e^{x} > 0$ y $y - \sqrt{y^{2}+1} < 0$, así que $e^{x} = y + \sqrt{y^{2}+1}$ y $x = \log\left( y + \sqrt{y^{2}+1} \right)$.
>
> *$\cosh^{-1}$.* Igual, $y = \cosh(x)$ con $x \geq 0$ da $e^{2x} - 2ye^{x} + 1 = 0$, con raíces $u = y \pm \sqrt{y^{2}-1}$ ($y \geq 1$). Como $x \geq 0$, $e^{x} \geq 1$, y la raíz con $+$ es la que es $\geq 1$ (el producto de las raíces es $1$). Así $x = \log\left( y + \sqrt{y^{2}-1} \right)$.
>
> *$\tanh^{-1}$.* $y = \frac{e^{2x} - 1}{e^{2x} + 1}$ (multiplicando arriba y abajo por $e^{x}$). Despejando, $e^{2x}(1 - y) = 1 + y$, así que $e^{2x} = \frac{1+y}{1-y}$ (positivo justo cuando $\left| y \right| < 1$) y $x = \frac{1}{2}\log\left( \frac{1+y}{1-y} \right)$.
>
> *$\coth^{-1}$.* Igual con $y = \frac{e^{2x}+1}{e^{2x}-1}$: $e^{2x} = \frac{y+1}{y-1}$, positivo justo cuando $\left| y \right| > 1$.
>
> *$\operatorname{sech}^{-1}$ y $\operatorname{csch}^{-1}$.* $\operatorname{sech}^{-1}(y) = \cosh^{-1}\left( \frac{1}{y} \right) = \log\left( \frac{1}{y} + \sqrt{\frac{1}{y^{2}} - 1} \right) = \log\left( \frac{1 + \sqrt{1-y^{2}}}{y} \right)$ para $0 < y \leq 1$, y $\operatorname{csch}^{-1}(y) = \sinh^{-1}\left( \frac{1}{y} \right) = \log\left( \frac{1}{y} + \sqrt{\frac{1}{y^{2}} + 1} \right)$, con $\sqrt{\frac{1}{y^{2}}+1} = \frac{\sqrt{1+y^{2}}}{\left| y \right|}$. $\blacksquare$

> [!observation]+ **Observación.**
>
> En $\operatorname{csch}^{-1}$ el $\left| x \right|$ no se puede "simplificar" con el $\frac{1}{x}$: si $x < 0$, $\operatorname{csch}^{-1}(x)$ debe ser negativo, y $\log\left( \frac{1 + \sqrt{1+x^{2}}}{\left| x \right|} \right)$ sería positivo.

> [!theorem] **Teorema.** (Derivadas)
>
> $$
> \begin{align}
> \frac{d}{dx}\sinh^{-1}(x) &= \frac{1}{\sqrt{x^{2} + 1}}\\[0.5em]
> \frac{d}{dx}\cosh^{-1}(x) &= \frac{1}{\sqrt{x^{2}- 1}} \quad x > 1\\[0.5em]
> \frac{d}{dx}\tanh^{-1}(x) &=  \frac{1}{1-x^{2}} \quad \left| x \right| < 1 \\[0.5em]
> \frac{d}{dx}\coth^{-1}(x) &= \frac{1}{1-x^{2}} \quad \left| x \right|>1 \\[0.5em]
> \frac{d}{dx}\operatorname{sech}^{-1}(x) &= - \frac{1}{x\sqrt{1-x^{2}}} \quad 0 < x < 1 \\[0.5em]
> \frac{d}{dx}\operatorname{csch}^{-1}(x) &= - \frac{1}{\left| x \right|\sqrt{1+x^{2}}} \quad x\neq 0
> \end{align}
> $$

> [!proof]- **Proof.**
>
> Por la derivada de la función inversa ([[Funcion Inversa]]), si $y = f(x)$ entonces $(f^{-1})'(y) = \frac{1}{f'(x)}$, y luego escribimos $f'(x)$ en términos de $y$ con las identidades:
> - $\sinh$: $\frac{1}{\cosh(x)} = \frac{1}{\sqrt{1 + \sinh^{2}(x)}} = \frac{1}{\sqrt{1+y^{2}}}$ (pues $\cosh > 0$).
> - $\cosh$ (con $x > 0$): $\frac{1}{\sinh(x)} = \frac{1}{\sqrt{\cosh^{2}(x) - 1}} = \frac{1}{\sqrt{y^{2}-1}}$ (pues $\sinh(x) > 0$).
> - $\tanh$ y $\coth$: $\frac{1}{\operatorname{sech}^{2}(x)} = \frac{1}{1 - \tanh^{2}(x)} = \frac{1}{1-y^{2}}$ y $\frac{1}{-\operatorname{csch}^{2}(x)} = \frac{-1}{\coth^{2}(x) - 1} = \frac{1}{1-y^{2}}$.
> - $\operatorname{sech}$ (con $x > 0$): $\frac{-1}{\operatorname{sech}(x)\tanh(x)} = \frac{-1}{y\sqrt{1-y^{2}}}$, pues $\tanh(x) = \sqrt{1 - \operatorname{sech}^{2}(x)} > 0$.
> - $\operatorname{csch}$: $\frac{-1}{\operatorname{csch}(x)\coth(x)}$, con $\coth(x) = \operatorname{csch}(x)\cosh(x)$ y $\cosh(x) = \frac{\sqrt{1+y^{2}}}{\left| y \right|}$, da $\frac{-1}{y^{2}\frac{\sqrt{1+y^{2}}}{\left| y \right|}} = \frac{-1}{\left| y \right|\sqrt{1+y^{2}}}$. $\blacksquare$

Las tablas resumen están en [[Fomulasos de Derivadas y Antiderivadas]].

---

Sigue: [[Polinomio de Taylor]].
