---
modified: 2026-11-17T21:38:33Z
publish: true
type: zettel
date: "2026-09-28"
status: seed
aliases:
tags:
 - probability
cssclasses: 
 - romana
---
# $\sigma$-álgebra de $\mathcal{B}$orel

Para hablar de la probabilidad de que una v.a. caiga en un intervalo, necesitamos una $\sigma$-álgebra sobre $\mathbb{R}$ que contenga a los intervalos. $\mathcal{P}(\mathbb{R})$ es demasiado grande (no se le puede asignar probabilidad coherente a todos los subconjuntos, ver [[Espacio de Probabilidad]]), así que buscamos la **más chica** que contenga a los intervalos. Para que "la más chica" tenga sentido, primero hay que ver que siempre existe.

> [!theorem] **Proposición.**
>
> Sea $\{ \mathcal{F}_{j} \}_{j \in J}$ una familia no vacía de $\sigma$-álgebras sobre $\Omega$. Ent. $\bigcap_{j \in J} \mathcal{F}_{j}$ también es una $\sigma$-álgebra sobre $\Omega$.

> [!proof]- **Proof.**
>
> Sea $\mathcal{F} = \bigcap_{j \in J}\mathcal{F}_{j}$.
> 1. $\Omega \in \mathcal{F}_{j}$ para todo $j$, ent. $\Omega \in \mathcal{F}$.
> 2. Si $A \in \mathcal{F}$, ent. $A \in \mathcal{F}_{j}$ para todo $j$, y como cada $\mathcal{F}_{j}$ es $\sigma$-álgebra, $A^{c} \in \mathcal{F}_{j}$ para todo $j$, i.e. $A^{c} \in \mathcal{F}$.
> 3. Si $A_{1}, A_{2}, \dots \in \mathcal{F}$, ent. están en cada $\mathcal{F}_{j}$, y $\bigcup_{i=1}^{\infty} A_{i} \in \mathcal{F}_{j}$ para todo $j$, i.e. $\bigcup_{i=1}^{\infty} A_{i} \in \mathcal{F}$. $\blacksquare$

> [!theorem] **Definición.** ($\sigma$-álgebra generada)
>
> Sea $\mathcal{C}$ una colección de subconjuntos de $\Omega$. La **$\sigma$-álgebra generada** por $\mathcal{C}$, denotada $\sigma(\mathcal{C})$, es la intersección de todas las $\sigma$-álgebras sobre $\Omega$ que contienen a $\mathcal{C}$.

> [!observation]+ **Observación.**
>
> - La familia que se intersecta no es vacía: $\mathcal{P}(\Omega)$ siempre contiene a $\mathcal{C}$. Por la Proposición, $\sigma(\mathcal{C})$ es una $\sigma$-álgebra.
> - Es la **mínima** que contiene a $\mathcal{C}$: si $\mathcal{G}$ es una $\sigma$-álgebra con $\mathcal{C} \subseteq \mathcal{G}$, ent. $\mathcal{G}$ es una de las que se intersectan, así que $\sigma(\mathcal{C}) \subseteq \mathcal{G}$.

> [!theorem] **Definición.** (Sigma álgebra de Borel)
>
> La **sigma álgebra de Borel** de $\mathbb{R}$, denotada $\mathcal{B}(\mathbb{R})$, se define como la mínima $\sigma$-álgebra de subconjuntos de $\mathbb{R}$ que contiene todos los intervalos de la forma $(-\infty,x]$. Esto se escribe:
> $$
> \mathcal{B}(\mathbb{R})  := \sigma \{ (-\infty,x] \mid x \in  \mathbb{R}\}
> $$
>
> A los elementos de $\mathcal{B}(\mathbb{R})$ se les llama conjuntos de Borel, o Borel medibles, o borelianos de $\mathbb{R}$.

Aunque la definición solo pone semirrectas $(-\infty, x]$, con las operaciones de $\sigma$-álgebra ya salen todos los intervalos y los puntos:

> [!theorem] **Proposición.** (Propiedades)
>
> Para $a < b$ en $\mathbb{R}$, son borelianos:
> 1. $(a, \infty)$ y $(a, b]$.
> 2. $(-\infty, a)$ y $\{ a \}$.
> 3. $(a, b)$, $[a, b]$ y $[a, b)$.

> [!proof]- **Proof.**
>
> 1. $(a, \infty) = (-\infty, a]^{c}$, y $(a, b] = (-\infty, b] \setminus (-\infty, a]$ (cerradura bajo diferencia, ver [[Sigma-algebra de eventos]]).
> 2. $(-\infty, a) = \bigcup_{n=1}^{\infty}\left( -\infty, a - \frac{1}{n} \right]$, unión numerable. Y $\{ a \} = (-\infty, a] \setminus (-\infty, a)$.
> 3. $(a, b) = (-\infty, b) \cap (a, \infty)$, $[a, b] = (a, b) \cup \{ a \} \cup \{ b \}$ y $[a, b) = (a, b) \cup \{ a \}$, por 1, 2 y cerradura bajo uniones e intersecciones finitas. $\blacksquare$

> [!observation]+ **Observación.**
>
> Por lo mismo, cualquier conjunto numerable (como $\mathbb{N}$ o $\mathbb{Q}$) es boreliano: es unión numerable de puntos. Y $\mathcal{B}(\mathbb{R})$ se pudo haber generado con los intervalos abiertos, o con los cerrados: todas esas colecciones generan la misma $\sigma$-álgebra.
