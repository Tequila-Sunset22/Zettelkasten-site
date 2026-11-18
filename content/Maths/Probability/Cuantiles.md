---
modified: 2026-11-17T22:20:24Z
title: "Cuantiles"
publish: true
type: zettel
date: "2026-11-17"
status: seed
aliases:
 - Cuantil
 - Mediana
 - Funcion Cuantil
tags:
 - probability
cssclasses:
 - romana
---
La [[Esperanza]] y la [[Varianza]] resumen a una v.a. con un par de números, pero no dicen **dónde** se acumula la probabilidad. Los cuantiles responden justo eso: ¿hasta qué valor llevamos acumulado el $25\%$, la mitad, el $90\%$? Y lo interesante es que, si conocemos *todos* los cuantiles, conocemos la distribución completa.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> El cuantil $p$ es el primer punto donde la función de distribución alcanza la altura $p$.

Recordemos que toda [[Funcion de Distribucion Acumulada|función de distribución]] $F$ es no decreciente, continua por la derecha, y va de $0$ (en $-\infty$) a $1$ (en $\infty$). Crece de forma continua o a saltos, y puede quedarse plana en algunos tramos. Esos saltos y tramos planos son los que impiden definir el cuantil simplemente como "$F^{-1}(p)$".

> [!tip|idea]+ **Idea Intuitiva.**
>
> $c_{p}$ es el primer $x$ donde $F$ alcanza la altura $p$. Si $F$ es continua y creciente, $c_{p} = F^{-1}(p)$; si $p$ es la altura de un tramo plano, $c_{p}$ es su inicio; si $p$ cae dentro de un salto, $c_{p}$ es el punto del salto.
> ![[cuantil-generalizado.svg|center|600]]
>
> En movimiento, con la misma $F$: dentro del salto $c_{p}$ se queda quieto, y al pasar $p = 0.3$ brinca de $1$ a $2$.
> <img src="/videos/cuantil-generalizado.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** (Cuantil)
>
> Sea $X$ v.a. con función de distribución $F$ y sea $p \in (0,1]$. El **cuantil** $p$ de $X$ (o de $F$) es el número más pequeño $c_{p}$, si existe, tal que
> $$
> F(c_{p}) \geq p,
> $$
> i.e. $c_{p} = \min \{ x \in \mathbb{R} \mid F(x) \geq p \}$.
>
> Se dice que $c_{p}$ es el *cuantil de orden $p$* o el *cuantil al $100p\%$*. En particular, $c_{0.5}$ es la **mediana** y $c_{0.25}, c_{0.5}, c_{0.75}$ son los **cuartiles**.

> [!observation]+ **Observación.**
>
> 1. Se omite $p = 0$ porque **no** hay un $x$ más pequeño con $F(x) \geq 0$: todos los $x$ cumplen.
> 2. La definición dice "si existe", pero para $p \in (0,1)$ el mínimo **siempre** existe (lo probamos abajo). El único caso problemático es $p = 1$: si $F(x) < 1$ para todo $x$, no hay ningún $x$ con $F(x) \geq 1$, y se conviene en decir que $c_{1} = \infty$. Por eso muchos textos definen los cuantiles solo para $p \in (0,1)$.
> 3. El **mínimo** (no ínfimo) en la definición no es un adorno: que se alcance es justo lo que da la continuidad por la derecha de $F$.

> [!Info]- **Nota!** (Otras notaciones)
>
> - A la función $p \mapsto c_{p}$ se le llama **función cuantil**. Muchos textos la escriben $F^{-1}(p)$ (o $Q(p)$) y la llaman **inversa generalizada** de $F$, aunque $F$ no tenga inversa: coincide con la inversa de verdad cuando esta existe (Corolario de abajo).
> - En estadística se habla de *percentiles* ($c_{0.9}$ es el percentil $90$) y de *deciles* ($c_{0.1}, c_{0.2}, \dots$). Rincón cuenta también a $c_{1}$ entre los cuartiles; lo usual son solo los tres que parten la distribución en cuatro.
> - Para la normal estándar se usa $z_{\alpha}$ para el cuantil al $100(1-\alpha)\%$, i.e. $\Phi(z_{\alpha}) = 1 - \alpha$ (ver [[Distribucion Normal]]).

Con una v.a. discreta se ve por qué la definición pide "$\geq$" y no "$=$":

> [!example]- **Ejemplo 1.** (Discreto)
>
> Sea $X$ con $f(0) = \frac{1}{2}$, $f(1) = \frac{1}{4}$, $f(2) = \frac{1}{4}$. Ent. $F$ es escalonada con $F(0) = 0.5$, $F(1) = 0.75$, $F(2) = 1$, y
> $$
> c_{0.7} = 1, \qquad c_{0.8} = 2, \qquad c_{0.9} = 2.
> $$
> Por ejemplo, $c_{0.7} = 1$ porque $F(0) = 0.5 < 0.7$ pero $F(1) = 0.75 \geq 0.7$. Aquí **no hay** ningún $x$ con $F(x) = 0.7$ ($F$ brinca de $0.5$ a $0.75$), así que pedir la igualdad no funcionaría. Y $0.8$ y $0.9$ caen en el **mismo salto** (el de $x = 2$), así que tienen el mismo cuantil.

> [!example]- **Ejemplo 2.** (Sin $c_{1}$)
>
> Sea $X$ con $f(n) = \frac{1}{2^{n}}$ para $n = 1, 2, \dots$ Ent. $F(n) = 1 - \frac{1}{2^{n}}$, y $c_{p}$ es el menor $n$ con $1 - 2^{-n} \geq p$, i.e. con $n \geq -\log_{2}(1-p)$:
> $$
> c_{p} = \left\lceil -\log_{2}(1-p) \right\rceil, \qquad c_{0.7} = 2, \quad c_{0.8} = 3, \quad c_{0.9} = 4.
> $$
> En cambio $F(n) < 1$ para todo $n$, así que $c_{1}$ no existe.

### Existencia del cuantil

Antes de seguir usando $c_{p}$ conviene demostrar que de verdad existe. La clave es ver cómo es el conjunto de puntos que "ya llegaron" a la altura $p$.

> [!tip|idea]- **Idea Intuitiva.**
>
> Como $F$ no decrece, $\{ x \mid F(x) \geq p \}$ es una semirrecta; la continuidad por la derecha hace que incluya a su extremo.

> [!theorem] **Proposición.** (Existencia del cuantil)
>
> Sea $F$ una función de distribución y sea $p \in (0,1)$. Ent. el conjunto $A_{p} = \{ x \in \mathbb{R} \mid F(x) \geq p \}$ es de la forma
> $$
> A_{p} = [c_{p}, \infty)
> $$
> para algún $c_{p} \in \mathbb{R}$. En particular $c_{p}$ existe, y para todo $x \in \mathbb{R}$,
> $$
> F(x) \geq p \iff x \geq c_{p}.
> $$

> [!proof]- **Proof.**
>
> **Borrador.** Hay que ver que $A_{p}$ no es vacío, que está acotado por abajo (para que tenga ínfimo), que es "cerrado hacia arriba" (por monotonía) y que contiene a su ínfimo (por continuidad por la derecha).
>
> **Proof.**
> 1. *No vacío:* como $\displaystyle \lim_{ x \to \infty } F(x) = 1 > p$, existe $x$ con $F(x) > p$, i.e. $x \in A_{p}$.
> 2. *Acotado por abajo:* como $\displaystyle \lim_{ x \to -\infty } F(x) = 0 < p$, existe $M$ tq. $F(x) < p$ para todo $x \leq M$. Ent. ningún $x \leq M$ está en $A_{p}$, y $M$ es cota inferior. Sea $c_{p} = \inf A_{p} \in \mathbb{R}$ (existe por el axioma del supremo).
> 3. *Hacia arriba:* si $x \in A_{p}$ y $y \geq x$, como $F$ no decrece, $F(y) \geq F(x) \geq p$, i.e. $y \in A_{p}$. Ent. $(c_{p}, \infty) \subseteq A_{p}$: si $y > c_{p}$, por def. de ínfimo hay $x \in A_{p}$ con $x < y$.
> 4. *Contiene al ínfimo:* la sucesión $x_{n} = c_{p} + \frac{1}{n}$ está en $A_{p}$ (por 3), así que $F(x_{n}) \geq p$ para todo $n \geq 1$. Por continuidad por la derecha,
> $$
> F(c_{p}) = \lim_{ n \to \infty } F\left( c_{p} + \frac{1}{n} \right) \geq p,
> $$
> i.e. $c_{p} \in A_{p}$, y ningún punto menor que $c_{p}$ está en $A_{p}$ (es el ínfimo).
>
> $\therefore$ $A_{p} = [c_{p}, \infty)$, y la equivalencia $F(x) \geq p \iff x \geq c_{p}$ es solo reescribir $x \in A_{p}$. $\blacksquare$

Cuando $F$ no tiene saltos, la desigualdad de la definición se vuelve igualdad, y si además no tiene tramos planos, el cuantil es la inversa de toda la vida:

> [!theorem] **Corolario.** (Caso continuo)
>
> Sea $p \in (0,1)$.
> 1. Si $F$ es continua, ent. $F(c_{p}) = p$.
> 2. Si además $F$ es estrictamente creciente, ent. $c_{p} = F^{-1}(p)$.

> [!proof]- **Proof.**
>
> 1. Por la Proposición, $F(c_{p}) \geq p$ y $F(x) < p$ para todo $x < c_{p}$. Como $F$ es continua,
> $$
> F(c_{p}) = \lim_{ x \to c_{p}^{-} } F(x) \leq p.
> $$
> Ent. $F(c_{p}) = p$. $\blacksquare$
> 2. Si $F$ es continua y estrictamente creciente, es inyectiva, y por 1 $c_{p}$ es el único $x$ con $F(x) = p$, i.e. $c_{p} = F^{-1}(p)$. $\blacksquare$

En la práctica, para una v.a. continua el cuantil se encuentra despejando $F(c_{p}) = p$:

> [!example]- **Ejemplo 3.** (Exponencial: la mediana no es la media)
>
> Sea $X \sim \operatorname{Exp}(\lambda)$ ([[Distribucion Exponencial]]), con $F(x) = 1 - e^{-\lambda x}$ para $x \geq 0$. En $[0, \infty)$, $F$ es continua y estrictamente creciente, así que
> $$
> \begin{align}
> 1 - e^{-\lambda c_{p}} = p &\iff e^{-\lambda c_{p}} = 1 - p \\[0.5em]
> &\iff c_{p} = -\frac{1}{\lambda}\ln(1-p)
> \end{align}
> $$
> En particular la mediana es $c_{0.5} = \frac{\ln 2}{\lambda} \approx \frac{0.693}{\lambda}$, **menor** que la media $\operatorname{E}(X) = \frac{1}{\lambda}$: la cola larga a la derecha jala a la media, pero no a la mediana. Y $c_{1} = \infty$, pues $F(x) < 1$ siempre.

> [!example]- **Ejemplo 4.** (Despejando)
>
> Sea $F(x) = 1 - \cos x$ para $0 \leq x \leq \frac{\pi}{2}$ ($0$ antes, $1$ después). En $[0, \frac{\pi}{2}]$, $F$ es continua y estrictamente creciente, así que $1 - \cos c_{p} = p$, i.e.
> $$
> c_{p} = \arccos(1-p), \qquad c_{0.25} \approx 0.723, \quad c_{0.5} = \frac{\pi}{3}, \quad c_{0.75} \approx 1.318.
> $$

### La mediana

La mediana $c_{0.5}$ es "el centro" de la distribución, y a diferencia de la esperanza siempre existe y no la mueven las colas largas (Ejemplo 3). Pero con v.a.s discretas puede dar una sorpresa:

> [!example]- **Ejemplo 5.** (Una mediana "rara")
>
> Sea $X$ con $P(X = -1) = P(X = 1) = \frac{1}{2}$, i.e. $F(x) = \frac{1}{2}$ para $-1 \leq x < 1$. Ent. $F(-1) = \frac{1}{2} \geq \frac{1}{2}$ y $F(x) = 0$ para $x < -1$, así que la mediana es
> $$
> c_{0.5} = -1.
> $$
> Raro, ¿no? Por simetría uno esperaría $0$. Lo que pasa es que $p = \frac{1}{2}$ es la altura de un **tramo plano** de $F$ (todo $[-1, 1)$), y la definición escoge su inicio.

> [!observation]+ **Observación.** (Otra definición de mediana)
>
> En otros textos la mediana se define como **cualquier** $m$ con
> $$
> P(X \leq m) \geq \frac{1}{2} \qquad \text{y} \qquad P(X \geq m) \geq \frac{1}{2},
> $$
> y en el Ejemplo 5 **todo** $m \in [-1, 1]$ cumple las dos: el conjunto de medianas es un intervalo, y $c_{0.5}$ es su extremo izquierdo. Ninguna está mal: con la de cuantiles ganamos que $p \mapsto c_{p}$ sea una función. Pero si te piden "la mediana" de una v.a. discreta, vale la pena preguntar cuál definición usan.

### La función cuantil

Veamos ahora a $p \mapsto c_{p}$ como función. Lo primero es que no puede bajar: pedir más probabilidad acumulada nunca nos regresa a la izquierda.

> [!theorem] **Proposición.** (La función cuantil no decrece)
>
> Si $0 < p_{1} \leq p_{2} \leq 1$ y los cuantiles existen, ent. $c_{p_{1}} \leq c_{p_{2}}$.

> [!proof]- **Proof.**
>
> Si $F(x) \geq p_{2}$ ent. $F(x) \geq p_{1}$, i.e. $A_{p_{2}} \subseteq A_{p_{1}}$. El mínimo de un conjunto más chico es mayor o igual: $c_{p_{1}} = \min A_{p_{1}} \leq \min A_{p_{2}} = c_{p_{2}}$. $\blacksquare$

> [!observation]+ **Observación.** (Saltos y tramos planos se intercambian)
>
> La gráfica de $p \mapsto c_{p}$ es la de $F$ reflejada sobre la recta $y = x$, y al reflejar:
> 1. un **salto** de $F$ en $x_{0}$ (de altura $a$ a altura $b$) se vuelve un **tramo plano** de la función cuantil: $c_{p} = x_{0}$ para todo $p \in (a, b]$;
> 2. un **tramo plano** de $F$ a la altura $p_{0}$ se vuelve un **salto** de la función cuantil en $p_{0}$.
>
> Por eso para una v.a. discreta la función cuantil es escalonada (Ejemplo 1).

La función cuantil importa mucho fuera de la teoría: si $U \sim \operatorname{Unif}(0,1)$, ent. $c_{U}$ tiene distribución $F$. Así, con una sola uniforme se fabrica cualquier distribución (y en particular la función cuantil determina la distribución). La prueba sale directo de la equivalencia $F(x) \geq p \iff x \geq c_{p}$, y junto con su recíproco ($F(X)$ es uniforme si $F$ es continua) está en [[Metodo de la Transformada Inversa]].

---
Siguiente: [[Moda]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 2, §2.9 (pp. 182–186) y sus ejercicios. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
