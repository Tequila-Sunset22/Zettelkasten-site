---
modified: 2026-11-18T03:32:53Z
title: "Distribución Exponencial"
publish: true
type: zettel
date: "2026-09-01"
status: seed
aliases:
 - Variable Aleatoria Exponencial
tags:
 - probability
cssclasses:
 - romana
---
Es el modelo del tiempo de espera hasta que ocurre un evento que llega "sin avisar": la siguiente llamada, la siguiente desintegración, la falla de una pieza que no se desgasta. Su propiedad clave es que **no tiene memoria**: lo que ya se esperó no cuenta.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!theorem] **Definición.** ($\operatorname{Exp}(\lambda)$)
>
> Sea $\lambda>0$. Decimos que $X \sim \operatorname{Exp} (\lambda)$ si su función de densidad es
> $$
> f_{X}(x) = \lambda e^{-\lambda x} \cdot \mathbb{1}_{[0,\infty)}(x)
> $$
> donde observamos que el soporte es $\operatorname{supp}(X) = [0,\infty)$. $\lambda$ es una **tasa** (eventos por unidad de tiempo).

> [!proof]- **Proof.** (Es función de densidad)
>
> Claramente es función de densidad, pues
> $$
> \forall x \in \mathbb{R} \ \ f_{X}(x) = \lambda e ^{-\lambda x} \mathbb{1}_{[0,\infty)}(x) \geq 0
> $$
> Además,
> $$
> \begin{align}
> \int_{\mathbb{R}} f_{X}(x) \, dx &= \int_{-\infty}^{0} 0 \, dx + \int_{0}^{\infty} \lambda e^{-\lambda x} \, dx \\[0.5em]
>  &= - e ^{-\lambda x} \bigg|_{0}^{\infty} = - (0 - 1) = 1 \tag*{$\blacksquare$}
> \end{align}
> $$

![[Pasted image 20261030092032.png|center|350]]

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Exp} (\lambda)$,
> 1. $F(x) = 1 - e^{-\lambda x}$ para $x \geq 0$, i.e. $P(X > x) = e^{-\lambda x}$.
> 2. $\displaystyle \operatorname{E} (X) = \frac{1}{\lambda}$
> 3. $\displaystyle \operatorname{Var} (X) = \frac{1}{\lambda^{2}}$
> 4. $M(t) = \dfrac{\lambda}{\lambda - t}$ para $t < \lambda$.

> [!proof]- **Proof.**
>
> 1. $\int_{0}^{x} \lambda e^{-\lambda u}\,du = 1 - e^{-\lambda x}$. $\blacksquare$
> 2. Por la fórmula del área de [[Esperanza]] ($X \geq 0$), $\operatorname{E}(X) = \int_{0}^{\infty} e^{-\lambda x}\,dx = \frac{1}{\lambda}$. O por partes, con $u = x$, $dv = \lambda e^{-\lambda x}\,dx$, $v = -e^{-\lambda x}$:
> $$
> \begin{align}
> & \operatorname{E}(X) \\[0.5em]
> &= -xe^{-\lambda x}\bigg|_{0}^{\infty} + \int_{0}^{\infty} e^{-\lambda x} \, dx \\[0.5em]
> &= 0 + \frac{1}{\lambda} \tag*{$\blacksquare$}
> \end{align}
> $$
> 3. $\operatorname{Var} (X) = \operatorname{E} (X^{2}) - \operatorname{E}^{2} (X)$, y el segundo momento es, por partes con $u = x^{2}$ ($du = 2x\,dx$) y $dv = \lambda e^{-\lambda x}\,dx$ ($v = -e^{-\lambda x}$),
> $$
> \begin{align}
> & \operatorname{E}(X^{2}) \\[0.5em]
> &= \int_{0}^{\infty} x^{2}\lambda e^{-\lambda x} \, dx \\[0.5em]
> &= -x^{2}e^{-\lambda x}\bigg|_{0}^{\infty} + \frac{2}{\lambda}\int_{0}^{\infty} x\lambda e^{-\lambda x} \, dx \\[0.5em]
> &= 0 + \frac{2}{\lambda}\operatorname{E}(X) = \frac{2}{\lambda^{2}}
> \end{align}
> $$
> Ent. $\operatorname{Var}(X) = \frac{2}{\lambda^{2}} - \frac{1}{\lambda^{2}} = \frac{1}{\lambda^{2}}$. $\blacksquare$
> 4. $\int_{0}^{\infty} e^{tx}\lambda e^{-\lambda x}\,dx = \frac{\lambda}{\lambda - t}$ si $t < \lambda$. $\blacksquare$

> [!example]- **Ejemplo 1.**
>
> 1. Un estudiante debe llegar a un examen a las 9:00 am y sabe que el tiempo que le toma llegar a la facultad es una v.a. $X \sim \operatorname{Exp}(1)$ (en horas). Si sale a las 8 am de su casa, ¿cuál es la proba. de que llegue a tiempo a su examen? Queremos $P(X \leq 1)$:
> $$
> \int_{0}^{1} e^{-x} \, dx = -e ^{-x} \bigg|_{0}^{1} = -(e^{-1} - e^{0}) \approx 0.6321
> $$
> 2. El tiempo de llegada de un auto de una ciudad $A$ a la ciudad $B$ se modela con $X \sim  \operatorname{Exp} (\frac{1}{3})$ en horas; ¿cuál es la proba. de que llegue entre $1$ y $4$ horas? Conviene separarla, $P(1 \leq X \leq 4) = P(X \leq 4) - P(X \leq 1)$, así que si ya conocemos $F_{X}$ solo evaluamos y restamos jaja:
> $$
> F(4) - F(1) = e^{-1/3} - e^{-4/3} \approx 0.453.
> $$

### Pérdida de memoria

Si una pieza con vida exponencial ya funcionó $s$ horas, la proba. de que dure $t$ horas más es la misma que si fuera nueva: no envejece.

> [!tip|idea]+ **Idea Intuitiva.**
>
> La cola desde $s$, recorrida a $0$ y dividida entre $P(X > s)$, es otra vez la densidad $\operatorname{Exp}(\lambda)$.
> ![[perdida-memoria.svg|center|650]]

> [!theorem] **Proposición.** (Pérdida de memoria)
>
> Sea $X \sim \operatorname{Exp}(\lambda)$. Para todos $s, t \geq 0$,
> $$
> P(X > s + t \mid X > s) = P(X > t).
> $$

> [!proof]- **Proof.**
>
> Como $(X > s + t) \subseteq (X > s)$, por la Propiedad 1,
> $$
> P(X > s + t \mid X > s) = \frac{e^{-\lambda(s+t)}}{e^{-\lambda s}} = e^{-\lambda t} = P(X > t). \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> 1. Es la **única** distribución continua (con valores $\geq 0$) sin memoria: $g(x) = P(X > x)$ cumple $g(s + t) = g(s)g(t)$ y es monótona, y las únicas soluciones son $g(x) = e^{-\lambda x}$. Equivale a tasa de falla constante (ver [[Distribucion Weibull]]).
> 2. Su análogo discreto es la [[Distribucion Geometrica|geométrica]], y de hecho la **parte entera** de una exponencial es geométrica: $P(\lfloor X \rfloor = k) = P(k \leq X < k+1) = e^{-\lambda k}(1 - e^{-\lambda})$, que es $\operatorname{Geo}(p)$ con $p = 1 - e^{-\lambda}$.

> [!example]- **Ejemplo 2.**
>
> Un foco con vida $\operatorname{Exp}(\frac{1}{1000})$ (horas) ya lleva $2000$ horas prendido. La proba. de que dure otras $500$ es $e^{-0.5} \approx 0.607$, la misma que para uno nuevo. (Un foco de verdad sí se desgasta; para eso está la [[Distribucion Weibull|Weibull]].)

La suma de exponenciales indep. con la misma tasa es una [[Distribucion Gamma|gamma]], y la mediana y la simulación de la exponencial están en [[Cuantiles]] y [[Metodo de la Transformada Inversa]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.9 (pp. 253–257). <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
