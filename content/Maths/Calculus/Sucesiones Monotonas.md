---
modified: 2026-11-15T03:52:29Z
title: "Sucesiones Monótonas"
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
> [!theorem] **Definición.**
>
> Sea $\{ x_{n} \}$ una sucesión, se dice que $\{ x_{n} \}$ es **creciente** si $\forall n \in \mathbb{N} \ (x_{n} \leq x_{n+1})$. Igualmente, se dice que es **estrictamente** **creciente** si $\forall  n \in  \mathbb{N} \ (x_{n} < x_{n+1})$.

> [!theorem] **Definición.**
>
> Sea $\{ x_{n} \}$ una sucesión, decimos que $\{ x_{n} \}$ es **decreciente** si $\forall n \in \mathbb{N} \ (x_{n} \geq   x_{n+1})$. Igualmente, se dice que es **estrictamente decreciente** si $\forall  n \in  \mathbb{N} \ (x_{n} > x_{n+1})$.

> [!theorem] **Definición.**
>
> Sea $\{ x_{n} \} \in \mathbb{R}^{\mathbb{N}}$, decimos que $\{ x_{n} \}$ es **monótona** si es creciente o decreciente.

> [!example]- Ejemplo.
>
>  $\displaystyle \left( 0,1,\frac{1}{2}, \frac{3}{4},\dots \right)$ es una sucesión no monótona: $0 < 1$ pero $1 > \frac{1}{2}$.

> [!observation]+ **Observación.**
>
> 1. $\{ x_{n} \}$ es creciente si y sólo si $\{ -x_{n} \}$ es decreciente.
> 2. Si $\{ x_{n} \}$ es creciente, ent. $x_{m} \leq x_{n}$ para todo $m \leq n$ (no solo para términos consecutivos).
> > [!proof]- **Proof.**
> >
> > 1. Para todo $n \in \mathbb{N}$, $x_{n} \leq x_{n+1} \iff -x_{n} \geq -x_{n+1}$ (multiplicar por $-1$ invierte la desigualdad).
> > 2. Por inducción sobre $n \geq m$: si $n = m$, $x_{m} \leq x_{m}$. Si $x_{m} \leq x_{n}$ (H.I.), ent. $x_{m} \leq x_{n} \leq x_{n+1}$.
> > $$
> > \tag*{$\blacksquare$}
> > $$

Por (1), todo lo que probemos para crecientes vale, cambiando el signo, para decrecientes.

Lo importante de las monótonas es que para ellas acotada **sí** implica convergente: es el **Criterio 4** (crecientes) y el **Criterio 5** (decrecientes) de [[Criterios de Convergencia de Sucesiones]], junto con el caso no acotado ($\pm\infty$). También, toda sucesión tiene una subsucesión monótona (Lema de [[Teorema del Bolzano-Weierstrass]]).
