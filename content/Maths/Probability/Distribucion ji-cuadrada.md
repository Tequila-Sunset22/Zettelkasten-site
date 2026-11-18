---
modified: 2026-11-17T22:20:24Z
title: "Distribución ji-cuadrada"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Distribucion Chi-cuadrada
 - Ji-cuadrada
tags:
 - probability
cssclasses:
 - romana
---
En estadística casi todo error se mide **al cuadrado**: la varianza muestral, la suma de residuos de una regresión, la distancia entre lo observado y lo esperado en una tabla. Si los errores son normales estándar, la suma de sus cuadrados tiene una distribución fija que solo depende de cuántos sumandos hay. Esa es la ji-cuadrada, y el número de sumandos se llama **grados de libertad**.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> $\chi^{2}(n)$ es la distribución de $Z_{1}^{2} + \dots + Z_{n}^{2}$.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Cada $Z_{i}^{2}$ suele ser chico y a veces grande. Al sumar $n$ de ellos la masa se recorre a la derecha (media $n$) y la forma se acerca a una campana.
> ![[densidad-ji-cuadrada.svg|center|600]]

> [!theorem] **Definición.** ($\chi^{2}(n)$)
>
> Sea $n > 0$. Decimos que la v.a. continua $X$ tiene **distribución ji-cuadrada con $n$ grados de libertad**, y escribimos $X \sim \chi^{2}(n)$, si su función de densidad es
> $$
> f_{X}(x) = \frac{1}{\Gamma(n/2)}\left( \frac{1}{2} \right)^{n/2} x^{n/2-1}e^{-x/2} \cdot \mathbb{1}_{(0,\infty)}(x).
> $$

La fórmula asusta, pero es una vieja conocida: comparándola con la densidad [[Distribucion Gamma|gamma]],
$$
\frac{(\lambda x)^{\alpha-1}}{\Gamma(\alpha)}\lambda e^{-\lambda x} \quad \text{con} \quad \alpha = \frac{n}{2}, \ \lambda = \frac{1}{2},
$$
se ve que $\chi^{2}(n) = \operatorname{Gamma}\left( \frac{n}{2}, \frac{1}{2} \right)$. Así que la ji-cuadrada **hereda** todo lo de la gamma (en particular, $f_{X}$ integra $1$), y lo único nuevo es de dónde sale.

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \chi^{2}(n)$.
> 1. $\operatorname{E}(X^{m}) = 2^{m}\dfrac{\Gamma(n/2 + m)}{\Gamma(n/2)} = n(n+2)\cdots(n+2m-2)$ para $m \in \mathbb{N}$.
> 2. $\operatorname{E}(X) = n$ y $\operatorname{Var}(X) = 2n$.
> 3. $M(t) = \left( \dfrac{1}{1-2t} \right)^{n/2}$ para $t < \frac{1}{2}$.
> 4. ([[Moda]]) Si $n > 2$, la moda es única: $x^{*} = n - 2$. Si $n \leq 2$, $f_{X}$ decrece y no hay moda.
> 5. $\chi^{2}(2) = \operatorname{Exp}\left( \frac{1}{2} \right)$.
> 6. Si $c > 0$, $cX \sim \operatorname{Gamma}\left( \frac{n}{2}, \frac{1}{2c} \right)$.

> [!proof]- **Proof.**
>
> Todo es la gamma con $\alpha = \frac{n}{2}$, $\lambda = \frac{1}{2}$ (Propiedades y Escalamiento de [[Distribucion Gamma]]):
> 1. $\operatorname{E}(X^{m}) = \frac{\Gamma(\alpha+m)}{\Gamma(\alpha)\lambda^{m}} = 2^{m}\frac{\Gamma(n/2+m)}{\Gamma(n/2)}$, y $2^{m}\cdot\frac{n}{2}\left( \frac{n}{2}+1 \right)\cdots\left( \frac{n}{2}+m-1 \right) = n(n+2)\cdots(n+2m-2)$. $\blacksquare$
> 2. $\operatorname{E}(X) = \frac{\alpha}{\lambda} = n$ y $\operatorname{Var}(X) = \frac{\alpha}{\lambda^{2}} = 2n$. $\blacksquare$
> 3. $\left( \frac{\lambda}{\lambda-t} \right)^{\alpha} = \left( \frac{1/2}{1/2-t} \right)^{n/2} = \left( \frac{1}{1-2t} \right)^{n/2}$, para $t < \lambda = \frac{1}{2}$. $\blacksquare$
> 4. $\frac{\alpha-1}{\lambda} = 2\left( \frac{n}{2}-1 \right) = n - 2$, si $\alpha > 1$, i.e. $n > 2$. $\blacksquare$
> 5. $\operatorname{Gamma}(1, \frac{1}{2}) = \operatorname{Exp}(\frac{1}{2})$. $\blacksquare$
> 6. Por el escalamiento de la gamma, $cX \sim \operatorname{Gamma}\left( \frac{n}{2}, \frac{1/2}{c} \right)$. $\blacksquare$

> [!observation]+ **Observación.**
>
> La varianza $2n$ crece con $n$, pero la **desviación relativa** $\frac{\sqrt{ 2n }}{n} = \sqrt{ \frac{2}{n} }$ se va a $0$: con muchos grados de libertad, $\frac{X}{n}$ se concentra cerca de $1$. Es la versión ji-cuadrada de que un promedio de muchos $Z_{i}^{2}$ se acerca a $\operatorname{E}(Z^{2}) = 1$.

### De dónde sale

La definición con una densidad no dice por qué esta distribución importa. La razón es el siguiente resultado, que conecta a la ji-cuadrada con la [[Distribucion Normal|normal]] y explica el nombre "grados de libertad".

> [!tip|idea]- **Idea Intuitiva.**
>
> $Z^{2} \leq x$ sii $-\sqrt{ x } \leq Z \leq \sqrt{ x }$; al derivar, la raíz da el factor $x^{-1/2}$ y $\phi(\sqrt{ x })$ da el $e^{-x/2}$ de la densidad $\chi^{2}(1)$.

> [!theorem] **Proposición.** ($Z^{2}$)
>
> Si $Z \sim \operatorname{N}(0,1)$, ent. $Z^{2} \sim \chi^{2}(1)$.

> [!proof]- **Proof.**
>
> **Borrador.** Para cualquier v.a. continua $X$ y $x > 0$, $F_{X^{2}}(x) = F_{X}(\sqrt{ x }) - F_{X}(-\sqrt{ x })$; se deriva y se usa $\Gamma\left( \frac{1}{2} \right) = \sqrt{ \pi }$.
>
> **Proof.** Para $x > 0$,
> $$
> F_{Z^{2}}(x) = P(-\sqrt{ x } \leq Z \leq \sqrt{ x }) = \Phi(\sqrt{ x }) - \Phi(-\sqrt{ x }),
> $$
> y derivando (regla de la cadena, $\frac{d}{dx}\sqrt{ x } = \frac{1}{2\sqrt{ x }}$, y $\phi$ par),
> $$
> \begin{align}
> & f_{Z^{2}}(x) \\[0.5em]
> &= \frac{\phi(\sqrt{ x }) + \phi(-\sqrt{ x })}{2\sqrt{ x }} = \frac{\phi(\sqrt{ x })}{\sqrt{ x }} \\[0.5em]
> &= \frac{1}{\sqrt{ 2\pi }}x^{-1/2}e^{-x/2} \\[0.5em]
> &= \frac{1}{\Gamma(1/2)}\left( \frac{1}{2} \right)^{1/2}x^{1/2-1}e^{-x/2} \tag{$\Gamma(\frac{1}{2}) = \sqrt{ \pi }$}
> \end{align}
> $$
> que es la densidad $\chi^{2}(1)$ (y $F_{Z^{2}}(x) = 0$ para $x \leq 0$). $\blacksquare$

> [!example]- **Ejemplo 1.**
>
> $P(Z^{2} \leq 1) = P(\lvert Z \rvert \leq 1) = 2\Phi(1) - 1 \approx 0.6827$: la misma cuenta es una pregunta de $\chi^{2}(1)$ o de la normal, según cómo la mires.

Sumando cuadrados independientes se suman los grados de libertad, porque se suman los parámetros de forma de la gamma (con la misma tasa $\frac{1}{2}$):

> [!theorem] **Proposición.** (Suma)
>
> Si $X \sim \chi^{2}(n)$ y $Y \sim \chi^{2}(m)$ son [[Independencia de Variables Aleatorias|independientes]], ent. $X + Y \sim \chi^{2}(n+m)$.

> [!proof]- **Proof.**
>
> Es la suma de gammas con la misma tasa: $\operatorname{Gamma}(\frac{n}{2}, \frac{1}{2}) + \operatorname{Gamma}(\frac{m}{2}, \frac{1}{2}) \sim \operatorname{Gamma}(\frac{n+m}{2}, \frac{1}{2})$ (ver [[Distribucion Gamma]]). O directo con la f.g.m.: $(1-2t)^{-n/2}(1-2t)^{-m/2} = (1-2t)^{-(n+m)/2}$. $\blacksquare$

> [!theorem] **Corolario.**
>
> Si $Z_{1}, \dots, Z_{n}$ son indep. $\operatorname{N}(0,1)$, ent. $Z_{1}^{2} + \dots + Z_{n}^{2} \sim \chi^{2}(n)$.

> [!proof]- **Proof.**
>
> Cada $Z_{i}^{2} \sim \chi^{2}(1)$, son indep. (funciones de v.a.s indep.), y por la Proposición e inducción la suma es $\chi^{2}(1 + \dots + 1) = \chi^{2}(n)$. $\blacksquare$

> [!example]- **Ejemplo 2.** (Con una uniforme)
>
> Si $U \sim \operatorname{Unif}(0,1)$, ent. $-2\ln U \sim \chi^{2}(2)$. En efecto, $-\ln U \sim \operatorname{Exp}(1)$ (ver [[Metodo de la Transformada Inversa]]), y para $x > 0$,
> $$
> P(-2\ln U \leq x) = P\left( -\ln U \leq \tfrac{x}{2} \right) = 1 - e^{-x/2},
> $$
> la función de distribución de $\operatorname{Exp}(\frac{1}{2}) = \chi^{2}(2)$.

Lo que hace a la ji-cuadrada indispensable en estadística es que la **varianza muestral** de datos normales también es una ji-cuadrada, salvo una constante:

> [!theorem] **Proposición.** (Varianza muestral)
>
> Sean $X_{1}, \dots, X_{n}$ indep., cada una $\operatorname{N}(\mu, \sigma^{2})$, y sean $\bar{X} = \frac{1}{n}\sum_{i=1}^{n} X_{i}$ y $S^{2} = \frac{1}{n-1}\sum_{i=1}^{n} (X_{i} - \bar{X})^{2}$. Ent.
> $$
> \frac{(n-1)S^{2}}{\sigma^{2}} \sim \chi^{2}(n-1).
> $$

> [!proof]- **Proof.**
>
> %% Pendiente: prueba cuando esté la nota de vectores aleatorios (independencia de X̄ y S², o una rotación ortogonal del vector normal). %%
> Se escribe $\sum \left( \frac{X_{i}-\mu}{\sigma} \right)^{2} = \frac{(n-1)S^{2}}{\sigma^{2}} + \left( \frac{\bar{X}-\mu}{\sigma/\sqrt{ n }} \right)^{2}$. El lado izquierdo es $\chi^{2}(n)$ y el último término es $\chi^{2}(1)$; si se prueba que los dos sumandos de la derecha son **independientes**, comparando f.g.m. queda que el primero es $\chi^{2}(n-1)$. Esa independencia necesita vectores aleatorios.

> [!observation]+ **Observación.** (Por qué $n-1$)
>
> Hay $n$ cuadrados, pero no son "libres": las desviaciones $X_{i} - \bar{X}$ siempre suman $0$, así que conociendo $n-1$ de ellas la última queda determinada. Se "gastó" un grado de libertad en estimar $\mu$ con $\bar{X}$. Por eso se divide entre $n-1$ en $S^{2}$, y con eso $\operatorname{E}(S^{2}) = \frac{\sigma^{2}}{n-1}\operatorname{E}(\chi^{2}(n-1)) = \sigma^{2}$.

---
Siguiente: [[Distribucion t]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.14 (pp. 278–282) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
