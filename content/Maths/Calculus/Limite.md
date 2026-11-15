---
modified: 2026-11-15T04:47:33Z
title: "Límite"
publish: true
type: zettel
date: "2026-07-10"
aliases:
 - Limites
tags: 
 - calculus
cssclasses: 
 - romana
---
Lo siguiente es el desarrollo de una noción intuitiva de la definición de límite, la **proximidad**: 

> Se dice que la función $f$ se aproxima al límite $l$ cerca de $a$, si $f(x)$ se aproxima tanto como se quiera a $l$ si $x$ se aproxima suficientemente a $a$ pero es distinto de $a$.


Entonces proponemos un $\varepsilon$, una distancia próxima a $l$, y para ese $\varepsilon$ deberíamos encontrar una distancia $\delta$ en el eje $X$ que la valide.

> [!tip|idea]+ **Idea Intuitiva.** (La banda $\varepsilon$ y la franja $\delta$)
>
> Nos dan una banda horizontal de radio $\varepsilon$ alrededor de $l$; nosotros respondemos con una franja vertical de radio $\delta$ alrededor de $a$ tal que, dentro de la franja (quitando $x = a$), la gráfica no se sale de la banda. Mientras más angosta la banda, más angosta la franja. Lo que valga $f(a)$, o si siquiera existe, no importa.
>
> <img src="/videos/limite-eps-delta.avif" alt="center" width="720" loading="lazy">
>
> *Función:* $f(x) = l + 0.6(x-a) + 0.25(x-a)^{2}$, con un hueco en $a$ y $f(a)$ en otro lado.

> [!theorem] **Def.** (Limite $\varepsilon - \delta$)
>
> La función $f$ **tiende al límite** $l$ en $a$, si para todo $\varepsilon >0$ existe algún $\delta >0$ tal que, para todo $x$ (en el dominio de $f$), si $0<\lvert x-a \rvert< \delta$, entonces $\lvert f(x)-l \rvert<\varepsilon$.
> 
> O de forma más directa:
>$$
> \forall \varepsilon > 0 \ \exists \delta > 0 \ \ \text{ tal que } \ \ \forall x (0 < \lvert x - a \rvert < \delta \implies \lvert f(x) - l \rvert < \varepsilon).
> $$
> Lo denotamos $\displaystyle \lim_{ x \to a } f(x) = l$.

> [!observation]+ **Observación.**
>
> El $0 < \lvert x - a \rvert$ dice que **no importa** qué pasa en $x = a$: $f$ puede no estar definida ahí, o valer otra cosa. (Pedimos que $a$ sea [[Punto de Acumulacion|punto de acumulación]] del dominio, para que haya $x$ que revisar.)

> [!note]-
>
> We would rarely use the definition to compute a limit, and we hope seldom to use the definition to verify one; we will use the definition to develop a theory that will verify limits for us.

> [!example]- **Example 1.**
>
> Any function $f(x) = ax + b$ will have the easily predicted limit
> $$
> \lim_{ x \to x_{0} }  f(x) = \lim_{ x \to x_{0} } (ax+b) = ax_{0} + b
> $$
> Let us do this for the linear function $f(x) = 10x - 11$. We expect that
> $$
> \lim_{ x \to 5 } (10x -11) = 10(5) -11 = 39
> $$
> Let us *prove* this. We need a condition ensuring that the expression
> $$
> \lvert (10x-11)-39 \rvert 
> $$
> is smaller than $\varepsilon$. Some arithmetic converts this to
> $$
> \lvert (10x-11)-39 \rvert = \lvert 10x -50 \rvert  = \lvert 10 \rvert \lvert x-5 \rvert 
> $$
> Now it is clear that, if we insist that $\lvert x-5 \rvert< \varepsilon / 10$, we will have
> $$
> \lvert (10x -11)-39 \rvert < \varepsilon
> $$
> Better, though, would be to write it in a more straightforward manner that obscures how we did it but gets to the point of the proof more simply:
> 
> **Proof.**
> Let $\varepsilon>0$. Let $\delta = \varepsilon / 10$. Then for all $x$ with $0 < \lvert x-5 \rvert<\delta$ we have
> $$
> \lvert (10x -11)-39 \rvert = \lvert 10 \rvert \lvert x-5 \rvert < 10\delta = \varepsilon
> $$
> By definition, $\displaystyle\lim_{ x \to 5 }(10x-11)=39$ as required. **Q.E.D.**

### Unicidad

> [!theorem] **Teorema.** (Unicidad del Límite)
>
> Si $\displaystyle \lim_{ x \to a } f(x) = L$ y $\displaystyle \lim_{ x \to a } f(x) = M$, ent. $L = M$.

> [!proof]- **Proof.**
>
> Sup. $L \neq M$ y sea $\varepsilon = \frac{\lvert L - M \rvert}{2} > 0$. Existen $\delta_{1}, \delta_{2} > 0$ tq. si $0 < \lvert x - a \rvert < \delta_{1}$, ent. $\lvert f(x) - L \rvert < \varepsilon$, y si $0 < \lvert x - a \rvert < \delta_{2}$, ent. $\lvert f(x) - M \rvert < \varepsilon$. Tomemos $x$ del dominio con $0 < \lvert x - a \rvert < \min \{ \delta_{1}, \delta_{2} \}$ (existe porque $a$ es punto de acumulación). Ent.
> $$
> \lvert L - M \rvert \leq \lvert L - f(x) \rvert + \lvert f(x) - M \rvert < 2\varepsilon = \lvert L - M \rvert \tag{Des. triang.}
> $$
> una contradicción!
> $$
> \therefore \ L = M \tag*{$\blacksquare$}
> $$

### Álgebra de límites

> [!theorem] **Teorema** (Álgebra de Limites)
>
> Sean $f, g$ funciones tales que $\displaystyle\lim_{ x \to a }f(x) = L$ y $\displaystyle\lim_{ x \to a }g(x) = M$ donde $L, M \in \mathbb{R}$, y sean $k, c \in \mathbb{R}$.
> 1. 
> $$
> \lim_{x \to a} k = k \qquad \text{y} \qquad \lim_{x \to a} x = a
> $$
> 2.
> $$
> \lim_{x \to a} c \cdot f(x) = cL
> $$
> 3. 
> $$
> \lim_{x \to a} \left[ f(x) \pm g(x) \right]  =  L \pm M
> $$
> 4.
> $$
> \lim_{x \to a} (f(x)g(x)) = L \cdot M
> $$
> 5. Si $M \neq 0$, entonces
> $$
> \lim_{ x \to a } \frac{f(x)}{g(x)} = \frac{L}{M}
> $$

> [!proof]- **Proof.**
>
> Sea $\varepsilon > 0$. Las pruebas son las mismas que para sucesiones ([[Limites de Sucesiones]]), cambiando "$n \geq N$" por "$0 < \lvert x - a \rvert < \delta$" y "$\max \{ N_{1}, N_{2} \}$" por "$\min \{ \delta_{1}, \delta_{2} \}$".
> 1. Para $k$: $\lvert k - k \rvert = 0 < \varepsilon$ con cualquier $\delta$. Para $x$: $\delta = \varepsilon$.
> 2. Si $c = 0$ es (1). Si $c \neq 0$, existe $\delta$ tq. $0 < \lvert x - a \rvert < \delta \implies \lvert f(x) - L \rvert < \frac{\varepsilon}{\lvert c \rvert}$, ent. $\lvert cf(x) - cL \rvert < \varepsilon$.
> 3. Existen $\delta_{1}, \delta_{2}$ con $\lvert f(x) - L \rvert < \frac{\varepsilon}{2}$ y $\lvert g(x) - M \rvert < \frac{\varepsilon}{2}$. Con $\delta = \min \{ \delta_{1}, \delta_{2} \}$,
> $$
> \lvert (f(x) \pm g(x)) - (L \pm M) \rvert \leq \lvert f(x) - L \rvert + \lvert g(x) - M \rvert < \varepsilon \tag{Des. triang.}
> $$
> 4. Por [[Acotacion de Limites]], existen $\delta_{0} > 0$ y $K > 0$ con $\lvert f(x) \rvert \leq K$ si $0 < \lvert x - a \rvert < \delta_{0}$. Existen $\delta_{1}, \delta_{2}$ con $\lvert g(x) - M \rvert < \frac{\varepsilon}{2K}$ y $\lvert f(x) - L \rvert < \frac{\varepsilon}{2(\lvert M \rvert + 1)}$. Con $\delta = \min \{ \delta_{0}, \delta_{1}, \delta_{2} \}$,
> $$
> \begin{align}
> \lvert f(x)g(x) - LM \rvert &= \lvert f(x)(g(x) - M) + M(f(x) - L) \rvert \\[0.5em]
> &\leq K \lvert g(x) - M \rvert + \lvert M \rvert \lvert f(x) - L \rvert \tag{Des. triang.} \\[0.5em]
> &< \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
> \end{align}
> $$
> 5. Por (4) basta ver $\frac{1}{g(x)} \to \frac{1}{M}$. Por la Acotación lejos de cero ([[Acotacion de Limites]]) existe $\delta_{0}$ con $\lvert g(x) \rvert \geq \frac{\lvert M \rvert}{2}$ si $0 < \lvert x - a \rvert < \delta_{0}$ (en particular $\frac{f}{g}$ está definida ahí). Existe $\delta_{1}$ con $\lvert g(x) - M \rvert < \frac{\varepsilon \lvert M \rvert^{2}}{2}$. Con $\delta = \min \{ \delta_{0}, \delta_{1} \}$,
> $$
> \left\lvert \frac{1}{g(x)} - \frac{1}{M} \right\rvert = \frac{\lvert g(x) - M \rvert}{\lvert g(x) \rvert \lvert M \rvert} \leq \frac{2 \lvert g(x) - M \rvert}{\lvert M \rvert^{2}} < \varepsilon
> $$
> $$
> \tag*{$\blacksquare$}
> $$


> [!observation]+ **Observación.**
>
> Podemos generalizar los puntos $(3)$ y $(4)$ (por inducción), de tal forma que si $f_{1},\dots,f_{n}$ son funciones de $I\to \mathbb{R}$ cada una con límite $L_{1},\dots,L_{n}$ en $x_{0}$, entonces
> $$
> \begin{align}
>   \lim_{x \to x_{0}} (f_{1}+\dots+f_{n})(x) &= L_{1}+\dots+L_{n}\\[0.5em]
>   \lim_{x \to x_{0}} (f_{1}\cdot \dots \cdot f_{n})(x) &= L_{1} \cdot \dots \cdot L_{n}
> \end{align}
> $$
> En particular, con (1), $\displaystyle \lim_{ x \to x_{0} } p(x) = p(x_{0})$ para todo polinomio $p$.

### Propiedades de orden

> [!theorem] **Teorema.** (Conservación de Desigualdades en el Límite)
>
> Sean $f$ y $g$ dos funciones tales que sus límites cuando $x \to a$ existen.
> Si existe vecindad alrededor de $a$ donde se cumple que $f(x) \leq g(x)$ (para todo $x \neq a$), entonces sus límites heredan la desigualdad. 
> $$
> \displaystyle \lim_{x \to a} f(x) \leq  \lim_{x \to a} g(x)
> $$

> [!proof]- **Proof.**
>
> Sean $L = \lim f$, $M = \lim g$ y sup. $L > M$. Con $\varepsilon = \frac{L - M}{2} > 0$ existe $\delta$ (más chico que el radio de la vecindad) tq. si $0 < \lvert x - a \rvert < \delta$, ent. $f(x) > L - \varepsilon = \frac{L + M}{2}$ y $g(x) < M + \varepsilon = \frac{L+M}{2}$. Ent. $g(x) < f(x)$, contradiciendo $f(x) \leq g(x)$.
> $$
> \therefore \ L \leq M \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Las desigualdades estrictas no se conservan: $x^{2} > 0$ si $x \neq 0$, pero $\lim_{ x \to 0 } x^{2} = 0$.

> [!theorem] **Teorema.** (Sandwich de Límites)
>
> Sean $f,g,h: A\to \mathbb{R}$ y sea $x_{0}$ punto de acumulación de $A$. Si $f(x) \leq g(x) \leq  h(x)$, para todo $x \in  A, x\neq  x_{0}$, y si $\displaystyle \lim_{x \to x_{0}} f(x)= L$ y $\displaystyle \lim_{x \to x_{0}} h(x) = L$, entonces
> $$
> \lim_{x \to x_{0}} g(x) = L
> $$

> [!proof]- **Proof.**
>
> Sea $\varepsilon > 0$. Existen $\delta_{1}, \delta_{2}$ tq. si $0 < \lvert x - x_{0} \rvert < \delta_{1}$, ent. $L - \varepsilon < f(x)$, y si $0 < \lvert x - x_{0} \rvert < \delta_{2}$, ent. $h(x) < L + \varepsilon$. Con $\delta = \min \{ \delta_{1}, \delta_{2} \}$,
> $$
> L - \varepsilon < f(x) \leq g(x) \leq h(x) < L + \varepsilon
> $$
> i.e. $\lvert g(x) - L \rvert < \varepsilon$.
> $$
> \tag*{$\blacksquare$}
> $$


> [!theorem] **Teorema.** (Límite de V.A.)
>
> Sea $f: A \to  \mathbb{R}$ y sea $\displaystyle \lim_{x \to x_{0}} f(x)=L$, entonces
> $$
> \lim_{x \to x_{0}} \left| f(x) \right| = \left| L \right|
> $$

> [!proof]- **Proof.**
>
> Por $\big\lvert \lvert a \rvert - \lvert b \rvert \big\rvert \leq \lvert a - b \rvert$ ([[Valor Absoluto]]), $\big\lvert \lvert f(x) \rvert - \lvert L \rvert \big\rvert \leq \lvert f(x) - L \rvert$, así que el mismo $\delta$ de $f \to L$ sirve.
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Corolario.** (Máximo y Mínimo)
>
> Si $\displaystyle \lim_{ x \to a } f(x) = L$ y $\displaystyle \lim_{ x \to a } g(x) = M$, ent.
> $$
> \lim_{ x \to a } \max \{ f(x), g(x) \} = \max \{ L, M \} \qquad \text{y} \qquad \lim_{ x \to a } \min \{ f(x), g(x) \} = \min \{ L, M \}
> $$

> [!proof]- **Proof.**
>
> Para todo $u, v \in \mathbb{R}$, $\max \{ u,v \} = \frac{u + v + \lvert u - v \rvert}{2}$ y $\min \{ u,v \} = \frac{u + v - \lvert u - v \rvert}{2}$. Por álgebra de límites y Límite de V.A. se sigue.
> $$
> \tag*{$\blacksquare$}
> $$

### Composición

> [!theorem] **Teorema.** (Límite de la Composición) (Continuidad)
>
> Si $\displaystyle  \lim_{x \to a} g(x) = L$ y sea $f$ función [[Continuidad|continua]] en $L$, entonces
> $$
> \lim_{x \to a} f(g(x)) = f(\lim_{x \to a} g(x)) = f(L)
> $$

> [!proof]- **Proof.**
>
> Sea $\varepsilon > 0$. Como $f$ es continua en $L$, existe $\eta > 0$ tq. si $\lvert y - L \rvert < \eta$, ent. $\lvert f(y) - f(L) \rvert < \varepsilon$. Como $g(x) \to L$, usando $\eta$ como "$\varepsilon$", existe $\delta > 0$ tq. si $0 < \lvert x - a \rvert < \delta$, ent. $\lvert g(x) - L \rvert < \eta$. Ent., con $y = g(x)$,
> $$
> 0 < \lvert x - a \rvert < \delta \implies \lvert f(g(x)) - f(L) \rvert < \varepsilon
> $$
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Hace falta que $f$ sea continua en $L$ (no basta que tenga límite): con $g(x) = 0$ y $f(y) = 1$ si $y = 0$, $f(y) = 0$ si $y \neq 0$, se tiene $\lim_{ y \to 0 } f(y) = 0$ pero $f(g(x)) = 1$ para todo $x$.

Otras formas del límite: [[Limites Laterales]], [[Limites en el Infinito]] ($x \to \pm\infty$) y [[Limites Infinitos]] ($f \to \pm\infty$). La versión con sucesiones está en [[Limites de Sucesiones]].
