---
modified: 2026-11-15T14:36:08Z
title: "Integral de Riemann"
publish: true
type: zettel
date: "2026-09-01"
status: seed
aliases:
tags:
 - calculus
cssclasses:
 - romana
---
Como previo ver: [[Sumas de Riemann]]

> [!tip|idea]- **Idea Intuitiva.**
>
> Darboux usa $\sup$ e $\inf$ sobre **todas** las particiones. Riemann pide algo que suena más fuerte: que **cualquier** [[Sumas de Riemann|suma de Riemann]], con **cualesquiera** etiquetas, se acerque a un número $S$ en cuanto la partición sea suficientemente fina ($\Delta \mathcal{P} < \delta$). Resulta que las dos definiciones dan las mismas funciones integrables y el mismo valor.

> [!theorem] **Definición.** (Integral de Riemann)
>
> Dada $f:[a,b]\to \mathbb{R}$ acotada, decimos que $S$ **es la integral de Riemann de** $f$ si para todo $\varepsilon >0$ existe $\delta > 0$ tal que para toda partición $\mathcal{P}$ de $[a,b]$ con $\Delta \mathcal{P} < \delta$ se cumple que $\lvert S- R \rvert < \varepsilon$ para toda suma de Riemann $R$ con partición $\mathcal{P}$ (con cualesquiera etiquetas). Es decir,
> $$
> \forall \varepsilon > 0 \ \exists \delta > 0 \ \forall \mathcal{P}_{[a,b]} \ \Big( \Delta \mathcal{P} < \delta \implies \forall z_{0} \in [x_{0},x_{1}], \dots, \forall z_{n-1} \in [x_{n-1},x_{n}] \ \ \big\lvert R(f,\mathcal{P},z) - S \big\rvert < \varepsilon \Big)
> $$
> De existir $S$, la llamamos **integral de Riemann** y decimos que $f$ es **Riemann-integrable**.

> [!observation]+ **Observación.**
>
> Es la misma estructura que un [[Limite|límite]] $\varepsilon$-$\delta$, con $\Delta \mathcal{P}$ en el papel de $\lvert x - a \rvert$. A veces se escribe $\displaystyle S = \lim_{\Delta \mathcal{P} \to 0} \sum_{k=0}^{n-1} f(z_{k})(x_{k+1} - x_{k})$.

Para comparar con Darboux, necesitamos que en una función integrable **toda** partición fina (no solo alguna) tenga $U - L$ chico.

> [!theorem] **Lema.** (Darboux)
>
> Si $f$ es integrable (de Darboux) en $[a,b]$, ent. para todo $\varepsilon > 0$ existe $\delta > 0$ tal que **toda** partición $\mathcal{P}$ con $\Delta \mathcal{P} < \delta$ cumple $U(f,\mathcal{P}) - L(f,\mathcal{P}) < \varepsilon$.

> [!proof]- **Proof.**
>
> **Borrador.** Ya tenemos una partición buena $\mathcal{P}_{0}$. Si $\mathcal{P}$ es fina, $\mathcal{P} \cup \mathcal{P}_{0}$ es buena (refina a $\mathcal{P}_{0}$), y agregarle a $\mathcal{P}$ los puntos de $\mathcal{P}_{0}$ cambia sus sumas poco: cada punto nuevo solo afecta un subintervalo, de ancho $\leq \Delta \mathcal{P}$.
>
> **Proof.** Sea $B > 0$ con $\lvert f \rvert \leq B$ en $[a,b]$, y sea $\varepsilon > 0$. Por el Teorema 2 ([[Integrabilidad]]) existe $\mathcal{P}_{0}$ con $U(f,\mathcal{P}_{0}) - L(f,\mathcal{P}_{0}) < \frac{\varepsilon}{2}$; sea $r$ su número de puntos. Sea $\delta = \frac{\varepsilon}{8Br}$ y $\mathcal{P}$ con $\Delta \mathcal{P} < \delta$.
>
> Agregar **un** punto $y$ a una partición parte un subintervalo $[x_{k}, x_{k+1}]$ en dos; en la suma superior, el sumando $M_{k}(x_{k+1} - x_{k})$ se cambia por $M'(y - x_{k}) + M''(x_{k+1} - y)$ con $M', M'' \geq -B$ y $M_{k} \leq B$, ent. $U$ baja a lo más $2B(x_{k+1} - x_{k}) \leq 2B\,\Delta \mathcal{P}$ (y nunca sube). Lo mismo con $L$. Agregando los $\leq r$ puntos de $\mathcal{P}_{0}$, con $\mathcal{Q} = \mathcal{P} \cup \mathcal{P}_{0}$ (cada partición intermedia sigue teniendo norma $\leq \Delta \mathcal{P}$),
> $$
> U(f,\mathcal{P}) \leq U(f,\mathcal{Q}) + 2Br\,\Delta \mathcal{P}, \qquad L(f,\mathcal{P}) \geq L(f,\mathcal{Q}) - 2Br\,\Delta \mathcal{P}
> $$
> Como $\mathcal{Q}$ refina a $\mathcal{P}_{0}$,
> $$
> U(f,\mathcal{P}) - L(f,\mathcal{P}) \leq U(f,\mathcal{Q}) - L(f,\mathcal{Q}) + 4Br\,\Delta \mathcal{P} < \frac{\varepsilon}{2} + 4Br\delta = \varepsilon
> $$
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Teorema.** (Integral de Darboux es equivalente a la Integral de Riemann)
>
> Sea $f:[a,b]\to \mathbb{R}$ acotada. Entonces $f$ es integrable (de Darboux) si y sólo si es Riemann-integrable, y en ese caso
> $$
> \int_{a}^{b} f(x) \, dx  = S
> $$

> [!proof]- **Proof.** 
>
> $(\implies)$ Veamos que la integral de Darboux implica la integral de Riemann, con $S = \int_{a}^{b} f$. Sea $\varepsilon>0$ y $\delta$ el del Lema. Si $\Delta \mathcal{P} < \delta$ y $R$ es cualquier suma de Riemann con partición $\mathcal{P}$, tanto $R$ como $\int_{a}^{b} f$ están en $[L(f,\mathcal{P}), U(f,\mathcal{P})]$ (Observación de [[Sumas de Riemann]]), ent.
> $$
> \left\lvert R - \int_{a}^{b} f(x) \, dx \right\rvert \leq U(f,\mathcal{P}) - L(f,\mathcal{P}) < \varepsilon
> $$
> $(\impliedby)$ Sup. que $S$ es la integral de Riemann. Sea $\varepsilon>0$ y $\delta$ el de la definición para $\frac{\varepsilon}{4}$; tomemos $\mathcal{P}$ con $\Delta \mathcal{P} < \delta$. Por la caracterización del $\sup$ con $\varepsilon$, en cada subintervalo hay $z_{k}$ con $f(z_{k}) > M_{k} - \frac{\varepsilon}{4(b-a)}$, y $w_{k}$ con $f(w_{k}) < m_{k} + \frac{\varepsilon}{4(b-a)}$. Las sumas de Riemann $R$ (con los $z_{k}$) y $R'$ (con los $w_{k}$) cumplen
> $$
> R > U(f,\mathcal{P}) - \frac{\varepsilon}{4}, \qquad R' < L(f,\mathcal{P}) + \frac{\varepsilon}{4}
> $$
> Ent.
> $$
> U(f,\mathcal{P}) - L(f,\mathcal{P}) < R - R' + \frac{\varepsilon}{2} \leq \lvert R - S \rvert + \lvert S - R' \rvert + \frac{\varepsilon}{2} < \frac{\varepsilon}{4} + \frac{\varepsilon}{4} + \frac{\varepsilon}{2} = \varepsilon
> $$
> Por el Teorema 2, $f$ es integrable, y por $(\implies)$ su integral de Darboux también cumple la definición de Riemann.
>
> Falta ver que son el **mismo** número (así lo hicimos en clase). Sea $\varepsilon>0$. Como $\int_{a}^{b} f = \sup \mathcal{L}$, existe una partición $\hat{\mathcal{P}}$ tal que
> $$
> \int_{a}^{b} f(x) \, dx -\frac{\varepsilon}{2} < L(f,\hat{\mathcal{P}}) \leq \int_{a}^{b} f(x) \, dx 
> $$
> Tomemos $\mathcal{P}$ refinamiento de $\hat{\mathcal{P}}$ tal que $\Delta \mathcal{P} < \delta$ (el $\delta$ de $S$ para $\frac{\varepsilon}{4}$). Por ser refinamiento, $L(f,\hat{\mathcal{P}}) \leq L(f,\mathcal{P})$, por lo que
> $$
> 0 \leq \int_{a}^{b} f(x) \, dx - L(f,\mathcal{P}) < \frac{\varepsilon}{2}
> $$
> Además, la suma $R'$ de arriba (con esta $\mathcal{P}$) cumple $\lvert S - R' \rvert < \frac{\varepsilon}{4}$ y $\lvert R' - L(f,\mathcal{P}) \rvert < \frac{\varepsilon}{4}$. Así,
> $$
> \left\lvert  \int_{a}^{b} f(x) \, dx - S  \right\rvert \leq \left\lvert  \int_{a}^{b} f(x) \, dx -L(f,\mathcal{P})  \right\rvert + \lvert L(f,\mathcal{P}) - R' \rvert + \lvert R' - S \rvert  < \varepsilon
> $$
> para toda $\varepsilon > 0$.
> $$
> \therefore S = \int_{a}^{b} f(x) \, dx  \tag*{$\blacksquare$}
> $$

### Calcular integrales con sucesiones de particiones

> [!theorem] **Teorema.** (Criterio de Integrabilidad 3)
>
> Sea $f:[a,b]\to\mathbb{R}$ acotada; $f$ es integrable si y sólo si existe un número $I$ tal que para toda sucesión $\{ \mathcal{P}_{n} \}_{n \in \mathbb{N}}$ de particiones con
> $$
> \lim_{n \to \infty} \Delta \mathcal{P}_{n} = 0
> $$
> y cualesquiera sumas de Riemann $R(f,\mathcal{P}_{n})$, se cumple que
> $$
> \lim_{n \to \infty} R(f,\mathcal{P}_{n}) = I
> $$
> En ese caso $I = \int_{a}^{b} f$.

> [!proof]- **Proof.**
>
> $(\implies)$ Por el Teorema, con $I = \int_{a}^{b} f$: dado $\varepsilon > 0$ y su $\delta$, como $\Delta \mathcal{P}_{n} \to 0$ existe $N$ con $\Delta \mathcal{P}_{n} < \delta$ si $n \geq N$, y ent. $\lvert R(f,\mathcal{P}_{n}) - I \rvert < \varepsilon$ (ver [[Sucesiones Convergentes]]).
>
> $(\impliedby)$ Veamos que $I$ es la integral de Riemann. Sup. que no: existe $\varepsilon > 0$ tal que para todo $\delta > 0$ hay una partición con norma $< \delta$ y una suma de Riemann $R$ con $\lvert R - I \rvert \geq \varepsilon$. Con $\delta = \frac{1}{n+1}$ obtenemos $\mathcal{P}_{n}$ con $\Delta \mathcal{P}_{n} < \frac{1}{n+1} \to 0$ y sumas con $\lvert R(f,\mathcal{P}_{n}) - I \rvert \geq \varepsilon$ para todo $n$, que no convergen a $I$. Contradicción! Por el Teorema, $f$ es integrable con integral $I$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Si ya sabemos que $f$ es integrable (p. ej. porque es continua, [[Integrabilidad]]), basta **una** sucesión de particiones con $\Delta \mathcal{P}_{n} \to 0$ y **una** elección de etiquetas para calcular $\int_{a}^{b} f$. Es lo que hacemos en los ejemplos.

> [!example]- Ejemplo. $f(x) = x^{2}$ en $[0,1]$
>
> Sea $n \in  \mathbb{N}^{+}$ y $\mathcal{P}_{n} = \{ 0, \frac{1}{n}, \frac{2}{n},\dots, \frac{n-1}{n}, 1 \}$.
> Esta es una sucesión particular de particiones tales que $\displaystyle \lim_{n \to \infty} \Delta \mathcal{P}_{n} = \lim_{n \to \infty} \frac{1}{n} = 0$. Con etiquetas por la izquierda, $z_{k} = \frac{k}{n}$:
> $$
> \begin{align}
> R(f,\mathcal{P}_{n}) &= \sum_{k=0}^{n-1} \frac{1}{n}\left( \frac{k}{n} \right)^{2} = \frac{1}{n^{3}} \left[ 0^{2} + 1^{2}+\dots+(n-1)^{2} \right] \\[0.5em]
> &=\frac{1}{n^{3}} \cdot \frac{(n-1)n(2n-1)}{6} = \frac{(n-1)(2n-1)}{6n^{2}} = \frac{2n^{2}-3n+1}{6n^{2}} \overset{n \to \infty}{\longrightarrow} \frac{1}{3}
> \end{align}
> $$
> Como $x^{2}$ es continua, $\displaystyle \int_{0}^{1} x^{2} \, dx = \frac{1}{3}$ (compara con el Ejemplo 3 de [[Integrabilidad]] y con el [[Teorema Fundamental de Cálculo]]).

> [!example]- Ejemplo. $f(x) = e^{x}$
>
> Sea $f(x) = e^{x}$  para $x \in  [a,b]$. Calcula $\displaystyle \int_{a}^{b} e^{x} \, dx$ con sumas de Riemann.
> Sea $h = \frac{b-a}{n}$ y $\mathcal{P}_{n} = \left\{a, a + h, a+ 2h,\dots, a + nh = b  \right\}$; observamos que
> $$
> \Delta \mathcal{P}_{n} = h = \frac{b-a}{n} \overset{n\to \infty}{\longrightarrow} 0
> $$
> Como $e^{x}$ es creciente, el $\inf$ en cada subintervalo está en el extremo izquierdo: la suma inferior es la suma de Riemann por la izquierda.
> $$
> \begin{align}
> L(f,\mathcal{P}_{n}) &= \sum_{k=0}^{n-1} \underset{[x_{k}, x_{k+1}]}{\inf \left\{f\right\} } (x_{k+1}- x_{k}) = \sum_{k=0}^{n-1} f(x_{k})\, h \\[0.5em]
>   &= h\left[e^{a} + e^{a + h} + e^{a + 2h} + \dots + e^{a + (n-1)h}  \right] \\[0.5em]
>  &= h \, e^{a}\left[1+e^{h}+ \left( e^{h} \right)^{2} + \dots + \left( e^{h} \right)^{n-1} \right] \\[0.5em]
>    &= h \, e^{a} \cdot \frac{\left( e^{h} \right)^{n} - 1}{e^{h} - 1} \tag{suma geométrica} \\[0.5em]
>  &= h \cdot \frac{e^{a}e^{b-a} - e^{a}}{e^{h} - 1} \tag{$nh = b-a$} \\[0.5em]
>    &= \frac{e^{b} - e^{a}}{\dfrac{e^{h} - e^{0}}{h-0}} \overset{n \to \infty}{\longrightarrow} \frac{e^{b}- e^{a}}{\left.\frac{d}{dx}e^{x}\right|_{x=0}} = \frac{e^{b}-e^{a}}{1}
> \end{align}
> $$
> pues el denominador es el cociente de Newton de $e^{x}$ en $0$ y $h \to 0$ ([[Funcion Exponencial]]). Como $e^{x}$ es continua,
> $$
> \int_{a}^{b} e^{x} \, dx = e^{b} - e^{a} \tag*{$\square$}
> $$
