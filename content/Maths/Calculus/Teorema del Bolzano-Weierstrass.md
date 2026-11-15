---
modified: 2026-11-15T03:56:58Z
title: "Teorema de Bolzano-Weierstrass"
publish: true
type: zettel
date: 2026-09-09
status: seed
aliases:
tags:
  - calculus
cssclasses:
  - romana
---
> Toda sucesión acotada en $\mathbb{R}$ posee al menos una subsucesión convergente en $\mathbb{R}$.

> [!theorem] **Teorema.** (Bolzano-Weierstrass)
>
> Sea $\{ a_{n} \}$ una sucesión acotada, entonces **existe** una **subsucesión** que converge a un número real $L$.

Ojo: no confundir con el **Teorema de Bolzano** (el de los signos opuestos, en [[Teorema del Valor Intermedio]]).

Para probarlo usamos que las [[Sucesiones Monotonas|monótonas]] acotadas convergen (Criterios 4 y 5 de [[Criterios de Convergencia de Sucesiones]]): basta encontrar una [[Subsucesiones|subsucesión]] monótona.

> [!theorem] **Lema.** (Subsucesión Monótona)
>
> Toda sucesión tiene una subsucesión monótona.

> [!proof]- **Proof.**
>
> **Borrador.** Decimos que $m$ es un **pico** de $\{ a_{n} \}$ si $a_{m} \geq a_{n}$ para todo $n > m$ (desde $a_{m}$ "se ve todo hacia abajo"). O hay una infinidad de picos, y forman una subsucesión decreciente, o hay finitos, y después del último siempre podemos subir.
>
> **Proof.**
> *Caso 1:* hay una infinidad de picos $m_{0} < m_{1} < m_{2} < \dots$ Como cada $m_{k}$ es pico y $m_{k+1} > m_{k}$, ent. $a_{m_{k}} \geq a_{m_{k+1}}$, i.e. $\{ a_{m_{k}} \}$ es decreciente.
>
> *Caso 2:* hay una cantidad finita de picos. Sea $n_{0}$ mayor que todos ellos ($n_{0} = 0$ si no hay). Como $n_{0}$ no es pico, existe $n_{1} > n_{0}$ con $a_{n_{1}} > a_{n_{0}}$. Como $n_{1} > n_{0}$ tampoco es pico, existe $n_{2} > n_{1}$ con $a_{n_{2}} > a_{n_{1}}$, y así sucesivamente (por inducción). Ent. $\{ a_{n_{k}} \}$ es estrictamente creciente.
> $$
> \tag*{$\blacksquare$}
> $$

> [!proof]- **Proof.** (Bolzano-Weierstrass)
>
> Por el Lema, $\{ a_{n} \}$ tiene una subsucesión monótona $\{ a_{n_{k}} \}$. Como $\lvert a_{n} \rvert \leq C$ para todo $n$ (por ser acotada), también $\lvert a_{n_{k}} \rvert \leq C$ para todo $k$, así que $\{ a_{n_{k}} \}$ es monótona y acotada. Por el Criterio 4 (si es creciente) o el Criterio 5 (si es decreciente), converge a algún $L \in \mathbb{R}$.
> $$
> \tag*{$\blacksquare$}
> $$

En un intervalo cerrado, además, el límite no se escapa del intervalo. Esta es la forma que se usa en los teoremas fuertes de continuidad ([[Teorema de Weierstrass y de Acotación]], [[Continuidad Uniforme]]):

> [!theorem] **Corolario.**
>
> Sea $[a,b]$ intervalo cerrado. Si $\{ x_{n} \}$ es una sucesión de puntos de $[a,b]$ entonces $\{ x_{n} \}$ tiene una subsucesión que converge a un punto de $[a,b]$.

> [!proof]- **Proof.**
>
> $a \leq x_{n} \leq b$ para todo $n$, ent. $\{ x_{n} \}$ está acotada y por Bolzano-Weierstrass tiene una subsucesión $x_{n_{k}} \to \alpha$. Como $a \leq x_{n_{k}} \leq b$ para todo $k$, por Conservación de Desigualdades ([[Limites de Sucesiones]]) $a \leq \alpha \leq b$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Hace falta que el intervalo sea **cerrado**: $\left\{ \frac{1}{n} \right\}$ está en $(0,1]$, pero todas sus subsucesiones tienden a $0 \notin (0,1]$.
