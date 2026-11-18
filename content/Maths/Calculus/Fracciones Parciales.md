---
modified: 2026-11-17T21:59:52Z
title: "Fracciones Parciales"
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
A veces encontramos integrales con cocientes de polinomios, es decir, $\int \frac{x^{2} + 2x + 1}{x^{3} + 3x^{2} -5x  +3} \, dx$, para estos casos, a veces puede que encontremos polinomios irreducibles en el denominador, para ello tendremos que hacer uso de las siguientes técnicas de integración.

Sean $f,g \in \mathbb{R}[x]$ polinomios. Denotamos $\operatorname{gr}(f)$ al grado del polinomio $f$. Los casos de aquí en adelante son para cocientes $\displaystyle \frac{f(x)}{g(x)}$ en donde $\operatorname{gr}(g) > \operatorname{gr}(f)$.

> [!observation]+ **Observación.** (Si $\operatorname{gr}(f) \geq \operatorname{gr}(g)$)
>
> Primero dividimos: por el algoritmo de la división existen polinomios $q, r$ con $f = qg + r$ y $\operatorname{gr}(r) < \operatorname{gr}(g)$ (o $r = 0$). Así
> $$
> \frac{f(x)}{g(x)} = q(x) + \frac{r(x)}{g(x)},
> $$
> el polinomio $q$ se integra directo y a $\frac{r}{g}$ ya le aplican los casos de abajo.

> [!tip|idea]- **Idea Intuitiva.**
>
> Si logramos reescribir $\displaystyle \frac{f(x)}{g(x)}$ como una comb. lineal de fracciones con denominadores lineales, podemos integrar de manera muy sencilla funciones de la forma $A\displaystyle \int  \frac{1}{x-x_{0}} \, dx$, los cuales son igual a $\displaystyle \sum_{i=1}^{n} A_{i}\log \lvert x-x_{i} \rvert + C$

> [!theorem] **Caso 1.**
>
> Sean el denominador $g(x) \in  \mathbb{R}[x]$ con $\operatorname{gr}(g(x)) = n$ de forma que puede expresarse como el producto de factores lineales **distintos**, i.e., $g(x) = (x - x_{1}) (x-x_{2}) \cdots(x-x_{n})$ con $x_{i} \neq x_{j}$ si $i \neq j$, entonces podemos encontrar $A_{1},\dots,A_{n}$ tales que
> $$
> \frac{A_{1}}{x-x_{1}} + \frac{A_{2}}{x-x_{2}} + \dots+ \frac{A_{n}}{x-x_{n}}
> $$
> sea una comb. lineal igual a nuestro cociente $\displaystyle \frac{f(x)}{g(x)}$.

> [!example]- Ejemplo. (Caso 1)
>
> $\displaystyle \int \frac{dx}{x^{2}-1}$. Como $x^{2}-1 = (x-1)(x+1)$, buscamos $A_{1}, A_{2}$ con
> $$
> \frac{1}{(x-1)(x+1)} = \frac{A_{1}}{x-1} + \frac{A_{2}}{x+1} \iff 1 = A_{1}(x+1) + A_{2}(x-1)
> $$
> Evaluando en $x = 1$: $A_{1} = \frac{1}{2}$; en $x = -1$: $A_{2} = -\frac{1}{2}$. Ent.
> $$
> \int \frac{dx}{x^{2}-1} = \frac{1}{2}\log\left| x-1 \right| - \frac{1}{2}\log\left| x+1 \right| + C = \frac{1}{2}\log\left| \frac{x-1}{x+1} \right| + C
> $$

> [!tip|idea]- **Idea Intuitiva.**
>
> Similar al caso anterior, solo que ahora tendremos también potencias de denominadores lineales en nuestra comb. lineal. Así que, además de $\log$, aparecen integrales $\int \frac{dx}{(x-x_{0})^{i}} = \frac{(x-x_{0})^{1-i}}{1-i}$ para $i \geq 2$.

> [!theorem] **Caso 2.**
>
> Sea $g(x) \in \mathbb{R}[x]$ con $\operatorname{gr}(g) = n$, de forma que $g(x)$ es el producto de factores lineales que pueden repetirse, i.e. $g(x) = (x-x_{1})(x-x_{2})^{k}\cdots$, ent. podemos encontrar $A_{1},\dots, A_{n}$ tales que
> $$
> \frac{f(x)}{g(x)} = \frac{A_{1}}{x-x_{1}} + \sum_{i=1}^{k} \frac{A_{i+1}}{(x-x_{2})^{i}} + \cdots
> $$
> En donde cada factor de la forma $(x-x_{0})^{k}$ aporta una suma con una fracción por cada potencia $1, \dots, k$.

> [!theorem] **Caso 3.**
>
> Sea $g(x) \in  \mathbb{R}[x]$, y $g(x)$ denominador con términos cuadráticos irreducibles, con ninguno repetido, es decir, $(x-x_{1})(ax^{2}+bx + c)\cdots$ donde $ax^{2}+bx+c$ es irreducible $(b^{2}-4ac < 0)$, ent. encontramos $A_{1},A_{2},\dots$ y $B,C$ tales que
> $$
> \frac{f(x)}{g(x)} = \frac{A_{1}}{x-x_{1}} + \frac{Bx + C}{ax^{2}+bx + c} + \cdots
> $$



> [!theorem] **Caso 4.**
>
> Sea $g \in  \mathbb{R}[x]$, y $g(x)$ denominador con términos cuadráticos irreducibles que puede haber alguno repetido, es decir, $(x-x_{1})(ax^{2}+bx+c)^{k}\cdots$ donde $ax^{2}+bx+c$ es irreducible $(b^{2}-4ac < 0)$, ent. encontramos $A_{1},A_{2},\dots$ y $B_{1},\dots B_{k}, C_{1},\dots,C_{k}$ tales que
> $$
> \frac{f(x)}{g(x)} = \frac{A_{1}}{x-x_{1}} + \sum_{i=1}^{k} \frac{B_{i}x + C_{i}}{(ax^{2} + bx + c)^{i}} + \cdots
> $$
