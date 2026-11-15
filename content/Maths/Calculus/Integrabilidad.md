---
modified: 2026-11-15T18:06:57Z
title: "Integrabilidad"
publish: true
type: zettel
date: "2026-07-03"
aliases:
 - Definicion de Integral
tags: 
 - calculus
cssclasses: 
 - romana
---
En el caso continuo ([[Integral de Darboux]]) la integral inferior y la superior siempre coinciden. Para funciones solo **acotadas** ([[Generalizando la Integral]], [[Suma Inferior y Superior]]) ya no, y eso es justo lo que pedimos para llamarla integrable.

> [!tip|idea]- **Idea Intuitiva.**
>
> Todas las sumas inferiores quedan a la izquierda de todas las superiores. Si entre ellas cabe **un solo** número (las sumas inferiores suben hasta donde bajan las superiores), ese número es el área: la integral. Si queda un hueco entre $\sup \mathcal{L}$ e $\inf \mathcal{U}$, no hay un número que merezca llamarse "el área", y decimos que $f$ no es integrable.

> [!theorem] **Def.** (Integral e Integrabilidad)
>
> Una función $f$ acotada en $[a,b]$ es **integrable** en $[a,b]$ si
> $$
> \begin{align}
> & \underline{I} \\[0.5em]
> &= \sup \{ L(f,\mathcal{P}): \mathcal{P} \text{ es partición de } [a,b] \} \\[0.5em]
> &= \inf \{ U(f,\mathcal{P}): \mathcal{P} \text{ es partición de } [a,b] \} \\[0.5em]
> &= \overline{I}.
> \end{align}
> $$
> En este caso, a este número común se le denomina la **integral** (de Darboux) de $f$ en $[a,b]$ y se denota
> $$
> \int_{a}^{b} f \qquad \text{o} \qquad \int_{a}^{b} f(x) \, dx.
> $$
> La integral $\int_{a}^{b} f$ se denomina también el **área** de la región bajo la gráfica cuando $f(x)\geq 0$ para todo $x \in [a,b]$.

Si $f$ es integrable, por el Corolario de [[Suma Inferior y Superior]],
$$
L(f,\mathcal{P})\leq \int_{a}^{b} f \leq U(f,\mathcal{P}) \quad \text{ para todas las particiones } \mathcal{P} \text{ de } [a,b].
$$
Además, el número $\displaystyle \int_{a}^{b} f$ es el **único** con esta propiedad: cualquier $I$ con $L \leq I \leq U$ para toda partición cumple $\underline{I} \leq I \leq \overline{I}$, y estos son iguales.

> [!observation]+ **Observación.**
>
> Para $f$ **continua** esta integral es la de [[Integral de Darboux]]: allá $\sup \mathcal{L}$ y $\inf \mathcal{U}$ coinciden siempre (Lema 4), así que toda continua es integrable y la integral es la misma.

Para discutir a fondo la *integral* es útil disponer del siguiente criterio, que no pide calcular $\sup$ ni $\inf$.

### Criterio $\varepsilon$

> Puedes acercar $U$ y $L$ tanto como quieras!

> [!theorem] **Teorema 2.** (Criterio de integrabilidad $\varepsilon$)
>
> Si $f$ está acotada en $[a,b]$, entonces $f$ es integrable en $[a,b]$ si y solamente si para cada $\varepsilon>0$ existe una partición $\mathcal{P}$ de $[a,b]$ tal que
> $$
> U(f,\mathcal{P}) - L(f,\mathcal{P}) <\varepsilon.
> $$

> [!proof]- **Proof.** 
>
> $(\impliedby)$
> Supongamos primero que para cada $\varepsilon>0$ existe una partición $\mathcal{P}$ con
> $$
> U(f,\mathcal{P}) - L(f,\mathcal{P}) < \varepsilon.
> $$
> Como
> $$
> \begin{align}
> \overline{I} = \inf \{ U(f,\mathcal{P}') \} \leq U(f,\mathcal{P}), \\[0.5em]
> \underline{I} = \sup \{ L(f,\mathcal{P}') \} \geq L(f,\mathcal{P})
> \end{align}
> $$
> resulta que
> $$
> 0 \leq \overline{I} - \underline{I} \leq U(f,\mathcal{P}) - L(f,\mathcal{P}) < \varepsilon
> $$
> Como esto es cierto para todo $\varepsilon>0$, se deduce que $\underline{I} = \overline{I}$; luego, por definición, $f$ es integrable.
>
> $(\implies)$
> Si $f$ es integrable, entonces
> $$
> I = \sup \{ L(f,\mathcal{P}) \} = \inf \{ U(f,\mathcal{P}) \}.
> $$
> Sea $\varepsilon > 0$. Por la caracterización del supremo e ínfimo con $\varepsilon$ ([[Supremo e Infimo]]), *"truco $\frac{\varepsilon}{2}$"*, existen particiones $\mathcal{P}', \mathcal{P}''$ con
> $$
> \begin{align}
> L(f, \mathcal{P}') > I - \frac{\varepsilon}{2} \\[0.5em]
> U(f, \mathcal{P}'') < I + \frac{\varepsilon}{2}
> \end{align}
> $$
> Ahora bien, sea $\mathcal{P} = \mathcal{P}' \cup \mathcal{P}''$, que contiene a $\mathcal{P}'$ y $\mathcal{P}''$. Entonces según el Lema de Refinamiento ([[Suma Inferior y Superior]]),
> $$
> \begin{align}
> U(f,\mathcal{P}) \leq U(f,\mathcal{P}''), \\[0.5em]
> L(f,\mathcal{P}) \geq L(f,\mathcal{P}');
> \end{align}
> $$
> por consiguiente,
> $$
> U(f,\mathcal{P})-L(f,\mathcal{P})\leq U(f,\mathcal{P}'')-L(f,\mathcal{P}')< \left( I + \frac{\varepsilon}{2} \right) - \left( I - \frac{\varepsilon}{2} \right) = \varepsilon. \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Para **calcular** una integral basta encontrar particiones $\mathcal{P}_{n}$ con $U(f,\mathcal{P}_{n}) - L(f,\mathcal{P}_{n}) \to 0$ y un número $I$ con $L(f,\mathcal{P}_{n}) \leq I \leq U(f,\mathcal{P}_{n})$ para todo $n$: por el criterio $f$ es integrable, y por la unicidad, $\int_{a}^{b} f = I$. Es lo que hacemos en los ejemplos.

### Ejemplos

Observamos que surgen dificultades ya sea $f$ discontinua o continua.

> [!example]- **Ejemplo 1:** $f(x) = \begin{cases}0,  & x\neq 1 \\  1,  &x=1.\end{cases}$ 
>
> Sea $f$ la función definida en $[0,2]$ mediante
> $$
> f(x) = \begin{cases}
> 0, & x\neq 1 \\
> 1,  & x = 1.
> \end{cases}
> $$
> Supongamos que $\mathcal{P} = \{ x_{0},\dots,x_{n} \}$ es una partición de $[0,2]$ con
> $$
> x_{j} < 1 < x_{j+1}.
> $$
> Entonces
> $$
> m_{k} = M_{k} = 0 \quad \text{ si } \quad k\neq j,
> $$
> pero $m_{j} = 0$ y $M_{j} =1$.
> Dado
> $$
> \begin{align}
> L(f,\mathcal{P}) &= \sum_{k \neq j} m_{k}(x_{k+1}-x_{k}) + m_{j}(x_{j+1}-x_{j}) = 0, \\[0.5em]
> U(f,\mathcal{P}) &= \sum_{k \neq j} M_{k}(x_{k+1}-x_{k}) + M_{j}(x_{j+1}-x_{j}) = x_{j+1} - x_{j},
> \end{align}
> $$
> obtenemos
> $$
> U(f,\mathcal{P})- L(f,\mathcal{P}) = x_{j+1}-x_{j}
> $$
> Lo cual demuestra que $f$ es integrable: para obtener una partición $\mathcal{P}$ respecto de la cual
> $$
> U(f,\mathcal{P}) - L(f,\mathcal{P}) < \varepsilon,
> $$
> basta tan sólo elegir una partición que verifique
> $$
> x_{j}< 1 < x_{j+1} \quad \text{ y } \quad x_{j+1}-x_{j}<\varepsilon.
> $$
> Además, está claro que
> $$
> L(f,\mathcal{P}) \leq 0 \leq U(f,\mathcal{P}) \quad\text{para todas las particiones } \mathcal{P}.
> $$
> Como $f$ es integrable, existe un único número comprendido entre todas las sumas inferiores y superiores, por lo tanto
> $$
> \int_{0}^{2} f = 0.
> $$

> [!example]+ **Ejemplo 2:** $f(x) = x$
>
> Sea $f(x) = x$, para simplificar consideramos un intervalo $[0,b]$, donde $b>0$. Si $\mathcal{P} = \{ x_{0},\dots,x_{n} \}$ es una partición de $[0,b]$, como $f$ es creciente,
> 
> ![[Pasted image 20260708131523.png|center]]
> 
> $$
> m_{k} = x_{k} \quad \text{ y } \quad M_{k}=x_{k+1}
> $$
> por tanto
> $$
> \begin{align}
> L(f,\mathcal{P}) &= \sum_{k=0}^{n-1} x_{k}(x_{k+1}-x_{k}) \\[0.5em]
> &= x_{0}(x_{1}-x_{0})+ x_{1}(x_{2}-x_{1})+\dots+ x_{n-1}(x_{n}-x_{n-1}) \\[0.5em]
> U(f,\mathcal{P}) &= \sum_{k=0}^{n-1} x_{k+1}(x_{k+1}-x_{k}) \\[0.5em]
> &= x_{1}(x_{1}-x_{0}) + \dots + x_{n}(x_{n}-x_{n-1})
> \end{align}
> $$
> Ninguna de estas fórmulas es particularmente interesante, pero ambas se simplifican considerablemente en el caso de particiones $\mathcal{P}_{n} = \{ x_{0},\dots,x_{n} \}$ con $n$ subintervalos *iguales*.
> En este caso, la longitud $x_{k+1}-x_{k}$ de cada subintervalo es $b / n$, de manera que
> $$
> x_{0} = 0, \quad x_{1} = \frac{b}{n}, \quad x_{2} = \frac{2b}{n}, \quad \dots
> $$
> en general
> $$
> x_{k} = \frac{kb}{n}
> $$
> Entonces 
> $$
> \begin{align}
> L(f,\mathcal{P}_{n}) &= \sum_{k=0}^{n-1} x_{k}(x_{k+1}-x_{k}) \\[0.5em]
> &= \sum_{k=0}^{n-1} \frac{kb}{n}\cdot \frac{b}{n} \\[0.5em]
> &= \left( \sum_{k=0}^{n-1} k \right) \frac{b^{2}}{n^{2}}.
> \end{align}
> $$
> Recordando la suma Gaussiana<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>
> $$
> 1 + \dots + m = \frac{m(m+1)}{2},
> $$
> $L(f,\mathcal{P}_{n})$ puede escribirse como
> $$
> L(f,\mathcal{P}_{n}) = \frac{(n-1)n}{2} \cdot \frac{b^{2}}{n^{2}} = \frac{n-1}{n}\cdot \frac{b^{2}}{2}.
> $$
> Análogamente,
> $$
> \begin{align}
> U(f,\mathcal{P}_{n}) &= \sum_{k=0}^{n-1} x_{k+1}(x_{k+1}-x_{k}) \\[0.5em]
> &= \sum_{k=0}^{n-1} \frac{(k+1)b}{n} \cdot \frac{b}{n} \\[0.5em]
> &= \frac{n(n+1)}{2} \cdot \frac{b^{2}}{n^{2}} \\[0.5em]
> &= \frac{n+1}{n} \cdot \frac{b^{2}}{2}.
> \end{align}
> $$
> Observamos que si $n$ es muy grande, $L(f,\mathcal{P}_{n})$ y $U(f,\mathcal{P}_{n})$ se aproximan a $\frac{b^{2}}{2}$, esta observación facilita la demostración de que $f$ es integrable:
> $$
> U(f,\mathcal{P}_{n}) - L(f,\mathcal{P}_{n}) = \frac{2}{n}\cdot \frac{b^{2}}{2} = \frac{b^{2}}{n}.
> $$
> Esto demuestra que existen particiones $\mathcal{P}_{n}$ para las cuales, la diferencia $U(f,\mathcal{P}_{n})- L(f,\mathcal{P}_{n})$ se puede hacer tan pequeña como se desee. Por el Teorema 2 la función $f$ es integrable. 
> Además, $\displaystyle \int_{0}^{b} f$ puede calcularse ahora tan sólo con un pequeño esfuerzo adicional.
> En primer lugar, está claro que
> $$
> L(f,\mathcal{P}_{n}) \leq \frac{b^{2}}{2}\leq U(f,\mathcal{P}_{n}) \quad \text{ para todo } n.
> $$
> Esta desigualdad demuestra tan sólo que $b^{2}/2$ se encuentra entre determinadas sumas superiores e inferiores, pero hemos visto que $U(f,\mathcal{P}_{n})- L(f,\mathcal{P}_{n})$ se puede hacer tan pequeña como se desee, por tanto existe *tan sólo un número con esta propiedad*. Como ciertamente la integral tiene esta propiedad, se deduce
> $$
> \int_{0}^{b} f = \frac{b^{2}}{2}
> $$
> Observamos que justo ésta es el área de un triángulo rectángulo de base y altura igual a $b$.
> ![[Pasted image 20260709115329.png|center]]
> Utilizando la Aditividad (Teorema 4 de [[Mas propiedades de la integral|Propiedades de la Integral]]), para $0 \leq a < b$ se puede demostrar que
> $$
> \int_{a}^{b} f  = \int_{0}^{b} f - \int_{0}^{a} f = \frac{b^{2}}{2} - \frac{a^{2}}{2}
> $$

> [!example]- **Ejemplo 3:** $f(x) = x^{2}$
>
> Si $\mathcal{P} = \{ x_{0},\dots,x_{n} \}$ es una partición de $[0,b]$, como $f$ es creciente en $[0,b]$, entonces
> $$
> m_{k} = f(x_{k}) = x_{k}^{2} \quad \text{ y } \quad M_{k} = f(x_{k+1}) = x_{k+1}^{2}.
> $$
> Eligiendo, una vez más, una partición $\mathcal{P}_{n} = \{ x_{0},\dots,x_{n} \}$ en $n$ subintervalos iguales, de manera que
> $$
> x_{k} = \frac{k\cdot b}{n}
> $$
> las sumas inferior y superior son
> $$
> \begin{align}
> L(f,\mathcal{P}_{n}) &= \sum_{k=0}^{n-1} x_{k}^{2} \cdot(x_{k+1}-x_{k}) \\[0.5em]
> &= \sum_{k=0}^{n-1} k^{2} \frac{b^{2}}{n^{2}} \cdot \frac{b}{n} \\[0.5em]
> &= \frac{b^{3}}{n^{3}} \cdot \sum_{k=0}^{n-1} k^{2}, \\[.7em]
> U(f,\mathcal{P}_{n}) &= \sum_{k=0}^{n-1} x_{k+1}^{2} \cdot(x_{k+1}-x_{k}) \\[0.5em]
> &= \sum_{k=0}^{n-1} (k+1)^{2} \frac{b^{2}}{n^{2}} \cdot \frac{b}{n} \\[0.5em]
> &= \frac{b^{3}}{n^{3}} \sum_{k=1}^{n} k^{2}.
> \end{align}
> $$
> Recordando la fórmula
> $$
> 1^{2}+\dots+m^{2} = \frac{1}{6}m(m+1)(2m+1)
> $$
> tenemos que (con $m = n-1$ y $m = n$)
> $$
> \begin{align}
> L(f,\mathcal{P}_{n}) &= \frac{b^{3}}{n^{3}}\cdot \frac{1}{6} (n-1)(n)(2n-1) = \frac{b^{3}}{3} \cdot \frac{2n^{2} - 3n + 1}{2n^{2}}, \\[0.5em]
> U(f,\mathcal{P}_{n}) &= \frac{b^{3}}{n^{3}}\cdot \frac{1}{6} (n)(n+1)(2n+1) = \frac{b^{3}}{3} \cdot \frac{2n^{2} + 3n + 1}{2n^{2}}.
> \end{align}
> $$
> Como $2n^{2} - 3n + 1 \leq 2n^{2} \leq 2n^{2} + 3n + 1$ para $n \geq 1$,
> $$
> L(f,\mathcal{P}_{n}) \leq \frac{b^{3}}{3} \leq U(f,\mathcal{P}_{n}),
> $$
> y $\displaystyle U(f,\mathcal{P}_{n}) - L(f,\mathcal{P}_{n} ) = \frac{b^{3}}{3} \cdot \frac{6n}{2n^{2}} = \frac{b^{3}}{n}$ se puede hacer tan pequeña como se desee, eligiendo un $n$ suficientemente grande. El mismo razonamiento que el ejemplo anterior permite deducir que
> $$
> \int_{0}^{b} f = \frac{b^{3}}{3}.
> $$

Estos cálculos nos permiten ya un resultado no trivial: el área de la región limitada por una parábola! Esto no lo sabíamos en la geometría elemental! Bueno, Arquímedes sí sabía y lo dedujo de forma similar :c
De nuevo, la única superioridad está entonces en otra forma más sencilla de llegar a este resultado: el [[Teorema Fundamental de Cálculo]].

> [!example]- **Ejemplo 4:** una función **no** integrable
>
> Sea $D: [0,1] \to \mathbb{R}$ la [[Dirichlet function|función de Dirichlet]], $D(x) = 1$ si $x \in \mathbb{Q}$ y $D(x) = 0$ si $x \notin \mathbb{Q}$. Está acotada. Pero todo subintervalo $[x_{k}, x_{k+1}]$ (con $x_{k} < x_{k+1}$) contiene racionales e irracionales ([[Densidad]]), así que $m_{k} = 0$ y $M_{k} = 1$ para todo $k$. Ent., para **toda** partición,
> $$
> L(D,\mathcal{P}) = 0 \qquad \text{y} \qquad U(D,\mathcal{P}) = \sum_{k=0}^{n-1} (x_{k+1} - x_{k}) = 1
> $$
> Así $\underline{I} = 0 \neq 1 = \overline{I}$, y $D$ **no** es integrable.

### Funciones continuas

En nuestra discusión hablamos del *verdadero* y "complicadísimo" criterio de integrabilidad (el de Lebesgue: $f$ acotada es integrable sii sus discontinuidades "no ocupan espacio"), el cual, antes de desarrollar, desmoronamos en varios resultados útiles. El primero es el caso particular que ya conocemos:

> [!theorem] **Teorema 3.** (Continua implica integrable)
>
> Si $f$ es continua en $[a,b]$, entonces $f$ es integrable en $[a,b]$, y su integral es la de [[Integral de Darboux]].

> [!proof]- **Proof.** 
>
> $f$ está acotada en $[a,b]$, pues es continua ([[Teorema de Weierstrass y de Acotación]]), y sus sumas con $\inf$/$\sup$ son las de $\min$/$\max$. Por el Lema 4 de [[Integral de Darboux]] (que se prueba con las $\varepsilon$-particiones), para cada $\varepsilon > 0$ existe $\mathcal{P}$ con $U(f,\mathcal{P}) - L(f,\mathcal{P}) < \varepsilon$. Por el Teorema 2, $f$ es integrable.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Más aún: si $f$ es continua, **toda** partición con $\Delta \mathcal{P} < \delta$ cumple $U - L < \varepsilon$ (Lema 3 de [[Integral de Darboux]]), no solo alguna. Esto se generaliza a toda función integrable en [[Integral de Reimann|Integral de Riemann]].

El teorema anterior aporta "toda la información necesaria" para el uso de las integrales en este nivel. Pero resulta satisfactorio poseer mayor surtido de herramientas: ¿y si $f$ no es continua?

### Funciones con discontinuidades

> [!tip|idea]+ **Idea Intuitiva.**
>
> Una discontinuidad en $c$ solo "estorba" en el subintervalo que contiene a $c$. Ese rectángulo aporta a $U - L$ a lo más $(\text{su ancho}) \cdot (\sup f - \inf f)$, y si lo hacemos angosto, su aporte se va a $0$. Lejos de $c$, $f$ es continua y ya sabemos acercar $U$ y $L$.
>
> <img src="/videos/discontinuidad-integrable.avif" alt="center" width="720" loading="lazy">
>
> *Función:* $f$ con un salto en $c = 2$; en rojo, el aporte del subintervalo que contiene a $c$.

> [!theorem] **Teorema.** (Una discontinuidad)
>
> Sea $f: [a,b] \to \mathbb{R}$ **acotada** y continua excepto en un punto $c \in (a,b)$. Entonces, $f$ es integrable en $[a,b]$.

> [!proof]- **Proof.** 
>
> La idea de la demostración es aproximar por derecha e izquierda nuestro punto $c$.
> Sea $D = \sup_{[a,b]} \{ f \} - \inf_{[a,b]} \{ f \}$, que existe porque $f$ está acotada. Si $D = 0$, $f$ es constante y no hay nada que hacer; sup. $D > 0$. Sea $\varepsilon >0$, y tomemos $a<y <c< z < b$ tales que
> $$
> z-y < \frac{\varepsilon}{3D}
> $$
> Sabemos que $f$ es continua en $[a,y]$ y $[z,b]$; observamos que estos intervalos son acotados y cerrados, i.e. **compactos**. Por el Teorema 3, es integrable en cada uno:
> en $[a,y]$ existe $\mathcal{P}_{1}$ partición tal que
> $$
> U(f,\mathcal{P}_{1}) - L(f,\mathcal{P}_{1}) < \frac{\varepsilon}{3}
> $$
> En $[z,b]$ existe $\mathcal{P}_{2}$ partición tal que
> $$
> U(f,\mathcal{P}_{2}) - L(f,\mathcal{P}_{2}) < \frac{\varepsilon}{3}
> $$
> Observamos que $\mathcal{P} = \mathcal{P}_{1}\cup \mathcal{P}_{2}$ es partición de $[a,b]$, cuyos subintervalos son los de $\mathcal{P}_{1}$, los de $\mathcal{P}_{2}$ y $[y,z]$. Además, se tiene que:
> $$
> \begin{align}
> U(f,\mathcal{P}) &= U(f,\mathcal{P}_{1}) + U(f,\mathcal{P}_{2}) + (z-y) \cdot \underset{[y,z]}{\sup }\{ f \}  \\[0.5em]
> L(f,\mathcal{P}) &= L(f,\mathcal{P}_{1}) + L(f,\mathcal{P}_{2}) + (z-y) \cdot \underset{[y,z]}{\inf  }\{ f \}
> \end{align}
> $$
> Como $[y,z] \subseteq [a,b]$, $\displaystyle \underset{[y,z]}{\sup }\{ f \} - \underset{[y,z]}{\inf }\{ f \} \leq D$ (en un cjto. más chico el $\sup$ baja y el $\inf$ sube). De esta manera:
> $$
> \begin{align}
> & U(f,\mathcal{P}) - L(f,\mathcal{P}) \\[0.5em]
> &= [U(f,\mathcal{P}_{1}) - L(f,\mathcal{P}_{1})] + [U(f,\mathcal{P}_{2}) - L(f,\mathcal{P}_{2})] + (z-y)\cdot \left[\underset{[y,z]}{\sup} \{ f \}-\underset{[y,z]}{\inf} \{ f \}\right] \\[0.5em]
> & < \frac{\varepsilon}{3} + \frac{\varepsilon}{3} + (z-y)D < \frac{\varepsilon}{3} + \frac{\varepsilon}{3} + \frac{\varepsilon}{3D} D \\[0.5em]
> &= \varepsilon
> \end{align}
> $$
> Por el Teorema 2, $f$ es integrable. (Si $c = a$ o $c = b$, se hace lo mismo con un solo lado.)
> $$
> \tag*{$\blacksquare$}
> $$

> [!note]- ¿Por qué se descarta el cociente?
>
> En la clase llegamos a que el aporte de $[y,z]$ es $(z-y)\left[\sup_{[y,z]} f - \inf_{[y,z]} f\right] < \frac{\varepsilon}{3D}\left[\sup_{[y,z]} f - \inf_{[y,z]} f\right] = \frac{\varepsilon}{3} \cdot \dfrac{\sup_{[y,z]} f - \inf_{[y,z]} f}{\sup_{[a,b]} f - \inf_{[a,b]} f}$. Ese cociente es $\leq 1$ porque $[y,z] \subseteq [a,b]$, así que todo es $\leq \frac{\varepsilon}{3}$: por eso se "descarta".

> [!theorem] **Corolario.**
>
> Sea $f: [a,b] \to \mathbb{R}$ acotada y continua en $[a,b]$ excepto en $\{ c_{1},c_{2},\dots,c_{m} \}$. Entonces, $f$ es integrable.

> [!proof]- **Proof.**
>
> Igual que el teorema, pero con $m$ intervalitos. Sea $\varepsilon > 0$ (y $D > 0$ como antes). Alrededor de cada $c_{i}$ tomamos un intervalo $[y_{i}, z_{i}] \ni c_{i}$ (con $y_{i} < c_{i} < z_{i}$ si $c_{i}$ es interior), ajenos entre sí y con $z_{i} - y_{i} < \frac{\varepsilon}{2mD}$. Lo que queda de $[a,b]$ son $r \leq m+1$ intervalos cerrados donde $f$ es continua; en cada uno hay una partición con $U - L < \frac{\varepsilon}{2r}$ (Teorema 3). Uniendo todas, obtenemos una partición $\mathcal{P}$ de $[a,b]$ con
> $$
> U(f,\mathcal{P}) - L(f,\mathcal{P}) < r \cdot \frac{\varepsilon}{2r} + m \cdot \frac{\varepsilon}{2mD} D = \varepsilon
> $$
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> La hipótesis de **acotada** es indispensable: $f(x) = \frac{1}{x}$ para $x \in (0,1]$ con $f(0) = 0$ tiene una sola discontinuidad, pero no está acotada y sus sumas superiores ni siquiera están definidas. Y con una infinidad de discontinuidades puede fallar: la función de Dirichlet es discontinua en todo punto y no es integrable (Ejemplo 4 de arriba).

Las propiedades de la integral (aditividad, linealidad, monotonía) están en [[Mas propiedades de la integral|Propiedades de la Integral]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

[[Suma Gaussiana]] <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
