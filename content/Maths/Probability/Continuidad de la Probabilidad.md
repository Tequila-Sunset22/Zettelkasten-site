---
modified: 2026-11-17T22:20:24Z
title: "Continuidad de la Probabilidad"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Teorema de Continuidad de la Probabilidad
tags:
 - probability
cssclasses:
 - romana
---
En cálculo, una función es continua si "el límite sale de la función": $f(\lim x_{n}) = \lim f(x_{n})$. La medida de probabilidad $P$ también es una función, pero sus argumentos son **conjuntos**, no números. Para preguntarnos si $P$ es continua necesitamos primero decir qué es el límite de una sucesión de eventos, y luego ver que $P(\lim A_{n}) = \lim P(A_{n})$. Esto es lo que justifica todos los pasos al límite de probabilidad que vienen después, empezando por las propiedades de la [[Funcion de Distribucion Acumulada|función de distribución]].<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> La probabilidad del límite es el límite de las probabilidades.

> [!tip|idea]+ **Idea Intuitiva.**
>
> El límite de una sucesión creciente de eventos es su unión, y el de una decreciente, su intersección. Como con áreas de regiones anidadas, $P(A_{n})$ tiende a la probabilidad del límite.
> ![[continuidad-anidados.svg|center|600]]

> [!theorem] **Definición.** (Límite de una sucesión monótona de eventos)
>
> Sea $A_{1}, A_{2}, \dots$ una sucesión de eventos.
> 1. Si es **creciente**, $A_{1} \subseteq A_{2} \subseteq \cdots$, definimos $\displaystyle \lim_{ n \to \infty } A_{n} = \bigcup_{n=1}^{\infty} A_{n}$, y escribimos $A_{n} \uparrow A$.
> 2. Si es **decreciente**, $A_{1} \supseteq A_{2} \supseteq \cdots$, definimos $\displaystyle \lim_{ n \to \infty } A_{n} = \bigcap_{n=1}^{\infty} A_{n}$, y escribimos $A_{n} \downarrow A$.
>
> En los dos casos el límite es un evento, porque $\mathcal{F}$ es cerrada bajo uniones e intersecciones numerables (ver [[Sigma-algebra de eventos]]).

> [!observation]+ **Observación.**
>
> La unión de una sucesión creciente no tiene por qué ser todo $\Omega$, y la intersección de una decreciente no tiene por qué ser vacía. Y si la sucesión no es monótona, esta definición no le asigna límite.

Con intervalos se ve bien qué puede pasar en el límite: a veces se gana o se pierde un extremo, a veces todo se colapsa a un punto.

> [!example]- **Ejemplo 1.** (Límites de intervalos)
>
> Sea $a \in \mathbb{R}$. Para $n \geq 1$:
> 1. $A_{n} = (-n, n)$ es creciente y $A_{n} \uparrow \mathbb{R}$: todo real está en algún $(-n,n)$.
> 2. $A_{n} = \left( -\infty, a + \frac{1}{n} \right]$ es decreciente y $A_{n} \downarrow (-\infty, a]$: $x$ está en todos sii $x \leq a + \frac{1}{n}$ para todo $n$, sii $x \leq a$ (Prop. Arquimediana<sup><a href="#user-content-fn-inline-2" id="user-content-fnref-inline-2" data-footnote-ref class="internal">2</a></sup>).
> 3. $A_{n} = \left( -\frac{1}{n}, \frac{1}{n} \right)$ es decreciente y $A_{n} \downarrow \{ 0 \}$: intervalos abiertos cuyo límite es un punto.
> 4. $A_{n} = \left( -\infty, a - \frac{1}{n} \right]$ es creciente y $A_{n} \uparrow (-\infty, a)$: semirrectas cerradas cuyo límite es abierto, pues $a$ no está en ninguna.

Ahora el teorema. La idea para el caso creciente es la misma que en la desigualdad de Boole (ver [[Propiedades de la Medida de Probabilidad]]): convertir la unión en una unión **ajena**, quedándonos solo con los "anillos" nuevos que agrega cada $A_{n}$.

> [!theorem] **Teorema.** (Continuidad de la probabilidad)
>
> Sea $(\Omega, \mathcal{F}, P)$ un esp. de prob. y $A_{1}, A_{2}, \dots$ eventos.
> 1. Si $A_{n} \uparrow A$, ent. $\displaystyle P(A) = \lim_{ n \to \infty } P(A_{n})$.
> 2. Si $A_{n} \downarrow A$, ent. $\displaystyle P(A) = \lim_{ n \to \infty } P(A_{n})$.

> [!proof]- **Proof.**
>
> **Borrador.** (1) Con $A_{0} = \varnothing$, los anillos $B_{n} = A_{n} \setminus A_{n-1}$ son ajenos y su unión es $A$; por $\sigma$-aditividad $P(A)$ es una serie, y como $P(B_{n}) = P(A_{n}) - P(A_{n-1})$ la suma parcial es telescópica. (2) Los complementos de una sucesión decreciente forman una creciente.
>
> **Proof.** 1. Sea $A_{0} = \varnothing$ y $B_{n} = A_{n} \setminus A_{n-1}$ para $n \geq 1$.
> - Son ajenos: si $m < n$, $B_{m} \subseteq A_{m} \subseteq A_{n-1}$ y $B_{n}$ no tiene puntos de $A_{n-1}$.
> - $\bigcup_{k=1}^{n} B_{k} = A_{n}$ (por inducción, pues $A_{n} = A_{n-1} \cup B_{n}$), así que $\bigcup_{k=1}^{\infty} B_{k} = \bigcup_{n=1}^{\infty} A_{n} = A$.
> - Como $A_{n-1} \subseteq A_{n}$, $P(B_{n}) = P(A_{n}) - P(A_{n-1})$ ([[Medida de Probabilidad]], Propiedad 4).
>
> Ent.
> $$
> \begin{align}
> & P(A) \\[0.5em]
> &= \sum_{k=1}^{\infty} P(B_{k}) = \lim_{ n \to \infty } \sum_{k=1}^{n} \left( P(A_{k}) - P(A_{k-1}) \right) \tag{axioma $(iii)$} \\[0.5em]
> &= \lim_{ n \to \infty } \left( P(A_{n}) - P(A_{0}) \right) = \lim_{ n \to \infty } P(A_{n}) \tag{telescópica}
> \end{align}
> $$
> pues $P(A_{0}) = P(\varnothing) = 0$. $\blacksquare$
>
> 2. Si $A_{n} \downarrow A$, ent. $A_{n}^{c}$ es creciente y, por Morgan, $\bigcup_{n} A_{n}^{c} = \left( \bigcap_{n} A_{n} \right)^{c} = A^{c}$. Por 1,
> $$
> 1 - P(A) = P(A^{c}) = \lim_{ n \to \infty } P(A_{n}^{c}) = \lim_{ n \to \infty } (1 - P(A_{n})) = 1 - \lim_{ n \to \infty } P(A_{n}),
> $$
> y se despeja. $\blacksquare$

> [!observation]+ **Observación.**
>
> 1. Los límites $\lim P(A_{n})$ siempre existen: por monotonía de $P$, la sucesión $P(A_{n})$ es creciente y acotada por $1$ en el caso 1, y decreciente y acotada por $0$ en el caso 2.
> 2. La prueba de 1 solo usa la $\sigma$-aditividad, y al revés también se puede: una función aditiva (en uniones finitas) que además es continua en sucesiones crecientes es $\sigma$-aditiva. La continuidad es otra forma de decir la $\sigma$-aditividad.

Un evento que se define "para siempre" (en infinitos ensayos) casi nunca se puede contar directamente; la continuidad lo calcula como límite de eventos finitos.

> [!example]- **Ejemplo 2.** (Nunca sale águila)<sup><a href="#user-content-fn-inline-3" id="user-content-fnref-inline-3" data-footnote-ref class="internal">3</a></sup>
>
> Se lanza una moneda justa una infinidad de veces, con lanzamientos independientes (ver [[Independencia de Eventos]]). Sea $C_{n}$ = "en los primeros $n$ lanzamientos no sale águila". La sucesión es decreciente ($C_{n+1} \subseteq C_{n}$), su intersección es "nunca sale águila", y por independencia $P(C_{n}) = \left( \frac{1}{2} \right)^{n}$. Por el Teorema (2),
> $$
> P(\text{nunca sale águila}) = \lim_{ n \to \infty } \left( \frac{1}{2} \right)^{n} = 0.
> $$
> Ojo: el evento **no** es vacío (la sucesión "sol, sol, sol, …" está en él), pero tiene probabilidad $0$.

La aplicación más importante está en el siguiente bloque: con los intervalos del Ejemplo 1 y una v.a. $X$, los eventos $\left( X \leq x + \frac{1}{n} \right) \downarrow (X \leq x)$ y $\left( X \leq x - \frac{1}{n} \right) \uparrow (X < x)$. Por el Teorema, $F$ es continua por la derecha y $F(x^{-}) = P(X < x)$ (ver [[Funcion de Distribucion Acumulada]]).

---
Siguiente: [[Variable Aleatoria]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 1, §1.17 (p. 99) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
<li id="user-content-fn-inline-2">

[[Propiedad Arquimediana]] <a href="#user-content-fnref-inline-2" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
<li id="user-content-fn-inline-3">

[NekoMath, *Probabilidad I: Teorema de Continuidad de la Probabilidad*](https://blog.nekomath.com/proba1-continuidad-de-la-probabilidad/). <a href="#user-content-fnref-inline-3" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
