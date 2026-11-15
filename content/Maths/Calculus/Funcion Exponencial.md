---
modified: 2026-11-15T19:41:25Z
title: "Función Exponencial"
publish: true
type: zettel
date: 2026-08-18
status: seed
aliases:
tags:
  - calculus
cssclasses:
  - romana
---
Con el logaritmo ya construido, la exponencial sale "gratis": es su inversa. Y con ella por fin le damos sentido a $a^{x}$ para **cualquier** $x \in \mathbb{R}$, irracionales incluidos.

> La exponencial es el logaritmo leído al revés: $\exp(x)$ es el número cuyo logaritmo es $x$.

Dado que $\log \left(x\right): (0, \infty) \to \mathbb{R}$ es una función estrictamente creciente y suprayectiva (Corolario de [[Funcion Logaritmo]]), garantizamos que tiene una función inversa única ([[Funcion Inversa]]).

> [!tip|idea]+ **Idea Intuitiva.**
>
> La gráfica de una inversa es el reflejo de la gráfica original sobre la recta $y = x$: si $(a, \log a)$ está en la gráfica de $\log$, entonces $(\log a, a)$ está en la de $\exp$. Todo lo que sabemos de $\log$ se "voltea": lo que era horizontal se vuelve vertical.
>
> <img src="/videos/exp-inversa.avif" alt="center" width="720" loading="lazy">
>
> *Animación:* la gráfica de $\log$ se refleja sobre $y = x$; el punto $(a, \log a)$ va a $(\log a, a)$.

> [!theorem] **Definición.** (Exponencial)
>
> La **función exponencial**, denotada como $\exp : \mathbb{R} \to (0,\infty)$, se define como la función inversa del logaritmo natural, $\log^{-1} \left(x\right)$. Es decir, para todo $x \in \mathbb{R}$ y todo $y > 0$,
> $$
> y = \exp \left(x\right) \iff \log \left(y\right) = x
> $$

![[Pasted image 20260903202925.png|center]]
> [!observation]+ **Observación.**
>
> Dado que es una función inversa, se heredan inmediatamente dos identidades fundamentales de cancelación:
> 1. $\log \left(\exp \left(x\right) \right) = x$ para todo $x \in \mathbb{R}$
> 2. $\exp \left(\log \left(y\right)\right) = y$ para todo $y >0$.

En general, ¡las propiedades de $\exp \left(x\right)$ son las de $\log \left(x\right)$ pero al revés!

> [!theorem] **Teorema.** (Propiedades de $\exp$)
>
> Para cualesquiera $x,y \in \mathbb{R}$,
> 1. $\exp(0) = 1$
> 2. $\exp \left(x+y\right) = \exp \left(x\right)\exp \left(y\right)$
> 3. $\exp(-y) = \dfrac{1}{\exp(y)}$
> 4. $\exp \left(x-y\right) = \dfrac{\exp \left(x\right)}{\exp \left(y\right)}$
> 5. $\exp(x) > 0$
> 6. $\exp$ es derivable y $\dfrac{d}{dx}\exp(x) = \exp(x)$
> 7. $\exp$ es estrictamente creciente y convexa.
> 8. $\displaystyle \lim_{x \to \infty} \exp(x) = \infty$ y $\displaystyle \lim_{x \to -\infty} \exp(x) = 0$.

> [!proof]- **Proof.**
>
> 1. $\log(1) = 0 \implies \exp(0) = 1$, por la definición de inversa.
> 2. Sean $x,y \in \mathbb{R}$. Definimos dos variables auxiliares para usar la def. de función inversa:
> Sea $u = \exp \left(x\right)$ y sea $v = \exp \left(y\right)$
> Por definición de inversa, tenemos
> $$
> \begin{align}
>   \log \left(u\right) &= x\\[0.5em]
>   \log \left(v\right) &= y
> \end{align}
> $$
> Ahora, sumando esto y aplicando propiedades de $\log$
> $$
> \begin{align}
>   x+y &= \log \left(u\right)+\log \left(v\right)\\[0.5em]
>   x+y &= \log \left(uv\right)\\[0.5em]
>   \exp \left(x+y\right) &= \exp \left(\log \left(uv\right)\right) \\[0.5em]
>   \exp \left(x+y\right) &= uv\\[0.5em]
>   \exp \left(x+y\right) &= \exp \left(x\right)\exp \left(y\right)  \tag*{$\blacksquare$}
> \end{align}
> $$
> 3. $1 = \exp(0) = \exp(y-y)= \exp(y)\exp(-y)\implies \exp(-y) = \frac{1}{\exp(y)}$.
> 4. Por 2 y 3, $\exp(x - y) = \exp(x)\exp(-y) = \frac{\exp(x)}{\exp(y)}$.
> 5. El codominio de $\exp$ es $(0,\infty)$, el dominio de $\log$.
> 6. $\log$ es continua, estrictamente creciente y derivable con $\log'(y) = \frac{1}{y} \neq 0$. Por el teorema de la derivada de la función inversa ([[Funcion Inversa]]), $\exp = \log^{-1}$ es derivable y
> $$
> \frac{d}{dx} \exp x = \frac{1}{\log'(\exp x)} = \frac{1}{\frac{1}{\exp x}} = \exp x
> $$
> 7. Por 5 y 6, $\exp'(x) = \exp(x) > 0$: por el criterio de la primera derivada, $\exp$ es estrictamente creciente. Y $\exp'' = \exp > 0$: es convexa.
> 8. Sea $M > 0$. Si $x > \log(M)$, como $\exp$ es creciente, $\exp(x) > \exp(\log M) = M$; así $\exp(x) \to \infty$. Sea $\varepsilon > 0$. Si $x < \log(\varepsilon)$, $0 < \exp(x) < \exp(\log\varepsilon) = \varepsilon$; así $\exp(x) \to 0$ cuando $x \to -\infty$. $\blacksquare$

> [!observation]+ **Observación.**
>
> La propiedad 6 es la que hace especial a $\exp$: es (salvo múltiplos) la **única** función que es su propia derivada. Si $f' = f$, ent. $\left( f(x)\exp(-x) \right)' = f'(x)\exp(-x) - f(x)\exp(-x) = 0$, así que $f(x) = C\exp(x)$ para una constante $C$.

### El número de Euler y la notación $e^{x}$

> [!theorem] **Definición.** (Número de Euler)
>
> Se denota por
> $$
> e := \exp(1)
> $$
> y se le conoce como el número de **Euler**. Equivalentemente, $e$ es el único número con $\log(e) = 1$: el área bajo $\frac{1}{t}$ entre $1$ y $e$ es exactamente $1$.

¿Por qué escribimos $e^{x}$ en lugar de $\exp(x)$? Porque para exponentes racionales coinciden con las potencias de siempre:

> [!theorem] **Proposición.** (otra propiedad)
>
> Para todo $r \in \mathbb{Q}$, $\exp(r) = e^{r}$ (la potencia usual: productos, inversos y raíces).

> [!proof]- **Proof.**
>
> *Caso $n \in \mathbb{N}$:*
> $$
> \exp(n)  = \exp(\underbrace{1+\dots+1}_{n \text{ veces}}) = \underbrace{\exp(1)\cdots \exp(1)}_{n \text{ veces}} = \exp(1)^{n} = e^{n}
> $$
> (y $\exp(0) = 1 = e^{0}$).
> Algo similar pero con racionales. *Caso $\frac{p}{q}$ con $p \in \mathbb{N}$, $q \in \mathbb{N}^{+}$:* primero,
> $$
> \exp\left( \tfrac{1}{q} \right)^{q} = \exp\left( \underbrace{\tfrac{1}{q}+\dots+\tfrac{1}{q}}_{q} \right) = \exp(1) = e,
> $$
> así que $\exp\left( \frac{1}{q} \right)$ es un número positivo cuya potencia $q$ es $e$: es la raíz $q$-ésima positiva, $e^{1/q}$. Ent.
> $$
> \exp\left( \frac{p}{q} \right) = \exp\left( \underbrace{\frac{1}{q}+\dots+\frac{1}{q}}_{p} \right) = \exp\left( \frac{1}{q} \right)^{p} = \left( e^{ \frac{1}{q} }  \right)^{p} = e^{\frac{p}{q}}
> $$
> *Caso $\frac{p}{q}$ con $p < 0$:* existe $p_{0} = -p > 0$ y, por la propiedad 3 y el caso anterior,
> $$
> \exp\left( \frac{p}{q} \right) = \frac{1}{\exp\left( \frac{p_{0}}{q} \right)} = \frac{1}{e^{p_{0}/q}} = e^{\frac{p}{q}} \tag*{$\blacksquare$}
> $$

> [!theorem] **Definición.** (Notación)
>
> Para $x \in \mathbb{R}$ escribimos $e^{x} := \exp(x)$.

Para $x$ racional la proposición dice que es lo mismo de siempre, y para $x$ irracional es la definición: $e^{\sqrt{2}}$ es, **por definición**, $\exp(\sqrt{2})$. Las propiedades de $\exp$ se leen como las leyes de exponentes: $e^{x+y} = e^{x}e^{y}$, $e^{-x} = \frac{1}{e^{x}}$, $(e^{x})' = e^{x}$.

### Potencias de base general

Si $a > 0$ y $r \in \mathbb{Q}$, por la propiedad 7 del logaritmo $\log(a^{r}) = r\log(a)$, es decir, $a^{r} = e^{r\log(a)}$. El lado derecho tiene sentido para **cualquier** exponente real, así que lo tomamos como definición:

> [!theorem] **Definición.** (Potencia de Base General)
>
> Sea $a>0$ y $x \in \mathbb{R}$. Definimos $a^{x}$ como:
> $$
> a^{x} = \exp \left(x \log \left(a\right)\right) \quad \text{ o } \quad a^{x} = e^{x \log \left(a\right)}
> $$

Para $x$ racional coincide con la potencia usual (lo acabamos de ver), y con $a = e$ da $e^{x\log e} = e^{x}$, así que no hay conflicto de notación.

> [!theorem] **Teorema.** (Propiedades de $a^{x}$)
>
> Sean $a, b > 0$ y $x, y \in \mathbb{R}$.
> 1. $\log(a^{x}) = x\log(a)$ (la propiedad 7 de $\log$, ahora para todo $x$ real).
> 2. $a^{x+y} = a^{x}a^{y}$ y $a^{-x} = \dfrac{1}{a^{x}}$.
> 3. $(a^{x})^{y} = a^{xy}$ y $(ab)^{x} = a^{x}b^{x}$.
> 4. $\dfrac{d}{dx}a^{x} = a^{x}\log(a)$.
> 5. Si $a \neq 1$, $x \mapsto a^{x}$ es biyectiva de $\mathbb{R}$ en $(0,\infty)$ y su inversa es $\log_{a}$: si $y = a^{x}$, ent. $x = \log_{a}(y) = \dfrac{\log(y)}{\log(a)}$.
> 6. Para $r \in \mathbb{R}$ y $x > 0$, $\dfrac{d}{dx}x^{r} = r x^{r-1}$.

> [!proof]- **Proof.**
>
> 1. $\log(a^{x}) = \log\left( e^{x\log(a)} \right) = x \log (a)$, por la cancelación $\log \circ \exp = \text{id}$.
> 2. $a^{x+y} = e^{(x+y)\log a} = e^{x\log a}e^{y\log a} = a^{x}a^{y}$, y $a^{-x} = e^{-x\log a} = \frac{1}{e^{x\log a}} = \frac{1}{a^{x}}$.
> 3. Por 1, $(a^{x})^{y} = e^{y\log(a^{x})} = e^{yx\log(a)} = a^{xy}$. Y $(ab)^{x} = e^{x\log(ab)} = e^{x\log a + x\log b} = a^{x}b^{x}$.
> 4. Regla de la cadena: $\frac{d}{dx}e^{x\log(a)} = e^{x\log(a)}\cdot \log(a) = a^{x}\log(a)$.
> 5. Si $a \neq 1$, $\log(a) \neq 0$, así que $x \mapsto x\log(a)$ es biyectiva de $\mathbb{R}$ en $\mathbb{R}$, y $\exp$ lo es de $\mathbb{R}$ en $(0,\infty)$; la composición también. Si $y = a^{x}$, por 1, $\log(y) = x\log(a)$, y despejando, $x = \frac{\log(y)}{\log(a)} = \log_{a}(y)$.
> 6. $x^{r} = e^{r\log(x)}$, así que $\frac{d}{dx}x^{r} = e^{r\log(x)}\cdot \frac{r}{x} = x^{r}\cdot \frac{r}{x} = rx^{r-1}$. $\blacksquare$

> [!example]- Ejemplo. (Derivación logarítmica con exponente variable)
>
> Derivar $y = x^{x}$ para $x > 0$. No es $x\cdot x^{x-1}$ (la base no es constante) ni $x^{x}\log(x)$ (el exponente tampoco). Por definición $x^{x} = e^{x\log(x)}$, y aplicando $\log$ (ver Derivación Logarítmica en [[Funcion Logaritmo]]):
> $$
> \log(y) = x\log(x) \implies \frac{y'}{y} = \log(x) + x\cdot \frac{1}{x} \implies y' = x^{x}\left( \log(x) + 1 \right)
> $$
> En general, para $f > 0$: $\displaystyle \frac{d}{dx}f(x)^{g(x)} = f(x)^{g(x)}\left[ g'(x)\log(f(x)) + g(x)\frac{f'(x)}{f(x)} \right]$.

### Crecimiento comparado

Con la nota del logaritmo ya sabemos que $x - m\log(x) \to \infty$. Leído con la exponencial, dice que $e^{x}$ le gana a cualquier polinomio:

> [!theorem] **Corolario 2.** 
>
> $$
> \lim_{ x \to \infty } \frac{e^{x}}{x^{m}} = \infty \quad \forall  m \in \mathbb{N}
> $$

> [!proof]- **Proof.** 
>
> Para $x > 0$, $x^{m} = e^{\log(x^{m})} = e^{m\log(x)}$, ent.
> $$
> \frac{e^{x}}{x^{m}} = \frac{e^{x}}{e^{\log(x^{m})}} = e ^{x - m\log(x)}
> $$
> Por el Corolario de [[Funcion Logaritmo]], $x - m\log(x) \to \infty$, y por la propiedad 8, $e^{u} \to \infty$ cuando $u \to \infty$; así que $\frac{e^{x}}{x^{m}} \to \infty$. $\blacksquare$

> [!theorem] **Corolario.** (El logaritmo es más lento que cualquier potencia)
>
> Para todo $\alpha > 0$,
> $$
> \lim_{ x \to \infty } \frac{\log(x)}{x^{\alpha}} = 0
> $$

> [!proof]- **Proof.**
>
> Sea $u = \alpha\log(x)$; cuando $x \to \infty$, $u \to \infty$, y $x^{\alpha} = e^{\alpha\log x} = e^{u}$. Ent.
> $$
> \frac{\log(x)}{x^{\alpha}} = \frac{u/\alpha}{e^{u}} = \frac{1}{\alpha}\cdot \frac{1}{e^{u}/u} \longrightarrow 0
> $$
> pues $\frac{e^{u}}{u} \to \infty$ por el Corolario 2 con $m = 1$. $\blacksquare$

### El número $e$ como límite

> [!theorem] **Proposición.** 
>
> $$
> \lim_{ t \to \infty } \left(  1 + \frac{1}{t} \right)^{t} = e
> $$

> [!proof]- **Proof.** 
>
> Sea $f(t) = (1 + \frac{1}{t}) ^{ t}$ (con $t > 0$) y veamos $\log (f(t))$.
> Probando que $\log(f(t)) \to 1$ cuando $t \to \infty$, ya acabé. ¡Trucaso!
> $$
> \begin{align}
> & \log(f(t)) \\[0.5em]
> &= \log\left( 1+\frac{1}{t} \right)^{t} = t\log\left( 1+\frac{1}{t} \right) \tag{Prop. 1 de $a^{x}$} \\[0.5em]
> &= \frac{\log\left( 1+\frac{1}{t} \right)}{\frac{1}{t}} \\[0.5em]
> &= \frac{\log\left( 1+\frac{1}{t} \right) - \log(1)}{\left( 1+\frac{1}{t} \right)- 1} \tag{$\log(1) = 0$}
> \end{align}
> $$
> Es un cociente de diferencias de $\log$ en $1$ con $h = \frac{1}{t} \to 0^{+}$. Así,
> $$
> \lim_{ t \to \infty } \log(f(t)) = \lim_{ h \to 0^{+} }\frac{\log\left( 1+h \right) - \log(1)}{h} = \log'(1) = \frac{1}{1} = 1
> $$
> Por eso, como $\exp$ es continua, $\displaystyle \lim_{ t \to \infty }\left( 1+\frac{1}{t} \right)^{t} = \lim_{ t \to \infty } e^{\log(f(t))} = e^{\lim_{ t \to \infty }\log(f(t))} = e^{1} = e$. $\blacksquare$

> [!observation]+ **Observación.**
>
> 1. En particular, para la sucesión, $\displaystyle \lim_{ n \to \infty } \left( 1+\frac{1}{n} \right)^{n} = e$ con $n \in \mathbb{N}$: dado $\varepsilon > 0$, el $N$ que funciona para $t > N$ funciona en particular para los naturales $n > N$.
> 2. La misma cuenta con $h = \frac{x}{t}$ da $\displaystyle \lim_{ t \to \infty }\left( 1+\frac{x}{t} \right)^{t} = e^{x}$ para todo $x \in \mathbb{R}$ (el interés compuesto continuo).

### Aproximando $e$

¿Cuánto vale $e$? Tenemos tres herramientas: las cotas de $\log(2)$, la sucesión $\left( 1+\frac{1}{n} \right)^{n}$ y el polinomio de Taylor.

> [!theorem] **Proposición.** (Primeras cotas)
>
> $2 < e < 4$.

> [!proof]- **Proof.**
>
> Por el Lema de [[Funcion Logaritmo]], $\log(2) < 1 = \log(e)$, y como $\log$ es creciente, $2 < e$. Además $\log(4) = 2\log(2) > 1 = \log(e)$, así que $e < 4$. $\blacksquare$

> [!theorem] **Proposición.** (La sucesión se acerca por abajo)
>
> Para todo $n \in \mathbb{N}^{+}$,
> $$
> \left( 1+\frac{1}{n} \right)^{n} < e
> $$

> [!proof]- **Proof.**
>
> Por la desigualdad fundamental de [[Funcion Logaritmo]] con $h = \frac{1}{n}$, $\log\left( 1+\frac{1}{n} \right) < \frac{1}{n}$. Multiplicando por $n$,
> $$
> \log\left( 1+\frac{1}{n} \right)^{n} = n\log\left( 1+\frac{1}{n} \right) < 1 = \log(e)
> $$
> y como $\log$ es creciente, $\left( 1+\frac{1}{n} \right)^{n} < e$. $\blacksquare$

> [!theorem] **Proposición.** (Cota superior por el binomio)
>
> Para todo $n \in \mathbb{N}^{+}$,
> $$
> \left( 1+\frac{1}{n} \right)^{n} \leq \sum_{k=0}^{n} \frac{1}{k!} < 3
> $$
> y por lo tanto $e \leq 3$.

> [!proof]- **Proof.**
>
> Por *Binomio de Newton*, recordando $\dbinom{n}{k} = \dfrac{n!}{k!(n-k)!}$,
> $$
> \left( 1+\frac{1}{n} \right)^{n} = \sum_{k=0}^{n} \binom{n}{k}1^{n-k}\left( \frac{1}{n} \right)^{k}
> $$
> y cada término se acota:
> $$
> \begin{align}
> & \binom{n}{k}\frac{1}{n^{k}} \\[0.5em]
> &= \frac{1}{k!}\cdot \frac{n(n-1)\cdots(n-k+1)}{n\cdot n\cdots n} \\[0.5em]
> &= \frac{1}{k!}\left( 1-\frac{1}{n} \right)\cdots\left( 1-\frac{k-1}{n} \right) \leq \frac{1}{k!} \tag{cada factor $\leq 1$}
> \end{align}
> $$
> Además $k! = 1\cdot 2\cdot 3\cdots k \geq 2^{k-1}$ para $k \geq 1$, así que
> $$
> \sum_{k=0}^{n} \frac{1}{k!} \leq 1 + \sum_{k=1}^{n} \frac{1}{2^{k-1}} < 1 + 2 = 3 \tag{serie geométrica}
> $$
> Por último, $e = \lim \left( 1+\frac{1}{n} \right)^{n}$ y por Conservación de Desigualdades ([[Limites de Sucesiones]]), $e \leq 3$. $\blacksquare$

Juntando: $2.25 = \left( 1+\frac{1}{2} \right)^{2} < e \leq 3$. La sucesión converge muy lento ($n = 100$ da $2.7048$), así que para calcular $e$ en serio usamos Taylor.

Por el Teorema de Taylor (ver [[Polinomio de Taylor]]), si $f$ es $(n+1)$ veces derivable alrededor de $x_{0}$, entonces
$$
f(x)= f(x_{0}) + f'(x_{0})(x-x_{0}) + \dots + \frac{f^{(n)}(x_{0})(x-x_{0})^{n}}{n!} + R_{n}(x)
$$
siendo $R_{n}(x)$ el residuo, que en su forma de Lagrange es $R_{n}(x) = \frac{f^{(n+1)}(\xi)}{(n+1)!}(x-x_{0})^{n+1}$ para algún $\xi$ entre $x_{0}$ y $x$.

Dado que $f(x)=e^{x}$ es $C^{\infty}$ (es infinitamente diferenciable) y todas sus derivadas son $e^{x}$, tomando $x_{0} = 0$
$$
\begin{align}
e^{x} &= e^{0} + e^{0}x + \frac{e^{0}x^{2}}{2!}+\frac{e^{0}x^{3}}{3!}+\dots + R_{n}(x) \\[0.5em]
&= 1 + x + \frac{x^{2}}{2!} + \frac{x^{3}}{3!} +\dots + \frac{x^{n}}{n!} + R_{n}(x)
\end{align}
$$

> [!theorem] **Proposición.** ($e$ con error controlado)
>
> Para todo $n \in \mathbb{N}$,
> $$
> e = \sum_{k=0}^{n} \frac{1}{k!} + R_{n}, \qquad 0 < R_{n} < \frac{3}{(n+1)!}
> $$

> [!proof]- **Proof.**
>
> Tomando $x = 1$ en lo anterior, $R_{n} = \frac{e^{\xi}}{(n+1)!}$ con $\xi \in (0,1)$. Como $e^{\xi} > 0$ y $e^{\xi} < e^{1} \leq 3$, se sigue $0 < R_{n} < \frac{3}{(n+1)!}$. $\blacksquare$

> [!example]- Ejemplo. (Calculando $e$)
>
> | $n$ | $\sum_{k=0}^{n} \frac{1}{k!}$ | cota del error $\frac{3}{(n+1)!}$ |
> |:--:|:--:|:--:|
> | $3$ | $2.6667$ | $0.125$ |
> | $5$ | $2.7167$ | $0.0042$ |
> | $8$ | $2.71827877$ | $8.3 \times 10^{-6}$ |
> | $10$ | $2.71828180$ | $7.5 \times 10^{-8}$ |
>
> Con $n = 10$ ya tenemos $e \approx 2.7182818$, mientras que $\left( 1+\frac{1}{n} \right)^{n}$ necesitaría $n$ del orden de millones para lo mismo.

---

Sigue: [[Funciones Hiperbolicas]], las partes par e impar de $e^{x}$.
