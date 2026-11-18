---
modified: 2026-11-18T16:46:59Z
title: "Variable Aleatoria Continua"
publish: true
type: zettel
date: 2026-09-30
status: seed
aliases:
tags:
  - probability
cssclasses:
  - romana
---
> Intuitivamente, una variable aleatoria es **continua** cuando puede tomar cualquier valor dentro de un intervalo $(a,b) \subseteq  \mathbb{R}$, sin que ningún valor en particular tenga probabilidad positiva. Para formalizar esto usamos la [[Funcion de Distribucion Acumulada|función de distribución]].

Los saltos de $F$ son exactamente los puntos con probabilidad positiva, así que "ningún valor tiene probabilidad positiva" se dice simplemente así:

> [!theorem] **Definición.** (V.A. Continua)
>
> Se dice que una v.a. $X$ es continua si su función de distribución $F(x)$ es una función continua.

> [!theorem] **Proposición.**
>
> Si $X$ es continua, ent. $P(X = x) = 0$ para todo $x \in \mathbb{R}$, y en particular $P(X \leq x) = P(X < x)$.

> [!proof]- **Proof.**
>
> Por la Proposición de [[Funcion de Distribucion Acumulada]], $P(X = x) = F(x) - F(x^{-})$, que es $0$ porque $F$ es continua. Y $P(X \leq x) = P(X < x) + P(X = x)$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Por eso con una v.a. continua da lo mismo usar $<$ o $\leq$ en los intervalos (como en [[Distribucion Uniforme Continua]]), y por eso preguntar por la proba. de un valor exacto no tiene sentido. Ojo: $P(X = x) = 0$ no quiere decir que $X = x$ sea imposible; algún valor tiene que salir.

En la práctica las v.a.s continuas se manejan con una **densidad**: una función cuya área da las probabilidades.

> [!theorem] **Definición.** (Función de Densidad)
>
> Sea $X$ una v.a. **continua**. Decimos que la función integrable y no negativa $f: \mathbb{R}\to \mathbb{R}$ es la **función de densidad de** $X$ si para cualquier intervalo $[a,b] \subseteq \mathbb{R}$ se cumple
> $$
> P(X \in [a,b]) = \int_{a}^{b} f(x) \, dx
> $$

> [!Info]- **Nota!** (No toda continua tiene densidad)
>
> Que $F$ sea continua **no** garantiza que exista una densidad: hay v.a.s continuas cuya $F$ (la "escalera del diablo", construida con el conjunto de Cantor) es continua, crece de $0$ a $1$, y aun así tiene derivada $0$ en casi todo punto, así que ninguna $f$ integra a ella. Las que sí tienen densidad se llaman **absolutamente continuas**, y son las que usamos en el curso: cuando decimos "$X$ continua con densidad $f$", es esto.

La densidad y la función de distribución se determinan una a la otra: $F$ es el área acumulada de $f$, y $f$ es la pendiente de $F$.

> [!theorem] **Teorema.** (Función de Distribución Continua)
>
> Sea $X$ con función de densidad $f$. Ent.
> $$
> F(x) = \int_{-\infty}^{x} f(u) \, du
> $$
> y, por el [[Teorema Fundamental de Cálculo|T.F.C.]], en cada punto $x$ donde $f$ es continua,
> $$
> F'(x) = f(x).
> $$

> [!proof]- **Proof.**
>
> $(X \in [-n, x]) \uparrow (X \leq x)$ (para $n \geq -x$), así que por [[Continuidad de la Probabilidad]],
> $$
> F(x) = \lim_{ n \to \infty } P(X \in [-n, x]) = \lim_{ n \to \infty } \int_{-n}^{x} f(u) \, du = \int_{-\infty}^{x} f(u) \, du.
> $$
> La segunda parte es el T.F.C. aplicado a $F(x) = \int_{-\infty}^{x} f$. $\blacksquare$

> [!theorem] **Teorema.** (Propiedades)
>
> Toda función de densidad $f(x)$ de una v.a. continua cumple, análogo a las propiedades discretas:
> 1. $f(x) \geq  0 \quad \forall  x \in \mathbb{R}$
> 2. $\displaystyle \int_{-\infty}^{\infty} f(x) \, dx = 1$

> [!proof]- **Proof.**
>
> 1. Es parte de la definición.
> 2. Por el Teorema, $\int_{-\infty}^{x} f = F(x)$, y haciendo $x \to \infty$ queda $\lim_{x \to \infty} F(x) = 1$ (Propiedades de [[Funcion de Distribucion Acumulada]]). $\blacksquare$

> [!example]- **Ejemplo 1.** (Exponencial)
>
> Sea $f(x) = e^{-x}$ para $x \geq 0$ y $0$ en otro caso ([[Distribucion Exponencial]] con $\lambda = 1$). Ent. para $x \geq 0$,
> $$
> F(x) = \int_{0}^{x} e^{-u} \, du = 1 - e^{-x},
> $$
> y $P(1 \leq X \leq 2) = F(2) - F(1) = e^{-1} - e^{-2} \approx 0.233$. Derivando, $F'(x) = e^{-x} = f(x)$ para $x > 0$; en $x = 0$, $f$ salta y $F$ no es derivable.

> [!theorem] **Definición.** (Soporte)
>
> Dada $X$ v.a. continua con función de densidad $f_{X}$, su soporte es
> $$
> \operatorname{sop}(X) = \{ x \in \mathbb{R} \mid f_{X}(x) > 0 \}
> $$

> [!observation]+ **Observación.**
>
> Cambiar $f_{X}$ en un punto no cambia ninguna integral, así que la densidad **no es única** y este conjunto depende de qué versión escojamos (lo mismo que pasa con la [[Moda]]). Se usa la versión "natural" de $f_{X}$; la definición general de soporte, que no tiene este problema, está en la Nota de [[Funcion de Masa de Probabilidad]].

---
Siguiente: [[Cambio de Variable Aleatoria]].
