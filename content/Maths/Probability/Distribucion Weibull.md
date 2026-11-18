---
modified: 2026-11-17T22:20:24Z
title: "Distribución Weibull"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Variable Aleatoria Weibull
 - Distribucion Rayleigh
tags:
 - probability
cssclasses:
 - romana
---
La [[Distribucion Exponencial|exponencial]] es el modelo clásico para el tiempo de vida de un componente, pero tiene una propiedad muy poco realista: el componente **no envejece**. Un foco que lleva mil horas encendido tendría la misma proba. de fallar en la próxima hora que uno nuevo. La Weibull arregla eso con un parámetro de forma $\alpha$ que permite que el riesgo de falla crezca con el tiempo (desgaste) o decrezca (defectos de fábrica que fallan pronto). Por eso es el modelo estándar en confiabilidad y durabilidad.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> La Weibull es una exponencial a la que se le permite envejecer.

> [!tip|idea]+ **Idea Intuitiva.**
>
> $\alpha$ da la forma y $\lambda$ reescala: con $\alpha < 1$ hay muchas fallas tempranas, con $\alpha = 1$ es la exponencial, y con $\alpha > 1$ las vidas se concentran alrededor de $\frac{1}{\lambda}$. En la figura, $\lambda = 1$:
> ![[densidad-weibull.svg|center|600]]

> [!theorem] **Definición.** ($\operatorname{Weibull}(\alpha, \lambda)$)
>
> Sean $\alpha > 0$ y $\lambda > 0$. Decimos que la v.a. continua $X$ tiene **distribución Weibull** con parámetros $\alpha$ (forma) y $\lambda$ (escala), y escribimos $X \sim \operatorname{Weibull}(\alpha, \lambda)$, si su función de densidad es
> $$
> f_{X}(x) = \lambda\alpha(\lambda x)^{\alpha-1}e^{-(\lambda x)^{\alpha}} \cdot \mathbb{1}_{(0,\infty)}(x).
> $$

> [!observation]+ **Observación.** (Casos particulares)
>
> 1. $\alpha = 1$: $f_{X}(x) = \lambda e^{-\lambda x}$, i.e. $\operatorname{Weibull}(1,\lambda) = \operatorname{Exp}(\lambda)$.
> 2. $\alpha = 2$, $\lambda = \frac{1}{\sigma\sqrt{ 2 }}$: es la **distribución Rayleigh**$(\sigma)$, con densidad $\frac{x}{\sigma^{2}}e^{-x^{2}/(2\sigma^{2})}$ (la distancia al origen de un punto con coordenadas normales indep.).

> [!Info]- **Nota!** (Otras notaciones)
>
> Lo más común (R, Python, ingeniería) es parametrizar con la **escala** $\eta = \frac{1}{\lambda}$ y la forma $k = \alpha$: $F(x) = 1 - e^{-(x/\eta)^{k}}$. En R, `pweibull(x, shape = α, scale = 1/λ)`; en Python, `scipy.stats.weibull_min(c = α, scale = 1/λ)`. Rincón escribe `pweibull(2,8,2)` y obtiene $0.632 = 1 - e^{-1}$: ese $2$ es la escala $\eta$, i.e. $\lambda = \frac{1}{2}$.

A diferencia de la gamma, la Weibull **sí** tiene función de distribución en forma cerrada, y eso es lo que la hace tan cómoda:

> [!theorem] **Proposición.** (Función de distribución)
>
> Sea $X \sim \operatorname{Weibull}(\alpha, \lambda)$. Ent.
> $$
> F_{X}(x) = \left( 1 - e^{-(\lambda x)^{\alpha}} \right) \mathbb{1}_{(0,\infty)}(x).
> $$
> En particular $f_{X}$ es, efectivamente, una función de densidad.

> [!proof]- **Proof.**
>
> Para $x > 0$, con el cambio $u = (\lambda y)^{\alpha}$ ($du = \lambda\alpha(\lambda y)^{\alpha-1}\,dy$),
> $$
> F_{X}(x) = \int_{0}^{x} \lambda\alpha(\lambda y)^{\alpha-1}e^{-(\lambda y)^{\alpha}} \, dy = \int_{0}^{(\lambda x)^{\alpha}} e^{-u} \, du = 1 - e^{-(\lambda x)^{\alpha}}.
> $$
> Como $f_{X} \geq 0$ y $F_{X}(x) \to 1$ cuando $x \to \infty$, $f_{X}$ integra $1$. $\blacksquare$

La fórmula de $F$ deja ver qué es realmente una Weibull: una exponencial con el eje deformado por una potencia.

> [!theorem] **Corolario.** (Relación con la exponencial)
>
> $X \sim \operatorname{Weibull}(\alpha, \lambda)$ sii $(\lambda X)^{\alpha} \sim \operatorname{Exp}(1)$. Equivalentemente, si $E \sim \operatorname{Exp}(1)$, ent. $\frac{1}{\lambda}E^{1/\alpha} \sim \operatorname{Weibull}(\alpha, \lambda)$.

> [!proof]- **Proof.**
>
> $(\implies)$ Para $y > 0$, como $x \mapsto (\lambda x)^{\alpha}$ es creciente en $(0,\infty)$,
> $$
> P\left( (\lambda X)^{\alpha} \leq y \right) = P\left( X \leq \frac{y^{1/\alpha}}{\lambda} \right) = 1 - e^{-y},
> $$
> que es la función de distribución de $\operatorname{Exp}(1)$.
> $(\impliedby)$ Si $(\lambda X)^{\alpha} = E \sim \operatorname{Exp}(1)$, ent. $X = \frac{1}{\lambda}E^{1/\alpha}$ y para $x > 0$, $P(X \leq x) = P(E \leq (\lambda x)^{\alpha}) = 1 - e^{-(\lambda x)^{\alpha}}$. $\blacksquare$

Esto es lo que se usa para simularla: con $E = -\ln(1-U)$, $U$ uniforme, sale $\frac{1}{\lambda}(-\ln(1-U))^{1/\alpha}$ (ver [[Metodo de la Transformada Inversa]]). Y también da todos los momentos, porque $X^{n} = \lambda^{-n}E^{n/\alpha}$ y los momentos de $E$ son valores de la [[Funcion Gamma]]:

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Weibull}(\alpha, \lambda)$.
> 1. $\displaystyle \operatorname{E}(X^{n}) = \frac{1}{\lambda^{n}}\Gamma\left( 1 + \frac{n}{\alpha} \right)$ para $n \in \mathbb{N}$.
> 2. $\displaystyle \operatorname{E}(X) = \frac{1}{\lambda}\Gamma\left( 1 + \frac{1}{\alpha} \right)$ y $\displaystyle \operatorname{Var}(X) = \frac{1}{\lambda^{2}}\left[ \Gamma\left( 1 + \frac{2}{\alpha} \right) - \Gamma^{2}\left( 1 + \frac{1}{\alpha} \right) \right]$.
> 3. ([[Cuantiles]]) $\displaystyle c_{p} = \frac{1}{\lambda}\left( -\ln(1-p) \right)^{1/\alpha}$ para $p \in (0,1)$; en particular la mediana es $\frac{1}{\lambda}(\ln 2)^{1/\alpha}$.
> 4. ([[Moda]]) Si $\alpha > 1$, la moda es única: $x^{*} = \frac{1}{\lambda}\left( \frac{\alpha-1}{\alpha} \right)^{1/\alpha}$. Si $\alpha \leq 1$, $f_{X}$ decrece y no hay moda.

> [!proof]- **Proof.**
>
> 1. Por el Corolario, $X^{n} = \lambda^{-n}E^{n/\alpha}$ con $E \sim \operatorname{Exp}(1)$, y
> $$
> \operatorname{E}(E^{r}) = \int_{0}^{\infty} u^{r}e^{-u} \, du = \Gamma(1 + r) \quad (r > -1). \tag*{$\blacksquare$}
> $$
> 2. Es 1 con $n = 1, 2$ y $\operatorname{Var}(X) = \operatorname{E}(X^{2}) - \operatorname{E}^{2}(X)$. $\blacksquare$
> 3. $F$ es continua y estrictamente creciente en $(0,\infty)$; despejando $1 - e^{-(\lambda c_{p})^{\alpha}} = p$ se obtiene $c_{p}$. Con $p = \frac{1}{2}$, $-\ln\frac{1}{2} = \ln 2$. $\blacksquare$
> 4. En $(0,\infty)$, $\frac{d}{dx}\ln f_{X}(x) = \frac{\alpha-1}{x} - \alpha\lambda^{\alpha}x^{\alpha-1}$. Si $\alpha > 1$, se anula sii $x^{\alpha} = \frac{\alpha-1}{\alpha\lambda^{\alpha}}$, y pasa de positiva a negativa ahí (el primer término decrece y el segundo crece): máximo único en $x^{*}$. Si $\alpha \leq 1$, los dos términos hacen la derivada negativa. $\blacksquare$

> [!example]- **Ejemplo 1.** (Vida de un componente)
>
> La vida $X$ (en horas) de un componente es $\operatorname{Weibull}(2, \frac{1}{1000})$, i.e. escala $\eta = 1000$ horas. Ent.
> - $P(X > 1000) = e^{-1} \approx 0.368$: la escala es el tiempo que sobrevive el $36.8\%$, para cualquier $\alpha$.
> - $\operatorname{E}(X) = 1000\,\Gamma\left( \frac{3}{2} \right) = 1000 \cdot \frac{\sqrt{ \pi }}{2} \approx 886.2$ horas.
> - La mediana es $1000\sqrt{ \ln 2 } \approx 832.6$ horas y la moda $1000\sqrt{ \tfrac{1}{2} } \approx 707.1$ horas.

### Tasa de falla

La forma de medir "envejecer" es la **tasa de falla**: la proba. (por unidad de tiempo) de fallar justo ahora, sabiendo que se ha sobrevivido hasta ahora.

> [!tip|idea]- **Idea Intuitiva.**
>
> Habiendo sobrevivido hasta $x$, la proba. de fallar en $(x, x+h]$ es aprox. $h\,\frac{f(x)}{1 - F(x)}$.

> [!theorem] **Definición.** (Tasa de falla)
>
> Sea $X > 0$ v.a. continua con densidad $f$ y función de distribución $F$. Su **tasa de falla** es
> $$
> h(x) = \frac{f(x)}{1 - F(x)} \qquad \text{para } x > 0 \text{ con } F(x) < 1.
> $$

> [!theorem] **Proposición.**
>
> Si $X \sim \operatorname{Weibull}(\alpha, \lambda)$, ent. $h(x) = \alpha\lambda(\lambda x)^{\alpha-1}$. En particular:
> 1. $\alpha < 1$: $h$ decrece (el riesgo baja con el tiempo).
> 2. $\alpha = 1$: $h \equiv \lambda$ es constante (la exponencial no envejece).
> 3. $\alpha > 1$: $h$ crece (desgaste).

> [!proof]- **Proof.**
>
> Para $x > 0$, $1 - F(x) = e^{-(\lambda x)^{\alpha}}$, así que
> $$
> h(x) = \frac{\lambda\alpha(\lambda x)^{\alpha-1}e^{-(\lambda x)^{\alpha}}}{e^{-(\lambda x)^{\alpha}}} = \alpha\lambda(\lambda x)^{\alpha-1},
> $$
> una potencia de $x$ con exponente $\alpha - 1$, de donde salen los tres casos. $\blacksquare$

> [!example]- **Ejemplo 2.** (Desgaste)
>
> En el Ejemplo 1 ($\alpha = 2$, $\lambda = \frac{1}{1000}$), $h(x) = \frac{2x}{1000^{2}}$: a las $500$ horas el riesgo es $0.001$ fallas por hora, y a las $1000$ horas ya es el doble. Una exponencial con la misma media tendría riesgo constante $\frac{1}{886.2} \approx 0.00113$ por hora a cualquier edad.

> [!observation]+ **Observación.**
>
> La tasa de falla determina la distribución: integrando, $\int_{0}^{x} h(u)\,du = -\ln(1 - F(x))$, así que $F(x) = 1 - e^{-\int_{0}^{x} h}$. La Weibull es exactamente la familia con tasa de falla **potencia** de $x$, igual que la exponencial es la de tasa constante.

---
Siguiente: [[Distribucion Normal]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.12 (pp. 266–268) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
