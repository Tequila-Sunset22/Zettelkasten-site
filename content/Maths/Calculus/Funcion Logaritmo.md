---
modified: 2026-11-15T19:57:33Z
title: "Función Logaritmo"
publish: true
type: zettel
date: "2026-09-01"
status: seed
aliases:
tags:
 - calculus
cssclasses: 
 - romana
---
> [!Quote]+ Un matemático buscando una definición
>
>  ![[Pasted image 20260819215736.png]]

Desde la prepa usamos $\log(x)$ y $e^{x}$ como si fueran obvias, pero ¿qué es exactamente $\log(2)$, o $2^{\sqrt{2}}$? Con potencias enteras y raíces solo llegamos a exponentes racionales; para un exponente irracional no hay una receta algebraica. La salida es al revés de como lo aprendimos: primero definimos el **logaritmo** con una integral (que ya sabemos que existe por el [[Teorema Fundamental de Cálculo]]), y después la **exponencial** como su inversa.

> El logaritmo es el área bajo la hipérbola $\frac{1}{t}$, medida desde $1$.

> [!tip]- ¿Qué características debe tener una función "logaritmo"?
>
> Para llegar a una definición, tenemos que observar que:
> - es continua y derivable,
> - biyectiva y estrictamente creciente,
> - con $\log(1) = 0$ y $\log(xy) = \log(x) + \log(y)$,
> - con derivada que decrece a medida que $x$ crece (función *cóncava*),
> - con $\log(x) \to \infty$ cuando $x \to \infty$ y $\log(x) \to -\infty$ cuando $x \to 0^{+}$.
>
> Si existe una función derivable con $\log(xy) = \log(x) + \log(y)$, derivando respecto a $x$ con $y$ fijo queda $y\log'(xy) = \log'(x)$, y con $x = 1$: $\log'(y) = \frac{\log'(1)}{y}$. Normalizando $\log'(1) = 1$, la derivada **tiene** que ser $\frac{1}{t}$, y como $\log(1) = 0$, por el T.F.C. **tiene** que ser $\int_{1}^{x} \frac{dt}{t}$. Así que la definición no es un truco: es la única opción.

> [!theorem] **Definición.** (Logaritmo)
>
> Para $x >0$, definimos:
> $$
> \log \left(x\right) = \int_{1}^{x} \frac{1}{t} \, dt  
> $$

La integral existe porque $\frac{1}{t}$ es continua en $(0,\infty)$, y por lo tanto integrable en cualquier $[1,x]$ (o $[x,1]$). Para $0 < x < 1$ usamos la convención $\int_{1}^{x} = -\int_{x}^{1}$.

> <img src="/videos/log-area.avif" alt="center" width="720" loading="lazy">
>
> El área bajo $\frac{1}{t}$ desde $1$ hasta $x$ (verde si $x > 1$, roja y con signo menos si $x < 1$) es la altura de la gráfica de $\log$ en $x$.

![[Pasted image 20260903203037.png|center|200]]

> [!observation]+ **Observación.** ($\log$ como área)
>
> 1. Si $x > 1$, $\log(x)$ es el área bajo la curva $f(t) = \frac{1}{t}$ entre $1$ y $x$, así que $\log(x) > 0$.
> 2. Si $0 < x < 1$, $\log(x) = -\int_{x}^{1} \frac{dt}{t}$ es **menos** el área entre $x$ y $1$, así que $\log(x) < 0$.
> 3. $\log(1) = \int_{1}^{1} \frac{dt}{t} = 0$.
>
>

### Propiedades

> [!theorem] **Teorema.** (Propiedades de $\log$)
>
> Para $x, y > 0$:
> 1. $\log(1) = 0$
> 2. $\log$ es derivable y $\displaystyle \frac{d}{dx}\log(x) = \frac{1}{x}$; en particular es continua.
> 3. $\log$ es estrictamente creciente y cóncava.
> 4. $\log \left(xy\right) = \log \left(x\right) +\log \left(y\right)$
> 5. $\log \left(\frac{1}{y}\right) = -\log(y)$
> 6. $\log \left(\frac{x}{y}\right) = \log \left(x\right) - \log \left(y\right)$
> 7. $\log \left(x^{r}\right) = r \log \left(x\right)$ para todo $r \in \mathbb{Q}$.

> [!proof]- **Proof.**
>
> 1. $\log(1) = \int_{1}^{1} \frac{dt}{t} = 0$.
> 2. $\frac{1}{t}$ es continua en $(0,\infty)$, así que por el T.F.C. (1ra parte) $G(x) = \int_{1}^{x} \frac{dt}{t}$ es derivable con $G'(x) = \frac{1}{x}$. Derivable implica continua.
> 3. Por el criterio de la primera derivada:
> $$
> \log' x = \frac{1}{x} >0 \implies \log \text{ es estrictamente creciente}
> $$
> y $\log''(x) = -\frac{1}{x^{2}} < 0$, así que es cóncava ([[Concavidad e Inflexion]]).
> 4. Fijemos $y > 0$ y sea $g(x) = \log(xy)$. Por la regla de la cadena,
> $$
> g'(x) = \frac{1}{xy}\cdot y = \frac{1}{x} = \log'(x)
> $$
> Dos funciones con la misma derivada en un intervalo difieren por una constante ([[Teorema del Valor Medio]]): $\log(xy) = \log(x) + C$. Evaluando en $x = 1$: $\log(y) = 0 + C$. Así $\log(xy) = \log(x) + \log(y)$.
> 5. Por 1 y 4, $0 = \log(1) = \log\left( y\cdot \frac{1}{y} \right) = \log(y) + \log\left( \frac{1}{y} \right)$.
> 6. Por 4 y 5, $\log\left( \frac{x}{y} \right) = \log(x) + \log\left( \frac{1}{y} \right) = \log(x) - \log(y)$.
> 7. *Caso $r = n \in \mathbb{N}$:* por inducción. Si $n = 0$, $\log(1) = 0 = 0\cdot\log(x)$. Si $\log(x^{n}) = n\log(x)$, por 4, $\log(x^{n+1}) = \log(x^{n}) + \log(x) = (n+1)\log(x)$.
> *Caso $r = -n$ con $n \in \mathbb{N}$:* por 5, $\log(x^{-n}) = -\log(x^{n}) = -n\log(x)$.
> *Caso $r = \frac{p}{q}$ con $p \in \mathbb{Z}$, $q \in \mathbb{N}^{+}$:* sea $u = x^{p/q}$ (la raíz $q$-ésima positiva de $x^{p}$). Como $u^{q} = x^{p}$, por los casos enteros $q\log(u) = \log(u^{q}) = \log(x^{p}) = p\log(x)$, y dividiendo entre $q$, $\log(x^{p/q}) = \frac{p}{q}\log(x)$. $\blacksquare$

> [!observation]+ **Observación.**
>
> El inciso $(vii)$ para $r$ **irracional** todavía no tiene sentido: no sabemos qué es $x^{\sqrt{2}}$. Lo definiremos con la exponencial, y ahí mismo veremos que la propiedad sigue valiendo (ver [[Funcion Exponencial]]).

La concavidad dice que la gráfica queda **debajo** de sus tangentes. La tangente en $x = 1$ es $y = x - 1$, y eso da una desigualdad que usaremos mucho:

> [!theorem] **Proposición.** (Desigualdad fundamental)
>
> Para todo $x > 0$,
> $$
> \log(x) \leq x - 1,
> $$
> con igualdad si y solo si $x = 1$. En particular, $\log(1 + h) < h$ para todo $h > -1$, $h \neq 0$.

> [!proof]- **Proof.**
>
> Sea $f(x) = x - 1 - \log(x)$. Ent. $f'(x) = 1 - \frac{1}{x}$, que es $< 0$ en $(0,1)$ y $> 0$ en $(1,\infty)$: $f$ decrece hasta $x = 1$ y crece después, así que su mínimo es $f(1) = 0$. Por lo tanto $f(x) \geq 0$, y como es estrictamente monótona a cada lado de $1$, $f(x) > 0$ si $x \neq 1$.
> Para la segunda parte, tomamos $x = 1 + h \neq 1$. $\blacksquare$

### Comportamiento en los extremos

Para saber qué tan grande se hace $\log$, basta con un solo valor bien acotado:

> [!theorem] **Lema.**
>
> $$
> \frac{1}{2} < \log(2) < 1
> $$

> [!proof]- **Proof.**
>
> En $[1,2]$ se cumple $\frac{1}{2} \leq \frac{1}{t} \leq 1$, con desigualdades estrictas en $(1,2)$. Por monotonía de la integral ([[Mas propiedades de la integral|Propiedades de la Integral]]),
> $$
> \frac{1}{2} = \int_{1}^{2} \frac{1}{2} \, dt < \int_{1}^{2} \frac{dt}{t} < \int_{1}^{2} 1 \, dt = 1
> $$
> (las desigualdades son estrictas porque las funciones son continuas y distintas en un subintervalo). $\blacksquare$

> [!theorem] **Teorema 1.1** (lolazo)
>
> $$
> \lim_{ x \to \infty } \log x = \infty
> $$

> [!proof]- **Proof.**
>
> Dado que $\frac{1}{2} < \log 2$ (Lema), observamos que $1< 2 \log 2 = \log 4$. Así, dado $n \in \mathbb{N}$, $n \leq n \log 4 = \log (4^{n})$.
> Sea $M > 0$, por P.A. existe $n \in \mathbb{N}$ tal que $n > M$. Definamos $N = 4^{n}$. Si $x > N \implies x > 4^{n}$. Dado que $\log$ es creciente, $\log x > \log (4^{n}) = n \log 4 \geq n > M$  
> $$
> \therefore \lim_{ x \to \infty } \log x = \infty \tag*{$\blacksquare$}
> $$

> [!theorem] **Teorema 1.2** 
>
> $$
> \lim_{  x \to 0^+ } \log x = -\infty
> $$

> [!proof]- **Proof.** 
>
> Si $y = \frac{1}{x}$ entonces $x \to 0^{+} \implies y \to \infty$. Así, por la propiedad 5 y el Teorema 1.1,
> $$
> \lim_{ x \to 0^{+} } \log x = \lim_{  y  \to \infty }  \log \left( \frac{1}{y} \right) = -\lim_{  y \to \infty } \log y = -\infty \tag*{$\blacksquare$}
> $$

> [!theorem] **Corolario.** ($\log$ es biyectiva)
>
> $\log: (0,\infty) \to \mathbb{R}$ es una biyección.

> [!proof]- **Proof.**
>
> *Inyectiva:* es estrictamente creciente.
> *Suprayectiva:* sea $c \in \mathbb{R}$. Por los Teoremas 1.1 y 1.2 existen $a < b$ en $(0,\infty)$ con $\log(a) < c < \log(b)$. Como $\log$ es continua en $[a,b]$, por el [[Teorema del Valor Intermedio]] existe $x \in (a,b)$ con $\log(x) = c$. $\blacksquare$

Este corolario es justo lo que necesitamos para definir la exponencial como su inversa.

### Crecimiento: el logaritmo es lento

$\log(x) \to \infty$, pero muy despacio: para que $\log(x)$ llegue a $10$, $x$ tiene que pasar de $22\,000$. Lo comparamos con $x$:

> [!theorem] **Proposición.**
>
> La función $f(x) = x - \log(x)$ es creciente para $x>1$; además,
> $$
> \lim_{ x \to \infty } x - \log(x) = \infty
> $$

> [!proof]- **Proof.** 
>
> $f'(x) =1 - \frac{1}{x}$. $f'(x)= 0 \iff 1 = \frac{1}{x} \iff x = 1$. Para $x >1$, claramente $f'(x) > 0$, así que $f$ es creciente ahí. Ahora, $1- \frac{1}{x} = \frac{1}{2} \iff x = 2$, y por el crecimiento de $1 - \frac{1}{x}$, $1 - \frac{1}{x} > \frac{1}{2} \iff x > 2$.
> Tomemos $c = 2$ y $x > c$. Por el [[Teorema del Valor Medio]] en $[c,x]$ existe $y \in (c,x)$ tal que
> $$
> \frac{(x-\log x)-(c-\log c)}{x - c} = 1 - \frac{1}{y}
> $$
> y como $y > 2$, $1 - \frac{1}{y} > \frac{1}{2}$. Ent.
> $$
> \begin{align}
> & x - \log x \\[0.5em]
> &= \left( 1- \frac{1}{y} \right)(x -c) + (c-\log c) \\[0.5em]
> &> \frac{1}{2}(x - 2) + (2 - \log 2) \overset{x \to \infty}{\longrightarrow} \infty \tag*{$\blacksquare$}
> \end{align}
> $$

> [!theorem] **Corolario.** 
>
> La función $f(x) = x - m\log x$ para $m \in \mathbb{N}^{+}$ es creciente en $x > m$; además $\displaystyle \lim_{ x \to \infty } x - m \log (x) = \infty$ 

> [!proof]- **Proof.** 
>
> $f'(x) = 1 - \frac{m}{x} > 0 \iff x>m$. Ahora $1 -\frac{m}{x} = \frac{1}{m+1} \iff x = m+1$.
> Así $1- \frac{m}{x} > \frac{1}{m+1} \iff x > m+1$.
> Tomemos $c = m+2$ y $x > c$. Por el T.V.M. existe $y \in (c,x)$ tal que 
> $$
> (x-m\log x) - (c-m\log c) = \left( 1 - \frac{m}{y} \right)(x - c)
> $$
> y como $y > m + 1$, $1 - \frac{m}{y} > \frac{1}{m+1}$. Ent.
> $$
> x - m \log (x) > \frac{x-c}{m+1} + (c - m \log (c)) \overset{x \to \infty}{\longrightarrow} \infty \tag*{$\blacksquare$}
> $$
> Reescribiendo, $f(x) = x - \log (x ^{m})$.

> [!theorem] **Corolario.** 
>
> $$
> \lim_{ x \to \infty } \frac{x}{\log(x)} = \infty
> $$

> [!proof]- **Proof.** 
>
> Sea $M > 0$ y tomemos $m \in \mathbb{N}$ con $m > M$. Por el corolario anterior, $x - m\log(x) \to \infty$, así que existe $N > 1$ tal que $x - m\log(x) > 0$ para todo $x > N$. Como $\log(x) > 0$ para $x > 1$, dividiendo:
> $$
> \frac{x}{\log(x)} > m > M \quad \forall x > N \tag*{$\blacksquare$}
> $$

De esta forma nos damos cuenta de que el logaritmo tiene un crecimiento lentísimo, **menor** que el de $x$. De hecho es más lento que cualquier potencia $x^{\alpha}$ con $\alpha > 0$, aunque sea $x^{0.001}$; eso lo probamos en [[Funcion Exponencial]], cuando ya tengamos $x^{\alpha}$ para $\alpha$ real.

### Logaritmo en otra base

> [!theorem] **Definición.** (Logaritmo Base General)
>
> Sea $a > 0$ con $a\neq 1$. Para cualquier $x >0$, el logaritmo en base $a$ de $x$ se define mediante el cambio de base al logaritmo natural:
> $$
> \log_{a} \left(x\right) = \frac{\log \left(x\right)}{\log \left(a\right)}
> $$

> [!observation]+ **Observación.**
>
> 1. Está bien definido porque $a \neq 1 \implies \log(a) \neq 0$ ($\log$ es inyectiva).
> 2. Hereda todas las propiedades de $\log$ (son las mismas divididas entre la constante $\log(a)$), y $\displaystyle \frac{d}{dx}\log_{a}(x) = \frac{1}{x\log(a)}$.
> 3. $\log_{a}$ es la inversa de $x \mapsto a^{x}$ (ver [[Funcion Exponencial]]); con $a = e$ se recupera $\log$, por eso a $\log$ se le llama **logaritmo natural** (otros lo escriben $\ln$).

### Derivación Logarítmica

> Esta técnica de derivación nos ahorra mucho estar aplicando álgebra de derivadas múltiples veces: se trata de aplicar la función logaritmo a una ecuación y simplificarla por medio de las propiedades de $\log$, para luego derivarla.

Como $\log$ solo acepta números positivos, se usa $\log\left| y \right|$:

> [!theorem] **Proposición.**
>
> Para $x \neq 0$, $\displaystyle \frac{d}{dx}\log\left| x \right| = \frac{1}{x}$. Por lo tanto, si $f$ es derivable y $f(x) \neq 0$,
> $$
> f'(x) = f(x)\cdot \frac{d}{dx}\log\left| f(x) \right|
> $$

> [!proof]- **Proof.**
>
> Si $x > 0$ es la propiedad 2. Si $x < 0$, $\log\left| x \right| = \log(-x)$ y por la regla de la cadena $\frac{d}{dx}\log(-x) = \frac{-1}{-x} = \frac{1}{x}$. La segunda parte es la regla de la cadena: $\frac{d}{dx}\log\left| f(x) \right| = \frac{f'(x)}{f(x)}$, y despejamos $f'(x)$. $\blacksquare$

> [!example]- Ejemplo.
>
> Derivar $\displaystyle y = \frac{(x^{2}+1)^{3}\sqrt{x}}{(x+2)^{5}}$ para $x > 0$.
> Con álgebra de derivadas sería un cociente de productos. Aplicando $\log$ y sus propiedades:
> $$
> \log(y) = 3\log(x^{2}+1) + \frac{1}{2}\log(x) - 5\log(x+2)
> $$
> Derivando ambos lados,
> $$
> \frac{y'}{y} = \frac{6x}{x^{2}+1} + \frac{1}{2x} - \frac{5}{x+2}
> \implies y' = \frac{(x^{2}+1)^{3}\sqrt{x}}{(x+2)^{5}}\left( \frac{6x}{x^{2}+1} + \frac{1}{2x} - \frac{5}{x+2} \right)
> $$

La versión con exponentes variables ($x^{x}$, $f(x)^{g(x)}$) necesita primero saber qué significa $a^{x}$: está en [[Funcion Exponencial]].

---

Sigue: [[Funcion Exponencial]].
