---
modified: 2026-11-17T22:20:24Z
title: "Distribución Gamma"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Variable Aleatoria Gamma
 - Distribucion Erlang
tags:
 - probability
cssclasses:
 - romana
---
La [[Distribucion Exponencial|exponencial]] modela cuánto esperamos a que ocurra **un** evento (que llegue un cliente, que falle una pieza). ¿Y si esperamos a que ocurran **varios**? El tiempo hasta el tercer cliente es la suma de tres esperas exponenciales, y su distribución ya no es exponencial: es una gamma. La familia gamma generaliza esa idea a un número de eventos $\alpha > 0$ no necesariamente entero, y para eso necesita una función que extienda al factorial.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> La exponencial espera un evento; la gamma espera $\alpha$ de ellos.

La herramienta es la [[Funcion Gamma]], $\Gamma(\alpha) = \int_{0}^{\infty} t^{\alpha-1}e^{-t}\,dt$ para $\alpha > 0$. De ella solo usaremos:

> [!Info]- **Nota!** (Lo que usamos de $\Gamma$)
>
> 1. $\Gamma(\alpha+1) = \alpha\,\Gamma(\alpha)$, y en particular $\Gamma(n+1) = n!$ para $n \in \mathbb{N}$.
> 2. Con $t = \lambda x$, para $\alpha, \lambda > 0$,
> $$
> \int_{0}^{\infty} x^{\alpha-1}e^{-\lambda x} \, dx = \frac{\Gamma(\alpha)}{\lambda^{\alpha}}.
> $$
>
> Las pruebas, $\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$ y dónde más aparece $\Gamma$, están en [[Funcion Gamma]].

Con $\Gamma$ en la mano, normalizar $x^{\alpha-1}e^{-\lambda x}$ para que integre $1$ es inmediato, y eso es toda la definición.

> [!tip|idea]+ **Idea Intuitiva.**
>
> $\alpha$ da la forma: decreciente si $\alpha \leq 1$, con una joroba que se recorre a la derecha si $\alpha > 1$. $\lambda$ es una tasa: solo reescala el eje $x$. En la figura, $\lambda = 1$:
> ![[densidad-gamma.svg|center|600]]

> [!theorem] **Definición.** ($\operatorname{Gamma}(\alpha, \lambda)$)
>
> Sean $\alpha > 0$ y $\lambda > 0$. Decimos que la v.a. continua $X$ tiene **distribución gamma** con parámetros $\alpha$ y $\lambda$, y escribimos $X \sim \operatorname{Gamma}(\alpha, \lambda)$, si su función de densidad es
> $$
> f_{X}(x) = \frac{(\lambda x)^{\alpha-1}}{\Gamma(\alpha)} \lambda e^{-\lambda x} \cdot \mathbb{1}_{(0,\infty)}(x).
> $$

> [!proof]- **Proof.** (Es función de densidad)
>
> Claramente $f_{X} \geq 0$. Con el cambio $t = \lambda x$ ($dt = \lambda\,dx$),
> $$
> \int_{0}^{\infty} \frac{(\lambda x)^{\alpha-1}}{\Gamma(\alpha)} \lambda e^{-\lambda x} \, dx = \frac{1}{\Gamma(\alpha)} \int_{0}^{\infty} t^{\alpha-1}e^{-t} \, dt = 1. \tag*{$\blacksquare$}
> $$

> [!Info]- **Nota!** (Otras notaciones: tasa contra escala)
>
> Hay dos parametrizaciones, y cada libro y programa escoge una:
>
> | | Parámetros | Densidad ($x > 0$) | $\operatorname{E}(X)$ |
> |---|---|---|---|
> | Esta nota (y Rincón) | forma $\alpha$, **tasa** $\lambda$ | $\dfrac{(\lambda x)^{\alpha-1}}{\Gamma(\alpha)}\lambda e^{-\lambda x}$ | $\dfrac{\alpha}{\lambda}$ |
> | Con escala | forma $\alpha$, **escala** $\theta = \dfrac{1}{\lambda}$ | $\dfrac{x^{\alpha-1}e^{-x/\theta}}{\Gamma(\alpha)\theta^{\alpha}}$ | $\alpha\theta$ |
>
> - R: `dgamma(x, shape = α, rate = λ)` (o `scale = θ`).
> - Python (`scipy.stats.gamma`): `a = α`, `scale = θ`; **no** tiene `rate`. Ojo: `gamma(a=2, scale=3)` no es nuestra $\operatorname{Gamma}(2,3)$ sino $\operatorname{Gamma}(2, \frac{1}{3})$, con media $6$ en vez de $\frac{2}{3}$.
>
> Con la tasa, la gamma queda en la misma notación que nuestra $\operatorname{Exp}(\lambda)$, y la conexión con Poisson (al final) es directa.

> [!observation]+ **Observación.** (Casos particulares)
>
> 1. $\alpha = 1$: $f_{X}(x) = \lambda e^{-\lambda x}$, i.e. $\operatorname{Gamma}(1, \lambda) = \operatorname{Exp}(\lambda)$.
> 2. $\alpha = n \in \mathbb{N}^{+}$: se le llama **distribución Erlang**$(n, \lambda)$, el tiempo hasta el $n$-ésimo evento (lo vemos abajo).
> 3. $\alpha = \frac{n}{2}$, $\lambda = \frac{1}{2}$: es la [[Distribucion ji-cuadrada|ji-cuadrada]] con $n$ grados de libertad, la que aparece en estadística.
> 4. La función de distribución $F(x)$ **no** tiene forma cerrada en general (la excepción es el caso Erlang), así que los [[Cuantiles]], incluida la mediana, solo se calculan numéricamente (`qgamma` en R, `gamma.ppf` en Python).

Todos los momentos salen con el mismo truco que normalizó la densidad: $x^{n}$ se "come" dentro del integrando subiendo el exponente, y lo que queda es otra vez una función gamma. Lo mismo pasa con la [[Funcion Generadora de Momentos|f.g.m.]]: $e^{tx}$ solo le resta $t$ a la tasa.

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Gamma}(\alpha, \lambda)$.
> 1. $\displaystyle \operatorname{E}(X^{n}) = \frac{\Gamma(\alpha+n)}{\Gamma(\alpha)\lambda^{n}} = \frac{\alpha(\alpha+1)\cdots(\alpha+n-1)}{\lambda^{n}}$ para $n \in \mathbb{N}$.
> 2. $\displaystyle \operatorname{E}(X) = \frac{\alpha}{\lambda}$ y $\displaystyle \operatorname{Var}(X) = \frac{\alpha}{\lambda^{2}}$.
> 3. $\displaystyle M(t) = \left( \frac{\lambda}{\lambda - t} \right)^{\alpha}$ para $t < \lambda$.
> 4. ([[Moda]]) Si $\alpha > 1$, la moda es única: $x^{*} = \frac{\alpha-1}{\lambda}$. Si $\alpha \leq 1$, $f_{X}$ es estrictamente decreciente en $(0,\infty)$ y no hay moda.

> [!proof]- **Proof.**
>
> 1. Con el cambio $t = \lambda x$ (o directo con la integral de la Nota de arriba),
> $$
> \operatorname{E}(X^{n}) = \frac{\lambda^{\alpha}}{\Gamma(\alpha)} \int_{0}^{\infty} x^{\alpha+n-1} e^{-\lambda x} \, dx = \frac{\lambda^{\alpha}}{\Gamma(\alpha)} \cdot \frac{\Gamma(\alpha+n)}{\lambda^{\alpha+n}} = \frac{\Gamma(\alpha+n)}{\Gamma(\alpha)\lambda^{n}},
> $$
> y aplicando $n$ veces $\Gamma(\beta+1) = \beta\,\Gamma(\beta)$ se obtiene $\Gamma(\alpha+n) = (\alpha+n-1)\cdots(\alpha+1)\,\alpha\,\Gamma(\alpha)$. $\blacksquare$
> 2. Con $n = 1$ y $n = 2$ en 1,
> $$
> \operatorname{Var}(X) = \frac{\alpha(\alpha+1)}{\lambda^{2}} - \frac{\alpha^{2}}{\lambda^{2}} = \frac{\alpha}{\lambda^{2}}. \tag*{$\blacksquare$}
> $$
> 3. Para $t < \lambda$, el integrando es el de la densidad con tasa $\lambda - t > 0$:
> $$
> M(t) = \frac{\lambda^{\alpha}}{\Gamma(\alpha)} \int_{0}^{\infty} x^{\alpha-1} e^{-(\lambda-t)x} \, dx = \frac{\lambda^{\alpha}}{\Gamma(\alpha)} \cdot \frac{\Gamma(\alpha)}{(\lambda-t)^{\alpha}} = \left( \frac{\lambda}{\lambda-t} \right)^{\alpha}.
> $$
> Si $t \geq \lambda$ la integral diverge (el exponente ya no decae). $\blacksquare$
> 4. En $(0,\infty)$, $f_{X} > 0$ y
> $$
> \frac{d}{dx} \ln f_{X}(x) = \frac{d}{dx}\left[ (\alpha-1)\ln x - \lambda x + \text{cte.} \right] = \frac{\alpha-1}{x} - \lambda.
> $$
> Si $\alpha > 1$, es positiva para $x < \frac{\alpha-1}{\lambda}$ y negativa después: máximo único en $x^{*}$. Si $\alpha \leq 1$, es $\leq -\lambda < 0$: $f_{X}$ decrece estrictamente, y el "máximo" se escaparía a $x = 0$, donde $f_{X}(0) = 0$ por definición. $\blacksquare$

### Tasas y sumas

Que $\lambda$ sea una tasa quiere decir que cambiar de unidades (horas a minutos) solo la cambia a ella, nunca a la forma:

> [!theorem] **Proposición.** (Escalamiento)
>
> Sea $X \sim \operatorname{Gamma}(\alpha, \lambda)$ y sea $c > 0$. Ent.
> $$
> cX \sim \operatorname{Gamma}\left( \alpha, \frac{\lambda}{c} \right).
> $$

> [!proof]- **Proof.**
>
> $\varphi(x) = cx$ es continua, estrictamente creciente y con inversa $\varphi^{-1}(y) = \frac{y}{c}$ diferenciable, así que por [[Cambio de Variable Aleatoria|cambio de v.a.]], para $y > 0$,
> $$
> \begin{align}
> & f_{cX}(y) \\[0.5em]
> &= f_{X}\left( \frac{y}{c} \right) \cdot \frac{1}{c} \\[0.5em]
> &= \frac{1}{\Gamma(\alpha)} \left( \frac{\lambda}{c} y \right)^{\alpha-1} \frac{\lambda}{c} e^{-\frac{\lambda}{c} y}
> \end{align}
> $$
> que es la densidad $\operatorname{Gamma}(\alpha, \frac{\lambda}{c})$ (y vale $0$ para $y \leq 0$). $\blacksquare$

> [!example]- **Ejemplo 1.** (Horas a minutos)
>
> Si $X \sim \operatorname{Gamma}(3, 2)$ mide horas ($2$ eventos por hora), la misma espera en minutos es $60X \sim \operatorname{Gamma}(3, \frac{2}{60}) = \operatorname{Gamma}(3, \frac{1}{30})$: $\frac{1}{30}$ de evento por minuto, y la media pasa de $\frac{3}{2}$ horas a $90$ minutos.

Y si esperamos primero $\alpha_{1}$ eventos y luego otros $\alpha_{2}$, **al mismo ritmo**, en total esperamos $\alpha_{1} + \alpha_{2}$:

> [!theorem] **Proposición.** (Suma con la misma tasa)
>
> Sean $X \sim \operatorname{Gamma}(\alpha_{1}, \lambda)$ y $Y \sim \operatorname{Gamma}(\alpha_{2}, \lambda)$ [[Independencia de Variables Aleatorias|independientes]]. Ent.
> $$
> X + Y \sim \operatorname{Gamma}(\alpha_{1} + \alpha_{2}, \lambda).
> $$

> [!proof]- **Proof.**
>
> Para v.a.s indep. la f.g.m. de la suma es el producto de las f.g.m., así que para $t < \lambda$,
> $$
> M_{X+Y}(t) = \left( \frac{\lambda}{\lambda-t} \right)^{\alpha_{1}}\left( \frac{\lambda}{\lambda-t} \right)^{\alpha_{2}} = \left( \frac{\lambda}{\lambda-t} \right)^{\alpha_{1}+\alpha_{2}},
> $$
> que es la f.g.m. de $\operatorname{Gamma}(\alpha_{1}+\alpha_{2}, \lambda)$. Como la f.g.m. (finita en un intervalo alrededor de $0$) determina la distribución, se sigue el resultado. $\blacksquare$

La hipótesis de **misma tasa** es indispensable:

> [!example]- **Ejemplo 2.** (Contraejemplo: tasas distintas)
>
> Sean $X \sim \operatorname{Exp}(1)$ y $Y \sim \operatorname{Exp}(2)$ indep. Para $t < 1$,
> $$
> M_{X+Y}(t) = \frac{1}{1-t} \cdot \frac{2}{2-t}.
> $$
> Sup. que $X + Y \sim \operatorname{Gamma}(\alpha, \lambda)$. Media y varianza tendrían que coincidir: $\frac{\alpha}{\lambda} = 1 + \frac{1}{2} = \frac{3}{2}$ y $\frac{\alpha}{\lambda^{2}} = 1 + \frac{1}{4} = \frac{5}{4}$, de donde $\lambda = \frac{6}{5}$ y $\alpha = \frac{9}{5}$. Pero en $t = \frac{1}{2}$,
> $$
> M_{X+Y}\left( \tfrac{1}{2} \right) = \frac{8}{3} \approx 2.667 \qquad \text{y} \qquad \left( \frac{6/5}{6/5 - 1/2} \right)^{9/5} \approx 2.638,
> $$
> que no coinciden. $\therefore$ $X + Y$ no es gamma, para ningún par de parámetros.

Como la exponencial es $\operatorname{Gamma}(1, \lambda)$, sumando exponenciales una por una sale la interpretación con la que empezamos:

> [!theorem] **Corolario.** (Erlang = suma de exponenciales)
>
> Sean $X_{1}, \dots, X_{n}$ v.a.s indep., cada una $\operatorname{Exp}(\lambda)$. Ent.
> $$
> X_{1} + \dots + X_{n} \sim \operatorname{Gamma}(n, \lambda).
> $$

> [!proof]- **Proof.**
>
> Inducción sobre $n \geq 1$. Para $n = 1$, $\operatorname{Exp}(\lambda) = \operatorname{Gamma}(1, \lambda)$. Sup. $S_{n} = X_{1} + \dots + X_{n} \sim \operatorname{Gamma}(n, \lambda)$ (H.I.). Como $X_{n+1}$ es indep. de $S_{n}$ y es $\operatorname{Gamma}(1,\lambda)$, por la Proposición anterior $S_{n+1} = S_{n} + X_{n+1} \sim \operatorname{Gamma}(n+1, \lambda)$. $\blacksquare$

### Erlang y Poisson

Si los tiempos **entre** eventos consecutivos son $\operatorname{Exp}(\lambda)$ indep., el tiempo hasta el $n$-ésimo evento es $\operatorname{Gamma}(n, \lambda)$. Y "el $n$-ésimo evento ya ocurrió antes de $x$" es lo mismo que "en $[0, x]$ hubo **al menos** $n$ eventos", que es una pregunta de [[Distribucion de Poisson|Poisson]]. Por eso, aunque la gamma en general no tiene $F$ en forma cerrada, la Erlang sí.

> [!tip|idea]- **Idea Intuitiva.**
>
> Si $T_{n}$ es el tiempo hasta el $n$-ésimo evento y $N_{x}$ el núm. de eventos en $[0,x]$, ent. $T_{n} \leq x \iff N_{x} \geq n$: la $F$ de la Erlang es una cola de la Poisson.

> [!theorem] **Proposición.** (Función de distribución Erlang)
>
> Sea $F_{n}$ la función de distribución de $\operatorname{Gamma}(n, \lambda)$ con $n \in \mathbb{N}^{+}$, y sea $F_{0}$ la de la v.a. constante $0$. Para $x > 0$,
> 1. $\displaystyle F_{n}(x) = F_{n-1}(x) - \frac{(\lambda x)^{n-1}}{(n-1)!}e^{-\lambda x}$.
> 2. $\displaystyle F_{n}(x) = 1 - \sum_{k=0}^{n-1} \frac{(\lambda x)^{k}}{k!}e^{-\lambda x} = P(N \geq n)$, con $N \sim \operatorname{Poisson}(\lambda x)$.

> [!proof]- **Proof.**
>
> **Borrador.** En vez de integrar por partes a ciegas, conviene notar que las densidades Erlang son "derivadas que se restan": si $g_{n}$ es la densidad $\operatorname{Gamma}(n, \lambda)$ en $u > 0$ y $h_{n}(u) = \frac{(\lambda u)^{n-1}}{(n-1)!}e^{-\lambda u}$, ent. $h_{n}' = g_{n-1} - g_{n}$.
>
> **Proof.** 1. Para $u > 0$, $g_{n}(u) = \lambda h_{n}(u)$. Si $n \geq 2$, por la regla del producto,
> $$
> \begin{align}
> & h_{n}'(u) \\[0.5em]
> &= \frac{\lambda(\lambda u)^{n-2}}{(n-2)!}e^{-\lambda u} - \frac{\lambda(\lambda u)^{n-1}}{(n-1)!}e^{-\lambda u} \\[0.5em]
> &= g_{n-1}(u) - g_{n}(u)
> \end{align}
> $$
> Integrando de $0$ a $x$ (por el [[Teorema Fundamental de Cálculo|T.F.C.]]) y como $h_{n}(0) = 0$ para $n \geq 2$,
> $$
> \frac{(\lambda x)^{n-1}}{(n-1)!}e^{-\lambda x} = F_{n-1}(x) - F_{n}(x).
> $$
> Si $n = 1$: $F_{1}(x) = 1 - e^{-\lambda x}$ (exponencial) y $F_{0}(x) = 1$ para $x > 0$, así que también $F_{1} = F_{0} - e^{-\lambda x}$. $\blacksquare$
>
> 2. Aplicando 1 repetidas veces (suma telescópica) desde $F_{0}(x) = 1$,
> $$
> F_{n}(x) = 1 - \sum_{k=1}^{n} \frac{(\lambda x)^{k-1}}{(k-1)!}e^{-\lambda x} = 1 - \sum_{k=0}^{n-1} \frac{(\lambda x)^{k}}{k!}e^{-\lambda x}.
> $$
> La suma es $P(N \leq n-1)$ con $N \sim \operatorname{Poisson}(\lambda x)$, así que $F_{n}(x) = P(N \geq n)$. $\blacksquare$

Con esto, las probabilidades de una Erlang se calculan sin integrar:

> [!example]- **Ejemplo 3.** ($\alpha = 2$, $\lambda = 3$)
>
> Sea $X \sim \operatorname{Gamma}(2, 3)$. Por la Proposición, $F(x) = 1 - e^{-3x}(1 + 3x)$ para $x > 0$. Ent.
> 1. $P(X < 1) = 1 - 4e^{-3} \approx 0.8009$.
> 2. $P(X \geq 2) = e^{-6}(1 + 6) = 7e^{-6} \approx 0.0174$.
> 3. $\displaystyle P(X < 1 \mid X < 2) = \frac{P(X<1)}{P(X<2)} = \frac{1 - 4e^{-3}}{1 - 7e^{-6}} \approx 0.8150$.
> 4. $P(1 \leq X \leq 2 \mid X > 0) = P(1 \leq X \leq 2)$, porque $P(X > 0) = 1$; vale $4e^{-3} - 7e^{-6} \approx 0.1818$.
>
> Sin la fórmula habría que integrar $9xe^{-3x}$ por partes cada vez.

> [!example]- **Ejemplo 4.** (El tercer cliente)
>
> A una tienda llegan clientes con tiempos entre llegadas $\operatorname{Exp}(2)$ indep. (en minutos; $2$ clientes por minuto en promedio). ¿Cuál es la proba. de que el **tercer** cliente llegue antes de $1.5$ minutos?
>
> El tiempo hasta el tercero es $T_{3} \sim \operatorname{Gamma}(3, 2)$ (Corolario), y por la Proposición, con $N \sim \operatorname{Poisson}(2 \cdot 1.5) = \operatorname{Poisson}(3)$:
> $$
> \begin{align}
> & P(T_{3} \leq 1.5) \\[0.5em]
> &= P(N \geq 3) = 1 - e^{-3}\left( 1 + 3 + \frac{9}{2} \right) \\[0.5em]
> &= 1 - 8.5\,e^{-3} \approx 0.5768
> \end{align}
> $$
> En promedio el tercero llega en $\operatorname{E}(T_{3}) = \frac{3}{2}$ minutos, y aun así la proba. de que llegue antes es mayor que $\frac{1}{2}$: la distribución es asimétrica, con la cola a la derecha.

Esta relación es la puerta a los **procesos de Poisson**: eventos que llegan con esperas exponenciales indep., vistos a la vez como tiempos (gamma) y como conteos (Poisson).

---
Siguiente: [[Distribucion Beta]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.10 (pp. 258–262) y sus ejercicios; para la f.g.m., cap. 2, §2.12 (p. 195). <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
