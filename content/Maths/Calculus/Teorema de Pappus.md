---
modified: 2026-11-15T20:20:59Z
title: "Teorema de Pappus"
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
> [!theorem] **Teorema.** (Teorema de Pappus)
>
> Sea $\mathscr{C}$ la gráfica de una función $f:[a,b]\to \mathbb{R}^{+}$ con derivada continua y $a>0$, o bien $b<0$ (esta última condición es para 2., para que la curva no cruce el eje $Y$).
> 1. El área de la superficie de revolución al hacer girar $\mathscr{C}$ alrededor del eje $x$ es $\boxed{2\pi \bar{y} \ell (\mathscr{C})}$ donde $\bar{y}$ es la ordenada del centroide de $\mathscr{C}$.
> 2. Similarmente, el área de la superficie de rev. al hacer girar $\mathscr{C}$ alrededor del eje $Y$ es $\boxed{2\pi \left| \bar{x} \right| \ell(\mathscr{C})}$ donde $\bar{x}$ es la abscisa del centroide de $\mathscr{C}$ (si $a > 0$, simplemente $2\pi \bar{x} \ell(\mathscr{C})$).

> [!proof]- **Proof.**
>
> 1. Por [[Centros de Masa para Físicos]] (con densidad constante), $\displaystyle \bar{y} = \frac{\int_{a}^{b} f(x) \sqrt{1 + f'(x)^{2}}\, dx}{\ell_{\operatorname{graf} (f)}}$, ent.
> $$
> 2\pi \bar{y} \ell (\mathscr{C}) = 2\pi \frac{\displaystyle\int_{a}^{b} f(x) \sqrt{1 + { f'(x)^{2}}}\, dx}{\ell_{\operatorname{graf} (f)}} \cdot  \ell_{\operatorname{graf} (f)} = 2\pi \int_{a}^{b} f(x) \sqrt{1 + f'(x)^{2}}\, dx
> $$
> que es el área de la superficie (ver [[Solidos de Revolución]]).
> 2. Es análogo, con $\displaystyle \bar{x} = \frac{\int_{a}^{b} x \sqrt{1 + f'(x)^{2}}\, dx}{\ell_{\operatorname{graf} (f)}}$ y el área $\displaystyle 2\pi \int_{a}^{b} \left| x \right| \sqrt{1 + f'(x)^{2}}\, dx$ (Corolario de [[Solidos de Revolución]]); como $x$ no cambia de signo en $[a,b]$, $\int \left| x \right| \sqrt{\cdots} = \left| \int x\sqrt{\cdots} \right| = \left| \bar{x} \right| \ell$. $\blacksquare$

> [!example]- Ejemplo.
>
> $\square$ Calcula el centroide del segmento de recta que genera un cono al hacerlo girar alrededor del eje $X$.
> Por el Teo. de Pappus y el área del cono $\pi r \ell$ (ver [[Solidos de Revolución]]), $2\pi \bar{y} \ell = \pi r \ell \implies  \bar{y} = \frac{r}{2}$
> Por semejanza de triángulos,
> $$
> \frac{\bar{x}}{\sqrt{\ell^{2} - r^{2}}} = \frac{\frac{r}{2}}{r} \implies  \bar{x} = \frac{\sqrt{\ell^{2} - r^{2}}}{2}
> $$
> Lo cual tiene sentido: el centroide de un segmento (con densidad constante) es su punto medio.

### Segundo Teorema de Pappus (volúmenes)

El teorema anterior es para **superficies** (una curva que gira). Hay uno gemelo para **volúmenes** (una región que gira), con la misma idea: lo que gira por la distancia que recorre su centroide.

> [!theorem] **Teorema.** (Teorema de Pappus para volúmenes)
>
> Sea $R$ la región entre las gráficas de $f \geq g$ en $[a,b]$, con $f, g$ continuas, área $A$ y centroide $(\bar{x}, \bar{y})$ (con densidad constante, ver [[Centros de Masa para Físicos]]).
> 1. Si $g \geq 0$ (la región no cruza el eje $X$), el volumen del sólido que se genera al girar $R$ alrededor del eje $X$ es $\boxed{V = 2\pi \bar{y} A}$.
> 2. Si $a \geq 0$ (la región no cruza el eje $Y$), el volumen al girar $R$ alrededor del eje $Y$ es $\boxed{V = 2\pi \bar{x} A}$.

> [!proof]- **Proof.**
>
> 1. Cada corte perpendicular al eje $X$ es un anillo de radios $g(x) \leq f(x)$ ([[Volumen por Secciones Transversales]]), así que $V = \pi\int_{a}^{b} \left( f^{2}(x) - g^{2}(x) \right) dx$. Por el Corolario de la región entre dos gráficas, $\displaystyle \bar{y} = \frac{\int_{a}^{b} (f^{2} - g^{2})\,dx}{2A}$, ent.
> $$
> 2\pi\bar{y}A = 2\pi \cdot \frac{\int_{a}^{b} (f^{2} - g^{2})\,dx}{2A}\cdot A = \pi\int_{a}^{b} (f^{2} - g^{2})\,dx = V
> $$
> 2. Por casquillos ([[Solidos de Revolución]]), cada franja vertical de altura $f(x) - g(x)$ a distancia $x$ del eje genera un casquillo, y $V = 2\pi\int_{a}^{b} x\left( f(x) - g(x) \right) dx$. Como $\displaystyle \bar{x} = \frac{\int_{a}^{b} x(f-g)\,dx}{A}$, se tiene $V = 2\pi\bar{x}A$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Se usa en los dos sentidos: si conocemos el centroide, sale el volumen (el [[Toroide]]: $V = 2\pi a\cdot \pi r^{2}$); y si conocemos el volumen, sale el centroide ($\bar{y} = \frac{V}{2\pi A}$). Ejercicios 7, 18 y 26 de [[Tarea III Calculo II]].
