---
modified: 2026-11-15T04:06:33Z
title: "Sucesiones"
publish: true
type: zettel
status: 
links: 
tags: [calculus]
date: "2026-05-01"
aliases: [ "sequences" ]
cssclasses: romana
materia: 
---
> [!theorem] **Definición.** (Sucesión)
>
> Sea $\mathbb{F}$ un campo, una **sucesión en** $\mathbb{F}$ es una función de la forma,
> $$
> a: \mathbb{N} \to \mathbb{F}
> $$
> **Notación.** Denotamos a $a(j)$ por $a_{j}$. Denotamos a $a$ como una $\mathbb{N}$-ada infinita $(a_{0},a_{1},\dots,a_{j},a_{j+1},\dots)$ o también es común $\{ a_{n} \}_{n \in \mathbb{N}}$, $\{ a_{n} \}_{n=0}^{\infty}$, o $\{ a_{n} \}$.

> [!Info]- **Notación.**
>
> Sea $X$ cjto, denotamos al **cjto. de todas las sucesiones en** $X$ como $X^{\mathbb{N}}$.


En Cálculo discutimos exclusivamente de $\mathbb{R}^{\mathbb{N}}$.
La definición implica que las sucesiones "recorren" $n \in \mathbb{N}$ de $0 \rightarrow \infty$.

> [!observation]+ **Observación.** (Índice inicial)
>
> Si la fórmula no tiene sentido en $n = 0$ (como $\frac{1}{n}$), entendemos que la sucesión empieza en el primer índice donde sí lo tiene: $\left\{ \frac{1}{n} \right\} = \left\{ \frac{1}{n} \right\}_{n=1}^{\infty}$. Como para los límites solo importa la *cola* (ver [[Sucesiones Convergentes]]), esto no cambia nada.

> [!example]- Ejemplos.
>
> $\displaystyle  \left\{a_n\right\}= \left\{ \left(1+\frac{1}{n}\right)^{n} \right\}_{n=1}^{\infty}=2, \left(\frac{3}{2}\right)^2, \left(\frac{4}{3}\right)^3, \dots$
>
> $\displaystyle \left\{(-1)^n\right\}=1, -1, 1, \dots$
>
> $\displaystyle \left\{\left(2-\frac{1}{n^{2}}\right)\right\}_{n=1}^{\infty}=1, \frac{7}{4}, \frac{17}{9}, \dots$
>
> $\displaystyle \left\{\frac{4^{n}}{n!}\right\}=1,4,8, \frac{32}{3}\dots$
>
> $\displaystyle \left\{\sqrt{n} \sin \frac{n \pi}{2}\right\} = 0,1,0,-\sqrt{3}, \ldots$

> [!example]- Ejemplo. (Sucesiones de Recursión)
>
> Sucesión de Fibonacci: $\displaystyle 1,1,2,3,5,8\dots$
>
> Sucesión de Newton: $\displaystyle x_{n+1}=x_{n} - \frac{f(x_{n})}{f'(x_{n})}$
>
> Sucesión Factorial: $x_{0} = 1$ y $x_{n} = nx_{n-1}$ con $n\geq 1$



> [!theorem] **Definición.** (Operaciones de Sucesiones)
>
> Sean $\{ x_{n} \}, \{ y_{n} \} \in \mathbb{R}^{\mathbb{N}}$ definimos las operaciones suma, producto, producto escalar y división de forma correspondiente:
> $$
> \begin{align}
> +: \mathbb{R}^{\mathbb{N}} \times  \mathbb{R}^{\mathbb{N}} \to \mathbb{R}^{\mathbb{N}}\quad \quad \quad \quad &\quad \quad \cdot : \mathbb{R}^{\mathbb{N}} \times \mathbb{R}^{\mathbb{N}} \to \mathbb{R}^{\mathbb{N}} \\[0.5em]
>  \{ x_{n} \} + \{ y_{n} \} = \{ x_{n} + y_{n} \} \ \quad &\quad \quad \{ x_{n} \} \cdot \{ y_{n} \} = \{ x_{n} \cdot y_{n} \}
> \end{align}
> $$
> Sean $\lambda \in \mathbb{R}$, $y_{n} \neq 0 \ \forall n \in \mathbb{N}$,
> $$
> \begin{align}
> \cdot: \mathbb{R} \times  \mathbb{R}^{\mathbb{N}} \to \mathbb{R}^{\mathbb{N}}\quad \quad \quad \quad &\quad \quad  / : \mathbb{R}^{\mathbb{N}} \times (\mathbb{R}\setminus\{0\})^{\mathbb{N}} \to \mathbb{R}^{\mathbb{N}} \\[0.5em]
>  \lambda \{ x_{n} \} = \{ \lambda x_{n} \} \ \quad \quad \quad \quad &\quad \quad \frac{\{ x_{n} \}}{\{ y_{n} \}} = \left\{  \frac{x_{n}}{y_{n}}  \right\}
> \end{align}
> $$

> [!example]- Ejemplos.
>
> Si $x_{n} = 2n^{2}$ y $y_{n} = 3n^{3}- 1$, ent. $\{ x_{n} \} + \{ y_{n} \} = \{ 3n^{3} + 2n^{2}-1 \}$
>
> $\displaystyle x_{n} = n!, y_n = 2^{n-1} \quad \left\{  \frac{x_{n}}{y_{n}}  \right\} = \left\{  \frac{n!}{2^{n-1}}  \right\}$
>
> $\displaystyle x_{n} = n, y_{n} = n-1 \quad \left\{  \frac{x_{n}}{y_{n}}  \right\}$ no está definida ($y_{1} = 0$).

Las propiedades de las sucesiones están repartidas así: [[Sucesiones Acotadas]], [[Sucesiones Monotonas]], [[Sucesiones Convergentes]], [[Sucesiones Divergentes]], [[Limites de Sucesiones]], [[Subsucesiones]], [[Criterios de Convergencia de Sucesiones]], [[Teorema del Bolzano-Weierstrass]] y [[Sucesiones de Cauchy]].


