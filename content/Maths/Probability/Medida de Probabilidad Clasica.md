---
modified: 2026-11-17T21:49:52Z
title: "Medida Clásica"
publish: true
type: zettel
date: "2026-08-28"
status: seed
aliases:
 - Medida Clasica
 - Probabilidad Clasica
tags:
 - probability
cssclasses: 
 - romana
---
Es la probabilidad "de toda la vida", la de los juegos de azar: si todos los resultados son igual de posibles, la probabilidad de un evento es la proporción de resultados que lo cumplen. Todo se reduce a **contar**, y por eso va de la mano con la [[Combinatoria]].

> Casos favorables entre casos totales.

> [!theorem] **Definición.** (Medida Clásica)
>
> Sea $\Omega$ un espacio muestral **finito**, $\mathcal{F} = \mathcal{P}(\Omega)$. La **medida clásica** es
> $$
> P[A] = \frac{\lvert A \rvert }{\lvert \Omega \rvert } = \frac{\# \text{Casos favorables}}{\# \text{Casos totales}}
> $$

> [!observation]+ **Observación.** (¿Cuándo usarla?)
>
> - $\Omega$ debe ser *finito* (si no, $\lvert \Omega \rvert$ no es un número).
> - Suponemos que cada elemento de $\Omega$ tiene la misma probabilidad: $P[\{ \omega \}] = \frac{1}{\lvert \Omega \rvert}$ para todo $\omega$. Esto es una **hipótesis sobre el experimento**, no algo que se demuestre (Ejemplo 2).

Que sea una "fórmula razonable" no basta: hay que ver que cumple los axiomas de [[Medida de Probabilidad]].

> [!theorem] **Proposición.**
>
> La medida clásica es una medida de probabilidad sobre $(\Omega, \mathcal{P}(\Omega))$.

> [!proof]- **Proof.**
>
> 1. $\lvert A \rvert \geq 0$, ent. $P[A] \geq 0$.
> 2. $P[\Omega] = \frac{\lvert \Omega \rvert}{\lvert \Omega \rvert} = 1$.
> 3. Sean $A_{1}, A_{2}, \dots$ ajenos. Como $\Omega$ es finito, solo una cantidad finita de ellos, digamos $A_{i_{1}}, \dots, A_{i_{m}}$, son no vacíos, y la cardinalidad de una unión finita ajena es la suma de las cardinalidades. Ent.
> $$
> P\left[ \bigcup_{i=1}^{\infty} A_{i} \right] = \frac{\lvert A_{i_{1}} \rvert + \dots + \lvert A_{i_{m}} \rvert}{\lvert \Omega \rvert} = \sum_{i=1}^{\infty} P[A_{i}],
> $$
> pues los demás términos son $P[\varnothing] = 0$. $\blacksquare$

> [!example]- **Ejemplo 1.** (Dos dados)
>
> Al lanzar dos dados, $\Omega = \{ (i,j) \mid i, j \in \{ 1, \dots, 6 \} \}$ y $\lvert \Omega \rvert = 36$, todos igual de probables. La suma es $7$ en $(1,6), (2,5), \dots, (6,1)$, así que $P[\text{suma} = 7] = \frac{6}{36} = \frac{1}{6}$.

> [!example]+ **Ejemplo 2.** (El $\Omega$ equivocado)
>
> Si para el Ejemplo 1 tomáramos $\Omega = \{ 2, 3, \dots, 12 \}$ (las sumas posibles), saldría $P[\text{suma} = 7] = \frac{1}{11}$, que es **falso**: las sumas **no** son igual de probables ($2$ solo sale de una forma, $7$ de seis). La medida clásica es correcta solo si se escoge un $\Omega$ cuyos resultados sí son equiprobables.
> ![[dos-dados.svg|center|500]]

Contar bien es lo difícil. Un ejemplo completo, con todas las manos del póker: [[Cartas de Poker]].

---
Su análogo continuo, con "contar" cambiado por "medir área", es la medida geométrica (Ejemplo 3 de [[Espacio de Probabilidad]]).
