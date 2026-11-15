---
modified: 2026-11-15T03:52:17Z
title: "Sucesiones Acotadas"
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
> [!theorem] **Definición.** (Sucesión Acotada)
>
> Sea $\{ x_{n} \}$ una sucesión,
> Decimos que $\{ x_{n} \}$ está **acotada superiormente** sii
> $$
> \exists M \in \mathbb{R} \ \forall n \in \mathbb{N}  \left( x_{n} \leq M  \right)
> $$
> En este caso, $M$ es la **cota superior** de la sucesión.
>
> Igualmente, decimos que $\{ x_{n} \}$ está **acotada inferiormente** sii
> $$
> \exists m \in  \mathbb{R} \ \forall n \in \mathbb{N}  \left( x_{n} \geq m  \right)
> $$
> A $m$ se llama **cota inferior** de la sucesión.
>
> Decimos que $\{ x_{n} \}$ está **acotada**, si lo está superior e inferiormente.



Supongamos que $\{ x_{n} \}$ está acotada, es decir, $m \leq x_{n} \leq M \quad \forall n \in \mathbb{N}$.
Se puede encontrar un número $k$ positivo tal que $-k \leq m$ y $M \leq k$ (p. ej. $k = \max \{ \lvert m \rvert, \lvert M \rvert, 1 \}$) de manera que
$$
-k \leq x_{n} \leq k \quad \forall  n \in \mathbb{N}
$$
Dicho esto, por propiedades de valor absoluto podemos proponer la siguiente caracterización:

> [!theorem] **Proposición.** (Sucesión Acotada)
>
> Una sucesión $\{ x_{n} \}$ está **acotada** si y sólo si,
> $$
> \exists k \in  \mathbb{R}^{+} \ \text{ tal que } \ \forall n \in \mathbb{N} \ \left( \lvert x_{n} \rvert \leq k \right)
> $$

> [!proof]- **Proof.**
>
> ($\implies$) Es lo que hicimos arriba: con $k = \max \{ \lvert m \rvert, \lvert M \rvert, 1 \} > 0$ se tiene $-k \leq -\lvert m \rvert \leq m \leq x_{n} \leq M \leq \lvert M \rvert \leq k$, i.e. $\lvert x_{n} \rvert \leq k$.
>
> ($\impliedby$) Si $\lvert x_{n} \rvert \leq k$, ent. $-k \leq x_{n} \leq k$, así que $-k$ es cota inferior y $k$ es cota superior.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Cambiar una cantidad finita de términos no afecta la acotación: un cjto. finito de números siempre tiene máximo y mínimo.

Resultados que usan esta noción:
- Toda sucesión convergente está acotada ([[Sucesiones Convergentes]]); el recíproco es falso, pero sí vale si además es monótona ([[Criterios de Convergencia de Sucesiones]]).
- Toda sucesión acotada tiene una subsucesión convergente ([[Teorema del Bolzano-Weierstrass]]).
- Toda sucesión de Cauchy está acotada ([[Sucesiones de Cauchy]]).
- Acotada por nula es nula ([[Limites de Sucesiones]]).
