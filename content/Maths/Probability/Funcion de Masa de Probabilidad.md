---
modified: 2026-11-18T16:47:12Z
title: "Variable Aleatoria Discreta"
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
El caso más sencillo de [[Variable Aleatoria|v.a.]] es cuando sus valores se pueden enlistar: $x_{0}, x_{1}, x_{2}, \dots$ Entonces toda la información de $X$ cabe en una lista de probabilidades, una por valor.

> [!theorem] **Definición.** (V.A. Discreta)
>
> Sea $X$ una v.a. sobre $(\Omega ,\mathcal{F},P)$, diremos que es una **variable aleatoria discreta** si el conjunto de valores que puede tomar $X$, o sea $\operatorname{Im} \{X\}$, es **finito** o **infinito numerable**.

> [!theorem] **Definición.** (Función de Masa, Densidad o Probabilidad)
>
> Sea $X$ una v.a. discreta con valores $x_{0},x_{1}, \dots$ La función de proba de $X$, denotada $f_{X}: \mathbb{R} \to \mathbb{R}$ se define como
> $$
> f_{X}(x) = \begin{cases}
>   P(X = x) & x = x_{0},x_{1}\dots \\[0.5em]
>   0 & \text{ en otro caso }
> \end{cases}
> $$
> Otra forma de escribirlo, $f_{X}(x)  = P(X=x)$

Con $f_{X}$ ya se puede calcular la proba. de **cualquier** evento sobre $X$, sumando:

> [!theorem] **Proposición.**
>
> Sea $X$ discreta y $A \in \mathcal{B}(\mathbb{R})$. Ent.
> $$
> P(X \in A) = \sum_{x \in A} f_{X}(x),
> $$
> donde la suma es sobre los valores $x_{k}$ de $X$ que están en $A$ (los demás términos son $0$).

> [!proof]- **Proof.**
>
> El evento $(X \in A)$ es la unión de los eventos $(X = x_{k})$ con $x_{k} \in A$, que son ajenos (un $\omega$ no puede tener dos valores) y a lo más numerables. Por $\sigma$-aditividad,
> $$
> P(X \in A) = P\left( \bigcup_{x_{k} \in A} (X = x_{k}) \right) = \sum_{x_{k} \in A} P(X = x_{k}) = \sum_{x \in A} f_{X}(x). \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Así, la función de densidad $f_{X}$ muestra la forma en la que la probabilidad $P$ se distribuye sobre el conjunto de puntos $x_{0},x_{1}\dots$, es decir, sobre $\operatorname{Im} \{X\}$.

Que $f_{X}$ venga de una probabilidad le impone dos condiciones, y son las únicas:

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X$ una v.a. discreta sobre $(\Omega ,\mathcal{F},P)$, se cumple que
> 1. $\displaystyle f_{X}(x) \geq  0 \quad \forall  x \in  \mathbb{R}$
> 2. $\displaystyle \sum_{x} f_{X}(x) =1$

> [!proof]- **Proof.**
>
> 1. $f_{X}(x)$ es una probabilidad o $0$.
> 2. Es la Proposición con $A = \mathbb{R}$: $\sum_{x} f_{X}(x) = P(X \in \mathbb{R}) = P(\Omega) = 1$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Al revés también: cualquier $f$ que cumpla 1 y 2 y sea positiva solo en una cantidad numerable de puntos es la función de probabilidad de alguna v.a. discreta. Por eso las [[Distribuciones de Probabilidad|distribuciones discretas]] se definen dando solo $f$.

> [!example]- **Ejemplo 1.** (Águilas en 4 volados)
>
> Sea $X$ el núm. de águilas en 4 lanzamientos de una moneda justa (Ejemplo 2 de [[Variable Aleatoria]]). Contando cuántas de las $16$ sucesiones tienen $x$ águilas, $f_{X}(x) = \binom{4}{x}\frac{1}{16}$:
>
> | $x$ | $0$ | $1$ | $2$ | $3$ | $4$ |
> |---|---|---|---|---|---|
> | $f_{X}(x)$ | $\frac{1}{16}$ | $\frac{4}{16}$ | $\frac{6}{16}$ | $\frac{4}{16}$ | $\frac{1}{16}$ |
>
> Suman $\frac{16}{16} = 1$, y por ejemplo $P(X \geq 3) = f_{X}(3) + f_{X}(4) = \frac{5}{16}$. Es la [[Distribucion Binomial]] con $n = 4$, $p = \frac{1}{2}$.

> [!theorem] **Definición.** (Soporte)
>
> Dada $X$ v.a. discreta, su **soporte**, denotado $\operatorname{sop}(X)$ o $\operatorname{supp}(X)$, es
> $$
> \operatorname{supp}(X) = \{ x \in \mathbb{R} \mid f_{X}(x) > 0 \}.
> $$
> Por la Proposición, $P(X \in \operatorname{supp}(X)) = 1$.

> [!Info]- **Nota!** (Soporte en general)
>
> Para una v.a. cualquiera, el soporte se define como el **menor conjunto cerrado** $C$ con $P(X \in C) = 1$. Para una discreta no siempre coincide con $\{ x \mid f_{X}(x) > 0 \}$: si $P(X = \frac{1}{n}) = \frac{1}{2^{n}}$ para $n \geq 1$, ent. $\{ x \mid f_{X}(x) > 0 \} = \{ 1, \frac{1}{2}, \frac{1}{3}, \dots \}$ no es cerrado, y el menor cerrado que lo contiene le agrega el $0$. En el curso usamos la versión de la Definición. Para v.a.s continuas, ver [[Funcion de Densidad de Probabilidad]].

---
Siguiente: [[Funcion de Distribucion Acumulada]].
