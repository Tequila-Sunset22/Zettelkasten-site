---
modified: 2026-11-17T22:20:24Z
title: "Variable Aleatoria"
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
> Es una función que asigna un real a cada resultado de un experimento.

Trabajar directamente con $\Omega$ es incómodo: sus elementos pueden ser sucesiones de volados, manos de póker, cualquier cosa. Una variable aleatoria **traduce** cada resultado a un número, y así las preguntas sobre el experimento se vuelven preguntas sobre subconjuntos de $\mathbb{R}$, donde sí tenemos herramientas (intervalos, sumas, integrales). Lo único que hay que pedirle a la traducción es que las preguntas razonables ("¿$X$ es a lo más $x$?") sigan siendo eventos, para poder medirlas.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Cada umbral $x$ en $\mathbb{R}$ define un evento en $\Omega$: los $\omega$ con $X(\omega) \leq x$. La definición pide que ese evento esté en $\mathcal{F}$.
> ![[variable-aleatoria-preimagen.svg|center|600]]

> [!theorem] **Definición.** (Variable Aleatoria)
>
> Una variable aleatoria, denotada $X$, es una función $X: \Omega \to \mathbb{R}$ tal que para cualquier $x \in  \mathbb{R}$,
> $$
> (X \leq x) := \{ \omega \in \Omega \mid X(\omega ) \leq x \} \in  \mathcal{F}
> $$
>
> Sea $A \subseteq \mathbb{R}$, denotamos $(X \in A)$ como la imagen inversa de $A$
> $$
> (X \in  A) = X^{-1}(A) = \{ \omega  \in  \Omega  \mid  X(\omega ) \in A \}
> $$

La variable aleatoria no es ni variable, ni aleatoria: es una función determinista, que relaciona resultados $\omega$ con números reales. Sin embargo, *su nombre se justifica al considerar que los posibles resultados del experimento son los valores de la función* $X$.

> [!example]- **Ejemplo 1.**
>
> Sea $A = (x,y)$, considerando $(X \in  A)$ podemos también escribirlo de la forma $( x < X < y )$, es decir
> $$
> (X \in (x,y)) = \{  \omega  \in  \Omega  \mid  x < X(\omega) < y \}
> $$
> De misma forma $(X \in (-\infty,x])$ es $(X \leq  x)$, es decir
> $$
> (X \in (-\infty,x]) = \{ \omega \in  \Omega  \mid X(\omega) \leq x  \}
> $$
> Y este último es una condición muy especial (*condición de medibilidad*), nótese que está en nuestra definición de Variable Aleatoria.

La definición solo pide que las semirrectas $(-\infty, x]$ tengan preimagen en $\mathcal{F}$. Pero queremos preguntar por cualquier intervalo, un punto, o cualquier boreliano. No hace falta pedirlo aparte: sale gratis.

> [!theorem] **Proposición.**
>
> Si $X$ es v.a., ent. $(X \in A) \in \mathcal{F}$ para todo $A \in \mathcal{B}(\mathbb{R})$ ([[Sigma-algebra de Borel]]).

> [!proof]- **Proof.**
>
> **Borrador.** Los conjuntos "buenos" (con preimagen en $\mathcal{F}$) forman una $\sigma$-álgebra, porque la imagen inversa respeta complementos y uniones. Como contiene a las semirrectas, contiene a la mínima que las contiene, que es $\mathcal{B}(\mathbb{R})$.
>
> **Proof.** Sea $\mathcal{G} = \{ A \subseteq \mathbb{R} \mid X^{-1}(A) \in \mathcal{F} \}$.
> 1. $X^{-1}(\mathbb{R}) = \Omega \in \mathcal{F}$, ent. $\mathbb{R} \in \mathcal{G}$.
> 2. Si $A \in \mathcal{G}$, $X^{-1}(A^{c}) = (X^{-1}(A))^{c} \in \mathcal{F}$, ent. $A^{c} \in \mathcal{G}$.
> 3. Si $A_{1}, A_{2}, \dots \in \mathcal{G}$, $X^{-1}\left( \bigcup_{n} A_{n} \right) = \bigcup_{n} X^{-1}(A_{n}) \in \mathcal{F}$, ent. $\bigcup_{n} A_{n} \in \mathcal{G}$.
>
> Así $\mathcal{G}$ es una $\sigma$-álgebra sobre $\mathbb{R}$ que, por la def. de v.a., contiene a todas las semirrectas $(-\infty, x]$. Como $\mathcal{B}(\mathbb{R})$ es la **mínima** con esa propiedad, $\mathcal{B}(\mathbb{R}) \subseteq \mathcal{G}$. $\blacksquare$

Como $(X \in A) \in \mathcal{F}$, podemos calcular $P(X \in A)$ para cualquier $A \in \mathcal{B}(\mathbb{R})$. Es decir, $X$ **induce** una medida de probabilidad sobre los subconjuntos de $\mathbb{R}$:

> [!theorem] **Definición.** (Medida de Probabilidad Inducida)
>
> Sea $X$ v.a. La **medida de probabilidad inducida por** $X$ es la función $P_{X}: \mathcal{B}(\mathbb{R}) \to \mathbb{R}$,
> $$
> P_{X}(A) = P(X \in A) = P(X^{-1}(A)).
> $$

> [!theorem] **Proposición.**
>
> $P_{X}$ es una medida de probabilidad sobre $(\mathbb{R}, \mathcal{B}(\mathbb{R}))$. Así pues, tenemos un nuevo esp. de proba. de interés, $(\mathbb{R}, \mathcal{B}(\mathbb{R}), P_{X})$.

> [!proof]- **Proof.**
>
> 1. $P_{X}(A) = P(X^{-1}(A)) \geq 0$.
> 2. $P_{X}(\mathbb{R}) = P(\Omega) = 1$.
> 3. Si $A_{1}, A_{2}, \dots$ son borelianos ajenos, sus preimágenes son ajenas (un $\omega$ no puede ir a dos lugares), y $X^{-1}\left( \bigcup A_{n} \right) = \bigcup X^{-1}(A_{n})$. Por $\sigma$-aditividad de $P$, $P_{X}\left( \bigcup A_{n} \right) = \sum P_{X}(A_{n})$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Desde aquí casi nunca volvemos a $\Omega$: todo lo que nos importa de $X$ está en $P_{X}$, su **distribución**. Por eso dos v.a.s definidas en experimentos completamente distintos pueden tener "la misma distribución" (ver [[Distribuciones de Probabilidad]]).

Un ejemplo sencillo y que se usa todo el tiempo es la v.a. que solo dice si un evento ocurrió o no:

> [!theorem] **Definición.** (Función Indicadora)
>
> Sea $A \in \mathcal{F}$ un evento. La v.a. que toma el valor $1$ si $A$ ocurre y $0$ si $A$ no ocurre es llamada **función indicadora**, denotada:
> $$
> \mathbb{1}_{A}(\omega) = \begin{cases}
>   1 & \omega \in A \\[0.5em]
>   0 & \omega \not\in A
> \end{cases}
> $$

> [!observation]+ **Observación.**
>
> $\mathbb{1}_{A}$ es v.a. **sii** $A \in \mathcal{F}$: $(\mathbb{1}_{A} \leq x)$ es $\varnothing$ si $x < 0$, $A^{c}$ si $0 \leq x < 1$, y $\Omega$ si $x \geq 1$, y los tres están en $\mathcal{F}$ sii $A$ lo está.

> [!example]- **Ejemplo 2.**
>
> Queremos saber la cantidad de águilas que salieron en 4 lanzamientos de una moneda. Esto podríamos definirlo como una función $X: \Omega \to \mathbb{R}$ tal que para cada $\omega  \in  \Omega$ se define $X(\omega ) = \# \text{ de águilas en } \omega$.
> Al ser función, tenemos su imagen inversa, sea $B \subseteq \mathbb{R}$.
> $$
> X^{-1}[B] = \{ \omega  \in  \Omega \mid X(\omega ) \in B  \}
> $$
> En este experimento nos interesa $B = \{ x \}$, con $x \in  \{ 0, 1, 2, 3, 4 \}$ (el núm. de águilas), es decir
> $$
> X^{-1}[\{ x \}] = \{ \omega \in \Omega \mid X(\omega ) = x \}
> $$
> Obsérvese que $X^{-1}[\{ 2 \}]$ está en $\mathcal{F}$ (*sigma-álgebra*), por lo que le podemos asignar una proba. Como $\Omega$ tiene $2^{4} = 16$ resultados igual de probables y $X^{-1}[\{ 2 \}]$ tiene $\binom{4}{2} = 6$ (escoger qué lanzamientos son águila), $P(X = 2) = \frac{6}{16}$ (ver [[Medida de Probabilidad Clasica]]).

---

###### Referencias

- https://blog.nekomath.com/proba1-variables-aleatorias/
