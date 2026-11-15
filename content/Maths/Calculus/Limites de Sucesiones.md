---
modified: 2026-11-15T04:18:18Z
title: "Límites de Sucesiones"
publish: true
type: zettel
date: "2026-11-10"
status: seed
aliases:
tags:
 - calculus
cssclasses:
 - romana
---
En [[Sucesiones Convergentes]] y [[Sucesiones Divergentes]] probamos cada límite con la definición ($\varepsilon$-$N$). Funciona, pero es cansado. Igual que con el [[Limite|límite de funciones]], la idea es usar la definición para **desarrollar una teoría** que calcule los límites por nosotros.

> Probamos pocas cosas con $\varepsilon$, y con ellas armamos todo lo demás.

### Álgebra de límites

> [!theorem] **Teorema.** (Álgebra de Límites de Sucesiones)
>
> Sean $\{ a_{n} \}, \{ b_{n} \}$ sucesiones tales que $a_{n} \to L$ y $b_{n} \to M$, con $L, M \in \mathbb{R}$, y sea $c \in \mathbb{R}$. Ent.
> 1. $(a_{n} + b_{n}) \to L + M$
> 2. $c \, a_{n} \to cL$
> 3. $a_{n} b_{n} \to LM$
> 4. Si $M \neq 0$ y $b_{n} \neq 0 \ \forall n \in \mathbb{N}$, ent. $\displaystyle \frac{a_{n}}{b_{n}} \to \frac{L}{M}$

> [!proof]- **Proof.**
>
> 1. **Borrador.** Por Des. triang.,
> $$
> \lvert (a_{n} + b_{n}) - (L + M) \rvert \leq \lvert a_{n} - L \rvert + \lvert b_{n} - M \rvert
> $$
> Si a cada sumando le pedimos ser menor que $\frac{\varepsilon}{2}$, la suma es menor que $\varepsilon$.
>
> **Proof.** Sea $\varepsilon > 0$. Como $a_{n} \to L$, existe $N_{1}$ tq. $\forall n \geq N_{1}$ $\lvert a_{n} - L \rvert < \frac{\varepsilon}{2}$. Como $b_{n} \to M$, existe $N_{2}$ tq. $\forall n \geq N_{2}$ $\lvert b_{n} - M \rvert < \frac{\varepsilon}{2}$. Sea $N = \max \{ N_{1}, N_{2} \}$, ent. $\forall n \geq N$,
> $$
> \lvert (a_{n} + b_{n}) - (L + M) \rvert \leq \lvert a_{n} - L \rvert + \lvert b_{n} - M \rvert < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon \tag*{$\blacksquare$}
> $$
> 2. Si $c = 0$, ent. $c\,a_{n} = 0$ es constante y tiende a $0 = cL$. Sup. $c \neq 0$. Sea $\varepsilon > 0$, existe $N$ tq. $\forall n \geq N$ $\lvert a_{n} - L \rvert < \frac{\varepsilon}{\lvert c \rvert}$. Ent. $\forall n \geq N$,
> $$
> \lvert c\,a_{n} - cL \rvert = \lvert c \rvert \lvert a_{n} - L \rvert < \lvert c \rvert \cdot \frac{\varepsilon}{\lvert c \rvert} = \varepsilon \tag*{$\blacksquare$}
> $$
> 3. **Borrador.** Sumamos y restamos $a_{n}M$:
> $$
> a_{n}b_{n} - LM = a_{n}b_{n} - a_{n}M + a_{n}M - LM = a_{n}(b_{n} - M) + M(a_{n} - L)
> $$
> El problema es el factor $a_{n}$, que cambia con $n$. Pero $\{ a_{n} \}$ converge, ent. está acotada: $\lvert a_{n} \rvert \leq k$. Así,
> $$
> \lvert a_{n}b_{n} - LM \rvert \leq k \lvert b_{n} - M \rvert + \lvert M \rvert \lvert a_{n} - L \rvert
> $$
> y le pedimos a cada sumando ser menor que $\frac{\varepsilon}{2}$. Usamos $\lvert M \rvert + 1$ en vez de $\lvert M \rvert$ para no dividir entre $0$ si $M = 0$.
>
> **Proof.** Como $\{ a_{n} \}$ converge, está acotada (ver [[Sucesiones Convergentes]]): existe $k > 0$ tq. $\forall n$ $\lvert a_{n} \rvert \leq k$. Sea $\varepsilon > 0$. Existen $N_{1}, N_{2}$ tq.
> $$
> \forall n \geq N_{1} \ \ \lvert b_{n} - M \rvert < \frac{\varepsilon}{2k} \qquad \text{y} \qquad \forall n \geq N_{2} \ \ \lvert a_{n} - L \rvert < \frac{\varepsilon}{2(\lvert M \rvert + 1)}
> $$
> Sea $N = \max \{ N_{1}, N_{2} \}$, ent. $\forall n \geq N$,
> $$
> \begin{align}
> \lvert a_{n}b_{n} - LM \rvert &= \lvert a_{n}(b_{n} - M) + M(a_{n} - L) \rvert \\[0.5em]
> &\leq \lvert a_{n} \rvert \lvert b_{n} - M \rvert + \lvert M \rvert \lvert a_{n} - L \rvert \tag{Des. triang.} \\[0.5em]
> &< k \cdot \frac{\varepsilon}{2k} + \lvert M \rvert \cdot \frac{\varepsilon}{2(\lvert M \rvert + 1)} \\[0.5em]
> &< \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon
> \end{align}
> $$
> $$
> \tag*{$\blacksquare$}
> $$
> 4. Por (3), como $\frac{a_{n}}{b_{n}} = a_{n} \cdot \frac{1}{b_{n}}$, basta probar que $\frac{1}{b_{n}} \to \frac{1}{M}$.
>
> **Borrador.**
> $$
> \left\lvert \frac{1}{b_{n}} - \frac{1}{M} \right\rvert = \frac{\lvert M - b_{n} \rvert}{\lvert b_{n} \rvert \lvert M \rvert}
> $$
> El numerador es chico, pero el $\lvert b_{n} \rvert$ del denominador podría ser muy chico y hacer grande la fracción. El Lema de abajo dice que a partir de cierto $n$, $\lvert b_{n} \rvert > \frac{\lvert M \rvert}{2}$, ent. la fracción es menor que $\frac{2 \lvert b_{n} - M \rvert}{\lvert M \rvert^{2}}$.
>
> **Proof.** Por el Lema, existe $N_{0}$ tq. $\forall n \geq N_{0}$ $\lvert b_{n} \rvert > \frac{\lvert M \rvert}{2}$. Sea $\varepsilon > 0$, existe $N_{1}$ tq. $\forall n \geq N_{1}$ $\lvert b_{n} - M \rvert < \frac{\varepsilon \lvert M \rvert^{2}}{2}$. Sea $N = \max \{ N_{0}, N_{1} \}$, ent. $\forall n \geq N$,
> $$
> \left\lvert \frac{1}{b_{n}} - \frac{1}{M} \right\rvert = \frac{\lvert b_{n} - M \rvert}{\lvert b_{n} \rvert \lvert M \rvert} < \frac{2\lvert b_{n} - M \rvert}{\lvert M \rvert^{2}} < \frac{2}{\lvert M \rvert^{2}} \cdot \frac{\varepsilon \lvert M \rvert^{2}}{2} = \varepsilon \tag*{$\blacksquare$}
> $$

> [!theorem] **Lema.** (Acotación lejos de cero)
>
> Si $b_{n} \to M$ y $M \neq 0$, ent. existe $N_{0} \in \mathbb{N}$ tq. $\forall n \geq N_{0}$
> $$
> \lvert b_{n} \rvert > \frac{\lvert M \rvert}{2}
> $$
> En particular, $b_{n} \neq 0$ para $n \geq N_{0}$.

> [!proof]- **Proof.**
>
> Para $\varepsilon = \frac{\lvert M \rvert}{2} > 0$ existe $N_{0}$ tq. $\forall n \geq N_{0}$ $\lvert b_{n} - M \rvert < \frac{\lvert M \rvert}{2}$. Ent. $\forall n \geq N_{0}$,
> $$
> \lvert M \rvert \leq \lvert M - b_{n} \rvert + \lvert b_{n} \rvert < \frac{\lvert M \rvert}{2} + \lvert b_{n} \rvert \tag{Des. triang.}
> $$
> Restando $\frac{\lvert M \rvert}{2}$ de ambos lados, $\lvert b_{n} \rvert > \frac{\lvert M \rvert}{2}$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> 1. Por el Lema, la hipótesis "$b_{n} \neq 0 \ \forall n$" del inciso (4) solo sirve para que $\left\{ \frac{a_{n}}{b_{n}} \right\}$ esté definida (ver la división en [[Sucesiones]]): si $M \neq 0$, de todos modos $b_{n} \neq 0$ a partir de cierto término.
> 2. Por inducción, (1) y (3) se generalizan a sumas y productos de una cantidad finita de sucesiones. En particular, si $a_{n} \to L$, ent. $a_{n}^{p} \to L^{p}$ para todo $p \in \mathbb{N}^{+}$.
> 3. **Cuidado:** el teorema solo se aplica cuando **cada** sucesión converge. El recíproco es falso: con $a_{n} = (-1)^{n}$ y $b_{n} = -(-1)^{n}$, la suma $a_{n} + b_{n} = 0$ converge y el producto $a_{n}b_{n} = -1$ también, pero ninguna de las dos converge.

> [!theorem] **Corolario.**
>
> Sean $a_{n} \to L$ y $b_{n} \to M$. Ent.
> 1. $(a_{n} - b_{n}) \to L - M$
> 2. Si $\{ a_{n} + b_{n} \}$ y $\{ a_{n} \}$ convergen, ent. $\{ b_{n} \}$ converge.

> [!proof]- **Proof.**
>
> 1. $a_{n} - b_{n} = a_{n} + (-1)b_{n}$, y por (2) y (1) del teorema, tiende a $L + (-1)M = L - M$.
> 2. Aquí solo suponemos que $\{ a_{n} + b_{n} \}$ y $\{ a_{n} \}$ convergen. Como $b_{n} = (a_{n} + b_{n}) - a_{n}$ es diferencia de dos sucesiones convergentes, por (1) converge.
> $$
> \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo 1.** (Cociente de polinomios)
>
> Calculemos $\displaystyle \lim_{ n \to \infty } \frac{3n^{2} + n - 1}{n^{2} + 5}$.
> No podemos aplicar (4) directamente: ni el numerador ni el denominador convergen. El truco es **dividir entre la mayor potencia** del denominador:
> $$
> \frac{3n^{2} + n - 1}{n^{2} + 5} = \frac{3 + \frac{1}{n} - \frac{1}{n^{2}}}{1 + \frac{5}{n^{2}}}
> $$
> Como $\frac{1}{n} \to 0$ y $\frac{1}{n^{2}} = \frac{1}{n} \cdot \frac{1}{n} \to 0$, por álgebra de límites el numerador tiende a $3 + 0 - 0 = 3$ y el denominador a $1 + 5 \cdot 0 = 1 \neq 0$, con $1 + \frac{5}{n^{2}} \neq 0 \ \forall n$. Ent.
> $$
> \lim_{ n \to \infty } \frac{3n^{2} + n - 1}{n^{2} + 5} = \frac{3}{1} = 3
> $$
> > [!observation]+ **Observación.**
> >
> > El mismo truco da el caso general (cociente de dos polinomios en $n$ según sus grados): es el primer teorema de [[Criterios de Convergencia de Sucesiones]].

### Valor absoluto

> [!theorem] **Proposición.** (Límite del Valor Absoluto)
>
> Si $a_{n} \to L$, ent. $\lvert a_{n} \rvert \to \lvert L \rvert$.

> [!proof]- **Proof.**
>
> Por la propiedad $\big\lvert \lvert a \rvert - \lvert b \rvert \big\rvert \leq \lvert a - b \rvert$ (ver [[Valor Absoluto]]),
> $$
> \big\lvert \lvert a_{n} \rvert - \lvert L \rvert \big\rvert \leq \lvert a_{n} - L \rvert
> $$
> Ent. el mismo $N$ que funciona para $a_{n} \to L$ funciona para $\lvert a_{n} \rvert \to \lvert L \rvert$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> El recíproco es falso: $\lvert (-1)^{n} \rvert = 1 \to 1$, pero $\{ (-1)^{n} \}$ diverge. Sin embargo, **sí** vale cuando $L = 0$: $\lvert a_{n} \rvert \to 0 \iff a_{n} \to 0$ (es la Proposición de [[Sucesiones Convergentes]] con $L = 0$).

### Propiedades de orden

> [!theorem] **Teorema.** (Conservación del Signo)
>
> Si $a_{n} \geq 0$ para todo $n$ y $a_{n} \to L$, ent. $L \geq 0$.

> [!proof]- **Proof.**
>
> **Borrador.** Si $L < 0$, una banda alrededor de $L$ que no llegue al $0$ dejaría fuera a todos los términos, que son $\geq 0$. La banda de radio $-L$ justo no llega al $0$.
>
> **Proof.** Sup. que $L < 0$ y sea $\varepsilon = -L > 0$. Existe $N$ tq. $\forall n \geq N$ $\lvert a_{n} - L \rvert < -L$. En particular, $a_{N} - L < -L$, i.e. $a_{N} < 0$, lo que contradice que $a_{N} \geq 0$.
> $$
> \therefore \ L \geq 0 \tag*{$\blacksquare$}
> $$

> [!theorem] **Corolario.** (Conservación de Desigualdades)
>
> Sean $a_{n} \to L$ y $b_{n} \to M$.
> 1. Si $a_{n} \leq b_{n}$ para todo $n$, ent. $L \leq M$.
> 2. Si $\alpha \leq a_{n} \leq \beta$ para todo $n$, ent. $\alpha \leq L \leq \beta$.

> [!proof]- **Proof.**
>
> 1. Sea $c_{n} = b_{n} - a_{n} \geq 0$. Por el Corolario de álgebra de límites $c_{n} \to M - L$, y por Conservación del Signo $M - L \geq 0$.
> 2. Aplicamos (1) con las sucesiones constantes $\alpha$ y $\beta$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> 1. Las desigualdades **estrictas** no se conservan: $\frac{1}{n} > 0$ para todo $n$, pero $\lim \frac{1}{n} = 0$. Lo más que se obtiene de $a_{n} < b_{n}$ es $L \leq M$.
> 2. Basta que las hipótesis valgan a partir de cierto $N_{0}$ (solo importa la cola).

El corolario supone que **ambas** sucesiones convergen. El siguiente teorema es más fuerte: si la sucesión de en medio está "apretada", su convergencia es parte de la conclusión.

> [!theorem] **Teorema.** (Sándwich)
>
> Sean $\{ a_{n} \}, \{ b_{n} \}, \{ c_{n} \}$ sucesiones tq. $a_{n} \leq b_{n} \leq c_{n}$ para todo $n \geq N_{0}$. Si $a_{n} \to L$ y $c_{n} \to L$, ent. $b_{n} \to L$.

> [!proof]- **Proof.**
>
> **Borrador.** A partir de cierto $n$, $a_{n}$ y $c_{n}$ están en la banda $(L-\varepsilon, L+\varepsilon)$, y $b_{n}$ está entre ellas.
>
> **Proof.** Sea $\varepsilon > 0$. Existen $N_{1}, N_{2}$ tq. $\forall n \geq N_{1}$ $L - \varepsilon < a_{n}$ y $\forall n \geq N_{2}$ $c_{n} < L + \varepsilon$. Sea $N = \max \{ N_{0}, N_{1}, N_{2} \}$, ent. $\forall n \geq N$,
> $$
> L - \varepsilon < a_{n} \leq b_{n} \leq c_{n} < L + \varepsilon
> $$
> i.e. $\lvert b_{n} - L \rvert < \varepsilon$.
> $$
> \therefore \ b_{n} \to L \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo 2.** ($\frac{n}{n^{2}+1} \to 0$)
>
> Para todo $n$, $0 \leq \frac{n}{n^{2}+1} \leq \frac{n}{n^{2}} = \frac{1}{n}$. Como $0 \to 0$ y $\frac{1}{n} \to 0$, por Sándwich $\frac{n}{n^{2}+1} \to 0$.

> [!theorem] **Corolario.** (Acotada por Nula)
>
> Si $\{ a_{n} \}$ está acotada y $b_{n} \to 0$, ent. $a_{n}b_{n} \to 0$.

> [!proof]- **Proof.**
>
> Sea $k > 0$ tq. $\lvert a_{n} \rvert \leq k$ para todo $n$. Ent.
> $$
> 0 \leq \lvert a_{n} b_{n} \rvert \leq k \lvert b_{n} \rvert
> $$
> Como $b_{n} \to 0$, por Valor Absoluto y álgebra de límites $k\lvert b_{n} \rvert \to k \cdot 0 = 0$. Por Sándwich $\lvert a_{n}b_{n} \rvert \to 0$, ent. $a_{n}b_{n} \to 0$.
> $$
> \tag*{$\blacksquare$}
> $$

Este corolario **no** es álgebra de límites: $\{ a_{n} \}$ puede no converger.

> [!example]- **Ejemplo 3.** ($\frac{\sin(n)}{n} \to 0$ y $\frac{(-1)^{n}}{n} \to 0$)
>
> $\{ \sin(n) \}$ y $\{ (-1)^{n} \}$ no convergen, pero están acotadas por $1$, y $\frac{1}{n} \to 0$. Por el corolario, ambos productos tienden a $0$.

### Límites importantes

> [!theorem] **Proposición.** (Potencias)
>
> Si $\lvert r \rvert < 1$, ent. $r^{n} \to 0$.

> [!proof]- **Proof.**
>
> **Borrador.** Si $0 < \lvert r \rvert < 1$, ent. $\frac{1}{\lvert r \rvert} > 1$ y lo escribimos como $1 + b$ con $b > 0$. La [[Desigualdad de Bernoulli]] dice que $(1+b)^{n} \geq 1 + nb > nb$, ent.
> $$
> \lvert r^{n} \rvert = \frac{1}{(1+b)^{n}} < \frac{1}{nb}
> $$
> y esto es menor que $\varepsilon$ si $n > \frac{1}{b\varepsilon}$.
>
> **Proof.** Si $r = 0$, $r^{n} = 0 \to 0$. Sup. $0 < \lvert r \rvert < 1$ y sea $b = \frac{1}{\lvert r \rvert} - 1 > 0$. Sea $\varepsilon > 0$. Por la Prop. Arquimediana existe $N$ tq. $N > \frac{1}{b\varepsilon}$. Ent. $\forall n \geq N$,
> $$
> \begin{align}
> \lvert r^{n} - 0 \rvert = \frac{1}{(1+b)^{n}} &\leq \frac{1}{1 + nb} \tag{Bernoulli} \\[0.5em]
> &< \frac{1}{nb} \leq \frac{1}{Nb} < \varepsilon
> \end{align}
> $$
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Completando los casos de $\{ r^{n} \}$:
> - $r = 1$: constante, converge a $1$.
> - $r = -1$: diverge oscilando (Ejemplo 6 de [[Sucesiones Divergentes]]).
> - $r > 1$: $r^{n} \to \infty$ (Ejemplo 5 abajo).
> - $r < -1$: diverge oscilando, pues $\lvert r^{n} \rvert = \lvert r \rvert^{n} \to \infty$ y el signo alterna.

> [!theorem] **Proposición.** (Raíz Cuadrada)
>
> Si $a_{n} \geq 0$ para todo $n$ y $a_{n} \to L$, ent. $\sqrt{ a_{n} } \to \sqrt{ L }$.

> [!proof]- **Proof.**
>
> Por Conservación del Signo $L \geq 0$, así que $\sqrt{ L }$ tiene sentido. Sea $\varepsilon > 0$.
>
> *Caso 1:* $L > 0$. Racionalizando,
> $$
> \lvert \sqrt{ a_{n} } - \sqrt{ L } \rvert = \frac{\lvert a_{n} - L \rvert}{\sqrt{ a_{n} } + \sqrt{ L }} \leq \frac{\lvert a_{n} - L \rvert}{\sqrt{ L }}
> $$
> Existe $N$ tq. $\forall n \geq N$ $\lvert a_{n} - L \rvert < \varepsilon \sqrt{ L }$, y ent. $\lvert \sqrt{ a_{n} } - \sqrt{ L } \rvert < \varepsilon$.
>
> *Caso 2:* $L = 0$. Existe $N$ tq. $\forall n \geq N$ $a_{n} = \lvert a_{n} - 0 \rvert < \varepsilon^{2}$, ent. $\sqrt{ a_{n} } < \varepsilon$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo 4.** ($\sqrt{ 12 + \frac{1}{n} } \to \sqrt{ 12 }$)
>
> $12 + \frac{1}{n} \geq 0$ y por álgebra de límites $12 + \frac{1}{n} \to 12$. Por la proposición, $\sqrt{ 12 + \frac{1}{n} } \to \sqrt{ 12 }$.

> [!theorem] **Proposición.** (Algunas sucesiones nulas)
>
> 1. $\displaystyle \frac{n!}{n^{n}} \to 0$
> 2. $\displaystyle \frac{1}{n^{r}} \to 0$ para todo $r \in \mathbb{Q}^{+}$
> 3. $\displaystyle \frac{\log(n)}{n} \to 0$

> [!proof]- **Proof.**
>
> 1. Para $n \geq 1$,
> $$
> 0 < \frac{n!}{n^{n}} = \frac{1}{n} \cdot \underbrace{\frac{2}{n} \cdots \frac{n}{n}}_{\text{cada factor } \leq 1} \leq \frac{1}{n}
> $$
> y por Sándwich $\frac{n!}{n^{n}} \to 0$.
> 2. Primero $r = \frac{1}{q}$ con $q \in \mathbb{N}^{+}$. Sea $\varepsilon > 0$. Por la Prop. Arquimediana existe $N$ tq. $N > \frac{1}{\varepsilon^{q}}$. Como $x \mapsto x^{1/q}$ es estrictamente creciente, $\forall n \geq N$,
> $$
> n^{1/q} \geq N^{1/q} > \frac{1}{\varepsilon} \implies \left\lvert \frac{1}{n^{1/q}} - 0 \right\rvert < \varepsilon
> $$
> Si $r = \frac{p}{q}$ con $p, q \in \mathbb{N}^{+}$, ent. $\frac{1}{n^{r}} = \left( \frac{1}{n^{1/q}} \right)^{p} \to 0^{p} = 0$ (Obs. (2) de álgebra de límites).
> 3. Para $x \geq 1$, como $\frac{1}{t} \leq 1$ si $t \geq 1$,
> $$
> \log(x) = \int_{1}^{x} \frac{1}{t} \, dt \leq \int_{1}^{x} 1 \, dt = x - 1 < x
> $$
> (ver [[Funcion Logaritmo]]). Con $x = \sqrt{ n }$ y $\log(n) = \log(\sqrt{ n } \cdot \sqrt{ n }) = 2\log(\sqrt{ n })$, para $n \geq 1$,
> $$
> 0 \leq \frac{\log(n)}{n} = \frac{2\log(\sqrt{ n })}{n} < \frac{2\sqrt{ n }}{n} = \frac{2}{\sqrt{ n }}
> $$
> Por (2) con $r = \frac{1}{2}$ y álgebra de límites, $\frac{2}{\sqrt{ n }} \to 0$, y por Sándwich $\frac{\log(n)}{n} \to 0$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Proposición.** (Raíz $n$-ésima)
>
> Si $c > 0$, ent. $\sqrt[n]{ c } \to 1$.

> [!proof]- **Proof.**
>
> $\sqrt[n]{ c }$ existe por el [[Teorema de Existencia de Raices]].
>
> *Caso 1:* $c \geq 1$. Ent. $\sqrt[n]{ c } \geq 1$ (si fuera $< 1$, tendríamos $c = (\sqrt[n]{ c })^{n} < 1$). Sea $h_{n} = \sqrt[n]{ c } - 1 \geq 0$. Por la [[Desigualdad de Bernoulli]],
> $$
> c = (1 + h_{n})^{n} \geq 1 + nh_{n} \implies 0 \leq h_{n} \leq \frac{c - 1}{n}
> $$
> Por Sándwich $h_{n} \to 0$, i.e. $\sqrt[n]{ c } = 1 + h_{n} \to 1$.
>
> *Caso 2:* $0 < c < 1$. Ent. $\frac{1}{c} > 1$ y por el Caso 1 $\sqrt[n]{ 1/c } = \frac{1}{\sqrt[n]{ c }} \to 1$. Por álgebra de límites (cociente), $\sqrt[n]{ c } = \dfrac{1}{1/\sqrt[n]{ c }} \to \frac{1}{1} = 1$.
> $$
> \tag*{$\blacksquare$}
> $$

### Propiedades de $\pm\infty$

Recordemos que $a_{n} \to \infty$ sii $\forall M \in \mathbb{R} \ \exists N \ \forall n \geq N \ (a_{n} > M)$ (ver [[Sucesiones Divergentes]]).

> [!theorem] **Teorema.** (Álgebra con $\infty$)
>
> Sean $a_{n} \to \infty$ y $b_{n} \to \infty$.
> 1. $(a_{n} + b_{n}) \to \infty$
> 2. $a_{n}b_{n} \to \infty$
> 3. Si $c > 0$, ent. $c\,a_{n} \to \infty$. Si $c < 0$, ent. $c\,a_{n} \to -\infty$.
> 4. Si $\{ f_{n} \}$ está acotada inferiormente (p. ej. si converge), ent. $(a_{n} + f_{n}) \to \infty$.
> 5. (Comparación) Si $a_{n} \leq d_{n}$ para todo $n \geq N_{0}$, ent. $d_{n} \to \infty$.

> [!proof]- **Proof.**
>
> Sea $M \in \mathbb{R}$.
> 1. Existen $N_{1}, N_{2}$ tq. $\forall n \geq N_{1}$ $a_{n} > \frac{M}{2}$ y $\forall n \geq N_{2}$ $b_{n} > \frac{M}{2}$. Para $n \geq \max \{ N_{1}, N_{2} \}$, $a_{n} + b_{n} > M$.
> 2. Sea $M' = \max \{ M, 1 \}$. Existen $N_{1}, N_{2}$ tq. $\forall n \geq N_{1}$ $a_{n} > M'$ y $\forall n \geq N_{2}$ $b_{n} > 1$. Para $n \geq \max \{ N_{1}, N_{2} \}$, como $a_{n} > M' \geq 1 > 0$ y $b_{n} > 1$,
> $$
> a_{n}b_{n} > a_{n} \cdot 1 > M' \geq M
> $$
> 3. Si $c > 0$, existe $N$ tq. $\forall n \geq N$ $a_{n} > \frac{M}{c}$, ent. $c\,a_{n} > M$. Si $c < 0$, ent. $-c > 0$ y $(-c)a_{n} \to \infty$, que equivale a $c\,a_{n} \to -\infty$.
> 4. Sea $m$ tq. $f_{n} \geq m$ para todo $n$. Existe $N$ tq. $\forall n \geq N$ $a_{n} > M - m$, ent. $a_{n} + f_{n} > (M - m) + m = M$.
> 5. Existe $N_{1}$ tq. $\forall n \geq N_{1}$ $a_{n} > M$. Para $n \geq \max \{ N_{0}, N_{1} \}$, $d_{n} \geq a_{n} > M$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Proposición.** ($c \cdot \infty$)
>
> Si $\displaystyle \lim_{n \to \infty} x_{n} = c \neq 0$ y $\lim_{n \to \infty} y_{n} = \infty$ entonces,
> $$
> \lim_{n \to \infty} x_{n}y_{n} = \begin{cases}
>   \infty & \text{ si } c>0\\
>   -\infty & \text{ si } c<0
> \end{cases}
> $$
> Generaliza (3) del teorema: ahí $x_{n} = c$ es constante.

> [!proof]- **Proof.**
>
> Supongamos que $c>0$. Sea $M \in \mathbb{R}$; basta el caso $M > 0$ (si $x_{n}y_{n} > 1$, ent. $x_{n}y_{n} > M$ para todo $M \leq 0$). Sean $0 < \varepsilon < c$ y $\displaystyle M' = \frac{M}{c-\varepsilon} > 0$. Entonces existe $N \in \mathbb{N}$ tal que $x_{n} > c-\varepsilon > 0$ y $y_{n} > M'$ para $n \geq N$. Por tanto:
> $$
> x_{n}y_{n} > (c - \varepsilon)M' = M
> $$
> Si $c < 0$, ent. $-x_{n} \to -c > 0$ y por lo anterior $(-x_{n})y_{n} \to \infty$, i.e. $x_{n}y_{n} \to -\infty$ (Obs. (2) de [[Sucesiones Divergentes]]).
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Tarea.**
>
> Supongamos que $\lim y_{n} = \infty$ y que $\{ x_{n} \}$ es una sucesión, entonces,
> $$
> \lim x_{n} = \begin{cases}
>   \infty & \text{ si } x_{n} \geq ky_{n} \quad \forall n\geq N_{0} \text{ y algún } k>0 \\[0.5em]
>   -\infty & \text{ si } x_{n} \leq -k y_{n} \quad \forall n \geq N_{0} \text{ y algún } k>0
> \end{cases}
> $$

> [!proof]- **Proof.**
>
> Por (3) del teorema, $ky_{n} \to \infty$.
> - Si $x_{n} \geq ky_{n}$ para $n \geq N_{0}$, por (5) Comparación $x_{n} \to \infty$.
> - Si $x_{n} \leq -ky_{n}$ para $n \geq N_{0}$, ent. $-x_{n} \geq ky_{n}$, así que $-x_{n} \to \infty$, i.e. $x_{n} \to -\infty$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Proposición.** (Recíprocos)
>
> 1. Si $a_{n} \neq 0$ para todo $n$, ent. $\lvert a_{n} \rvert \to \infty \iff \frac{1}{a_{n}} \to 0$. En particular, si $a_{n} \to \infty$ o $a_{n} \to -\infty$, ent. $\frac{1}{a_{n}} \to 0$.
> 2. Si $e_{n} > 0$ para todo $n$ y $e_{n} \to 0$, ent. $\frac{1}{e_{n}} \to \infty$.

> [!proof]- **Proof.**
>
> 1. Se basa en que $\lvert a_{n} \rvert > M \iff \frac{1}{\lvert a_{n} \rvert} < \varepsilon$, donde $M > 0$ y $\varepsilon = \frac{1}{M}$.
>
> ($\implies$) Sea $\varepsilon > 0$. Existe $N$ tq. $\forall n \geq N$ $\lvert a_{n} \rvert > \frac{1}{\varepsilon} > 0$, ent. $\left\lvert \frac{1}{a_{n}} - 0 \right\rvert = \frac{1}{\lvert a_{n} \rvert} < \varepsilon$.
>
> ($\impliedby$) Sea $M \in \mathbb{R}$. Si $M \leq 0$, ent. $\lvert a_{n} \rvert > 0 \geq M$ para todo $n$. Si $M > 0$, existe $N$ tq. $\forall n \geq N$ $\frac{1}{\lvert a_{n} \rvert} < \frac{1}{M}$, ent. $\lvert a_{n} \rvert > M$.
>
> Si $a_{n} \to \infty$, como $\lvert a_{n} \rvert \geq a_{n}$, por Comparación $\lvert a_{n} \rvert \to \infty$. Si $a_{n} \to -\infty$, lo mismo con $\lvert a_{n} \rvert \geq -a_{n}$.
> 2. Sea $M \in \mathbb{R}$. Si $M \leq 0$, ent. $\frac{1}{e_{n}} > 0 \geq M$ para todo $n$. Si $M > 0$, existe $N$ tq. $\forall n \geq N$ $e_{n} = \lvert e_{n} - 0 \rvert < \frac{1}{M}$, ent. $\frac{1}{e_{n}} > M$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> 1. En (1), $\frac{1}{a_{n}} \to 0$ **no** implica $a_{n} \to \pm\infty$, solo $\lvert a_{n} \rvert \to \infty$: con $a_{n} = (-1)^{n}n$, $\frac{1}{a_{n}} \to 0$ pero $\{ a_{n} \}$ oscila (Obs. (3) de [[Sucesiones Divergentes]]).
> 2. En (2) es indispensable que $e_{n} > 0$: con $e_{n} = \frac{(-1)^{n}}{n} \to 0$, $\frac{1}{e_{n}} = (-1)^{n}n$ oscila.

> [!example]- **Ejemplo 5.** ($c^{n} \to \infty$ si $c > 1$)
>
> Por la [[Desigualdad de Bernoulli]], con $c = 1 + (c-1)$ y $c - 1 > 0$,
> $$
> c^{n} = (1 + (c-1))^{n} \geq 1 + n(c-1) > n(c-1)
> $$
> Como $n \to \infty$ y $c - 1 > 0$, por (3) $n(c-1) \to \infty$, y por Comparación $c^{n} \to \infty$.

> [!example]- **Ejemplo 6.** ($\frac{n^{2}+1}{n+1} \to \infty$)
>
> Dividiendo polinomios, $\frac{n^{2}+1}{n+1} = n - 1 + \frac{2}{n+1}$, pues $(n-1)(n+1) + 2 = n^{2} + 1$. Ent.
> $$
> \frac{n^{2}+1}{n+1} \geq n - 1
> $$
> y $n - 1 \to \infty$ por (4) (con $f_{n} = -1$). Por Comparación, $\frac{n^{2}+1}{n+1} \to \infty$.

> [!example]- **Ejemplo 7.** (Por recíprocos)
>
> Las siguientes sucesiones son positivas y sus recíprocas son nulas, así que por Recíprocos (2) tienden a $\infty$:
> - $\lvert x \rvert^{n}$ con $\lvert x \rvert > 1$: su recíproca es $\left( \frac{1}{\lvert x \rvert} \right)^{n} \to 0$ por Potencias. En particular $\{ x^{n} \}$ diverge.
> - $\displaystyle \frac{n}{\log(n)}$ (para $n \geq 2$): su recíproca $\frac{\log(n)}{n} \to 0$.
> - $\displaystyle \frac{n^{n}}{n!}$: su recíproca $\frac{n!}{n^{n}} \to 0$.
> - $n^{r}$ con $r \in \mathbb{Q}^{+}$: su recíproca $\frac{1}{n^{r}} \to 0$.

> [!example]- **Ejemplo 8.** ($\frac{n^{n}}{\log(n)} \to \infty$)
>
> Para $n \geq 2$, $0 < \log(n) < n$ (ver la prueba de "Algunas sucesiones nulas"), ent.
> $$
> \frac{n^{n}}{\log(n)} > \frac{n^{n}}{n} = n^{n-1} \geq n
> $$
> y por Comparación $\frac{n^{n}}{\log(n)} \to \infty$.

### Formas indeterminadas

El teorema de "álgebra con $\infty$" **no** dice nada de $\infty - \infty$, $0 \cdot \infty$, $\frac{\infty}{\infty}$ o $\frac{0}{0}$. No es un olvido: en esos casos el resultado depende de las sucesiones concretas.

> [!example]- **Ejemplo 9.** (Todo puede pasar)
>
> **$\infty - \infty$.** En los tres casos $a_{n} \to \infty$ y $b_{n} \to \infty$:
> - $a_{n} = n + c$, $b_{n} = n$: $a_{n} - b_{n} = c \to c$, cualquier real.
> - $a_{n} = n^{2}$, $b_{n} = n$: $a_{n} - b_{n} = n(n-1) \geq n - 1 \to \infty$.
> - $a_{n} = n + (-1)^{n}$, $b_{n} = n$: $a_{n} - b_{n} = (-1)^{n}$ oscila.
>
> **$0 \cdot \infty$.** Con $\frac{c}{n} \to 0$ y $n \to \infty$, $\frac{c}{n} \cdot n = c$; pero con $\frac{1}{n} \to 0$ y $n^{2} \to \infty$, $\frac{1}{n} \cdot n^{2} = n \to \infty$.
>
> Por eso, ante una forma indeterminada hay que **reescribir** la sucesión (racionalizar, factorizar, dividir entre la mayor potencia) antes de aplicar los teoremas, como en el Ejemplo 4 de [[Sucesiones Convergentes]] ($\sqrt{ n+1 } - \sqrt{ n } \to 0$) o el Ejemplo 1 de esta nota.

### Sucesiones y funciones

Si tenemos una función $f:I\to \mathbb{R}$ y una sucesión $\{ x_{n} \}$ de puntos de $I$ que converge a $x_{0}$, obtenemos una nueva sucesión $\{ y_{n} \} = \{ f(x_{n}) \}$. Si $f$ es [[Continuidad|continua]], esta converge a $f(x_{0})$. Este teorema es el puente entre sucesiones y funciones que usan los [[Teorema del Valor Intermedio|teoremas fuertes de continuidad]].

> [!theorem] **Teorema.** (Continuidad por Sucesiones)
>
> Sea $f:I\to \mathbb{R}$ continua en $x_{0} \in I$. Si $\{ x_{n} \}$ es una sucesión de puntos de $I$ que converge a $x_{0}$, entonces
> $$
> \lim_{n \to \infty} f(x_{n}) = f(x_{0})
> $$

> [!proof]- **Proof.**
>
> Sea $\varepsilon > 0$. Como $f$ es continua en $x_{0}$, existe $\delta >0$ tal que si $x \in I$ y $\left| x-x_{0} \right|<\delta$, ent. $\left| f(x) - f(x_{0}) \right|<\varepsilon$.
> Como la sucesión $\{ x_{n} \}$ converge a $x_{0}$, usando $\delta$ en lugar de $\varepsilon$ en la def. de convergencia, existe $N \in  \mathbb{N}$ tal que si $n\geq N$ entonces $\left| x_{n} - x_{0} \right| < \delta$, lo que implica que
> $$
> \left| f(x_{n})-f(x_{0}) \right| < \varepsilon  \quad \text{ si } n \geq N \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo 10.**
>
> 1. Si $\lim_{n \to \infty} x_{n} = \alpha$, entonces $\lim_{n \to \infty} \sin(x_{n}) = \sin(\alpha)$.
> 2. Si $\alpha$ y los $x_{n}$ no son de la forma $(2k +1) \frac{\pi}{2}$, ent. $\lim_{n \to \infty} \tan(x_{n}) = \tan(\alpha)$ y $\lim_{n \to \infty} \sec(x_{n}) = \sec(\alpha)$.
> 3. Si $\alpha$ y los $x_{n}$ no son de la forma $k\pi$, ent. $\lim \csc(x_{n}) = \csc(\alpha)$ y $\lim \cot(x_{n}) = \cot(\alpha)$.
> 4. Si $x_{n} > 0$ para todo $n$ y $\alpha > 0$, entonces $\lim \log \left(x_{n}\right) = \log \left(\alpha\right)$ y $\lim \frac{1}{\sqrt{x_{n}}} = \frac{1}{\sqrt{\alpha}}$.

Un caso particular, con una prueba directa:

> [!theorem] **Proposición.**
>
> Sea $\{ x_{n} \}$ una sucesión nula, entonces $\displaystyle \lim_{n \to \infty} e^{x_{n}} = 1$.

> [!proof]- **Proof.**
>
> (También sale del teorema, pues $\exp$ es continua y $e^{0} = 1$.)
>
> Sea $\varepsilon >0$ y tomemos $\varepsilon' = \log \left(1+\varepsilon \right) \implies \varepsilon' > 0$.
> Como $\{ x_{n} \}$ es una sucesión nula, existe $N \in \mathbb{N}$ tal que si $n \geq N$ ent. $\left| x_{n} \right| < \varepsilon'$. Entonces, como $\exp$ es creciente,
> $$
> e^{\left| x_{n} \right|} < e^{\varepsilon'} = e^{\log \left(1 + \varepsilon \right)} = 1 + \varepsilon \implies e^{\left| x_{n} \right|} - 1 < \varepsilon
> $$
> Sea $n \geq N$, así:
> Caso 1. Sup. $x_{n} \geq 0$,
> Ent. $e^{x_{n}} \geq 1 \implies \left| e^{x_{n}}-1 \right| = e^{\left| x_{n} \right|}-1 <\varepsilon$
> Caso 2. Sup. $x_{n}<0$,
> Ent. $\displaystyle e^{x_{n}}<1 \implies \left| e^{x_{n}}-1 \right|= 1 - e^{-\left| x_{n} \right|} = 1 - \frac{1}{e^{\left| x_{n} \right|}}$. Con $t = e^{\lvert x_{n} \rvert} > 0$ se tiene $1 - \frac{1}{t} \leq t - 1$, pues $(t-1) - \left( 1 - \frac{1}{t} \right) = \frac{(t-1)^{2}}{t} \geq 0$. Entonces,
> $$
> \left| e^{x_{n}} - 1 \right| \leq e^{\left| x_{n} \right|} - 1 < \varepsilon \quad \text{ si } n\geq N \tag*{$\blacksquare$}
> $$

Lo mismo pasa con [[Limites en el Infinito|límites al infinito]] de funciones y sucesiones que tienden a $\infty$:

> [!theorem] **Teorema.**
>
> Sea $f: (a,\infty) \to \mathbb{R}$ tal que $\lim_{x \to \infty} f(x) = \alpha$, $\alpha \in \mathbb{R}$. Si $\{ x_{n} \}$ es una sucesión de puntos de $(a,\infty)$ que diverge a $\infty$, entonces $\displaystyle \lim f(x_{n}) = \alpha$.

> [!proof]- **Proof.**
>
> Tomemos $\varepsilon >0$. Por hip. existe $M > a$ tal que si $x > M$ ent. $\left| f(x) - \alpha \right| < \varepsilon$.
> A su vez, como $x_{n} \to \infty$, existe $N \in \mathbb{N}$ tal que $x_{n} > M$ para $n \geq N$. Ent.
> $$
> \left| f(x_{n}) - \alpha \right| < \varepsilon \quad \text{ si } n \geq N \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo 11.**
>
> - $\displaystyle \lim_{n \to \infty} \left(1 + \frac{y}{n}  \right)^{n} = e^{y} \quad \forall  y \in \mathbb{R}$: con $f(x) = \left( 1 + \frac{y}{x} \right)^{x} = e^{x\log\left( 1 + \frac{y}{x} \right)}$ en $(\lvert y \rvert, \infty)$, por [[Regla de L'Hopital]] $x\log\left( 1 + \frac{y}{x} \right) \to y$, ent. $f(x) \to e^{y}$; y $n \to \infty$.
> - $\displaystyle \lim \frac{1}{e^{n^{2}}} = 0$: $\lim_{x \to \infty} e^{-x} = 0$ y $n^{2} \to \infty$ (Ejemplo 10 de [[Sucesiones Divergentes]]).
> - $\displaystyle \lim \tan^{-1}(x^{n}) = \frac{\pi}{2}$ para $x > 1$: $x^{n} \to \infty$ (Ejemplo 5) y $\lim_{t \to \infty} \tan^{-1}(t) = \frac{\pi}{2}$. (Si $\lvert x \rvert < 1$, ent. $x^{n} \to 0$ y $\tan^{-1}(x^{n}) \to 0$.)
