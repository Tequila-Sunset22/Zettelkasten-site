---
modified: 2026-11-18T16:47:12Z
title: "Función de Distribución"
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
Conocida también como *función de distribución acumulada*, siempre puede definirse para cualquier v.a. (discreta, continua o ninguna de las dos) y gracias a ella podemos identificar todas las propiedades de la v.a.

De manera análoga a la *función de densidad*, traslada el estudio de un experimento aleatorio y su modelo de proba al estudio de las funciones reales.

> [!tip|idea]+ **Idea Intuitiva.**
>
> $F(x)$ es la proba. de caer en $(-\infty, x]$. Al mover $x$ a la derecha, el evento $(X \leq x)$ solo crece, y $F$ con él.
> <img src="/videos/distribucion-umbral.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** (Función de Distribución)
>
> Sea $X$ v.a. cualquiera. La **función de distribución** de $X$, denotada $F_{X}: \mathbb{R} \to \mathbb{R}$ (o solo $F$), se define como la probabilidad:
> $$
> F_{X}(x) = P(X \leq x)
> $$

Las propiedades que siguen son las que **caracterizan** a una función de distribución. Las de límites y continuidad son pasos al límite de probabilidades, así que todas usan la [[Continuidad de la Probabilidad]].

> [!theorem] **Teorema.** (Propiedades)
>
> Toda función de distribución $F(x)$ satisface:
> 1. $\displaystyle \lim_{x \to \infty} F(x) = 1$
> 2. $\displaystyle \lim_{x \to -\infty} F(x) = 0$
> 3. $\displaystyle x_{1}\leq x_{2} \implies F(x_{1}) \leq  F(x_{2})$, i.e. nunca es decreciente
> 4. $\displaystyle F(x) = F(x^{+})$, i.e. es continua por la derecha.

> [!proof]- **Proof.**
>
> **Borrador.** 3 es monotonía de $P$. Para 1, 2 y 4, como $F$ es monótona, basta tomar el límite sobre una sucesión ($x = n$, $x = -n$, $x + \frac{1}{n}$) y escribirlo como límite de eventos monótonos.
>
> **Proof.** 3. Si $x_{1} \leq x_{2}$, ent. $(X \leq x_{1}) \subseteq (X \leq x_{2})$, y por monotonía de [[Medida de Probabilidad|$P$]], $F(x_{1}) \leq F(x_{2})$. $\blacksquare$
>
> Por 3, los límites de 1, 2 y 4 existen (una función monótona y acotada tiene límites laterales y en $\pm\infty$), así que basta calcularlos sobre una sucesión.
> 1. $(X \leq n) \uparrow \bigcup_{n}(X \leq n) = \Omega$, pues todo $\omega$ cumple $X(\omega) \leq n$ para $n$ grande. Por continuidad, $F(n) = P(X \leq n) \to P(\Omega) = 1$. $\blacksquare$
> 2. $(X \leq -n) \downarrow \bigcap_{n}(X \leq -n) = \varnothing$, pues ningún real es $\leq -n$ para todo $n$. Ent. $F(-n) \to P(\varnothing) = 0$. $\blacksquare$
> 4. $\left( X \leq x + \frac{1}{n} \right) \downarrow (X \leq x)$ (Ejemplo 1 de [[Continuidad de la Probabilidad]]). Ent. $F\left( x + \frac{1}{n} \right) \to F(x)$, i.e. $F(x^{+}) = F(x)$. $\blacksquare$

Donde $F(x^{-}) = \lim_{h \to 0^{+}} F(x-h)$ y $F(x^{+}) = \lim_{h \to 0^{+}} F(x+h)$ son los límites laterales. Con $F$ se calcula la proba. de cualquier intervalo, y el **salto** de $F$ en un punto es la proba. de ese punto:

> [!theorem] **Proposición.** (Calcular con $F$)
>
> Sea $X$ v.a. con función de distribución $F$ y $a < b$. Ent.
> 1. $P(X < x) = F(x^{-})$
> 2. $P(X = x) = F(x) - F(x^{-})$
> 3. $P(a < X \leq b) = F(b) - F(a)$
> 4. $P(X > x) = 1 - F(x)$

> [!proof]- **Proof.**
>
> 1. $\left( X \leq x - \frac{1}{n} \right) \uparrow (X < x)$, y por continuidad de la probabilidad, $F\left( x - \frac{1}{n} \right) \to P(X < x)$. $\blacksquare$
> 2. $(X = x) = (X \leq x) \setminus (X < x)$ con $(X < x) \subseteq (X \leq x)$, y por 1. $\blacksquare$
> 3. $(a < X \leq b) = (X \leq b) \setminus (X \leq a)$, con $(X \leq a) \subseteq (X \leq b)$. $\blacksquare$
> 4. Complemento de $(X \leq x)$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Por 2, $F$ es continua en $x$ sii $P(X = x) = 0$: **los saltos de $F$ son exactamente los puntos con probabilidad positiva**. Abajo se ven los tres tipos de $F$: escalonada (toda la probabilidad en saltos), continua (ningún salto) y mixta.
> ![[tres-funciones-distribucion.svg|center|650]]

En el caso discreto, $F$ es escalonada:

> [!tip|idea]- **Idea Intuitiva.**
>
> $F(x)$ es la suma de todos los valores de la función de probabilidad hasta $x$.
> Y $f(x)$ es el tamaño del salto de la función de distribución en el punto $x$.

> [!theorem] **Teorema.** (Función de Distribución Discreta)
>
> Sea $X$ discreta con función de probabilidad $f$ ([[Funcion de Masa de Probabilidad]]). La función de distribución se calcula:
> $$
> F(x) = \sum_{u\leq x} f(u)
> $$
> y para obtener $f(x)$ a partir de $F(x)$, se tiene
> $$
> f(x) = F(x) - F(x^{-})
> $$

> [!proof]- **Proof.**
>
> La primera es $P(X \in (-\infty, x]) = \sum_{u \leq x} f(u)$ (suma sobre los valores de $X$ que son $\leq x$). La segunda es el inciso 2 de la Proposición, pues $f(x) = P(X = x)$. $\blacksquare$

> [!example]- **Ejemplo 1.** (Águilas en 4 volados)
>
> Con $f$ del Ejemplo 1 de [[Funcion de Masa de Probabilidad]]:
> $$
> F(x) = \begin{cases}
> 0 & x < 0 \\[0.5em]
> \frac{1}{16} & 0 \leq x < 1 \\[0.5em]
> \frac{5}{16} & 1 \leq x < 2 \\[0.5em]
> \frac{11}{16} & 2 \leq x < 3 \\[0.5em]
> \frac{15}{16} & 3 \leq x < 4 \\[0.5em]
> 1 & x \geq 4
> \end{cases}
> $$
> Por ejemplo, $P(1 < X \leq 3) = F(3) - F(1) = \frac{15}{16} - \frac{5}{16} = \frac{10}{16}$, y el salto en $2$ es $\frac{11}{16} - \frac{5}{16} = \frac{6}{16} = f(2)$.

El caso continuo, con densidad, está en [[Funcion de Densidad de Probabilidad]]. Hay v.a.s que no son ni discretas ni continuas:

> [!example]- **Ejemplo 2.** (Mixta)
>
> Al llegar a una ventanilla, con proba. $\frac{1}{2}$ no hay fila y no esperamos nada; si hay fila, esperamos un tiempo $\operatorname{Exp}(1)$. El tiempo de espera $X$ tiene
> $$
> F(x) = \begin{cases}
> 0 & x < 0 \\[0.5em]
> \frac{1}{2} + \frac{1}{2}(1 - e^{-x}) & x \geq 0
> \end{cases}
> $$
> Tiene un salto de $\frac{1}{2}$ en $0$ ($P(X = 0) = \frac{1}{2}$) y es continua en todos los demás puntos: no es discreta (no es escalonada) ni continua (tiene un salto). Es la tercera gráfica de la figura de arriba.

Las cuatro propiedades del Teorema no solo se cumplen: **caracterizan** a las funciones de distribución.

> [!theorem] **Definición.** (Función de Distribución)
>
> Toda función $F: \mathbb{R}\to \mathbb{R}$ que cumpla las cuatro propiedades anteriores se le llama **función de distribución**, sin importar si tiene una variable aleatoria que la defina.

> [!observation]+ **Observación.**
>
> Siempre la tiene: si $F$ cumple las cuatro propiedades y $U \sim \operatorname{Unif}(0,1)$, la v.a. $c_{U}$ (el cuantil de $F$ evaluado en $U$) tiene función de distribución exactamente $F$ (ver [[Metodo de la Transformada Inversa]]). Así que "función de distribución" y "distribución de una v.a." son lo mismo.

---
Siguiente: [[Funcion de Densidad de Probabilidad]].
