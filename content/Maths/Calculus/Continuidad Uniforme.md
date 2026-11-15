---
modified: 2026-11-15T14:39:22Z
title: "Continuidad Uniforme"
publish: true
type: zettel
status: 
links: 
tags: []
date: "2026-03-26"
aliases: [ "uniform continuity" ]
cssclasses: romana
materia: 
---
> [!theorem] **Definición.** (Alcance de una Función)
>
> Sea $f: [a,b] \to \mathbb{R}$ continua, llamamos el **alcance** u **oscilación** de $f$ a
> $$
> \max \left\{f\right\} - \min \left\{f\right\} 
> $$
> (el máximo y el mínimo existen por el [[Teorema de Weierstrass y de Acotación|Teorema de Weierstrass]]).



> [!tip|idea]+ **Idea Intuitiva.**
>
> A diferencia de la continuidad, la continuidad uniforme no tiene punto fijo $x_{0}$, su radio $\delta$ no depende del punto $x$. En la [[Continuidad|continuidad]], $\delta= \delta(f,\varepsilon,x_{0})$; aquí ya no depende de $x_{0}$, es decir, solo $\delta(f,\varepsilon)$.
>
> **Intuitivamente:** Imagina un cuadro que se desliza por toda la función.
>
> <img src="/videos/cuadro-uniforme.avif" alt="center" width="720" loading="lazy">
>
> *El cuadro mide $\delta$ de ancho y $\varepsilon$ de alto: cumple (verde) si la gráfica lo cruza por los lados, sin salirse por arriba o por abajo. Con $f(x) = x^{2}$, el mismo cuadro sirve en $[a,b]$, pero no en todo $\mathbb{R}$.*
> 
> En otras palabras, se evalúa globalmente, en todo el dominio, y no solo en un punto como la continuidad. Esto resulta en proponer un $\delta$ que funcione para toda la función por igual.
> ![[Pasted image 20260507154753.png|center]]


> En la continuidad uniforme, existe un solo $\delta$ universal que funciona para toda la función al mismo tiempo.

> [!theorem] **Definición.** (Continuidad Uniforme)
>
> Sea $f$ definida en $A \subseteq \mathbb{R}$ (p. ej. $A = [a,b]$). $f$ es **uniformemente continua** en $A$ si
> $$
> \forall  \varepsilon>0 \ \exists \delta >0 \ \text{ tal que } \ \forall x,y \in A \ \left( \lvert x-y \rvert <\delta \implies \lvert f(x)-f(y) \rvert < \varepsilon \right)
> $$

> [!theorem] **Teorema.** 
>
> Si $f$ es uniformemente continua, entonces es continua.

> [!proof]- **Proof.**
>
> Sea $x_{0} \in A$ y $\varepsilon > 0$. El $\delta$ de la continuidad uniforme sirve: fijando $y = x_{0}$, si $\lvert x - x_{0} \rvert < \delta$, ent. $\lvert f(x) - f(x_{0}) \rvert < \varepsilon$.
> $$
> \tag*{$\blacksquare$}
> $$

> Veremos que el recíproco no es verdad: una función continua no siempre es unif. continua, veamos un ejemplo.

> [!example]- **Ejemplo** ($f(x) = x^{2}$)
>
> Tomemos $f(x) = x^{2}$, $f:\mathbb{R}\to \mathbb{R}$. Probamos que $f$ es continua en $x_{0}$:
> 
> Sea $\varepsilon>0$. Observamos que $\lvert f(x)-f(x_{0}) \rvert  = \lvert x^{2} - x_{0}^{2} \rvert = \lvert x+x_{0} \rvert\lvert x-x_{0} \rvert$.
> 
> Si inicialmente tomamos $\lvert x-x_{0} \rvert<1$ por desigualdad del triángulo
> $$
> \lvert x \rvert \leq 1 + \lvert x_{0} \rvert 
> $$
> De esta forma,
> $$
> \begin{align}
> \lvert f(x)-f(x_{0}) \rvert  = \lvert x+x_{0} \rvert \lvert x-x_{0} \rvert &\leq (\lvert x \rvert +\lvert x_{0} \rvert )(\lvert x-x_{0} \rvert ) \\[.5em]
> &\leq (1 + \lvert x_{0} \rvert +\lvert x_{0} \rvert )(\lvert x-x_{0} \rvert ) \\[.5em]
> &= (1+2\lvert x_{0} \rvert )(\lvert x-x_{0} \rvert )
> \end{align}
> $$
> Si tomamos $\lvert x-x_{0} \rvert< \frac{\varepsilon}{1 + 2\lvert x_{0} \rvert}$
> $$
> \begin{align}
> \implies \lvert f(x)-f(x_{0}) \rvert &\leq (1+2\lvert x_{0} \rvert )(\lvert x-x_{0} \rvert ) \\[.5em]
> &< (1+2\lvert x_{0} \rvert ) \cdot \frac{\varepsilon}{(1+2\lvert x_{0} \rvert )} = \varepsilon
> \end{align}
> $$
> El valor que sirve es $\displaystyle \delta = \min\left\{  1, \frac{\varepsilon}{1+2\lvert x_{0} \rvert}  \right\}$.
> Este $\delta$ depende de $x_{0}$, $\delta = \delta(x_{0})$, y se hace chico cuando $\lvert x_{0} \rvert$ crece. Eso sugiere que **no** es uniformemente continua, pero hay que probar que **ningún** $\delta$ sirve:
>
> **Proof.** Sea $\varepsilon = 1$ y sea $\delta > 0$ cualquiera. Tomemos $x = \frac{1}{\delta}$ y $y = x + \frac{\delta}{2}$. Ent. $\lvert x - y \rvert = \frac{\delta}{2} < \delta$, pero
> $$
> \lvert y^{2} - x^{2} \rvert = (y - x)(y + x) = \frac{\delta}{2}\left( \frac{2}{\delta} + \frac{\delta}{2} \right) = 1 + \frac{\delta^{2}}{4} \geq 1 = \varepsilon
> $$
> Por def., $f$ **no** es uniformemente continua en $\mathbb{R}$. (En cambio, en cualquier $[a,b]$ sí lo es, por Heine-Cantor.)
> $$
> \tag*{$\blacksquare$}
> $$

El recíproco no siempre implica continuidad uniforme, ¿o sí? Hay un caso en el cual se cumple: si el $\operatorname{dom}f$ es un conjunto compacto (*cerrado y acotado*), como $[a,b]$.

> [!theorem] **Teorema.** (Heine-Cantor)
>
> Si $f:[a,b]\to \mathbb{R}$ es continua, Ent. es **uniformemente continua**.

> [!proof]- **Proof.** 
>
> Supongamos que $f$ no es unif. cont. Esto es,
> $$
> \neg(\forall \varepsilon > 0 \ \exists  \delta >0 \text{ tal que } \forall x,y \ (\lvert x-y \rvert < \delta \implies \lvert f(x)-f(y) \rvert < \varepsilon))
> $$
> Es decir,
> $$
> \exists  \hat{\varepsilon} > 0 \text{ tal que } \forall \delta > 0 \ \exists  x,y \in [a,b] \text{ tales que } \lvert x-y \rvert <\delta \ \text{ y } \ \lvert f(x)-f(y) \rvert \geq \hat{\varepsilon}
> $$
> Para $\delta_{0} = 1 \ \exists x_{0},y_{0} \mid \lvert x_{0}-y_{0} \rvert< \delta_{0} \text{ y } \lvert f(x_{0})-f(y_{0}) \rvert \geq \hat{\varepsilon}$
> Para $\delta_{1} = \frac{1}{2} \ \exists x_{1},y_{1} \mid \lvert x_{1}-y_{1}  \rvert< \delta_{1} \text{ y } \lvert f(x_{1})-f(y_{1}) \rvert \geq \hat{\varepsilon}$ 
> Para $\delta_{n} = \frac{1}{n+1} \ \exists x_{n},y_{n} \mid \lvert x_{n}-y_{n} \rvert< \frac{1}{n+1} \text{ y } \lvert f(x_{n})-f(y_{n})  \rvert  \geq \hat{\varepsilon}$
> 
> Tenga dos sucesiones $\{ x_{n} \}, \{ y_{n} \}$ en $[a,b]$; por el **[[Teorema del Bolzano-Weierstrass|Teorema de Bolzano-Weierstrass]]** (su Corolario en $[a,b]$), $\exists \{ x_{n_{k}} \}$ subsucesión de $\{ x_{n} \}$ convergente $x_{n_{k}} \overset{k\to \infty}{\longrightarrow} p$, con $p \in [a,b]$.
> 
> Tomemos la subsucesión respectiva $\{ y_{n_{k}} \}$. Probemos que $y_{n_{k}}\overset{k\to \infty}{\longrightarrow} p$:
> $$
> \begin{align}
> \lvert y_{n_{k}}-p \rvert &\leq \lvert y_{n_{k}}-x_{n_{k}} \rvert +\lvert x_{n_{k}}-p \rvert  \\[0.5em]
> &< \frac{1}{n_{k}+1}+\lvert x_{n_{k}}-p \rvert \tag{por Def. de $\delta_{n_{k}}$}
> \end{align}
> $$
> y ambos sumandos tienden a $0$ (pues $n_{k} \geq k$, ver [[Subsucesiones]]), así que por Sándwich $y_{n_{k}} \to p$.
> Así, tenemos que $\displaystyle \begin{cases}x_{n_{k}}\longrightarrow p \\  y_{n_{k}}\longrightarrow p\end{cases}$
> Como $f$ es continua (hip.) en $p$, por Continuidad por Sucesiones ([[Limites de Sucesiones]]) se tiene que 
> $$
> \lim_{ k \to \infty } f(x_{n_{k}}) = f(p) = \lim_{ k \to \infty } f(y_{n_{k}})
> $$
> Utilizando esto, observamos que
> $$
> \lvert f(x_{n_{k}})- f(y_{n_{k}}) \rvert \leq \lvert f(x_{n_{k}})-f(p) \rvert + \lvert f(p)-f(y_{n_{k}}) \rvert 
> $$
> Para $k$ suficientemente grande, $\displaystyle \begin{cases} \lvert f(x_{n_{k}}) - f(p) \rvert \\  \lvert f(y_{n_{k}})-f(p) \rvert \end{cases}$ $\displaystyle < \frac{\hat{\varepsilon}}{2}$, ent. $\lvert f(x_{n_{k}}) - f(y_{n_{k}}) \rvert < \hat{\varepsilon}$.
> Pero esto nos lleva a una contradicción con $\lvert f(x_{n_{k}}) - f(y_{n_{k}}) \rvert \geq \hat{\varepsilon}$!
> $$
> \therefore f \text{ es unif. continua} \tag*{$\blacksquare$}
> $$

Este resultado es importante para un criterio de integrabilidad (ver [[Integrabilidad]]).

---

> [!theorem] **Teorema.** 
>
> Si $f$ es uniformemente continua en un intervalo acotado $I$, entonces $f$ está acotada en $I$.

> [!proof]- **Proof.** 
>
> Suponemos que $I$ es alguno de $(a,b),[a,b],(a,b],[a,b)$. Para revisar si $f$ está acotada, elegimos $\delta$ tal que $\lvert f(x)-f(y) \rvert<1$ siempre que $x,y \in I$ y $\lvert x-y \rvert<\delta$. Existe un conjunto finito $a = x_{0}<x_{1}<\dots<x_{n} = b$ tal que $\lvert  x_{i}-x_{i-1} \rvert<\delta$ para $i = 1,\dots,n$ (p. ej. puntos equiespaciados con $n > \frac{b-a}{\delta}$, por la Prop. Arquimediana). Nuestra definición de $\delta$ implica que $f$ está acotada en cada uno de los intervalos $[x_{i-1},x_{i}]\cap I$: si $p_{i}$ es un punto fijo de ese cjto. (si es vacío no hay nada que acotar), para todo $x$ en él $\lvert x - p_{i} \rvert \leq x_{i} - x_{i-1} < \delta$, ent. $\lvert f(x) \rvert < \lvert f(p_{i}) \rvert + 1$. Sea
> $$
> \begin{align}
> m_{i} &= \inf \{ f(x):x_{i-1}\leq x\leq x_{i}, x \in I \} \\[0.5em]
> M_{i} &= \sup \{ f(x):x_{i-1}\leq x\leq x_{i}, x \in I \} \\[0.5em]
> m &= \min \{ m_{1},\dots,m_{n} \} \\[0.5em]
> M &= \max \{ M_{1},\dots ,M_{n} \}
> \end{align}
> $$
> Entonces, para todo $x \in I$, $m\leq f(x) \leq M$, y $f$ está acotada en $I$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Así, $f(x) = \frac{1}{x}$ es continua en $(0,1]$ pero **no** unif. continua ahí, pues no está acotada.
