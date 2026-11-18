---
modified: 2026-11-17T22:20:24Z
title: "Eventos independientes vs. ajenos"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Eventos Ajenos e Independientes
 - Mutuamente Excluyentes
tags:
 - probability
cssclasses:
 - romana
---
"Ajenos" e "independientes" suenan a lo mismo: dos eventos "que no tienen nada que ver". Es una de las confusiones más comunes al empezar probabilidad, y en realidad son casi lo **contrario**. Ser ajenos es una propiedad de los **conjuntos** ($A$ y $B$ no comparten resultados) y ni siquiera menciona a $P$; ser independientes es una propiedad de la **probabilidad** (saber que pasó uno no cambia la proba. del otro).<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> Ajenos habla de conjuntos; independientes habla de probabilidades.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Independientes: dos franjas que se cruzan, y la intersección mide ancho por alto. Ajenos: no se tocan, así que si caíste en $B$ seguro no estás en $A$.
> ![[independencia-vs-ajenos.svg|center|600]]

Recordemos las dos definiciones (ver [[Independencia de Eventos]]):
$$
A, B \text{ ajenos} \iff A \cap B = \varnothing, \qquad\quad A \perp\!\!\!\perp B \iff P(A \cap B) = P(A)\,P(B).
$$
La primera no usa $P$ para nada; la segunda solo usa $P$, y no dice nada de si $A \cap B$ es vacío.

### Cuándo pueden ser las dos cosas

Si $A$ y $B$ son ajenos, $P(A \cap B) = P(\varnothing) = 0$. Para que además sean independientes, el producto $P(A)P(B)$ también tiene que ser $0$, y eso solo pasa en un caso muy especial:

> [!theorem] **Proposición.**
>
> Sean $A, B \in \mathcal{F}$ ajenos. Ent. $A \perp\!\!\!\perp B$ sii $P(A) = 0$ o $P(B) = 0$.

> [!proof]- **Proof.**
>
> Como $A \cap B = \varnothing$, $P(A \cap B) = 0$ ([[Medida de Probabilidad]]). Ent.
> $$
> A \perp\!\!\!\perp B \iff 0 = P(A)\,P(B) \iff P(A) = 0 \ \lor \ P(B) = 0,
> $$
> pues un producto de reales es $0$ sii alguno de los factores lo es. $\blacksquare$

> [!theorem] **Corolario.**
>
> Si $A$ y $B$ son ajenos con $P(A) > 0$ y $P(B) > 0$, ent. **no** son independientes. De hecho, $P(A \mid B) = 0$.

> [!proof]- **Proof.**
>
> Lo primero es la contrapositiva de la Proposición. Y $P(A \mid B) = \frac{P(A \cap B)}{P(B)} = \frac{0}{P(B)} = 0$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Ser ajenos (con probabilidades positivas) es la **dependencia más fuerte** posible en este sentido: independencia sería $P(A \mid B) = P(A) > 0$, y aquí saber que pasó $B$ baja la proba. de $A$ hasta $0$. Lo "contrario" de independiente está más cerca de "ajeno" que lo "mismo".

> [!example]- **Ejemplo 1.** (Ajenos, no independientes)
>
> Se lanza un dado justo. Sean $A$ = "sale par" y $B$ = "sale impar". Son ajenos, pero
> $$
> P(A \cap B) = 0 \neq \frac{1}{4} = \frac{1}{2}\cdot\frac{1}{2} = P(A)\,P(B).
> $$
> Claro: si sé que salió impar, sé que **no** salió par.

> [!example]- **Ejemplo 2.** (Independientes, no ajenos)
>
> Para cualquier $A$ con $A \neq \varnothing$: $A$ y $\Omega$ son independientes, pues $P(A \cap \Omega) = P(A) = P(A)P(\Omega)$, pero $A \cap \Omega = A \neq \varnothing$. Saber que "pasó algo" no da información sobre $A$.

### Los cuatro casos

Las dos propiedades son independientes una de la otra (en el sentido de la lógica, no de la probabilidad): se pueden dar los cuatro casos.

> [!example]+ **Ejemplo 3.** (Uno de cada uno)
>
> Sea $\Omega = \{ a, b, c, d \}$ equiprobable, $A = \{ a, b \}$, $B = \{ a, c \}$ y $C = \{ a \}$.
> ![[cuatro-casos-ajenos-independientes.svg|center|650]]
>
> | Par | ¿Ajenos? | $P(\cap)$ | $P \cdot P$ | ¿Independientes? |
> |---|---|---|---|---|
> | $A, C$ | no | $\frac{1}{4}$ | $\frac{1}{8}$ | no |
> | $A, B$ | no | $\frac{1}{4}$ | $\frac{1}{4}$ | sí |
> | $A, A^{c}$ | sí | $0$ | $\frac{1}{4}$ | no |
> | $A, \varnothing$ | sí | $0$ | $0$ | sí |
>
> El único par que es las dos cosas, $A$ y $\varnothing$, es el que predice la Proposición: uno de los dos tiene proba. $0$.

El caso "ni ajenos ni independientes" es, en la práctica, el más común: dos eventos que se pueden dar juntos y que se influyen.

> [!example]- **Ejemplo 4.** (Ni lo uno ni lo otro)
>
> Se lanzan tres monedas justas. Sean $A$ = "la primera es sol" y $C$ = "salen al menos dos soles".<sup><a href="#user-content-fn-inline-2" id="user-content-fnref-inline-2" data-footnote-ref class="internal">2</a></sup> Por simetría $P(C) = \frac{1}{2}$, y $A \cap C$ = "la primera es sol y hay al menos un sol en las otras dos":
> $$
> P(A \cap C) = \frac{1}{2}\cdot\frac{3}{4} = \frac{3}{8} \neq \frac{1}{4} = P(A)\,P(C).
> $$
> No son ajenos (pueden pasar juntos) ni independientes: saber que la primera fue sol hace **más** probable tener al menos dos.

### La independencia depende de $P$

Hay una diferencia más de fondo. Que $A \cap B = \varnothing$ es un hecho sobre los conjuntos: no cambia si cambiamos la medida de probabilidad. Que $A \perp\!\!\!\perp B$ es un hecho sobre la terna $(A, B, P)$: los **mismos** eventos pueden ser independientes con una $P$ y no con otra.

> [!example]- **Ejemplo 5.** (Mismos eventos, otra $P$)
>
> Sea $\Omega = \{ 1, 2, 3, 4 \}$, $A = \{ 1, 2 \}$ y $B = \{ 1, 3 \}$.
> - Con la [[Medida de Probabilidad Clasica|medida clásica]]: $P(A \cap B) = P(\{ 1 \}) = \frac{1}{4} = \frac{1}{2}\cdot\frac{1}{2}$. Son independientes.
> - Con $P(\{ 1 \}) = 0.4$ y $P(\{ 2 \}) = P(\{ 3 \}) = P(\{ 4 \}) = 0.2$: $P(A) = P(B) = 0.6$ y $P(A \cap B) = 0.4 \neq 0.36$. Ya no lo son.
>
> En los dos casos $A \cap B = \{ 1 \} \neq \varnothing$: que no sean ajenos no cambió.

### Para qué sirve distinguirlos

Cada propiedad da una regla distinta para calcular, y confundirlas da números equivocados:

| | $A, B$ ajenos | $A \perp\!\!\!\perp B$ |
|---|---|---|
| $P(A \cap B)$ | $0$ | $P(A)\,P(B)$ |
| $P(A \cup B)$ | $P(A) + P(B)$ | $P(A) + P(B) - P(A)P(B)$ |
| $P(A \mid B)$ (si $P(B) > 0$) | $0$ | $P(A)$ |

Las dos fórmulas de la unión salen de $P(A \cup B) = P(A) + P(B) - P(A \cap B)$. Para independientes también se puede escribir $P(A \cup B) = 1 - (1 - P(A))(1 - P(B))$: la proba. de que pase al menos uno es $1$ menos la de que no pase ninguno, y $A^{c}, B^{c}$ también son independientes.

> [!example]- **Ejemplo 6.** (El mismo dato, dos respuestas)
>
> Sabemos que $P(A) = 0.4$ y $P(A \cup B) = 0.7$. ¿Cuánto vale $P(B)$?
> - Si son **ajenos**: $0.7 = 0.4 + P(B)$, ent. $P(B) = 0.3$.
> - Si son **independientes**: $0.7 = 0.4 + P(B) - 0.4\,P(B) = 0.4 + 0.6\,P(B)$, ent. $P(B) = 0.5$.
>
> Con la hipótesis equivocada, la respuesta sale mal.

---
Volver a [[Independencia de Eventos]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 1, §1.16 (pp. 89–98) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
<li id="user-content-fn-inline-2">

[NekoMath, *Probabilidad I: Independencia de Eventos*](https://blog.nekomath.com/proba1-independencia-de-eventos/). <a href="#user-content-fnref-inline-2" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
