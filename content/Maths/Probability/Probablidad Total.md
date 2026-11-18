---
modified: 2026-11-17T22:20:24Z
title: "Probabilidad Total"
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
Hay múltiples definiciones, dependiendo de la materia. Para Proba 1:

> [!theorem] **Definición.** (Partición de $\Omega$)
>
> Se cumple la definición de toda la vida de una partición, con eventos: una colección finita o numerable $\{ B_{1}, B_{2}, \dots \} \subseteq \mathcal{F}$ tal que
> 1. $\displaystyle \bigcup_{i} B_{i} = \Omega$
> 2. $B_{i} \cap B_{j} = \varnothing \ \forall i \neq j$
>
> (En una partición finita $\{ B_{1}, \dots, B_{n} \}$, las sumas de abajo son hasta $n$.)


> La **probabilidad total** es, de forma intuitiva, una manera de **calcular la probabilidad de un evento dividiéndolo en varios escenarios posibles** que no pueden ocurrir al mismo tiempo.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Cada escenario $B_{i}$ es una franja de ancho $P(B_{i})$, y dentro de ella $A$ ocupa una fracción $P(A \mid B_{i})$. $P(A)$ es la suma de esos pedazos. En la animación, el ejemplo de los ayudantes.
> <img src="/videos/bayes-franjas.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Teorema.** (Probabilidad Total)
>
> Sea $A$ un evento y una partición $\mathbb{B}= \{ B_{1},B_{2},\dots \}$ de $\Omega$ con $P[B_{i}] > 0 \ \forall i$.
>
> $$
> P[A] = \sum_{i=1}^{\infty} P[A \mid B_{i}] P [B_{i}]
> $$

> [!proof]- **Proof.**
>
> $$
> \begin{align}
> \sum_{i=1}^{\infty} P[A \mid  B_{i}]P[B_{i}] &= \sum_{i=1}^{\infty} \frac{P[A \cap B_{i}]}{P[B_{i}]} P[B_{i}]\\[0.5em]
>  &= \sum_{i=1}^{\infty} P[A\cap B_{i}] \\[0.5em]
>   &= P \left[\bigcup_{i=1}^{\infty} (A \cap B_{i})\right] \tag{ajenos} \\[0.5em]
>    &= P\left[ A \cap \left( \bigcup_{i=1}^{\infty} B_{i}  \right)  \right] \tag{Dist.} \\[0.5em]
>     &= P [ A \cap \Omega ] \\[0.5em]
>      &= P[A] \tag*{$\blacksquare$}
> \end{align}
> $$
> donde el paso (ajenos) es el axioma de $\sigma$-aditividad: los $A \cap B_{i}$ son ajenos porque los $B_{i}$ lo son.



> [!example]- **Ejemplo 1.** (Los ayudantes)
>
> En cierto curso hay 3 ayudantes. Con el ayudante 1 siempre es buena clase; con el 2, la clase es buena con proba. $0.5$, y con el 3, con proba. $0.2$. Cada martes llega un ayudante al azar (los tres con proba. $\frac{1}{3}$). ¿Cuál es la probabilidad de que el martes haya buena clase?
> **Solución.**
> Sea $A_{i}$ = "da la clase el ayudante $i$" (una partición de $\Omega$) y $B$ = "buena clase". Sabemos $P[A_{i}] = \frac{1}{3}$ y
> $P[B \mid A_{1} ] = 1$, $P[B \mid A_{2}] = 0.5$, $P[B \mid A_{3}] = 0.2$.
> Utilizando el Teorema de Proba Total,
> $$
> \begin{align}
> & P[B] \\[0.5em]
> &= P[B\mid A_{1}]P[A_{1}] + P[B \mid A_{2}]P[A_{2}] + P[B \mid A_{3}]P[A_{3}] \\[0.5em]
> &= \frac{1}{3}(1 + 0.5 + 0.2) = \frac{17}{30} \approx 0.5667
> \end{align}
> $$
> La pregunta al revés (sabiendo que la clase fue buena, ¿quién la dio?) es el [[Teorema de Bayes]].

---
Siguiente: [[Teorema de Bayes]].
