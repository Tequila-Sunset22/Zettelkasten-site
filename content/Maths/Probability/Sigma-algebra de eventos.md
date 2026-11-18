---
modified: 2026-11-17T21:38:33Z
publish: true
type: zettel
date: "2026-08-24"
status: seed
aliases:
tags:
 - probability
cssclasses: 
 - romana
---
# $\sigma$-álgebra de Eventos

$\mathcal{F}$ es una colección de subconjuntos de $\Omega$ que agrupa a todos los eventos que pueden ser medidos lógicamente.

> **Notación.** Denotamos $(A_{n})_{n=1}^{\infty}$ ó $A_{1},A_{2},A_{3},\dots$ a cualquier sucesión infinita *numerable* de *eventos*.

> [!theorem] **Definición.** ($\sigma$-álgebra de Eventos)
>
> Sea $\Omega$ un conjunto arbitrario no vacío (*espacio muestral*). Un conjunto $\mathcal{F}$ de subconjuntos de $\Omega$ (i.e. una familia $\mathcal{F} \subseteq \mathcal{P}(\Omega)$), se denomina $\sigma$**-álgebra** sobre $\Omega$ si satisface axiomáticamente las siguientes condiciones:
> 1. $\Omega \in \mathcal{F}$
> 2. $\forall A (A \in \mathcal{F} \implies A^{c} \in \mathcal{F})$
> 3. Cerradura bajo uniones numerables:
> Sea $(A_{i})_{i=1}^{\infty}$ una sucesión de eventos tal que $A_{i} \in \mathcal{F}$ para todo $i \geq 1$. Ent.
> $$
> 	\bigcup_{i=1}^{\infty} A_{i} \in \mathcal{F}
> $$


> [!Info]- **Nota!**
>
> Podemos interpretar a $\mathcal{F}$ como una "lista de eventos válidos" que se define con los axiomas:
> - $(i) \ \ \Omega \in \mathcal{F}$ representa la pregunta fundamental: ¿Cuál es la probabilidad de que ocurra cualquier cosa dentro de todas las posiblidades?
> - $(ii)$ Si se puede saber la probabilidad de que suceda $A$, por coherencia lógica, debe ser capaz de medir lo que falta ("que **no** suceda $A$").
> - $(iii)$ Si mi "lista" me permite hacer una secuencia infinita pero **numerable** (*indexada*) de preguntas válidas, agrupar todas esas preguntas en una sola también debe ser válido. *Esto es lo que permite usar límites, convergencia, cálculo...*


> [!theorem] **Teorema.** (Propiedades)
>
> Sea $\mathcal{F}$ una $\sigma$-álgebra sobre $\Omega$.
> 1. $\varnothing \in \mathcal{F}$
> 2. Cerradura bajo uniones finitas: Sea $k \geq 1$,
> $$
> A_{1},A_{2},\dots,A_{k} \in \mathcal{F} \implies \bigcup_{i=1}^{k} A_{i} \in \mathcal{F}
> $$
> 3. Cerradura bajo intersecciones numerables (infinitas):
> $$
> A_{1},A_{2},\dots \in \mathcal{F} \implies\bigcap_{i=1}^{\infty}A_{i} \in \mathcal{F}
> $$
> 4. Cerradura bajo intersecciones finitas:
> $$
> A_{1},A_{2},\dots,A_{k} \in \mathcal{F} \implies \bigcap_{i=1}^{k} A_{i} \in \mathcal{F}
> $$
> 5. Cerradura bajo diferencia:
> $$
> A,B \in \mathcal{F} \implies A\setminus B \in \mathcal{F}
> $$

> [!proof]- **Proof.** 
>
> 1. **P.D.** $\varnothing \in \mathcal{F}$
> Por axioma $(i)$ tenemos que $\Omega \in \mathcal{F}$. Aplicando axioma $(ii)$, $\Omega^{c} \in \mathcal{F}$. Pero $\Omega^{c} = \varnothing \ !$ Por lo que $\varnothing \in \mathcal{F} \quad \blacksquare$
> 2. **P.D.** $\displaystyle A_{1},\dots,A_{k} \in \mathcal{F} \implies \bigcup_{n=1}^{k} A_{n} \in \mathcal{F}$
> Sean $A_{1},\dots,A_{k} \in \mathcal{F}$. Definimos constructivamente una sucesión infinita $(B_{n})_{n=1}^{\infty}$ de la siguiente manera:
> $$
> B_{n} = \begin{cases}
> A_{n} &  1\leq n\leq k \\
> \varnothing & n>k
> \end{cases}
> $$
> Dado $\varnothing \in \mathcal{F}$ (por 1), $B_{n} \in \mathcal{F}$ para todo $n \geq 1$. Utilizando el axioma $(iii)$, tenemos
> $$
> \bigcup_{n=1}^{k} A_{n} = \left( \bigcup_{n=1}^{k} A_{n} \right) \cup \left( \bigcup_{n=k+1}^{\infty} \varnothing  \right) = \bigcup_{n=1}^{\infty} B_{n} \in \mathcal{F} \tag*{$\blacksquare$}
> $$
> 3. **P.D.** $\displaystyle A_{1}, A_{2}, \dots \in \mathcal{F} \implies \bigcap_{n=1}^{\infty}A_{n} \in \mathcal{F}$
> Sean $A_{1}, A_{2}, \dots \in \mathcal{F}$. Por axioma $(ii)$, los complementos cumplen que $A_{n}^{c} \in \mathcal{F}$ para todo $n \geq 1$. Por axioma $(iii)$ obtenemos
> $$
> \bigcup_{n=1}^{\infty} A_{n}^{c} \in \mathcal{F}
> $$
> Aplicando axioma $(ii)$ nuevamente
> $$
> \left( \bigcup_{n=1}^{\infty} A_{n}^{c} \right)^{c} \in \mathcal{F}
> $$
> por la Ley de DeMorgan<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup> para la unión tenemos
> $$
> \left( \bigcup_{n=1}^{\infty} A_{n}^{c} \right)^{c} = \bigcap_{n=1}^{\infty} (A^{c}_{n})^{c} = \bigcap_{n=1}^{\infty} A_{n} \tag*{$\blacksquare$}
> $$
> 4. **P.D.** $\displaystyle A_{1},\dots,A_{k} \in \mathcal{F} \implies \bigcap_{n=1}^{k}A_{n} \in \mathcal{F}$
> La demo. es análoga a la de la propiedad 2, usando 3 y con $\Omega$ en lugar de $\varnothing$: $B_{n} = A_{n}$ para $n \leq k$ y $B_{n} = \Omega$ para $n > k$, ent. $\bigcap_{n=1}^{k} A_{n} = \bigcap_{n=1}^{\infty} B_{n} \in \mathcal{F}$. $\blacksquare$
> 
> 5. **P.D.** $A,B \in \mathcal{F} \implies A\setminus B \in \mathcal{F}$
> Por def. $A \setminus B = A \cap B^{c}$. Por hip. $B \in \mathcal{F}$. Mediante axioma $(ii)$, se deduce que $B^{c} \in \mathcal{F}$. Dado que tenemos $A,B^{c} \in \mathcal{F}$, y $\mathcal{F}$ es cerrada bajo intersecciones finitas (propiedad 4), la intersección de ambos eventos pertenece a $\mathcal{F}$. Por lo tanto, $A\cap B^{c} \in \mathcal{F}\quad \blacksquare$

> [!observation]+ **Observación.**
>
> - El complemento siempre es respecto a $\Omega$: $A^{c} = \Omega \setminus A$.
> - Por definición, cualquier $\sigma$-álgebra cumple $\mathcal{F} \subseteq \mathcal{P}(\Omega)$.

Las dos $\sigma$-álgebras extremas sobre cualquier $\Omega$ son la más chica posible y la más grande posible:

> [!example]- **Ejemplo 1.** ($\sigma$-álgebra trivial)
>
> $\mathcal{F}_{0} = \{ \varnothing, \Omega \}$ es una $\sigma$-álgebra, conocida como $\sigma$-álgebra cero o trivial: $\Omega \in \mathcal{F}_{0}$, $\Omega^{c} = \varnothing$ y $\varnothing^{c} = \Omega$, y cualquier unión de elementos de $\mathcal{F}_{0}$ es $\varnothing$ (si todos son $\varnothing$) o $\Omega$. Por la propiedad 1, está contenida en **toda** $\sigma$-álgebra sobre $\Omega$.

> [!theorem] **Tarea.**
>
> Demuestra que $\mathcal{P}(\Omega)$ es una $\sigma$-álgebra.

> [!proof]- **Proof.**
>
> 1. $\Omega \subseteq \Omega$, ent. $\Omega \in \mathcal{P}(\Omega)$.
> 2. Si $A \in \mathcal{P}(\Omega)$, ent. $A^{c} = \Omega \setminus A \subseteq \Omega$, i.e. $A^{c} \in \mathcal{P}(\Omega)$.
> 3. Si $A_{1}, A_{2}, \dots \in \mathcal{P}(\Omega)$, cada $A_{i} \subseteq \Omega$, ent. $\bigcup_{i=1}^{\infty} A_{i} \subseteq \Omega$, i.e. $\bigcup_{i=1}^{\infty} A_{i} \in \mathcal{P}(\Omega)$. $\blacksquare$
>
> Es la $\sigma$-álgebra más grande sobre $\Omega$: cualquier otra está contenida en ella.

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

[[Leyes de DeMorgan]] <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
