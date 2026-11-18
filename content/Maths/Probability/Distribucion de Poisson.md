---
modified: 2026-11-18T03:32:08Z
title: "Distribución de Poisson"
publish: true
type: zettel
date: "2026-09-01"
status: seed
aliases:
tags:
 - probability
cssclasses:
 - romana
---
Cuenta cuántas veces ocurre un evento **raro** en un intervalo de tiempo o espacio: llamadas a un conmutador en una hora, erratas por página, desintegraciones radiactivas por segundo. No hay un número fijo de "ensayos", solo una tasa promedio $\lambda$.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!tip|idea]- **Idea Intuitiva.**
>
> Parte el intervalo en $n$ pedacitos, con proba. $\frac{\lambda}{n}$ de un evento en cada uno: el total es $\operatorname{Bin}(n, \frac{\lambda}{n})$, y cuando $n \to \infty$ eso es la Poisson (lo probamos abajo).

Sea $X$ el núm. de ocurrencias en el intervalo de tiempo dado. $X$ puede tomar valores $0,1,2,\dots$ y en principio no acotamos estos valores. El parámetro $\lambda > 0$ se interpreta como el núm. promedio de ocurrencias del evento por unidad de tiempo o espacio.

> [!theorem] **Definición.** ($\operatorname{Poisson} (\lambda )$)
>
> Decimos que $X$ tiene distrib. de Poisson con parámetro $\lambda >0$, i.e. $X \sim \operatorname{Poisson} (\lambda )$, si la probabilidad de que $X$ tome un valor entero $x\geq 0$ es:
> $$
> f(x) = \begin{cases}
>   \displaystyle e^{-\lambda }\frac{\lambda ^{x}}{x!} & x = 0,1,2,\dots \\[0.5em]
>   0 & \text{en otro caso } 
> \end{cases}
> $$

> [!observation]+ **Observación.**
>
> Suma $1$ por la serie de la exponencial: $\sum_{x \geq 0}\frac{\lambda^{x}}{x!} = e^{\lambda}$.

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Poisson} (\lambda)$
> 1. $G(t) = e^{-\lambda(1-t)}$ y $M(t) = e^{\lambda(e^{t} - 1)}$.
> 2. $\operatorname{E} (X) = \lambda$
> 3. $\operatorname{Var} (X) = \lambda$

> [!proof]- **Proof.**
>
> 1. $G(t) = \sum_{x} t^{x}e^{-\lambda}\frac{\lambda^{x}}{x!} = e^{-\lambda}e^{\lambda t}$, y $M(t) = G(e^{t})$. $\blacksquare$
> 2. $G'(t) = \lambda G(t)$, ent. $\operatorname{E}(X) = G'(1) = \lambda$ ([[Funcion Generadora de Probabilidad]]). $\blacksquare$
> 3. $G''(1) = \lambda^{2}$, ent. $\operatorname{Var}(X) = \lambda^{2} + \lambda - \lambda^{2} = \lambda$. $\blacksquare$

> [!example]- **Ejemplo 1.**
>
> A un conmutador llegan en promedio $2$ llamadas por minuto. Con $X \sim \operatorname{Poisson}(2)$: $P(X = 0) = e^{-2} \approx 0.135$ y $P(X \geq 2) = 1 - e^{-2}(1 + 2) \approx 0.594$.

La distrib. de Poisson tiene teoremas muy útiles en su práctica. El primero: sumar conteos independientes da otra Poisson, con las tasas sumadas.

> [!theorem] **Teorema.**
>
> Sean $X, Y$ v.a. indep. con distribución $\operatorname{Poisson} (\lambda_{1})$ y $\operatorname{Poisson} (\lambda_{2})$, respectivamente. Ent.
> $$
> X + Y \sim \operatorname{Poisson} (\lambda_{1} + \lambda_{2})
> $$

> [!proof]- **Proof.**
>
> Por la f.g.p., $G_{X+Y}(t) = e^{-\lambda_{1}(1-t)}e^{-\lambda_{2}(1-t)} = e^{-(\lambda_{1}+\lambda_{2})(1-t)}$, y por la caracterización es $\operatorname{Poisson}(\lambda_{1}+\lambda_{2})$ (Ejemplo 7 de [[Funcion Generadora de Probabilidad]]). $\blacksquare$

### Como límite de la binomial

El segundo es el que justifica la Idea Intuitiva y por qué la Poisson aparece en todos lados: muchos ensayos, cada uno con proba. muy chica, dan una Poisson.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Con $np = \lambda$ fijo, las barras de $\operatorname{Bin}(n, \frac{\lambda}{n})$ se pegan a los puntos de $\operatorname{Poisson}(\lambda)$ conforme $n$ crece (aquí $\lambda = 3$).
> <img src="/videos/binomial-poisson.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Teorema.** (Aproximación de Poisson)
>
> Sea $\lambda > 0$ y $X_{n} \sim \operatorname{Bin}(n, \frac{\lambda}{n})$ para $n > \lambda$. Para cada $x = 0, 1, 2, \dots$,
> $$
> \lim_{ n \to \infty } P(X_{n} = x) = e^{-\lambda}\frac{\lambda^{x}}{x!}.
> $$

> [!proof]- **Proof.**
>
> **Borrador.** Se separa la fórmula binomial en tres factores: uno que tiende a $1$, $\frac{\lambda^{x}}{x!}$ fijo, y $\left( 1 - \frac{\lambda}{n} \right)^{n} \to e^{-\lambda}$.
>
> **Proof.** Para $n \geq x$,
> $$
> \begin{align}
> & P(X_{n} = x) \\[0.5em]
> &= \frac{n(n-1)\cdots(n-x+1)}{x!}\left( \frac{\lambda}{n} \right)^{x}\left( 1 - \frac{\lambda}{n} \right)^{n-x} \\[0.5em]
> &= \frac{\lambda^{x}}{x!}\cdot\underbrace{\frac{n}{n}\cdot\frac{n-1}{n}\cdots\frac{n-x+1}{n}}_{\to 1}\cdot\underbrace{\left( 1 - \frac{\lambda}{n} \right)^{n}}_{\to e^{-\lambda}}\cdot\underbrace{\left( 1 - \frac{\lambda}{n} \right)^{-x}}_{\to 1}
> \end{align}
> $$
> El primer corchete es un producto de $x$ factores (fijo) que tienden a $1$, y $\left( 1 + \frac{a}{n} \right)^{n} \to e^{a}$. $\blacksquare$

> [!example]- **Ejemplo 2.**
>
> Un libro de $500$ páginas tiene $300$ erratas repartidas al azar. ¿Proba. de que una página tenga al menos dos? Cada errata cae en esa página con proba. $\frac{1}{500}$, así que el núm. es $\operatorname{Bin}(300, \frac{1}{500}) \approx \operatorname{Poisson}(0.6)$, y $P(X \geq 2) \approx 1 - e^{-0.6}(1 + 0.6) \approx 0.122$.

> [!observation]+ **Observación.**
>
> Si los eventos llegan con tasa $\lambda$ y los tiempos entre llegadas son exponenciales indep., el núm. de eventos en $[0, t]$ es $\operatorname{Poisson}(\lambda t)$: es la conexión entre Poisson, [[Distribucion Exponencial|exponencial]] y [[Distribucion Gamma|gamma]] (proceso de Poisson).

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.7 (pp. 238–247). <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
