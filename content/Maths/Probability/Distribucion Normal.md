---
modified: 2026-11-17T22:20:24Z
title: "Distribución Normal"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Distribucion Gaussiana
 - Normal Estandar
 - Variable Aleatoria Normal
tags:
 - probability
cssclasses:
 - romana
---
Es, probablemente, la distribución más importante de todas. La campana aparece en las estaturas, en los errores de medición, en las calificaciones de un examen, y la razón de fondo es que **sumar muchos efectos pequeños e independientes** produce, casi sin importar cómo sea cada efecto, una normal (eso es el teorema central del límite, que veremos más adelante). Por eso casi toda la estadística clásica está construida sobre ella.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> Dos números, el centro $\mu$ y el ancho $\sigma$, describen toda la campana.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Máxima en $\mu$, simétrica, y con colas que decaen como $e^{-x^{2}}$. $\mu$ la recorre, $\sigma$ la abre, y las inflexiones están en $\mu \pm \sigma$.
> ![[densidad-normal.svg|center|600]]

> [!theorem] **Definición.** ($\operatorname{N}(\mu, \sigma^{2})$)
>
> Sean $\mu \in \mathbb{R}$ y $\sigma > 0$. Decimos que la v.a. continua $X$ tiene **distribución normal** (o gaussiana) con parámetros $\mu$ y $\sigma^{2}$, y escribimos $X \sim \operatorname{N}(\mu, \sigma^{2})$, si su función de densidad es
> $$
> f_{X}(x) = \frac{1}{\sqrt{ 2\pi\sigma^{2} }}\, e^{-(x-\mu)^{2}/(2\sigma^{2})}, \qquad x \in \mathbb{R}.
> $$
> Si $\mu = 0$ y $\sigma^{2} = 1$ se llama **normal estándar**, y se acostumbra denotarla con $Z$, su densidad con $\phi(z) = \frac{1}{\sqrt{ 2\pi }}e^{-z^{2}/2}$ y su función de distribución con $\Phi$.

> [!proof]- **Proof.** (Es función de densidad)
>
> Claramente $f_{X} > 0$. Con el cambio $z = \frac{x-\mu}{\sigma}$ ($dz = \frac{dx}{\sigma}$) y la [[Integral Gaussiana]],
> $$
> \int_{-\infty}^{\infty} \frac{1}{\sqrt{ 2\pi\sigma^{2} }}\, e^{-(x-\mu)^{2}/(2\sigma^{2})} \, dx = \frac{1}{\sqrt{ 2\pi }}\int_{-\infty}^{\infty} e^{-z^{2}/2} \, dz = 1. \tag*{$\blacksquare$}
> $$

> [!Info]- **Nota!** (Otras notaciones)
>
> - El segundo parámetro es la **varianza** $\sigma^{2}$: $\operatorname{N}(5, 10)$ tiene desviación estándar $\sqrt{ 10 }$, no $10$.
> - R y Python usan la **desviación estándar**: `dnorm(x, μ, σ)`, `scipy.stats.norm(loc = μ, scale = σ)`. Es el error más común al pasar de la notación a la computadora.

El cambio de variable de esa prueba es el resultado más útil de la nota: **toda** normal es una normal estándar recorrida y reescalada.

> [!theorem] **Proposición.** (Estandarización)
>
> 1. Si $X \sim \operatorname{N}(\mu, \sigma^{2})$, ent. $Z = \frac{X - \mu}{\sigma} \sim \operatorname{N}(0,1)$.
> 2. Si $Z \sim \operatorname{N}(0,1)$, ent. $X = \mu + \sigma Z \sim \operatorname{N}(\mu, \sigma^{2})$.

> [!proof]- **Proof.**
>
> 1. $\varphi(x) = \frac{x-\mu}{\sigma}$ es creciente con inversa $\varphi^{-1}(z) = \mu + \sigma z$, de derivada $\sigma$. Por [[Cambio de Variable Aleatoria|cambio de v.a.]],
> $$
> f_{Z}(z) = f_{X}(\mu + \sigma z) \cdot \sigma = \frac{\sigma}{\sqrt{ 2\pi\sigma^{2} }}e^{-(\sigma z)^{2}/(2\sigma^{2})} = \frac{1}{\sqrt{ 2\pi }}e^{-z^{2}/2}. \tag*{$\blacksquare$}
> $$
> 2. Igual, con $\varphi(z) = \mu + \sigma z$ y $(\varphi^{-1})'(x) = \frac{1}{\sigma}$: $f_{X}(x) = \phi\left( \frac{x-\mu}{\sigma} \right)\frac{1}{\sigma}$, que es la densidad $\operatorname{N}(\mu, \sigma^{2})$. $\blacksquare$

> [!theorem] **Corolario.**
>
> Si $X \sim \operatorname{N}(\mu, \sigma^{2})$ y $a \neq 0$, $b \in \mathbb{R}$, ent. $aX + b \sim \operatorname{N}(a\mu + b, a^{2}\sigma^{2})$.

> [!proof]- **Proof.**
>
> $aX + b = (a\mu + b) + a\sigma Z$ con $Z$ estándar. Si $a > 0$ es el inciso 2 con $\mu' = a\mu + b$ y $\sigma' = a\sigma$; si $a < 0$, $-Z$ también es estándar (por simetría de $\phi$) y $aX + b = (a\mu + b) + \lvert a \rvert\sigma(-Z)$. $\blacksquare$

Con $X = \mu + \sigma Z$, todo lo de $X$ se reduce a calcularlo para $Z$:

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{N}(\mu, \sigma^{2})$.
> 1. $f_{X}$ es simétrica respecto a $\mu$: $f_{X}(\mu + x) = f_{X}(\mu - x)$.
> 2. $\operatorname{E}(X) = \mu$ y $\operatorname{Var}(X) = \sigma^{2}$.
> 3. La [[Moda]] y la mediana (ver [[Cuantiles]]) son $\mu$.
> 4. $f_{X}$ tiene puntos de inflexión en $\mu \pm \sigma$.
> 5. $M(t) = e^{\mu t + \frac{1}{2}\sigma^{2}t^{2}}$ para todo $t \in \mathbb{R}$.
> 6. $\operatorname{E}\left( (X-\mu)^{n} \right) = 0$ si $n$ es impar, y $(n-1)(n-3)\cdots 3 \cdot 1 \cdot \sigma^{n}$ si $n$ es par.

> [!proof]- **Proof.**
>
> 1. Depende de $x$ solo por $(x-\mu)^{2}$. $\blacksquare$
> 2. $z\phi(z)$ es impar e integrable, así que $\operatorname{E}(Z) = 0$. Por partes ($u = z$, $dv = z\phi(z)\,dz$, $v = -\phi(z)$, pues $\phi' = -z\phi$):
> $$
> \operatorname{E}(Z^{2}) = \int_{-\infty}^{\infty} z^{2}\phi(z) \, dz = -z\phi(z)\bigg|_{-\infty}^{\infty} + \int_{-\infty}^{\infty} \phi(z) \, dz = 1.
> $$
> Ent. $\operatorname{Var}(Z) = 1$, y con $X = \mu + \sigma Z$, $\operatorname{E}(X) = \mu$ y $\operatorname{Var}(X) = \sigma^{2}\operatorname{Var}(Z) = \sigma^{2}$. $\blacksquare$
> 3. El exponente $-\frac{(x-\mu)^{2}}{2\sigma^{2}}$ es máximo sii $x = \mu$: moda única $\mu$. Por 1, $P(X \leq \mu) = P(X \geq \mu) = \frac{1}{2}$, y como $F_{X}$ es continua y estrictamente creciente, $c_{1/2} = \mu$. $\blacksquare$
> 4. Para $Z$: $\phi'(z) = -z\phi(z)$ y $\phi''(z) = (z^{2}-1)\phi(z)$, que cambia de signo exactamente en $z = \pm 1$. Para $X$, $f_{X}(x) = \frac{1}{\sigma}\phi\left( \frac{x-\mu}{\sigma} \right)$, así que la inflexión está en $\frac{x-\mu}{\sigma} = \pm 1$. $\blacksquare$
> 5. Completando el cuadrado, $tz - \frac{z^{2}}{2} = \frac{t^{2}}{2} - \frac{(z-t)^{2}}{2}$, ent.
> $$
> M_{Z}(t) = \int_{-\infty}^{\infty} e^{tz}\phi(z) \, dz = e^{t^{2}/2}\int_{-\infty}^{\infty} \phi(z-t) \, dz = e^{t^{2}/2},
> $$
> y $M_{X}(t) = \operatorname{E}(e^{t(\mu + \sigma Z)}) = e^{\mu t}M_{Z}(\sigma t) = e^{\mu t + \frac{1}{2}\sigma^{2}t^{2}}$. $\blacksquare$
> 6. $(X - \mu)^{n} = \sigma^{n}Z^{n}$. Si $n$ es impar, $z^{n}\phi(z)$ es impar e integrable: $\operatorname{E}(Z^{n}) = 0$. Si $n \geq 2$, por partes como en 2 ($u = z^{n-1}$, $dv = z\phi(z)\,dz$), $\operatorname{E}(Z^{n}) = (n-1)\operatorname{E}(Z^{n-2})$, y desde $\operatorname{E}(Z^{0}) = 1$ se obtiene el producto. $\blacksquare$

> [!example]- **Ejemplo 1.** (Momentos)
>
> Para $X \sim \operatorname{N}(0, \sigma^{2})$: $\operatorname{E}(X^{4}) = 3\sigma^{4}$ y $\operatorname{E}(X^{6}) = 15\sigma^{6}$, mientras que $\operatorname{E}(X^{2001}) = 0$.

### Calcular con $\Phi$

$\Phi(x) = \int_{-\infty}^{x}\phi(z)\,dz$ **no** tiene forma cerrada (la integral gaussiana solo se puede calcular sobre toda la recta), así que se usan tablas o la computadora. Con la estandarización basta una sola tabla para todas las normales:

> [!theorem] **Proposición.**
>
> Sea $X \sim \operatorname{N}(\mu, \sigma^{2})$ y $a < b$. Ent.
> 1. $\displaystyle P(a < X < b) = \Phi\left( \frac{b-\mu}{\sigma} \right) - \Phi\left( \frac{a-\mu}{\sigma} \right)$.
> 2. $\Phi(-x) = 1 - \Phi(x)$ para todo $x$.

> [!proof]- **Proof.**
>
> 1. Los eventos $\{ a < X < b \}$ y $\left\{ \frac{a-\mu}{\sigma} < Z < \frac{b-\mu}{\sigma} \right\}$ son el mismo, con $Z = \frac{X-\mu}{\sigma}$ estándar, y $F_{Z} = \Phi$ es continua. $\blacksquare$
> 2. Como $-Z$ también es estándar, $\Phi(-x) = P(Z \leq -x) = P(-Z \geq x) = P(Z \geq x) = 1 - \Phi(x)$. $\blacksquare$

El inciso 2 es por qué las tablas solo traen $x \geq 0$.

> [!example]- **Ejemplo 2.** (Con la tabla)
>
> Sea $X \sim \operatorname{N}(5, 10)$, i.e. $\sigma = \sqrt{ 10 } \approx 3.162$.
> 1. $P(X \leq 7) = \Phi\left( \frac{2}{\sqrt{ 10 }} \right) = \Phi(0.63) \approx 0.7357$.
> 2. $P(0 < X < 5) = \Phi(0) - \Phi(-1.58) = 0.5 - (1 - 0.9429) \approx 0.4429$.
> 3. $P(X > 10) = 1 - \Phi(1.58) \approx 0.0571$.
>
> (Con la computadora, $0.7365$, $0.4431$ y $0.0569$: la tabla redondea $\frac{2}{\sqrt{ 10 }} = 0.632$ a $0.63$.) Rincón da $0.2357$ para el inciso 2; no coincide con la cuenta, así que parece errata (del libro o del OCR).

El problema inverso, encontrar el $x$ con cierta probabilidad a su izquierda, es buscar un [[Cuantiles|cuantil]]. Para la estándar hay notación propia:

> [!theorem] **Definición.** ($z_{\alpha}$)
>
> Para $\alpha \in (0,1)$, $z_{\alpha}$ es el número tal que $\Phi(z_{\alpha}) = 1 - \alpha$, i.e. el cuantil al $100(1-\alpha)\%$ de $\operatorname{N}(0,1)$: deja una proba. $\alpha$ **a su derecha**.

> [!example]- **Ejemplo 3.** (Valores que conviene saber)
>
> $z_{0.1} \approx 1.2816$, $z_{0.05} \approx 1.6449$, $z_{0.025} \approx 1.96$ y $z_{0.005} \approx 2.5758$. Por simetría, $P(\lvert Z \rvert \leq z_{\alpha/2}) = 1 - \alpha$: el $95\%$ de una normal está a menos de $1.96$ desviaciones de su media, y el $99\%$ a menos de $2.576$.

> [!example]- **Ejemplo 4.** (Regla 68–95–99.7)
>
> Para cualquier $X \sim \operatorname{N}(\mu, \sigma^{2})$, $P(\lvert X - \mu \rvert < k\sigma) = 2\Phi(k) - 1$, que vale
> $$
> 0.6827 \ (k = 1), \qquad 0.9545 \ (k = 2), \qquad 0.9973 \ (k = 3).
> $$
> Casi nada de la probabilidad está a más de $3\sigma$ de la media.

> [!example]- **Ejemplo 5.** (Tiempo para un examen)
>
> El tiempo para terminar un examen es aprox. $\operatorname{N}(30, 25)$ (minutos). ¿Cuánto tiempo hay que dar para que el $95\%$ termine? Buscamos $c_{0.95} = 30 + 5z_{0.05} \approx 30 + 5(1.645) \approx 38.2$ minutos.

> [!example]- **Ejemplo 6.** (La normal sí "envejece")
>
> La vida de un componente es aprox. $\operatorname{N}(20000, 500^{2})$ horas. Ent. $P(X > 21000) = 1 - \Phi(2) \approx 0.0228$. Sabiendo que ya duró $21000$ horas, la proba. de que dure $500$ más es
> $$
> \frac{P(X > 21500)}{P(X > 21000)} = \frac{1 - \Phi(3)}{1 - \Phi(2)} \approx 0.0593,
> $$
> i.e. sobrevivir $500$ horas más se vuelve **menos** probable conforme el componente envejece: a las $20000$ horas (su media) la proba. de llegar a $20500$ es $\frac{1 - \Phi(1)}{1 - \Phi(0)} \approx 0.317$, y a las $21000$ la de llegar a $21500$ ya es $0.059$. Con una [[Distribucion Exponencial|exponencial]] las dos cosas serían iguales (pérdida de memoria); la normal tiene tasa de falla creciente (ver [[Distribucion Weibull]]).

### Sumas de normales

La propiedad que hace a la normal tan cómoda en estadística: sumar normales independientes da otra normal, y los parámetros simplemente se suman.

> [!theorem] **Proposición.** (Suma)
>
> Sean $X_{1} \sim \operatorname{N}(\mu_{1}, \sigma_{1}^{2})$ y $X_{2} \sim \operatorname{N}(\mu_{2}, \sigma_{2}^{2})$ [[Independencia de Variables Aleatorias|independientes]]. Ent.
> $$
> X_{1} + X_{2} \sim \operatorname{N}(\mu_{1}+\mu_{2}, \sigma_{1}^{2}+\sigma_{2}^{2}).
> $$

> [!proof]- **Proof.**
>
> Por independencia la f.g.m. de la suma es el producto, y por la Propiedad 5,
> $$
> M_{X_{1}+X_{2}}(t) = e^{\mu_{1}t + \frac{1}{2}\sigma_{1}^{2}t^{2}}\, e^{\mu_{2}t + \frac{1}{2}\sigma_{2}^{2}t^{2}} = e^{(\mu_{1}+\mu_{2})t + \frac{1}{2}(\sigma_{1}^{2}+\sigma_{2}^{2})t^{2}},
> $$
> la f.g.m. de $\operatorname{N}(\mu_{1}+\mu_{2}, \sigma_{1}^{2}+\sigma_{2}^{2})$. Como la f.g.m. determina la distribución, se sigue. $\blacksquare$

> [!observation]+ **Observación.**
>
> Se suman las **varianzas**, no las desviaciones estándar. Con el Corolario de la estandarización, por inducción: si $X_{1}, \dots, X_{n}$ son indep. $\operatorname{N}(\mu, \sigma^{2})$, el promedio $\bar{X} = \frac{1}{n}\sum X_{i} \sim \operatorname{N}\left( \mu, \frac{\sigma^{2}}{n} \right)$: promediar $n$ mediciones reduce el error típico por $\sqrt{ n }$.

### Qué tan rápido decae la cola

"Casi nada de probabilidad lejos de $\mu$" se puede hacer preciso: la cola $1 - \Phi(x)$ se comporta como $\frac{\phi(x)}{x}$.

> [!theorem] **Proposición.** (Cotas de la cola)
>
> Para todo $x > 0$,
> $$
> \frac{x}{1+x^{2}}\,e^{-x^{2}/2} \leq \int_{x}^{\infty} e^{-u^{2}/2} \, du \leq \frac{1}{x}\,e^{-x^{2}/2}.
> $$

> [!proof]- **Proof.**
>
> **Borrador.** La cota de arriba sale de meter un factor $\frac{u}{x} \geq 1$ para poder integrar. La de abajo: la diferencia entre la integral y la cota es una función que tiende a $0$ en $\infty$ y es decreciente, así que es positiva.
>
> **Proof.** *(Arriba)* Para $u \geq x > 0$, $\frac{u}{x} \geq 1$, ent.
> $$
> \int_{x}^{\infty} e^{-u^{2}/2} \, du \leq \int_{x}^{\infty} \frac{u}{x}\,e^{-u^{2}/2} \, du = \frac{1}{x}\,e^{-x^{2}/2}.
> $$
> *(Abajo)* Sea $g(x) = \int_{x}^{\infty} e^{-u^{2}/2}\,du - \frac{x}{1+x^{2}}e^{-x^{2}/2}$. Derivando (T.F.C. y regla del producto),
> $$
> \begin{align}
> & g'(x) \\[0.5em]
> &= -e^{-x^{2}/2}\left[ 1 + \frac{1-x^{2}}{(1+x^{2})^{2}} - \frac{x^{2}}{1+x^{2}} \right] \\[0.5em]
> &= -e^{-x^{2}/2}\left[ \frac{1}{1+x^{2}} + \frac{1-x^{2}}{(1+x^{2})^{2}} \right] \tag{$1 - \frac{x^{2}}{1+x^{2}}$} \\[0.5em]
> &= -\frac{2\,e^{-x^{2}/2}}{(1+x^{2})^{2}} < 0
> \end{align}
> $$
> Ent. $g$ es decreciente, y como $g(x) \to 0$ cuando $x \to \infty$ (ambos términos tienden a $0$), $g(x) \geq 0$ para todo $x > 0$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Dividiendo entre $\sqrt{ 2\pi }$: $\frac{x}{1+x^{2}}\phi(x) \leq 1 - \Phi(x) \leq \frac{\phi(x)}{x}$, y el cociente de las dos cotas tiende a $1$. Ent. $1 - \Phi(x) \approx \frac{\phi(x)}{x}$ para $x$ grande: la cola decae como $e^{-x^{2}/2}$, muchísimo más rápido que la cola $e^{-\lambda x}$ de una exponencial. Por ejemplo, para $x = 3$ la cota da $1 - \Phi(3) \in [0.00133, 0.00148]$ (el valor real es $0.00135$).

### Transformaciones

Con el [[Cambio de Variable Aleatoria|cambio de v.a.]] salen otras distribuciones importantes:

> [!example]- **Ejemplo 7.** (Lognormal)
>
> Si $X \sim \operatorname{N}(\mu, \sigma^{2})$, ent. $Y = e^{X}$ toma valores en $(0,\infty)$ y, para $y > 0$, $F_{Y}(y) = P(X \leq \ln y) = F_{X}(\ln y)$. Derivando,
> $$
> f_{Y}(y) = \frac{1}{y\sqrt{ 2\pi\sigma^{2} }}\exp\left[ -\frac{(\ln y - \mu)^{2}}{2\sigma^{2}} \right].
> $$
> Es la **distribución lognormal**: el modelo para cantidades que son *producto* de muchos factores (precios, tamaños), igual que la normal lo es para sumas.

> [!example]- **Ejemplo 8.** (Valor absoluto)
>
> Si $X \sim \operatorname{N}(0, \sigma^{2})$ y $Y = \lvert X \rvert$, para $y > 0$, $F_{Y}(y) = P(-y \leq X \leq y) = F_{X}(y) - F_{X}(-y)$, así que $f_{Y}(y) = 2f_{X}(y)$: la mitad positiva de la campana, al doble de altura. Su media es
> $$
> \operatorname{E}(Y) = 2\int_{0}^{\infty} \frac{y}{\sqrt{ 2\pi\sigma^{2} }}e^{-y^{2}/(2\sigma^{2})} \, dy = \sigma\sqrt{ \frac{2}{\pi} },
> $$
> y como $Y^{2} = X^{2}$, $\operatorname{Var}(Y) = \sigma^{2} - \frac{2\sigma^{2}}{\pi}$.

El cuadrado de una normal estándar es la puerta a la estadística: $Z^{2} \sim \chi^{2}(1)$ (ver [[Distribucion ji-cuadrada]]).

---
Siguiente: [[Distribucion ji-cuadrada]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.13 (pp. 269–277) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
