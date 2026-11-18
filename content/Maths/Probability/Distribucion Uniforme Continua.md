---
modified: 2026-11-18T16:58:57Z
title: "Distribución Uniforme Continua"
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
Es el modelo de "un punto al azar en un intervalo": ninguna zona de $(a,b)$ es preferida, así que la probabilidad de un subintervalo es proporcional a su longitud. Es la base de toda la simulación (ver [[Metodo de la Transformada Inversa]]).<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> [!theorem] **Definición.** ($\operatorname{Unif} (a,b)$ continua)
>
> Sean $a < b$. Decimos que la v.a. $X$ tiene distrib. uniforme continua en el intervalo $(a,b)$, i.e. $X \sim \operatorname{Unif} (a,b)$, cuando su función de densidad es:
> $$
> f(x) =\begin{cases}
>   \displaystyle \frac{1}{b-a} & a < x < b \\[0.5em]
>   0 &  \text{otro caso }
> \end{cases}
> $$

> [!observation]+ **Observación.**
>
> Solo para tenerlo en claro, se puede ver en $f(x)$ que $\operatorname{supp}(X) = [a,b]$. También, recuérdese que $f(x)$ puede verse de forma equivalente con la función indicadora: $f(x) = \frac{1}{b-a} \mathbb{1}_{(a,b)}(x)$.
>
> Como $X$ es continua, usar $P(X<x)$ o $P(X\leq x)$ da lo mismo (ver [[Funcion de Densidad de Probabilidad]]).

![[Pasted image 20261028091746.png|center|300]]

Sea $X \sim \operatorname{Unif} (a,b)$. Veamos sus resultados básicos; primero, su función de distribución. Para $a \leq x \leq b$,
$$
\begin{align}
F_{X} (x) &= P(X \leq x)\\[0.5em]
 &= \int_{-\infty}^{x} f_{X}(u) \, du \\[0.5em]
 &= \int_{a}^{x} \frac{1}{b-a} \, du = \frac{x-a}{b-a}
\end{align}
$$

![[Pasted image 20261028092818.png|center|250]]

> [!theorem] **Teorema.** (Propiedades)
>
> Sea $X \sim \operatorname{Unif}(a,b)$.
> 1. Función de Distribución.
> $$
> F_{X}(x) = \begin{cases}
>   0 & \text{ si } x<a \\
>   \displaystyle \frac{x - a}{b-a} & \text{ si } a\leq x \leq  b \\
>   1 & \text{ si } x >  b
> \end{cases}
> $$
> 2. $\operatorname{E}(X) = \frac{a+b}{2}$ (el punto medio) y $\operatorname{Var}(X) = \frac{(b-a)^{2}}{12}$.
> 3. Si $a \leq c < d \leq b$, $P(c < X < d) = \frac{d - c}{b - a}$: solo importa la longitud.
> 4. Si $\alpha > 0$ y $\beta \in \mathbb{R}$, $\alpha X + \beta \sim \operatorname{Unif}(\alpha a + \beta, \alpha b + \beta)$. En particular, si $U \sim \operatorname{Unif}(0,1)$, $a + (b-a)U \sim \operatorname{Unif}(a,b)$.
> 5. $\operatorname{E}(X^{n}) = \dfrac{b^{n+1} - a^{n+1}}{(n+1)(b-a)}$ y $M(t) = \dfrac{e^{bt} - e^{at}}{t(b-a)}$ para $t \neq 0$.
> 6. ([[Cuantiles]]) $c_{p} = a + p(b - a)$.
> 7. Dados $\mu$ y $\sigma^{2} > 0$, la única uniforme con esa media y varianza es $\operatorname{Unif}(\mu - \sqrt{ 3 }\sigma, \mu + \sqrt{ 3 }\sigma)$.

> [!proof]- **Proof.**
>
> 1. Es la cuenta de arriba, con $F = 0$ antes de $a$ y $F = 1$ después de $b$. $\blacksquare$
> 2. $\operatorname{E}(X) = \frac{1}{b-a}\int_{a}^{b} x\,dx = \frac{b^{2}-a^{2}}{2(b-a)} = \frac{a+b}{2}$, y $\operatorname{E}(X^{2}) = \frac{b^{3}-a^{3}}{3(b-a)} = \frac{a^{2}+ab+b^{2}}{3}$, ent.
> $$
> \operatorname{Var}(X) = \frac{a^{2}+ab+b^{2}}{3} - \frac{(a+b)^{2}}{4} = \frac{a^{2} - 2ab + b^{2}}{12} = \frac{(b-a)^{2}}{12}. \tag*{$\blacksquare$}
> $$
> 3. $F(d) - F(c)$. $\blacksquare$
> 4. Por [[Cambio de Variable Aleatoria|cambio de v.a.]], $f_{\alpha X + \beta}(y) = \frac{1}{\alpha}f_{X}\left( \frac{y-\beta}{\alpha} \right)$, que vale $\frac{1}{\alpha(b-a)}$ en $(\alpha a + \beta, \alpha b + \beta)$ y $0$ fuera. $\blacksquare$
> 5. $\frac{1}{b-a}\int_{a}^{b} x^{n}\,dx$ y $\frac{1}{b-a}\int_{a}^{b} e^{tx}\,dx$. $\blacksquare$
> 6. Despejando $\frac{c_{p} - a}{b-a} = p$ (Corolario de [[Cuantiles]]). $\blacksquare$
> 7. Con 2, $\frac{a+b}{2} = \mu$ y $\frac{b - a}{2\sqrt{ 3 }} = \sigma$: la semiamplitud es $\sqrt{ 3 }\sigma$. $\blacksquare$

> [!example]- **Ejemplo 1.**
>
> Cierta inversión tiene una tasa de rendimiento $X$ efectiva anual, y se sabe que dicha tasa es una v.a. uniforme entre el 25% y el 50%. Si tenemos una inversión inicial de \$100, ¿cuál es la probabilidad de que en un año se haya acumulado más de \$130?
> Comencemos llamando $Y$ a la inversión acumulada: $Y = 100(1+ X)$, y queremos $P(Y \geq 130)$.
> $$
> \begin{align}
> & P(100(1+X) \geq 130) \\[0.5em]
> &= P(X \geq 0.3) \tag{despejando} \\[0.5em]
> &= \int_{0.3}^{\infty} \frac{1}{0.5 - 0.25} \mathbb{1}_{(0.25, 0.5)}(x) \, dx \\[0.5em]
> &= \int_{0.3}^{0.5} 4 \, dx = 0.8 = 80\% \tag*{$\square$}
> \end{align}
> $$
> (O directo con 3: $\frac{0.5 - 0.3}{0.25} = 0.8$.)

Con puntos uniformes se pueden aproximar probabilidades, áreas e integrales por simulación: [[Metodo de Monte Carlo]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3, §3.8 (pp. 248–252) y Ejs. 356–370. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
