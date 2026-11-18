---
modified: 2026-11-17T21:38:33Z
title: "Espacio de Probabilidad"
publish: true
type: zettel
date: "2026-08-19"
status: seed
aliases:
tags:
 - probability
cssclasses: 
 - romana
---
> [!theorem] **Definición.** (Espacio de Probabilidad)
>
> Un **espacio de probabilidad** es un espacio de medida finita cuya medida total es igual a la unidad. Se define como la terna $(\Omega,\mathcal{F},P)$:
> - **Espacio Muestral:** $\Omega \neq \varnothing$
> - $\sigma$**-álgebra de Eventos:** $\mathcal{F}$
> - **Medida de Probabilidad:** $P(A)$

> [!theorem] **Definición.** (Espacio Muestral) [Sample Space]
>
> El espacio muestral de un experimento aleatorio es el conjunto de todos los posibles resultados del experimento, denotado $\Omega$. A un resultado particular del experimento se le denota $\omega$.

La $\sigma$*-álgebra de eventos*<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup> es una familia de subconjuntos de $\Omega$ que cumple con tres propiedades. Funciona como ***aduana*** para restringir $\operatorname{dom}P$ a solo conjuntos tratables. Si $\Omega$ es finito o numerable no hace falta (podemos tomar $\mathcal{F} = \mathcal{P}(\Omega)$), pero si $\Omega$ es no numerable, como $[0,1]$, no se le puede asignar una probabilidad coherente a **todos** sus subconjuntos, y hay que quedarse con una familia más chica.

La *medida de probabilidad*<sup><a href="#user-content-fn-inline-2" id="user-content-fnref-inline-2" data-footnote-ref class="internal">2</a></sup> es una función $P: \mathcal{F} \to \mathbb{R}$ que asigna a cada *evento* en $\mathcal{F}$ un número real, y tiene que cumplir con tres axiomas. 

> [!Info]- **Nota!**
>
> - Un **experimento aleatorio** $\mathcal{E}$ aunque no lo parezca, también tiene su definición formal fenomenológica:
> 	- *Replicabilidad:* $\mathcal{E}$ puede ser repetido infinitamente bajo condiciones iniciales idénticas.
> 	- *Indeterminismo:* El resultado $\omega$ de una ejecución individual de $\mathcal{E}$ es impredecible *a priori*. Ningún modelo determinista puede asegurar cuál será el resultado de la siguiente iteración.
> 	- *Exhaustividad:* Se conoce el conjunto de todos los resultados posibles del experimento, esto es $\Omega$.
> 	- *Estabilidad de Frecuencias:* Si $\mathcal{E}$ se repite $n$-veces con $n\to \infty$, la frecuencia relativa con la que ocurre un evento $A \in \mathcal{F}$ tiende a estabilizarse alrededor de un límite constante, lo que designa a $P(A)$. Ojo: esto es la *interpretación* frecuentista de $P$, no parte de la definición formal; en el enfoque axiomático (Kolmogórov) se **demuestra** a partir de los axiomas, y es la ley de los grandes números.
> - Un **resultado** o **resultado elemental** $\omega$ es el desenlace más básico, indivisible y específico de un *experimento aleatorio*. Es claro que $\omega \in \Omega$. Los resultados elementales son mutuamente excluyentes (*si ocurre uno, es imposible que ocurra otro simultáneamente en la misma iteración del experimento*).
> - Un **evento** $A$ es una agrupación de resultados, denotados $A_{1},A_{2},A_{3},\dots$ Por definición, $A \subseteq \Omega$ y $A \in \mathcal{F}$.
> 	- **Ej.** Sea $\Omega = \{ \omega_{1},\omega_{2},\dots,\omega_{n} \}$ y sea $A = \{ \omega_{2},\omega_{4},\omega_{8} \}$.
> 	Es a los *eventos* a los que la función $P$ les asigna un número, $P(A)$. $P(\omega)$ es incorrecto: lo correcto es $P(\{ \omega \})$, la proba. del evento que solo contiene a $\omega$.
> - El par $(\Omega,\mathcal{F})$ constituye de manera independiente un **espacio medible**.

Muyyy en síntesis,
- $\Omega:=$ Conjunto de posibles resultados
- $\mathcal{F}:=$ Conjunto de posibles eventos
- $P :=$ Función que da probabilidades

Las propiedades básicas de $\mathcal{F}$ (que $\varnothing \in \mathcal{F}$, cerradura bajo intersecciones, etc.) están en [[Sigma-algebra de eventos]].

> [!example]- **Ejemplo 1.** (Medida clásica)
>
> Si $\Omega$ es finito y todos sus elementos son igual de probables, $P[A] = \frac{\lvert A \rvert}{\lvert \Omega \rvert}$: casos favorables entre casos totales. Los detalles, y por qué cumple los axiomas, en [[Medida de Probabilidad Clasica]].

> [!example]- **Ejemplo 2.** (Medida Frecuentista)
>
> Necesitamos que se realice el experimento muchas veces. Si en $n$ repeticiones el evento $A$ ocurre $n_{A}$ veces, su **frecuencia relativa** es $\frac{n_{A}}{n}$, y la idea frecuentista es
> > [!theorem] **Definición.** (Medida Frecuentista)
> >
> > $$
> > P[A] = \lim_{ n \to \infty } \frac{n_{A}}{n}
> > $$
> Ejemplo. Lanzar una moneda:
> - Experimentos $= \{ S, S, S, S, S ,A, S, A , A, A\}$ 
> $\frac{n_{S}}{n} = \frac{6}{10}$ y $\frac{n_{A}}{n} = \frac{4}{10}$. Con solo $10$ lanzamientos esto es una **estimación** de $P[S]$, no $P[S]$: con otros $10$ lanzamientos saldría otro número.

> [!example]- **Ejemplo 3.** (Medida Geométrica)
>
> Útil cuando $\Omega$ es una región del plano (**no numerable**) y todos sus puntos son "igual de probables". Definimos
> $$
> P[A] = \frac{\text{Área } (A) }{\text{Área }(\Omega)}
> $$
> Donde $0 < \text{Área }(\Omega) < \infty$.
> En esta medida, la probabilidad depende del tamaño (área) de $A$: es el análogo continuo de la *medida clásica*, con "contar" cambiado por "medir área".
> Tiene una consecuencia interesante, para todo punto $x$ su probabilidad es $0$, pues un punto tiene área $0$.
> 

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

[[Sigma-algebra de eventos]] <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
<li id="user-content-fn-inline-2">

[[Medida de Probabilidad]] <a href="#user-content-fnref-inline-2" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
