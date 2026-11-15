---
modified: 2026-11-15T03:57:24Z
title: "Raíces"
publish: true
type: zettel
date: "2026-10-02"
status: seed
aliases:
tags:
 - calculus
cssclasses: 
 - romana
---
Algunas consecuencias de los teoremas fuertes de continuidad de los reales.

> [!theorem] **Teorema.** (Existencia de Raíces)
>
> Sea $n \in \mathbb{N}^{+}$ y sea $a \in \mathbb{R}, a > 0$, entonces existe un $b \in \mathbb{R}, b > 0$ tal que $b^{n} = a$.
>
> Además, $b$ es **único**, y lo denotamos $b = \sqrt[n]{ a } = a^{1/n}$.

> [!proof]- **Proof.**
>
> **Existencia.** Sea $f(x) = x^{n}$, que es continua en $[0, 1+a]$ (producto de continuas). Tenemos
> $$
> f(0) = 0 < a \qquad \text{y} \qquad f(1+a) = (1+a)^{n} \geq 1 + a > a
> $$
> donde $(1+a)^{n} \geq 1+a$ porque $1 + a \geq 1$ (o por la [[Desigualdad de Bernoulli]]). Por el T.V.I. ([[Teorema del Valor Intermedio]]) existe $b \in (0, 1+a)$ tal que $b^{n} = a$, y $b > 0$.
>
> **Unicidad.** $x \mapsto x^{n}$ es estrictamente creciente en $[0, \infty)$: si $0 \leq x < y$, ent. $x^{n} < y^{n}$ (por inducción, multiplicando desigualdades de positivos). Si $b, b' > 0$ con $b \neq b'$, s.p.g. $b < b'$, ent. $b^{n} < b'^{n}$, así que no pueden ser ambos iguales a $a$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Esto **no** se puede probar en $\mathbb{Q}$: $x^{2} = 2$ no tiene solución racional. El T.V.I. depende del Axioma del Supremo (a través de la convergencia de sucesiones monótonas).
