---
modified: 2026-11-17T22:14:29Z
title: "Independencia de V.A.s"
publish: true
type: zettel
date: "2026-09-01"
status: seed
aliases:
tags:
 - probability
cssclasses:
 - romana
---
Dos v.a.s son independientes cuando saber el valor de una no dice nada sobre la otra. Como ya sabemos qué es que dos **eventos** sean independientes ([[Independencia de Eventos]]), la definición pide justo eso para los eventos más básicos que da cada v.a.: $(X \leq x)$ y $(Y \leq y)$.

> [!theorem] **Definición.** (Independencia de v.a.s)
>
> Sean $X$ y $Y$ v.a.s, se dice que son **independientes** si los eventos $(X\leq x)$  y $(Y\leq y)$ son independientes para cualesquiera valores $x,y \in \mathbb{R}$, es decir, si se cumple:
> $$
> P[(X\leq x)\cap (Y\leq y)] = P(X\leq x) P(Y\leq y)
> $$
> A $P[(X \leq x) \cap (Y\leq y)]$ se le conoce como **función de distribución conjunta de** $X$ y $Y$ evaluada en $(x,y)$, también se denota como $P(X\leq x,Y\leq y)$ o $F_{X,Y}(x,y)$, es decir, la condición también adquiere la expresión:
> $$
> F_{X,Y}(x,y) = F_{X}(x)F_{Y}(y), \quad -\infty<x,y<\infty
> $$

> [!observation]+ **Observación.**
>
> Como esta afirmación es por definición $\forall x,y \in \mathbb{R}$, por lógica, para ver que no es cierta basta encontrar al menos un $(x,y)$ para el cual no se cumpla.

> [!Info]- **Nota!** (Equivalencias que conviene saber)
>
> - Con herramientas de teoría de la medida se prueba que la definición equivale a $P(X \in A, Y \in B) = P(X \in A)P(Y \in B)$ para **todos** los borelianos $A, B$, no solo semirrectas.
> - En consecuencia, si $X$ y $Y$ son independientes, también lo son $g(X)$ y $h(Y)$ para cualesquiera funciones (medibles) $g, h$: $(g(X) \in A) = (X \in g^{-1}(A))$.
>
> Las dos se usan seguido (p. ej. $X^{2}$ y $Y^{2}$ independientes en [[Distribucion ji-cuadrada]]); la prueba queda para cuando veamos vectores aleatorios.

En la práctica no se revisa la función de distribución conjunta, sino la función de probabilidad (o la densidad): la condición se vuelve "la tabla conjunta es el producto de las marginales".

> [!theorem] **Teorema.** (Independencia de V.A.s Discretas)
>
> Sean $X,Y$ discretas, ent. son independientes sii
> $$
> P(X=x,Y=y) = P(X=x)P(Y=y), \quad -\infty<x,y <\infty
> $$
> En donde, por Proba. Total, las **marginales** se obtienen de la conjunta:
> $$
> \begin{align}
>   P(X=x) &=  \sum_{y} P(X=x,Y=y) \\[0.5em]
>   P(Y=y) &=  \sum_{x} P(X=x,Y=y)
> \end{align}
> $$

> [!proof]- **Proof.**
>
> **Borrador.** $(\impliedby)$ sumar la tabla. $(\implies)$ el punto $(x,y)$ es el límite de rectángulos $(x-h, x] \times (y-h, y]$, cuya probabilidad se escribe con $F_{X,Y}$ (inclusión-exclusión) y se factoriza.
>
> **Proof.** $(\impliedby)$ Sumando sobre los valores $u \leq x$ de $X$ y $v \leq y$ de $Y$,
> $$
> F_{X,Y}(x,y) = \sum_{u \leq x}\sum_{v \leq y} P(X=u)P(Y=v) = F_{X}(x)F_{Y}(y).
> $$
> $(\implies)$ Para $h > 0$, por inclusión-exclusión ([[Propiedades de la Medida de Probabilidad]]),
> $$
> \begin{align}
> & P(x-h < X \leq x, \ y-h < Y \leq y) \\[0.5em]
> &= F_{X,Y}(x,y) - F_{X,Y}(x-h,y) - F_{X,Y}(x,y-h) + F_{X,Y}(x-h,y-h) \\[0.5em]
> &= \left[ F_{X}(x) - F_{X}(x-h) \right]\left[ F_{Y}(y) - F_{Y}(y-h) \right] \tag{hip.}
> \end{align}
> $$
> Con $h = \frac{1}{n}$, los eventos de la izquierda decrecen a $(X = x, Y = y)$, y cada corchete tiende a $P(X = x)$ y $P(Y = y)$ (Proposición de [[Funcion de Distribucion Acumulada]]). Por [[Continuidad de la Probabilidad]], $P(X=x,Y=y) = P(X=x)P(Y=y)$. $\blacksquare$

> [!example]- **Ejemplo 1.** (Independientes y dependientes)
>
> Se lanzan dos dados. Sean $X$ el primero, $Y$ el segundo y $Z = X + Y$.
> - $X$ y $Y$ son independientes: $P(X = i, Y = j) = \frac{1}{36} = \frac{1}{6}\cdot\frac{1}{6}$ para todo $i, j$.
> - $X$ y $Z$ **no**: basta un par (Observación), por ejemplo $P(X = 1, Z = 12) = 0 \neq \frac{1}{6}\cdot\frac{1}{36} = P(X = 1)P(Z = 12)$. Si el primer dado es $1$, la suma no puede ser $12$.

> [!theorem] **Teorema.** (Independencia de V.A.s Continuas)
>
> Sean $X,Y$ continuas, con **función de densidad conjunta** $f_{X,Y}$, i.e.
> $$
> F_{X,Y}(x,y) = \int_{-\infty}^{x} \int_{-\infty}^{y} f_{X,Y}(u,v) \, dv \, du.
> $$
> Entonces son independientes sii
> $$
> f_{X,Y}(x,y) = f_{X}(x)f_{Y}(y), \quad -\infty<x,y < \infty,
> $$
> en donde $\displaystyle f_{X}(x) = \int_{-\infty}^{\infty} f_{X,Y}(x,y) \, dy$ y $\displaystyle f_{Y}(y) = \int_{-\infty}^{\infty} f_{X,Y}(x,y) \, dx$ son las **densidades marginales**.

> [!proof]- **Proof.**
>
> $(\impliedby)$ Integrando el producto (Fubini), $F_{X,Y}(x,y) = \int_{-\infty}^{x} f_{X}(u)\,du \int_{-\infty}^{y} f_{Y}(v)\,dv = F_{X}(x)F_{Y}(y)$.
> $(\implies)$ Si $F_{X,Y} = F_{X}F_{Y}$, derivando $\frac{\partial^{2}}{\partial x\,\partial y}$ en los puntos donde $f_{X,Y}$, $f_{X}$ y $f_{Y}$ son continuas (T.F.C. en cada variable), $f_{X,Y}(x,y) = f_{X}(x)f_{Y}(y)$. La igualdad en todos los puntos es "salvo versión", como siempre con densidades. $\blacksquare$

> [!example]- **Ejemplo 2.**
>
> Si $f_{X,Y}(x,y) = e^{-x}e^{-y}$ para $x, y > 0$, ent. $f_{X}(x) = e^{-x}\int_{0}^{\infty} e^{-y}\,dy = e^{-x}$ y lo mismo para $Y$: la conjunta es el producto de las marginales, y $X$, $Y$ son $\operatorname{Exp}(1)$ independientes. En cambio, $f_{X,Y}(x,y) = 2$ en el triángulo $0 < y < x < 1$ no se factoriza: el soporte "$y < x$" ya amarra a $Y$ con $X$.

---
Siguiente: [[Esperanza]].
