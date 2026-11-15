---
modified: 2026-11-15T18:06:57Z
title: "Métodos numéricos"
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
Algunas funciones no tienen antiderivada explícita (en términos de funciones elementales) y no se puede aplicar T.F.C. 2.
Por ejemplo, algunas integrales "feas":
$$
\begin{align}
\int e^{-x^{2}} \, dx, \quad \int \frac{\sin(x)}{x} \, dx, \quad \int \frac{\cos(x)}{x} \, dx, \quad \int \frac{1}{\log \left(x\right)} \, dx, \quad \text{ integrales Elípticas }\dots
\end{align}
$$

Veamos un ejemplo de integrales elípticas.
El perímetro de una Elipse está dado por $\displaystyle \int_{0}^{2\pi} \sqrt{a^{2}\cos^{2}(x) + b^{2}\sin^{2}(x)} \, dx$ (en [[Funciones Uniparametricas]] aparece con $\sin$ y $\cos$ intercambiados; con $x \mapsto \frac{\pi}{2} - x$ es la misma integral, pues el integrando tiene periodo $\pi$)
Suponiendo que $a>b$,
$$
\begin{align}
& \int_{0}^{2\pi}  \sqrt{a^{2}\cos^{2}(x) + b^{2}- b^{2}\cos^{2}(x)}\, dx \\[0.5em]
&= \int_{0}^{2\pi} \sqrt{b^{2} + (a^{2} - b^{2})\cos^{2}(x)} \, dx \tag{$\sin^{2} = 1 - \cos^{2}$}
\end{align}
$$
Entonces tenemos que aproximar, podemos hacerlo de las siguientes formas:

- Sumas inferiores, sumas superiores (Sumas de Darboux). Esta aproximación no siempre es la mejor.
$$
\sum_{k=0}^{n-1} \min_{[x_{k},x_{k+1}]} f \cdot (x_{k+1}-x_{k}) \quad \text{ y } \quad \sum_{k=0}^{n-1} \max_{[x_{k},x_{k+1}]} f \cdot (x_{k+1}-x_{k})
$$
(con $f$ continua; en general se usan $\inf$ y $\sup$, ver [[Suma Inferior y Superior]]).

- [[Sumas de Riemann]], la generalización de las anteriores.
$$
R(f,\mathcal{P},z) = \sum_{k=0}^{n-1} f(z_{k})(x_{k+1}-x_{k}) \quad z_{k} \in  [x_{k}, x_{k+1}]
$$
A partir de sumas de Riemann vemos: Aproximación por puntos medios.


### Aproximación por puntos medios

Considérese una partición equidistante dada por $\mathcal{P} = \{ a,a+\frac{b-a}{n}, a+\frac{2(b-a)}{n}, \dots, b \}$
Para estos puntos vamos a considerar sus puntos medios y esto va llevar a un refinamiento de $\mathcal{P}$ de la siguiente manera:
$$
\mathcal{P}' = \left\{ a , a+ \frac{1}{2}\left(\frac{b-a}{n}  \right) , a + \frac{b-a}{n}, \dots, b  \right\}
$$
Podemos nombrar a cada punto de mi partición como $\{ a = x_{0},x_{1},\dots,x_{2n} =b \}$ en donde observamos que los índices pares son los puntos de nuestra partición original $\mathcal{P}$, y los impares, los adicionales de refinamiento $\mathcal{P}'$.
Observamos que $\displaystyle x_{k+1} - x_{k} = \frac{b-a}{2n} \ \  \forall k$.
De esta forma, en la suma de Riemann evaluamos $f(x)$ en el punto medio ($x$ *impares*), y cada subintervalo de $\mathcal{P}$ mide $\frac{b-a}{n}$.
$$
\int_{a}^{b} f(x) \, dx \approx \sum_{k=0}^{n-1} \left(\frac{b-a}{n}  \right) f(x_{2k+1}) = \boxed{\left(\frac{b-a}{n}  \right) \cdot  \sum_{k=0}^{n-1} f(x_{2k+1})
}
$$


> [!Info]- **Nota!**
>
> Es "buena" aproximación para funciones monótonas (tomando $n$ "grande").
> En métodos numéricos lo que nos interesa es la eficiencia.

Otros métodos: [[Metodo de los Trapecios]], [[Metodo de Simpson]], [[Metodo de Taylor]].

