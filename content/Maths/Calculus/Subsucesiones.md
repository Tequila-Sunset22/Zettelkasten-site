---
modified: 2026-11-15T04:47:33Z
title: "Subsucesiones"
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
> [!example]- Ejemplos.
>
> $\displaystyle \{ x_{n} \} = \{ n \} = 0,1,2,3,\dots \text{ y } \{ y_{k} \} = 1,3,5,\dots$ Y observamos que $y_{0} = x_{1}; \ y_{1} = x_{3}; \ y_{2} = x_{5}\dots$, i.e. $y_{k} = x_{2k+1}$. Así, $\{ y_{k} \}$ es una subsucesión de $\{ x_{n} \}$.
>
> $\displaystyle \{ x_{n} \} = \{ n \} \text{ y } \{ y_{k} \} = \{ x_{n} \}_{n=4}^{\infty} = 4,5,6,\dots$ Y observamos que $y_{0} = x_{4}; \ y_{1} = x_{5}; \ y_{2} = x_{6}\dots$ Así, $\{ y_{k} \}$ es subsucesión de $\{ x_{n} \}$.
>
> $\displaystyle \{ y_{k} \} = 16,64,144,\dots$ es subsucesión de $\{ n^{2} \} = \{ x_{n} \} = 0,1,4,9,16,\dots$ en donde
> $y_{0} = x_{4} \quad y_{1} = x_{8} \ \ \dots \ \  y_{k} = x_{4k+4}$.
>
> $\displaystyle \{ x_{n+p} \}_{n=0}^{\infty} = \{ x_{n} \}_{n=p}^{\infty}$ con $p \in \mathbb{N}$ fijo es subsucesión de $\{ x_{n} \}$ (quitarle los primeros $p$ términos), con $n_{k} = k + p$. Se le llama una **cola** de $\{ x_{n} \}$.
>
> $\displaystyle \{ y_{k} \} = (1,8,6,2,3)$ no es subsucesión de $\{ n \} = \{ x_{n} \}$: es finita y sus términos no respetan el orden de $\{ x_{n} \}$ ($8$ va antes que $6$).


> [!tip|idea]+ **Idea Intuitiva.**
>
> Una subsucesión se obtiene **tachando términos** de $\{ x_{n} \}$, pero:
> 1. Nos quedamos con una infinidad de términos.
> 2. No cambiamos el orden: no repetimos ni regresamos a un término anterior.
>
> Las posiciones que conservamos son $n_{0}<n_{1}<n_{2}<\dots$, y el $k$-ésimo término de la subsucesión es el que estaba en la posición $n_{k}$, i.e. $y_{k} = x_{n_{k}}$.
>
> <img src="/videos/subsucesion.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** (Subsucesión)
>
> Una sucesión $\{ y_{k} \}$ es una **subsucesión** de $\{ x_{n} \}$ si existe una sucesión $\{ n_{k} \}_{k \in \mathbb{N}}$ de números naturales tales que $n_{0}<n_{1}<n_{2}<\dots$ y tal que $\forall k \in \mathbb{N} \ (y_{k} = x_{n_{k}})$. Se suele escribir $\{ x_{n_{k}} \}$.

> [!example]- Ejemplo.
>
> En el ejemplo $\{ y_{k} \} = 16,64, 144,\dots$ Sí es subsucesión de $\{ 4n \} = ( 0,4,8,12,16,\dots )$ ya que $16 = 4 \cdot 4$, $64 = 4 \cdot 16$, $144 = 4 \cdot 36$, y se tiene $y_{0} = x_{4} \quad y_{1} = x_{16} \quad y_{2} = x_{36},\dots$. En este caso nuestra sucesión $\{ n_{k} \} = \{ 4(k+1)^{2} \} = (4,16,36,\dots)$.

> [!observation]+ **Observación.**
>
> $$
> \forall k \in \mathbb{N} \ (n_{k} \geq k)
> $$
>
> > [!proof]- **Proof.**
> >
> > Por inducción sobre $k$. Para $k = 0$: $n_{0} \in \mathbb{N}$, ent. $n_{0} \geq 0$.
> > Sup. $n_{k} \geq k$ (H.I.). Como $n_{k+1} > n_{k}$ y ambos son naturales, $n_{k+1} \geq n_{k} + 1 \geq k + 1$.
> > $$
> > \tag*{$\blacksquare$}
> > $$

### Convergencia de subsucesiones

> [!theorem] **Proposición.** (Convergencia por Subsucesiones)
>
> Una sucesión $\{ x_{n} \}$ converge a $\alpha$ sii todas sus subsucesiones convergen a $\alpha$.

> [!proof]- **Proof.**
>
> ($\implies$) Supongamos que $\{ x_{n} \}$ converge a $\alpha$, y que $\{ x_{n_{k}} \}$ es subsucesión de $\{ x_{n} \}$. Sea $\varepsilon > 0$, entonces existe $N \in \mathbb{N}$ tal que $\lvert x_{n}-\alpha \rvert<\varepsilon$ si $n \geq N$. Si $k \geq N$, por la Observación $n_{k} \geq k \geq N$, ent.
> $$
> \lvert x_{n_{k}} - \alpha \rvert < \varepsilon \quad \text{ si } k \geq N
> $$
> ($\impliedby$) $\{ x_{n} \}$ es subsucesión de sí misma (con $n_{k} = k$), ent. converge a $\alpha$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Corolario.**
>
> 1. (Colas) Si $x_{n} \to \alpha$, ent. $x_{n+p} \to \alpha$ para todo $p \in \mathbb{N}$. En particular, $x_{n+1} \to \alpha$.
> 2. (Criterio de divergencia) Si $\{ x_{n} \}$ tiene dos subsucesiones que convergen a límites distintos, o una subsucesión que no converge, ent. $\{ x_{n} \}$ diverge.

> [!proof]- **Proof.**
>
> 1. $\{ x_{n+p} \}$ es subsucesión de $\{ x_{n} \}$ con $n_{k} = k + p$.
> 2. Si $\{ x_{n} \}$ convergiera a $\alpha$, por la Proposición todas sus subsucesiones convergerían al mismo $\alpha$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!example]- Ejemplo. ($\{ (-1)^{n} \}$ diverge)
>
> $x_{2k} = 1 \to 1$ y $x_{2k+1} = -1 \to -1$. Como $1 \neq -1$, por el Corolario (2) $\{ (-1)^{n} \}$ diverge (compara con la prueba $\varepsilon$ del Ejemplo 6 de [[Sucesiones Divergentes]]).

El recíproco de (1) también vale (cambiar finitos términos no afecta, Obs. (3) de [[Sucesiones Convergentes]]). Otros resultados con subsucesiones: toda sucesión tiene una subsucesión monótona y toda acotada tiene una convergente ([[Teorema del Bolzano-Weierstrass]]); y una de Cauchy con una subsucesión convergente converge ([[Sucesiones de Cauchy]]).
