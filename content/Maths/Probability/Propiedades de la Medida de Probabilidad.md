---
modified: 2026-11-18T22:43:31Z
title: "Propiedades de la Medida de Probabilidad"
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
Desarrollamos más propiedades a partir de los axiomas y las propiedades básicas de [[Medida de Probabilidad]]. Todas responden a lo mismo: cómo calcular, o al menos acotar, la probabilidad de uniones e intersecciones de varios eventos que **no** son ajenos.

### Inclusión-exclusión

Para dos eventos ya sabemos que $P(A \cup B) = P(A) + P(B) - P(A \cap B)$: la intersección se contó dos veces y se resta una. Con tres eventos, al restar las tres intersecciones de a pares quitamos de más la parte común a los tres, y hay que volver a sumarla.

> [!tip|idea]- **Idea Intuitiva.**
>
> Un punto que está en exactamente $k$ de los eventos se cuenta, con los signos, $k - \binom{k}{2} + \binom{k}{3} - \dots = 1 - (1-1)^{k} = 1$ vez.

> [!theorem] **Teorema.** (Inclusión-exclusión)
>
> Sean $A_{1}, \dots, A_{n} \in \mathcal{F}$. Ent.
> $$
> P\left[ \bigcup_{i=1}^{n} A_{i} \right] = \sum_{k=1}^{n} (-1)^{k+1} \sum_{1 \leq i_{1} < \dots < i_{k} \leq n} P\left[ A_{i_{1}} \cap \dots \cap A_{i_{k}} \right]
> $$
> Para tres eventos,
> $$
> \begin{align}
> P[A\cup B\cup C] &= P[A] + P[B] +P[C] \\[0.5em]
> &\quad - P[A \cap B] -P[A\cap C] - P[B\cap C] \\[0.5em]
> &\quad + P[A\cap B\cap C]
> \end{align}
> $$
> y para cuatro hay $4$ términos simples, $6$ intersecciones de a dos ($AB$, $AC$, $AD$, $BC$, $BD$, $CD$), $4$ de a tres y $1$ de las cuatro.

> [!proof]- **Proof.**
>
> **Borrador.** Inducción sobre $n$, usando el caso de dos eventos con $U = A_{1} \cup \dots \cup A_{n}$ y $A_{n+1}$. La intersección $U \cap A_{n+1}$ es otra unión de $n$ eventos, a la que se le aplica la H.I.
>
> **Proof.** Para $n = 1$ es trivial, y $n = 2$ es la Propiedad 7 de [[Medida de Probabilidad]]. Sup. que vale para cualesquiera $n$ eventos (H.I.), y sean $A_{1}, \dots, A_{n+1}$. Con $U = \bigcup_{i=1}^{n} A_{i}$,
> $$
> P\left[ \bigcup_{i=1}^{n+1} A_{i} \right] = P[U] + P[A_{n+1}] - P[U \cap A_{n+1}]
> $$
> y por distributividad $U \cap A_{n+1} = \bigcup_{i=1}^{n} (A_{i} \cap A_{n+1})$, otra unión de $n$ eventos. Aplicando la H.I. a $P[U]$ y a $P[U \cap A_{n+1}]$:
> - $P[U]$ da todos los términos con índices en $\{ 1, \dots, n \}$, con su signo correcto.
> - $P[A_{n+1}]$ es el término $\{ n+1 \}$, con signo $+$.
> - $-P[U \cap A_{n+1}]$ da, para cada $i_{1} < \dots < i_{k} \leq n$, el término de $\{ i_{1}, \dots, i_{k}, n+1 \}$ (de tamaño $k+1$) con signo $-(-1)^{k+1} = (-1)^{(k+1)+1}$, que es el correcto.
>
> Cada subconjunto de $\{ 1, \dots, n+1 \}$ aparece exactamente una vez y con su signo, que es la fórmula para $n+1$. $\blacksquare$

### Cotas

Cuando no conocemos las intersecciones, la inclusión-exclusión no sirve, pero quedándonos con el primer término sí podemos **acotar**:

> [!theorem] **Teorema.** (Desigualdad de Boole)
>
> Para $(A_{n})_{n=1}^{\infty}$ eventos en $\mathcal{F}$, se tiene que
> $$
> P\left[ \bigcup_{i=1}^{\infty} A_{i} \right] \leq \sum_{i=1}^{\infty} P[A_{i}],
> $$
> y lo mismo con una cantidad finita: $P\left[ \bigcup_{i=1}^{n} A_{i} \right] \leq \sum_{i=1}^{n} P[A_{i}]$.

> [!proof]- **Proof.** 
>
> **Borrador.** Volvemos ajena la unión: a cada $A_{k}$ le quitamos lo que ya estaba en los anteriores. Los pedazos $D_{k}$ son ajenos, cubren lo mismo y son más chicos.
>
> **Proof.** Vamos a usar a los eventos:
> $$
> D_{1} = A_{1}, \qquad D_{k} = A_{k} \setminus \bigcup_{i=1}^{k-1} A_{i} \quad (k \geq 2)
> $$
> que están en $\mathcal{F}$. ¿Qué cumplen los $D_{i}$?
> 1. $\displaystyle \bigcup_{i=1}^{\infty} D_{i} = \bigcup_{i=1}^{\infty} A_{i}$: $(\subseteq)$ porque $D_{i} \subseteq A_{i}$. $(\supseteq)$ si $\omega \in \bigcup A_{i}$, sea $k$ el menor índice con $\omega \in A_{k}$; ent. $\omega \notin A_{1}, \dots, A_{k-1}$, i.e. $\omega \in D_{k}$.
> 2. Son ajenos: $D_{i} \cap D_{j} = \varnothing$ si $i < j$, pues $D_{i} \subseteq A_{i}$ y $D_{j}$ no tiene puntos de $A_{i}$.
> 3. $\forall i  \ (D_{i} \subseteq A_{i}) \implies P[D_{i}]\leq P[A_{i}]$ (monotonía).
> 
> Con esto:
> $$
> \begin{align}
> P\left[ \bigcup_{i=1}^{\infty} A_{i} \right] &= P\left[  \bigcup_{i=1}^{\infty} D_{i} \right] \tag{1} \\[.5em]
> &= \sum_{i=1}^{\infty} P[D_{i}] \tag{2, axioma $(iii)$} \\[.5em]
> &\leq \sum_{i=1}^{\infty} P[A_{i}] \tag{3}
> \end{align}
> $$
> El caso finito sale tomando $A_{k} = \varnothing$ para $k > n$. $\blacksquare$

Aplicando Boole a los complementos sale una cota **inferior** para la intersección, útil cuando cada evento es muy probable:

> [!theorem] **Proposición.** (Desigualdad de Bonferroni)
>
> Sean $A_{1}, \dots, A_{n} \in \mathcal{F}$. Ent.
> $$
> P\left[  \bigcap_{i=1}^{n} A_{i} \right] \geq \sum_{i=1}^{n} P[A_{i}] - (n-1)
> $$

> [!proof]- **Proof.**
>
> Por Morgan, $\left( \bigcap_{i=1}^{n} A_{i} \right)^{c} = \bigcup_{i=1}^{n} A_{i}^{c}$. Ent.
> $$
> \begin{align}
> & P\left[ \bigcap_{i=1}^{n} A_{i} \right] \\[0.5em]
> &= 1 - P\left[ \bigcup_{i=1}^{n} A_{i}^{c} \right] \tag{complemento} \\[0.5em]
> &\geq 1 - \sum_{i=1}^{n} (1 - P[A_{i}]) \tag{Boole} \\[0.5em]
> &= \sum_{i=1}^{n} P[A_{i}] - (n-1) \tag*{$\blacksquare$}
> \end{align}
> $$

> [!example]- **Ejemplo 1.**
>
> Si cada uno de $5$ componentes funciona con proba. $0.98$, sin saber nada de cómo dependen entre sí, la proba. de que funcionen **todos** es al menos $5(0.98) - 4 = 0.9$.

### Diferencia simétrica

La **diferencia simétrica** $A \vartriangle B = (A \setminus B) \cup (B \setminus A)$ es el evento "ocurre exactamente uno de los dos". Su probabilidad se comporta como una distancia entre eventos:

> [!theorem] **Proposición.** (Propiedades)
>
> Sean $A, B, C \in \mathcal{F}$.
> 1. $P[A \vartriangle B ] = P[A] + P[B] - 2P[A \cap B]$
> 2. Desigualdad del triángulo:
> $$
> P[A \vartriangle C] \leq  P[A \vartriangle B] + P[B \vartriangle C]
> $$

> [!proof]- **Proof.**
>
> 1. $A \setminus B$ y $B \setminus A$ son ajenos, así que por la Propiedad 4 de [[Medida de Probabilidad]],
> $$
> P[A \vartriangle B] = (P[A] - P[A \cap B]) + (P[B] - P[A \cap B]). \tag*{$\blacksquare$}
> $$
> 2. Primero, $A \vartriangle C \subseteq (A \vartriangle B) \cup (B \vartriangle C)$: si $\omega \in A \setminus C$, o $\omega \in B$ (y ent. $\omega \in B \setminus C$) o $\omega \notin B$ (y ent. $\omega \in A \setminus B$); el caso $\omega \in C \setminus A$ es simétrico. Por monotonía y Boole,
> $$
> P[A \vartriangle C] \leq P[(A \vartriangle B) \cup (B \vartriangle C)] \leq P[A \vartriangle B] + P[B \vartriangle C]. \tag*{$\blacksquare$}
> $$
