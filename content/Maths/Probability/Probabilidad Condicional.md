---
modified: 2026-11-17T22:14:29Z
title: "Probabilidad Condicional"
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
Hasta ahora hemos medido eventos estáticos dentro de un universo $\Omega$ congelado. La probabilidad condicional introduce el concepto de **flujo de información**: cómo cambia la probabilidad de $A$ cuando sabemos que ocurrió $B$.

> La intuición de la **proba. condicional** es geométrica, al saber que ha sucedido un evento $B$, nuestro universo de posibilidades se *"encoge"*. Todo lo que está fuera de $B$ pasa a tener probabilidad cero! $B$ se *"convierte"* en $\Omega$.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Si ocurrió $B$, lo de fuera de $B$ ya no cuenta: de $A$ queda $A \cap B$, y se divide entre $P(B)$ para que el nuevo total sea $1$.
> <img src="/videos/condicional-encoge.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** (Probabilidad Condicional)
>
> Sea $(\Omega ,\mathcal{F}, P)$ un esp. de prob. y sea $B \in  \mathcal{F}$ un evento tal que $P[B] > 0$. Para cualquier evento $A \in  \mathcal{F}$, la **probabilidad condicional de** $A$ **dado** $B$ se define como,
> $$
> P[A \mid B] = \frac{P[ A \cap B ]}{P[B]}
> $$

Que $B$ "se convierta en $\Omega$" es literal: condicionar a $B$ da otra medida de probabilidad, así que todo lo que sabemos de $P$ vale también para $P[\,\cdot \mid B]$.

> [!theorem] **Proposición.**
>
> Sea $(\Omega , \mathcal{F}, P)$ espacio de probabilidad, y $B \in  \mathcal{F}$ con $P[B] > 0$. Ent. $P^{*}[A] = P[A \mid B]$ es una medida de probabilidad sobre $(\Omega, \mathcal{F})$.

> [!proof]- **Proof.**
>
> 1. $P^{*}[A] = \frac{P[A \cap B]}{P[B]} \geq 0$.
> 2. $P^{*}[\Omega] = \frac{P[\Omega \cap B]}{P[B]} = \frac{P[B]}{P[B]} = 1$.
> 3. Si $A_{1}, A_{2}, \dots$ son ajenos, también lo son los $A_{n} \cap B$, y $\left( \bigcup_{n} A_{n} \right) \cap B = \bigcup_{n} (A_{n} \cap B)$. Ent.
> $$
> P^{*}\left[ \bigcup_{n=1}^{\infty} A_{n} \right] = \frac{1}{P[B]}\sum_{n=1}^{\infty} P[A_{n} \cap B] = \sum_{n=1}^{\infty} P^{*}[A_{n}]. \tag*{$\blacksquare$}
> $$

> ¿Cuál es la probabilidad de que ocurra una cosa y ocurra otra al mismo tiempo?

> [!observation]+ **Observación.**
>
> Si $P[B]>0$, despejando de la definición,
> $$
> P[A\cap B ]= P[A \mid B] P[B]
> $$
> Análogamente, si $P[B \cap C] > 0$,
> $$
> P[A \cap  (B \cap  C)] = P[A \mid B \cap C]P[B \mid  C] P[C]
> $$
> Generalizando esto tenemos el siguiente Teorema que surge directamente de la Def. Proba Condicional.

> [!theorem] **Teorema.** (Regla de la Multiplicación)
>
> Sean $A_{1}, \dots, A_{n} \in \mathcal{F}$ con $P\left[ \bigcap_{i=2}^{n} A_{i} \right] > 0$. Ent.
> $$
> \begin{align}
> & P\left[\bigcap_{i=1}^{n} A_{i}\right] \\[0.5em]
> &= P\left[A_{1} \mid  \bigcap_{i=2}^{n} A_{i}\right] P\left[A_{2}\mid \bigcap_{i=3}^{n} A_{i}\right]\cdots P\left[A_{n-1}\mid A_{n}\right]P\left[A_{n}\right]
> \end{align}
> $$

> [!proof]- **Proof.**
>
> Primero, todas las condicionales están definidas: $\bigcap_{i=k}^{n} A_{i} \supseteq \bigcap_{i=2}^{n} A_{i}$, así que por monotonía tienen proba. $> 0$.
> Inducción sobre $n$. Para $n = 2$ es la Observación. Sup. que vale para $n$ eventos (H.I.), y sean $A_{1}, \dots, A_{n+1}$. Por la Observación con $B = \bigcap_{i=2}^{n+1} A_{i}$,
> $$
> P\left[ \bigcap_{i=1}^{n+1} A_{i} \right] = P\left[ A_{1} \mid \bigcap_{i=2}^{n+1} A_{i} \right] P\left[ \bigcap_{i=2}^{n+1} A_{i} \right],
> $$
> y el último factor es una intersección de $n$ eventos, a la que se le aplica la H.I. $\blacksquare$

> [!example]- **Ejemplo 1.** (Tres ases)
>
> Se sacan $3$ cartas de una baraja de $52$, sin reemplazo. Con $A_{k}$ = "la $k$-ésima es as",
> $$
> P[A_{1} \cap A_{2} \cap A_{3}] = P[A_{1}]\,P[A_{2} \mid A_{1}]\,P[A_{3} \mid A_{1} \cap A_{2}] = \frac{4}{52}\cdot\frac{3}{51}\cdot\frac{2}{50}.
> $$
> Es la regla de la multiplicación leída en el orden en que se sacan las cartas: cada factor es la proba. con lo que queda en la baraja.

El caso extremo, cuando saber que ocurrió $B$ no cambia nada, es la [[Independencia de Eventos]].

---
Siguiente: [[Independencia de Eventos]].
