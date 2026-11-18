---
modified: 2026-11-17T22:20:24Z
title: "Teorema de Bayes"
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
> Puede verse como el "inverso" de la Proba Total. Calcula la Proba de un evento a partir de nueva información o evidencia que ya ha sucedido!

La [[Probablidad Total|probabilidad total]] va de las causas al efecto: si sé qué tan probable es cada escenario $B_{i}$ y qué tan probable es $A$ en cada uno, obtengo $P[A]$. Bayes va al revés: **vi** el efecto $A$, ¿qué tan probable es que haya venido de cada causa?

> [!tip|idea]+ **Idea Intuitiva.**
>
> Si ocurrió $B$, se juntan los pedazos sombreados de todas las franjas; la proba. de cada escenario es la fracción que aporta su pedazo.
> <img src="/videos/bayes-franjas.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Teorema.** (Teorema de Bayes)
>
> Dado un evento $A$ con $P[A] > 0$ y una partición $\mathbb{B} = \{ B_{1},B_{2},\dots \}$ de $\Omega$ con $P[B_{i}] > 0 \ \forall  i$.
> $$
> P[B_{i} \mid A] = \frac{P[A \cap B_{i}]}{P[A]} = \frac{P[A\mid B_{i}]P[B_{i}]}{\displaystyle  \sum_{j}P[A \mid B_{j}]P[B_{j}] }
> $$

> [!proof]- **Proof.**
>
> La primera igualdad es la def. de [[Probabilidad Condicional|proba. condicional]]. En la segunda, el numerador es $P[A \cap B_{i}] = P[A \mid B_{i}]P[B_{i}]$ (la misma def., despejada) y el denominador es $P[A]$ escrita con el Teorema de Probabilidad Total. $\blacksquare$

> [!observation]+ **Observación.**
>
> A $P[B_{i}]$ se le llama probabilidad **a priori** (lo que creíamos antes de ver $A$) y a $P[B_{i} \mid A]$ probabilidad **a posteriori** (lo que creemos después). El denominador es el mismo para todos los $i$: solo normaliza para que las posteriores sumen $1$.

> [!example]- **Ejemplo 1.** (¿Quién dio la clase?)
>
> Con los ayudantes del Ejemplo 1 de [[Probablidad Total]]: un estudiante falta a la clase del martes y su amigo le dice que la clase fue buena. ¿Cuál es la probabilidad de que la haya dado el segundo ayudante?
> **Solución.**
> Ya sabemos que $P[B] = \frac{17}{30}$, y $P[B \cap A_{2}]  = P[B \mid A_{2}] P[A_{2}] = (0.5)\left(\frac{1}{3}\right) = \frac{1}{6}$. Ent.
> $$
> \therefore P[A_{2}\mid B] = \frac{1/6}{17/30} = \frac{5}{17} \approx 0.2941
> $$
> Antes de saber nada, la proba. del ayudante 2 era $\frac{1}{3}$; saber que la clase fue buena la **baja**, porque con él la clase es buena solo la mitad de las veces. Las otras dos: $P[A_{1} \mid B] = \frac{10}{17}$ y $P[A_{3} \mid B] = \frac{2}{17}$, y las tres suman $1$.
