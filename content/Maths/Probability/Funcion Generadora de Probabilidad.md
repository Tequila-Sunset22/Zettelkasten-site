---
modified: 2026-11-17T22:20:24Z
title: "Función Generadora de Probabilidad"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - f.g.p.
tags:
 - probability
cssclasses:
 - romana
---
Si $X$ toma valores en $\mathbb{N}$, su distribución es una lista de números $P(X=0), P(X=1), P(X=2), \dots$ La idea de la función generadora es **empaquetar** toda esa lista en una sola función: usarlos como coeficientes de una serie de potencias. Lo que se gana es que operaciones incómodas con las probabilidades (sumar v.a.s independientes, calcular momentos) se vuelven álgebra y cálculo con esa función.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> Guardamos toda la distribución en los coeficientes de una serie de potencias.

> [!tip|idea]- **Idea Intuitiva.**
>
> $$
> G(t) = P(X=0) + P(X=1)\,t + P(X=2)\,t^{2} + \cdots
> $$
> La potencia de $t$ marca a qué valor corresponde cada probabilidad, como en las funciones generadoras de [[Combinatoria]].

> [!theorem] **Definición.** (f.g.p.)
>
> Sea $X$ v.a. discreta con valores en $\mathbb{N} = \{ 0, 1, 2, \dots \}$. La **función generadora de probabilidad** de $X$ es
> $$
> G(t) = \operatorname{E}(t^{X}) = \sum_{x=0}^{\infty} t^{x} P(X = x),
> $$
> para los $t \in \mathbb{R}$ donde la serie converge. Se escribe f.g.p., y $G_{X}$ si hay que decir de qué v.a. es.

> [!observation]+ **Observación.**
>
> 1. La serie converge (absolutamente) por lo menos para $t \in [-1, 1]$, porque ahí $\lvert t^{x}P(X=x) \rvert \leq P(X=x)$ y $\sum_{x} P(X=x) = 1$ (criterio de comparación). Así que el radio de convergencia es $\geq 1$.
> 2. $G(1) = \sum_{x} P(X = x) = 1$ y $G(0) = P(X = 0)$.
> 3. La igualdad $G(t) = \operatorname{E}(t^{X})$ es el [[Esperanza|teorema del estadístico inconsciente]] con $\varphi(x) = t^{x}$.

> [!example]- **Ejemplo 1.** (Bernoulli)
>
> Si $X \sim \operatorname{Ber}(p)$, ent. $G(t) = (1-p) + pt$, un polinomio de grado $1$.

> [!example]- **Ejemplo 2.** (Geométrica desde $1$)
>
> Sea $X$ con $f(x) = \frac{1}{2^{x}}$ para $x = 1, 2, \dots$ No toma el valor $0$, pero eso no importa ($P(X=0) = 0$). Es una serie geométrica:
> $$
> G(t) = \sum_{x=1}^{\infty} \left( \frac{t}{2} \right)^{x} = \frac{t/2}{1 - t/2} = \frac{t}{2-t} \qquad \text{para } \lvert t \rvert < 2.
> $$
> Aquí la serie converge más allá de $[-1,1]$: el radio es $2$.

> [!example]- **Ejemplo 3.** (Uniforme discreta)
>
> Si $f(x) = \frac{1}{n}$ para $x = 0, 1, \dots, n-1$, ent. por la suma geométrica finita, para $t \neq 1$,
> $$
> G(t) = \frac{1}{n}\sum_{x=0}^{n-1} t^{x} = \frac{1 - t^{n}}{n(1-t)}.
> $$

### Recuperar la distribución

El nombre "generadora" viene de que, de $G$, salen todas las probabilidades: son los coeficientes de su serie de Taylor en $0$.

> [!theorem] **Proposición.** (Fórmula de inversión)
>
> Sea $X$ con valores en $\mathbb{N}$ y f.g.p. $G$. Para $x \in \mathbb{N}$,
> $$
> P(X = x) = \frac{G^{(x)}(0)}{x!}.
> $$

> [!proof]- **Proof.**
>
> Una serie de potencias se puede derivar término a término dentro de su intervalo de convergencia, que contiene a $(-1,1)$. Derivando $x$ veces,
> $$
> G^{(x)}(t) = \sum_{k=x}^{\infty} k(k-1)\cdots(k-x+1)\, t^{k-x} P(X=k).
> $$
> En $t = 0$ solo sobrevive el término $k = x$ (los demás tienen una potencia positiva de $t$), que vale $x!\,P(X=x)$. $\blacksquare$

Como $G$ cerca de $0$ ya fija todas sus derivadas en $0$, fija también todas las probabilidades: la f.g.p. **caracteriza** la distribución.

> [!theorem] **Corolario.** (Caracterización)
>
> Sean $X, Y$ con valores en $\mathbb{N}$ y $G_{X}(t) = G_{Y}(t)$ para todo $t \in (-s, s)$, con $s > 0$. Ent. $X$ y $Y$ tienen la misma distribución.

> [!proof]- **Proof.**
>
> Si $G_{X} = G_{Y}$ en $(-s,s)$, sus derivadas de todos los órdenes coinciden en $0$, y por la Proposición, $P(X = x) = \frac{G_{X}^{(x)}(0)}{x!} = \frac{G_{Y}^{(x)}(0)}{x!} = P(Y = x)$ para todo $x$. $\blacksquare$

> [!example]- **Ejemplo 4.** (Reconstruir)
>
> En el Ejemplo 2, $G(t) = \frac{t}{2-t}$, y se puede ver por inducción que $G^{(x)}(t) = 2\,x!\,(2-t)^{-x-1}$ para $x \geq 1$. Ent.
> $$
> \frac{G^{(x)}(0)}{x!} = \frac{2}{2^{x+1}} = \frac{1}{2^{x}},
> $$
> que es justo $f(x)$.

### Momentos

Si en vez de evaluar en $0$ evaluamos en $1$, las derivadas de $G$ dan momentos. Pero no los momentos usuales $\operatorname{E}(X^{k})$, sino los **momentos factoriales** $\operatorname{E}(X(X-1)\cdots(X-k+1))$, porque eso es lo que baja al derivar $t^{X}$ $k$ veces.

Hay un detalle: $t = 1$ puede estar en la frontera del intervalo de convergencia (cuando el radio es exactamente $1$, como pasa si $X$ tiene colas pesadas), y ahí no podemos derivar término a término, así que se toma el límite por la izquierda, $G^{(k)}(1^{-}) = \lim_{t \to 1^{-}} G^{(k)}(t)$. Para pasar ese límite adentro de la suma hace falta un lema.

> [!theorem] **Lema.** (de Abel, términos no negativos)
>
> Si $a_{n} \geq 0$ para todo $n$, ent.
> $$
> \lim_{t \to 1^{-}} \sum_{n=0}^{\infty} a_{n}t^{n} = \sum_{n=0}^{\infty} a_{n},
> $$
> donde ambos lados pueden valer $\infty$.

> [!proof]- **Proof.**
>
> Sea $S = \sum a_{n} \in [0,\infty]$ y $g(t) = \sum a_{n}t^{n}$ para $t \in [0,1)$ (si $S = \infty$, $g$ puede valer $\infty$ en algún $t$; el argumento es igual). Como $a_{n} \geq 0$, $g$ es no decreciente en $t$, así que el límite existe.
> - $(\leq)$ Para $t \in [0,1)$, $a_{n}t^{n} \leq a_{n}$, ent. $g(t) \leq S$.
> - $(\geq)$ Para cada $N$, $g(t) \geq \sum_{n=0}^{N} a_{n}t^{n}$, y esa suma finita tiende a $\sum_{n=0}^{N} a_{n}$ cuando $t \to 1^{-}$. Ent. $\lim g(t) \geq \sum_{n=0}^{N} a_{n}$ para todo $N$, y haciendo $N \to \infty$, $\lim g(t) \geq S$. $\blacksquare$

> [!theorem] **Proposición.** (Momentos factoriales)
>
> Sea $X$ con valores en $\mathbb{N}$ y f.g.p. $G$. Para $k \geq 1$,
> $$
> G^{(k)}(1^{-}) = \operatorname{E}\big( X(X-1)\cdots(X-k+1) \big),
> $$
> y uno es finito sii el otro lo es.

> [!proof]- **Proof.**
>
> Para $t \in [0,1)$, derivando término a término (ver la prueba de la fórmula de inversión),
> $$
> G^{(k)}(t) = \sum_{x=k}^{\infty} x(x-1)\cdots(x-k+1)\, P(X=x)\, t^{x-k}.
> $$
> Los coeficientes son $\geq 0$, así que por el Lema de Abel, al tomar $t \to 1^{-}$ queda $\sum_{x} x(x-1)\cdots(x-k+1)P(X=x)$, que es $\operatorname{E}(X(X-1)\cdots(X-k+1))$ por el teorema del estadístico inconsciente (los términos con $x < k$ valen $0$). $\blacksquare$

De ahí salen la esperanza y la varianza, que son lo que más se usa:

> [!theorem] **Corolario.** (Propiedades)
>
> Sea $X$ con valores en $\mathbb{N}$ y f.g.p. $G$.
> 1. $G(1^{-}) = 1$.
> 2. Si $X$ tiene esperanza finita, $\operatorname{E}(X) = G'(1^{-})$.
> 3. Si $X$ tiene varianza finita, $\operatorname{Var}(X) = G''(1^{-}) + G'(1^{-}) - \left[ G'(1^{-}) \right]^{2}$.

> [!proof]- **Proof.**
>
> 1. Es el Lema de Abel con $a_{n} = P(X = n)$: $G(1^{-}) = \sum P(X = n) = 1$. $\blacksquare$
> 2. Es la Proposición con $k = 1$. $\blacksquare$
> 3. Con $k = 2$, $G''(1^{-}) = \operatorname{E}(X^{2}) - \operatorname{E}(X)$, así que
> $$
> \operatorname{Var}(X) = \operatorname{E}(X^{2}) - \operatorname{E}^{2}(X) = G''(1^{-}) + G'(1^{-}) - \left[ G'(1^{-}) \right]^{2}. \tag*{$\blacksquare$}
> $$

> [!example]- **Ejemplo 5.** (Momentos del Ejemplo 2)
>
> Con $G^{(x)}(t) = 2\,x!\,(2-t)^{-x-1}$, en $t = 1$: $G'(1) = 2$, $G''(1) = 4$, $G'''(1) = 12$. Ent.
> $$
> \operatorname{E}(X) = 2, \qquad \operatorname{E}(X^{2}) = 4 + 2 = 6, \qquad \operatorname{Var}(X) = 6 - 4 = 2,
> $$
> y de $G'''(1) = \operatorname{E}(X^{3}) - 3\operatorname{E}(X^{2}) + 2\operatorname{E}(X)$ sale $\operatorname{E}(X^{3}) = 12 + 18 - 4 = 26$.

> [!example]- **Ejemplo 6.** (Otra geométrica)
>
> Sea $f(x) = \frac{2}{3^{x}}$ para $x = 1, 2, \dots$ Ent. $G(t) = \sum_{x \geq 1} 2\left( \frac{t}{3} \right)^{x} = \frac{2t}{3-t}$ para $\lvert t \rvert < 3$, con
> $$
> G'(t) = \frac{6}{(3-t)^{2}}, \qquad G''(t) = \frac{12}{(3-t)^{3}}.
> $$
> En $t = 1$: $\operatorname{E}(X) = \frac{3}{2}$ y $\operatorname{Var}(X) = \frac{3}{2} + \frac{3}{2} - \frac{9}{4} = \frac{3}{4}$.

### Sumas de v.a.s independientes

Aquí es donde la f.g.p. se paga sola: la distribución de una suma de v.a.s independientes es complicada (una convolución), pero su f.g.p. es simplemente el **producto**.

> [!theorem] **Proposición.**
>
> Sean $X, Y$ v.a.s [[Independencia de Variables Aleatorias|independientes]] con valores en $\mathbb{N}$. Ent.
> $$
> G_{X+Y}(t) = G_{X}(t)\,G_{Y}(t).
> $$

> [!proof]- **Proof.**
>
> Como $X$ y $Y$ son indep., también lo son $t^{X}$ y $t^{Y}$, y la esperanza de un producto de v.a.s indep. es el producto de las esperanzas:
> $$
> G_{X+Y}(t) = \operatorname{E}(t^{X}t^{Y}) = \operatorname{E}(t^{X})\operatorname{E}(t^{Y}) = G_{X}(t)G_{Y}(t). \tag*{$\blacksquare$}
> $$

Con la caracterización, para saber la distribución de una suma basta reconocer el producto:

> [!example]- **Ejemplo 7.** (Suma de Poisson)
>
> Si $X \sim \operatorname{Poisson}(\lambda)$,
> $$
> G(t) = \sum_{x=0}^{\infty} t^{x}e^{-\lambda}\frac{\lambda^{x}}{x!} = e^{-\lambda}e^{\lambda t} = e^{-\lambda(1-t)}.
> $$
> Si $X \sim \operatorname{Poisson}(\lambda_{1})$ y $Y \sim \operatorname{Poisson}(\lambda_{2})$ son indep., ent. $G_{X+Y}(t) = e^{-(\lambda_{1}+\lambda_{2})(1-t)}$, que es la f.g.p. de $\operatorname{Poisson}(\lambda_{1}+\lambda_{2})$. Por la caracterización, $X + Y \sim \operatorname{Poisson}(\lambda_{1}+\lambda_{2})$ (el teorema de [[Distribucion de Poisson]], en dos líneas).

> [!example]- **Ejemplo 8.** (Binomial)
>
> Si $X_{1}, \dots, X_{n}$ son indep. $\operatorname{Ber}(p)$, la f.g.p. de la suma es $(1 - p + pt)^{n}$. Desarrollando con el binomio de Newton, el coeficiente de $t^{x}$ es $\binom{n}{x}p^{x}(1-p)^{n-x}$: la suma es $\operatorname{Bin}(n,p)$ (ver [[Distribucion Binomial]]).

> [!Info]- **Nota!** (Relación con la f.g.m.)
>
> Cuando ambas existen, $M(t) = \operatorname{E}(e^{tX}) = G(e^{t})$: la [[Funcion Generadora de Momentos|f.g.m.]] es la f.g.p. evaluada en $e^{t}$. La f.g.m. da momentos usuales y sirve para cualquier v.a.; la f.g.p. da momentos factoriales y solo para valores en $\mathbb{N}$, pero siempre existe en $[-1,1]$.

---
Siguiente: [[Funcion Generadora de Momentos]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 2, §2.11 (pp. 187–194) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
