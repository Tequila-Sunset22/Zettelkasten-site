---
modified: 2026-11-17T22:14:29Z
title: "Independencia de Eventos"
publish: true
type: zettel
date: "2026-09-07"
status: seed
aliases:
tags:
 - probability
cssclasses: 
 - romana
---
> la probabilidad independiente significa que **lo que pasa en un evento no cambia ni afecta las probabilidades de que ocurra el otro**

La intuición nos diría que dos eventos son independientes si "no tienen nada que ver el uno con el otro", es decir, saber que $B$ ocurrió aporta cero información sobre $P[A]$. Usando esta intuición y la [[Probabilidad Condicional|probabilidad condicional]], si $P[B] > 0$ pediríamos
$$
P[A \mid B] = P[A] \iff \frac{P[A \cap B]}{P[B]} = P[A] \iff P[A \cap B] = P[A]P[B].
$$
El tema es cuando $P[B] = 0$: ahí $P[A \mid B]$ no está definida. La última igualdad no tiene ese problema, por ello construimos como sigue la siguiente def.


> [!theorem] **Definición.** (Proba Independiente)
>
> Sean $A, B \in  \mathcal{F}$, decimos que $A$ **es independiente de** $B$, denotado $A \perp\!\!\!\perp B,$ si y sólo si
> $$
> P[A \cap B] = P[A] \cdot P[B]
> $$

> [!observation]+ **Observación.**
>
> Vemos que $\perp\!\!\!\perp$ es una relación con las siguientes propiedades:
> 1. Simetría: $A \perp\!\!\!\perp B \iff  B \perp\!\!\!\perp  A$ (la definición es simétrica).
> 2. Ajenos **no** es lo mismo que independientes: si $A \cap B = \varnothing$ con $P[A], P[B] > 0$, ent. $P[A \cap B] = 0 \neq P[A]P[B]$, así que **no** son independientes. De hecho dependen muchísimo: si ocurre uno, seguro no ocurre el otro (ver [[Eventos Independientes vs. Ajenos]]).
> 3. $\Omega$ y $\varnothing$ son independientes de cualquier evento: $P[A \cap \Omega] = P[A] = P[A]P[\Omega]$ y $P[A \cap \varnothing] = 0 = P[A]P[\varnothing]$.
> 4. No es reflexiva: $A \perp\!\!\!\perp A$ sii $P[A] = P[A]^{2}$, i.e. sii $P[A] \in \{ 0, 1 \}$.
> 5. No es transitiva: con $B = \Omega$ y $0 < P[A] < 1$, se tiene $A \perp\!\!\!\perp \Omega$ y $\Omega \perp\!\!\!\perp A$ (por 3), pero no $A \perp\!\!\!\perp A$ (por 4).

Si $A$ no aporta información sobre $B$, tampoco debería aportarla sobre "que **no** pase $B$":

> [!theorem] **Teorema.** (Propiedades)
>
> Equivalencias de Complementos:
> $$
> A \perp\!\!\!\perp B \iff A \perp\!\!\!\perp B^{c} \iff A^{c} \perp\!\!\!\perp B^{c}
> $$

> [!proof]- **Proof.**
>
> **Borrador.** Basta un solo paso, "si $A \perp\!\!\!\perp B$ ent. $A \perp\!\!\!\perp B^{c}$", y aplicarlo varias veces usando la simetría y que $(B^{c})^{c} = B$.
>
> **Proof.** Sup. $A \perp\!\!\!\perp B$. Como $A = (A \cap B) \cup (A \cap B^{c})$ es unión ajena,
> $$
> \begin{align}
> & P[A \cap B^{c}] \\[0.5em]
> &= P[A] - P[A \cap B] \\[0.5em]
> &= P[A] - P[A]P[B] \tag{hip.} \\[0.5em]
> &= P[A](1 - P[B]) = P[A]P[B^{c}]
> \end{align}
> $$
> i.e. $A \perp\!\!\!\perp B^{c}$. Aplicando esto a $B^{c} \perp\!\!\!\perp A$ (simetría) sale $B^{c} \perp\!\!\!\perp A^{c}$, i.e. $A^{c} \perp\!\!\!\perp B^{c}$. Para las vueltas, el mismo paso aplicado a $B^{c}$ en lugar de $B$ regresa a $B$, porque $(B^{c})^{c} = B$. $\blacksquare$

### Más de dos eventos

Con más de dos eventos hay que tener cuidado: no basta revisar de dos en dos.

> [!theorem] **Definición.** (Independencia de $n$ eventos)
>
> Los eventos $A_{1}, \dots, A_{n}$ son **independientes** si para cualquier subcolección $A_{i_{1}}, \dots, A_{i_{k}}$ ($2 \leq k \leq n$, $i_{1} < \dots < i_{k}$),
> $$
> P[A_{i_{1}} \cap \dots \cap A_{i_{k}}] = P[A_{i_{1}}]\cdots P[A_{i_{k}}].
> $$
> Si solo se cumple para $k = 2$, se dice que son independientes **a pares**.

> [!example]- **Ejemplo 2.** (A pares no basta)
>
> Se lanzan dos monedas justas. Sean $A$ = "la primera es sol", $B$ = "la segunda es sol" y $C$ = "las dos salen igual". Cada uno tiene proba. $\frac{1}{2}$, y cada intersección de dos tiene proba. $\frac{1}{4}$ (p. ej. $A \cap C$ = "las dos son sol"), así que son independientes a pares. Pero
> $$
> P[A \cap B \cap C] = P[\text{dos soles}] = \frac{1}{4} \neq \frac{1}{8} = P[A]P[B]P[C],
> $$
> pues si ocurren $A$ y $B$, $C$ ocurre seguro. No son independientes.

---
Ver también [[Eventos Independientes vs. Ajenos]]. Siguiente: [[Probablidad Total]].
