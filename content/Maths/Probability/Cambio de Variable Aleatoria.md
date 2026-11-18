---
modified: 2026-11-18T16:46:59Z
title: "Teorema de Cambio de Variable Aleatoria"
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
Muchas veces la v.a. que nos interesa es una función de otra que ya conocemos: el área de un cuadrado de lado aleatorio, una ganancia que depende de una tasa aleatoria, el tiempo en minutos en vez de horas. Si $Y = \varphi(X)$ y conocemos la distribución de $X$, ¿cuál es la de $Y$? La idea es siempre la misma: **la probabilidad no se crea ni se destruye, solo se mueve** con $\varphi$.

En el caso discreto basta juntar la probabilidad de todos los $x$ que $\varphi$ manda al mismo $y$:

> [!theorem] **Teorema.** (Cambio de V.A. discreta)
>
> Sea $X$ una v.a. discreta y sea $Y = \varphi  (X)$ en donde $\varphi$ es cualquier función definida por lo menos en el conjunto de valores de $X$. Para cualquier $y \in \mathbb{R}$,
> $$
> f_{Y}(y) = P(Y= y) = P(X \in \varphi ^{-1} (y)) = \sum_{x \in \varphi ^{-1}(y)} P(X= x)
> $$
> donde $\varphi ^{-1}(y) = \{ x : \varphi (x) = y \}$, i.e. es la imagen inversa de $\{ y \}$ bajo $\varphi$.

> [!proof]- **Proof.**
>
> $\varphi(X(\omega)) = y$ sii $X(\omega) \in \varphi^{-1}(y)$, así que los eventos $(Y = y)$ y $(X \in \varphi^{-1}(y))$ son el mismo. La suma es la Proposición de [[Funcion de Masa de Probabilidad]]. $\blacksquare$

> [!example]- **Ejemplo 1.** (Se juntan dos valores)
>
> Sea $X$ uniforme en $\{ -1, 0, 1 \}$ y $Y = X^{2}$. Ent. $\varphi^{-1}(0) = \{ 0 \}$ y $\varphi^{-1}(1) = \{ -1, 1 \}$, así que $f_{Y}(0) = \frac{1}{3}$ y $f_{Y}(1) = \frac{1}{3} + \frac{1}{3} = \frac{2}{3}$.

En el caso continuo no hay puntos con probabilidad, hay **densidad**, y la densidad sí cambia: si $\varphi$ estira un intervalo, la misma probabilidad queda repartida en un intervalo más largo, y la densidad baja.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Un intervalito de ancho $dx$ tiene probabilidad $f_{X}(x)\,dx$; $\varphi$ lo manda a uno de ancho $dy$ con la misma probabilidad, así que $f_{Y}(y) = f_{X}(x)\left\lvert \frac{dx}{dy} \right\rvert$. En la animación, $X \sim \operatorname{Unif}(0,1)$ e $Y = X^{2}$.
> <img src="/videos/cambio-variable.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Teorema.** (Cambio de V.A continua)
>
> Sea $X$ v.a. continua con función de densidad $f_{X}(x)$, y sea $I$ un intervalo con $P(X \in I) = 1$. Sea $\varphi : I \to \mathbb{R}$ continua, estrictamente monótona y con inversa $\varphi ^{-1}$ diferenciable. Entonces la función de densidad de $Y = \varphi (X)$ está dada por
> $$
> f_{Y}(y) = \begin{cases}
>   f_{X}(\varphi ^{-1}(y)) \left\lvert \displaystyle \frac{d}{dy} \varphi ^{-1}(y) \right\rvert & \text{ si } y \in \varphi(I) \\[0.5em]
>   0 & \text{ otro caso }
> \end{cases}
> $$

> [!proof]- **Proof.**
>
> **Borrador.** Se calcula $F_{Y}$ con $F_{X}$ (despejando la desigualdad, que se voltea si $\varphi$ decrece) y se deriva con la regla de la cadena. El valor absoluto junta los dos casos.
>
> **Proof.** Sea $y \in \varphi(I)$.
> - Si $\varphi$ es creciente, $\varphi(X) \leq y \iff X \leq \varphi^{-1}(y)$, ent. $F_{Y}(y) = F_{X}(\varphi^{-1}(y))$, y derivando,
> $$
> f_{Y}(y) = f_{X}(\varphi^{-1}(y))\,\frac{d}{dy}\varphi^{-1}(y),
> $$
> con $\frac{d}{dy}\varphi^{-1} \geq 0$.
> - Si $\varphi$ es decreciente, $\varphi(X) \leq y \iff X \geq \varphi^{-1}(y)$, ent. $F_{Y}(y) = 1 - F_{X}(\varphi^{-1}(y))$ (aquí $P(X = \varphi^{-1}(y)) = 0$ porque $X$ es continua), y
> $$
> f_{Y}(y) = -f_{X}(\varphi^{-1}(y))\,\frac{d}{dy}\varphi^{-1}(y),
> $$
> con $\frac{d}{dy}\varphi^{-1} \leq 0$.
>
> En los dos casos es $f_{X}(\varphi^{-1}(y))\left\lvert \frac{d}{dy}\varphi^{-1}(y) \right\rvert$. Fuera de $\varphi(I)$, $Y$ no toma valores (salvo con proba. $0$). $\blacksquare$

> [!example]- **Ejemplo 2.** (Recorrer y reescalar)
>
> Si $Y = aX + b$ con $a \neq 0$, ent. $\varphi^{-1}(y) = \frac{y-b}{a}$ y
> $$
> f_{Y}(y) = \frac{1}{\lvert a \rvert}\,f_{X}\left( \frac{y-b}{a} \right).
> $$
> Es lo que se usa para estandarizar una [[Distribucion Normal|normal]] y para el escalamiento de la [[Distribucion Gamma|gamma]].

> [!example]- **Ejemplo 3.** (De uniforme a exponencial)
>
> Sea $X \sim \operatorname{Unif}(0,1)$ e $Y = -\ln X$. En $I = (0,1)$, $\varphi(x) = -\ln x$ es decreciente, con $\varphi^{-1}(y) = e^{-y}$ y $\varphi(I) = (0, \infty)$. Para $y > 0$,
> $$
> f_{Y}(y) = 1 \cdot \lvert -e^{-y} \rvert = e^{-y},
> $$
> i.e. $Y \sim \operatorname{Exp}(1)$. Es el [[Metodo de la Transformada Inversa]] visto desde aquí.

Si $\varphi$ **no** es monótona el teorema no aplica, pero la idea de su prueba sí: calcular $F_{Y}$ despejando el evento, y derivar.

> [!example]- **Ejemplo 4.** (No monótona: $Y = X^{2}$)
>
> Sea $X \sim \operatorname{Unif}(-1,1)$ e $Y = X^{2}$. Para $0 \leq y \leq 1$,
> $$
> F_{Y}(y) = P(-\sqrt{ y } \leq X \leq \sqrt{ y }) = \frac{2\sqrt{ y }}{2} = \sqrt{ y },
> $$
> ent. $f_{Y}(y) = \frac{1}{2\sqrt{ y }}$ en $(0,1)$. Los dos lados ($x$ y $-x$) caen en el mismo $y$, y por eso hay que sumar ambos, igual que en el Ejemplo 1. Con $X$ normal estándar, la misma cuenta da la [[Distribucion ji-cuadrada]].

---
Siguiente: [[Independencia de Variables Aleatorias]].
