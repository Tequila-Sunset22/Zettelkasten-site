---
modified: 2026-11-15T05:26:37Z
title: "Teorema Fundamental del Cálculo"
publish: true
type: zettel
date: "2026-09-07"
status: seed
aliases:
tags:
 - calculus
cssclasses: 
 - romana
---
> La integración y la derivación son operaciones inversas. La integral es una función de *"acumulación"*, y la derivada *"el ritmo actual"*.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Fijamos $a$ y dejamos que el extremo derecho $x$ se mueva: $G(x) = \int_{a}^{x} f$ es el área acumulada hasta $x$. Si avanzamos un poquito $h$, el área nueva es casi un rectángulo de base $h$ y altura $f(x)$, así que $G(x+h) - G(x) \approx f(x)\,h$: el ritmo al que crece el área es la altura de la gráfica. Abajo se dibuja $G$, y su pendiente en $x$ es justo $f(x)$.
>
> <img src="/videos/tfc-acumulacion.avif" alt="center" width="720" loading="lazy">
>
> *Función:* $f(x) = 1 + 0.8x - 0.15x^{2}$ en $[0,5]$ y $G(x) = \int_{0}^{x} f$.

> [!theorem] **Teorema.** (Teorema Fundamental del Cálculo 1)
>
> Sea $f:[a,b] \to \mathbb{R}$ continua, si definimos $G: [a,b] \to \mathbb{R}$ de tal forma que $\displaystyle G(x) = \int_{a}^{x} f(z) \, dz$, entonces $G$ es continua en $[a,b]$ y derivable en $(a,b)$ y su derivada para todo $x \in (a,b)$ es
> $$
> G'(x) = \frac{d}{dx} \int_{a}^{x} f(z) \, dz = f(x)
> $$

> [!proof]- **Proof.** 
>
> Como $f$ es continua, su integral existe en todo $[u,v] \subseteq [a,b]$ y cumple las propiedades de [[Integral de Darboux]]. Por la propiedad 1 (Aditividad),
> $$
> \int_{a}^{u} f(x) \, dx + \int_{u}^{v} f(x) \, dx = \int_{a}^{v} f(x) \, dx 
> $$
> Lo que implica,
> $$
> \int_{u}^{v} f(x) \, dx = \int_{a}^{v} f(x) \, dx - \int_{a}^{u} f(x) \, dx = G(v) - G(u)
> $$
> Por la propiedad 2 (Intercalación), $\forall u,v \in [a,b], \ u< v$
> $$
> (v-u)\underset{[u,v]}{\min } \{ f \} \leq \int_{u}^{v} f(x) \, dx \leq (v-u)\underset{[u,v]}{\max } \{ f \}
> $$
> Entonces, dividiendo entre $v - u > 0$,
> $$
> \underset{[u,v]}{\min } \{ f \} \leq \frac{G(v) - G(u)}{v-u} \leq \underset{[u,v]}{\max } \{ f \} \tag{1}
> $$
> Sea $x \in (a,b)$. Tomamos $u =x$ y $v = x+h$ si $h > 0$, o $u = x+h$ y $v = x$ si $h < 0$; en ambos casos $\frac{G(v) - G(u)}{v - u} = \frac{G(x+h) - G(x)}{h}$, y llamando $J_{h}$ al intervalo entre $x$ y $x+h$,
> $$
> \underset{J_{h}}{\min } \{ f \} \leq \frac{G(x+h) - G(x)}{h} \leq \underset{J_{h}}{\max } \{ f \}
> $$
> **El $\min$ y el $\max$ tienden a $f(x)$.** Sea $\varepsilon > 0$. Por continuidad de $f$ en $x$ existe $\delta > 0$ tal que $\lvert z - x \rvert < \delta \implies \lvert f(z) - f(x) \rvert < \varepsilon$. Si $0 < \lvert h \rvert < \delta$, todo $z \in J_{h}$ cumple $\lvert z - x \rvert \leq \lvert h \rvert < \delta$; como el $\min$ y el $\max$ se alcanzan en puntos de $J_{h}$ ([[Teorema de Weierstrass y de Acotación]]), ambos están a distancia $< \varepsilon$ de $f(x)$. Así,
> $$
> \lim_{ h \to 0 } \underset{J_{h}}{\min } \{ f \} = f(x) = \lim_{ h \to 0 } \underset{J_{h}}{\max } \{ f \}
> $$
> Por el Teorema del Sándwich ([[Limite]])
> $$
> \lim_{ h \to 0 } \frac{G(x+h) - G(x)}{h} = \frac{d}{dx} \int_{a}^{x} f(z) \, dz = f(x)
> $$
> **Continuidad de $G$.** Sea $B$ con $\lvert f \rvert \leq B$ en $[a,b]$. Por $(1)$, $\lvert G(v) - G(u) \rvert \leq B(v - u)$, así que si $x_{n} \to x$ en $[a,b]$, ent. $G(x_{n}) \to G(x)$ (incluso en $a$ y $b$).
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> 1. En los extremos, el mismo argumento con $h > 0$ (en $a$) o $h < 0$ (en $b$) da las derivadas laterales: $G'(a^{+}) = f(a)$ y $G'(b^{-}) = f(b)$.
> 2. Hace falta que $f$ sea continua en $x$: con $f = 0$ en $[0,2]$ salvo $f(1) = 1$ (Ejemplo 1 de [[Integrabilidad]], más adelante), $G = 0$ y $G'(1) = 0 \neq f(1)$.
> 3. Cuidado! $\displaystyle \frac{d}{dx} \int_{a}^{b} f(z) \, dz = 0$ pues no hay variable de derivación $x$, solo estamos derivando una constante.

Después del teorema fundamental, podemos estudiar... [[Antiderivada|Antiderivadas]]: el T.F.C. 1 dice que toda $f$ continua **tiene** antiderivada, $G$. Y llegamos al siguiente resultado.

> La Regla de Barrow (T.F.C. 2) nos permite conectar integrales definidas con antiderivadas, permitiendo calcular la función de acumulación (*integral*).

> [!theorem] **Teorema.** (Teorema Fundamental del Cálculo 2) (Regla de Barrow)
>
> Sea $f: [a,b] \to \mathbb{R}$ continua, y sea $F$ una antiderivada de $f$ (i.e. $F$ continua en $[a,b]$ y $F'(x) = f(x)$ en $(a,b)$), entonces,
> $$
> \int_{a}^{b} f(x) \, dx = F(b)-F(a) = \left. F(x) \right|_{a}^{b}
> $$

> [!proof]- **Proof.**
>
> Sea $G(x) = \int_{a}^{x} f(z)\,dz$. Por el T.F.C. 1, $G' = f = F'$ en $(a,b)$, así que $(F - G)' = 0$ en $(a,b)$ y $F - G$ es continua en $[a,b]$. Por el [[Teorema del Valor Medio|T.V.M.]], una función con derivada $0$ en un intervalo es constante: $F(x) - G(x) = k$ para todo $x \in [a,b]$. Como $G(a) = \int_{a}^{a} f = 0$, se tiene $k = F(a)$, y
> $$
> \int_{a}^{b} f(x) \, dx = G(b) = F(b) - k = F(b) - F(a) \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> - De otra forma,
> $$
> \int_{a}^{b} f(x) \, dx = \int_{a}^{b} \frac{d \ F(x)}{dx} \, dx = F(b) - F(a)
> $$
> - En [[Antiderivada]] está otra prueba, que solo usa el T.V.M. en cada subintervalo: $F(b) - F(a) = \sum_{k} F'(c_{k})(x_{k+1} - x_{k})$ es una [[Sumas de Riemann|suma de Riemann]] de $f$ para **toda** partición, así que vale incluso si $f$ solo es integrable (no necesariamente continua) y tiene antiderivada.
> - La convención $\int_{a}^{b} f = -\int_{b}^{a} f$ (ver [[Mas propiedades de la integral|Propiedades de la Integral]], más adelante) es consistente con Barrow: $F(a) - F(b) = -(F(b) - F(a))$.

Con esto, podemos desarrollar más resultados.

> [!theorem] **Corolario.** (No importa la antiderivada)
>
> Si $F$ y $G$ son antiderivadas de $f$ continua en $[a,b]$, ent. $F(b) - F(a) = G(b) - G(a)$.

> [!proof]- **Proof.** 
>
> Por el T.V.M., $F - G = k$ es constante. Ent. $F(b) - F(a) = (G(b) + k) - (G(a) + k) = G(b) - G(a)$: la constante se cancela, y el valor de $\int_{a}^{b} f$ no depende de la antiderivada que usemos.
> $$
> \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo.** 
>
> $$
> f(x) = x^{2}, \quad x \in [0,1]
> $$
> Consideramos la partición, $\mathcal{P} = \left\{  0, \frac{1}{n}, \frac{2}{n}, \dots , \frac{n}{n}  = 1 \right\}$
> tenemos que
> $$
> \begin{align}
> L(f,\mathcal{P}) &= \sum_{k=0}^{n-1} (x_{k+1}-x_{k}) \cdot \underset{[x_{k},x_{k+1}]}{\min } \{ f(x) \} \\[0.5em]
> &= \sum_{k=0}^{n-1} \frac{1}{n}f(x_{k}) = \frac{1}{n}\left[ 0^{2} +\left( \frac{1}{n} \right)^{2}+\dots+ \left( \frac{n-1}{n} \right)^{2} \right] \\[0.5em]
> &=\frac{1}{n} \cdot \frac{1}{n^{2}} [1^{2}+2^{2}+\dots+(n-1)^{2}] \\[0.5em]
> &=\frac{1}{n}\cdot \frac{1}{n^{2}} \left[ \frac{(n-1)n(2n-1)}{6} \right] = \frac{(n-1)(2n-1)}{6n^{2}} \\[0.5em]
> &= \frac{2n^{2}-3n+1}{6n^{2}} \overset{n \to \infty}{\longrightarrow} \frac{1}{3}
> \end{align}
> $$
> Dada $f(x)=x^{2}$, $\displaystyle F(x) = \frac{x^{3}}{3}$ es antiderivada
> Por T.F.C. 2,
> $$
> \int_{0}^{1} f(x) \, dx  = F(1)- F(0) = \frac{1}{3}
> $$
> Si tomamos $\displaystyle G(x) = \frac{x^{3}}{3} + 1$, $G'(x) = x^{2}$
> Por T.F.C. 2,
> $$
> \int_{0}^{1} f(x) \, dx  = G(1)-G(0) = \left( \frac{1}{3}+1 \right)-(1) = \frac{1}{3}
> $$
> Mucho más fácil que con sumas!
