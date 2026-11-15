---
modified: 2026-11-15T05:05:34Z
title: "Partición de un conjunto"
publish: true
type: zettel
date: "2026-07-02"
aliases:
 - Partition
tags: 
 - calculus
 - algebra
 - sets
cssclasses: 
 - romana
---
> [!theorem] **Def.** (Partition)
>
> Let $S$ be a nonempty set. A **partition** $\mathscr{P}$ of $S$ is a family<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup> $\mathscr{P} = \{ A_{i} \}_{i \in I}$ of nonempty subsets of $S$ satifying:
> $$
> \begin{align}
> \bigcup_{i \in I} A_{i} &= S  \\[1em]
> A_{i} \cap A_{j} &= \varnothing \ \ \ \text{ if } \ \ i \neq j
> \end{align}
> $$
> The $A_{i}$ are called the **blocks** of the partition.


> [!theorem] **Def.** (Particiones)
>
> Sean $A$ e $I$ conjuntos no vacíos tales que para cada $i \in I$, existe un subconjunto $A_{i}$ de $A$. Decimos que el conjunto
> $$
> P= \{ A_{i} : i \in I \}
> $$
> es una **partición** de $A$ si y sólo si
> 1. $\forall i \in I, A_{i} \neq \varnothing$
> 2. si $i,j \in I$ son tales que $A_{i} \neq A_{j}$, entonces $A_{i}\cap A_{j} = \varnothing$
> 3. $\forall a \in A \ \exists i \in I \mid a \in A_{i}$

> [!observation]+ **Observación**
>
> La condición (iii) y dado que los elementos de la partición son subconjuntos de $A$, obtenemos que 
> $$
> A = \bigcup_{i \in I} A_{i}
> $$


---

La partición de un **intervalo** $[a,b]$ (en Cálculo) es otra cosa: puntos $a = x_{0} < \dots < x_{n} = b$ cuyos subintervalos comparten extremos. Está en [[Definiendo la Integral]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

[[Familia Indexada]] <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
