---
modified: 2026-11-15T18:07:51Z
title: "Integrales Trigonométricas"
publish: true
type: zettel
date: "2026-10-05"
status: seed
aliases:
tags:
 - calculus
cssclasses:
 - romana
---
Aquí van las pruebas. La tabla rápida de todas está en [[Fomulasos de Derivadas y Antiderivadas]]. Las herramientas son: identidades pitagóricas ($\sin^{2} + \cos^{2} = 1$, $1 + \tan^{2} = \sec^{2}$, $1 + \cot^{2} = \csc^{2}$), ángulo doble ($\sin^{2}(x) = \frac{1-\cos(2x)}{2}$, $\cos^{2}(x) = \frac{1+\cos(2x)}{2}$), [[Cambio de Variable]] e [[Integracion por Partes]].

Para cada función vamos en el mismo orden: potencias $1$, $2$ y $3$; luego la **fórmula de reducción** para $n \geq 2$ (que baja la potencia de $n$ a $n-2$ y, aplicada varias veces, resuelve cualquier potencia); y al final la integral de su **inversa**.

> [!tip|idea]- **Idea Intuitiva.** (Fórmulas de reducción)
>
> Para $\int f^{n}$ no buscamos una fórmula cerrada para cada $n$: buscamos escribirla en términos de $\int f^{n-2}$. Aplicándola una y otra vez, la potencia baja de dos en dos hasta llegar a $\int f$ o a $\int f^{0} = x$, que ya conocemos. Las de $\sin$, $\cos$, $\sec$, $\csc$ salen por partes (son integrales cíclicas); las de $\tan$, $\cot$, con la identidad pitagórica.

## Seno

> [!theorem] **Senos.**
>
> $$
> \begin{align}
> \int \sin(x) \, dx &= - \cos(x) + C \\[0.5em]
> \int \sin^{2}(x) \, dx &= \frac{x}{2} - \frac{\sin(2x)}{4} + C \\[0.5em]
> \int \sin^{3}(x) \, dx &= -\cos(x) + \frac{\cos^{3}(x)}{3} + C
> \end{align}
> $$

> [!proof]- **Proof.**
>
> 1. $(-\cos)' = \sin$.
> 2. $\displaystyle \int \sin^{2}(x) \, dx = \int \frac{1-\cos(2x)}{2} \, dx= \frac{1}{2}\left[ \int  \, dx - \int \cos(2x) \, dx  \right] = \frac{1}{2}\left[ x - \frac{\sin(2x)}{2}  \right] + C$
> 3. Separamos un $\sin$ y usamos $\sin^{2} = 1 - \cos^{2}$:
> $$
> \begin{align}
> & \int \sin^{3}(x) \, dx \\[0.5em]
> &= \int (1-\cos^{2}(x))\sin(x) \, dx \\[0.5em]
> &= \int \sin(x) \, dx - \int \sin(x)\cos^{2}(x) \, dx \\[0.5em]
> &= -\cos(x) + \int u^{2} \, du \tag{$u = \cos(x)$, $du = -\sin(x)\,dx$} \\[0.5em]
> &= -\cos(x) + \frac{\cos^{3}(x)}{3} + C \tag*{$\blacksquare$}
> \end{align}
> $$

> [!theorem] **Fórmula de reducción.** ($\sin^{n}$)
>
> Para $n \geq 2$,
> $$
> \int \sin^{n}(x) \, dx = -\frac{\sin^{n-1}(x)\cos(x)}{n} + \frac{n-1}{n}\int \sin^{n-2}(x) \, dx
> $$

> [!proof]- **Proof.**
>
> Partes con $u = \sin^{n-1}(x)$, $dv = \sin(x)\,dx$ ($du = (n-1)\sin^{n-2}(x)\cos(x)\,dx$, $v = -\cos(x)$):
> $$
> \begin{align}
> & \int \sin^{n}(x) \, dx \\[0.5em]
> &= -\sin^{n-1}(x)\cos(x) + (n-1)\int \sin^{n-2}(x)\cos^{2}(x) \, dx \\[0.5em]
> &= -\sin^{n-1}(x)\cos(x) \\[0.5em]
> &\quad + (n-1)\int \sin^{n-2}(x)\left( 1 - \sin^{2}(x) \right) dx \tag{$\cos^{2} = 1 - \sin^{2}$} \\[0.5em]
> &= -\sin^{n-1}(x)\cos(x) \\[0.5em]
> &\quad + (n-1)\int \sin^{n-2}(x) \, dx - (n-1)\int \sin^{n}(x) \, dx
> \end{align}
> $$
> Es cíclica: pasando $(n-1)\int \sin^{n}$ al lado izquierdo queda $n\int \sin^{n}(x)\,dx = -\sin^{n-1}(x)\cos(x) + (n-1)\int\sin^{n-2}(x)\,dx$, y dividimos entre $n$. $\blacksquare$

> [!example]- Ejemplo. ($\sin^{4}$)
>
> Con $n = 4$ y luego $n = 2$:
> $$
> \begin{align}
> & \int \sin^{4}(x) \, dx \\[0.5em]
> &= -\frac{\sin^{3}(x)\cos(x)}{4} + \frac{3}{4}\int \sin^{2}(x) \, dx \\[0.5em]
> &= -\frac{\sin^{3}(x)\cos(x)}{4} + \frac{3}{4}\left[ \frac{x}{2} - \frac{\sin(2x)}{4} \right] + C \\[0.5em]
> &= -\frac{\sin^{3}(x)\cos(x)}{4} + \frac{3x}{8} - \frac{3\sin(2x)}{16} + C
> \end{align}
> $$
> Con $n = 3$ se recupera $\int \sin^{3}$ de arriba: $-\frac{\sin^{2}\cos}{3} - \frac{2}{3}\cos = -\frac{(1-\cos^{2})\cos}{3} - \frac{2\cos}{3} = -\cos + \frac{\cos^{3}}{3}$ ✓.

> [!theorem] **Inversa.** ($\sin^{-1}$)
>
> Para $\left| x \right| < 1$,
> $$
> \int \sin^{-1}(x) \, dx = x\sin^{-1}(x) + \sqrt{1-x^{2}} + C
> $$

> [!proof]- **Proof.**
>
> Partes con $u = \sin^{-1}(x)$, $dv = dx$ ($du = \frac{dx}{\sqrt{1-x^{2}}}$, $v = x$):
> $$
> \begin{align}
> & \int \sin^{-1}(x) \, dx \\[0.5em]
> &= x\sin^{-1}(x) - \int \frac{x}{\sqrt{1-x^{2}}} \, dx \\[0.5em]
> &= x\sin^{-1}(x) + \frac{1}{2}\int w^{-\frac{1}{2}} \, dw \\[0.5em]
> &= x\sin^{-1}(x) + \sqrt{1-x^{2}} + C
> \end{align}
> $$
> con $w = 1-x^{2}$, $dw = -2x\,dx$. $\blacksquare$

> [!observation]+ **Observación.** (Potencias impares vs. pares)
>
> - **Impar:** se separa un $\sin(x)$ y el resto se pasa a cosenos con $\sin^{2} = 1 - \cos^{2}$; queda un polinomio en $u = \cos(x)$ (así salió $\sin^{3}$). Es más rápido que la reducción.
> - **Par:** no sobra ningún factor para el $du$, así que se baja el grado con el ángulo doble o con la fórmula de reducción.
>
> Con cosenos es igual, intercambiando papeles.

## Coseno

> [!theorem] **Cosenos.**
>
> $$
> \begin{align}
> \int \cos(x) \, dx &=  \sin(x) + C \\[0.5em]
> \int \cos^{2}(x) \, dx &= \frac{x}{2} + \frac{\sin(2x)}{4} + C \\[0.5em]
> \int \cos^{3}(x) \, dx &= \sin(x) - \frac{\sin^{3}(x)}{3} + C
> \end{align}
> $$

> [!proof]- **Proof.**
>
> 1. $(\sin)' = \cos$.
> 2. $\displaystyle \int \cos^{2}(x) \, dx = \int \frac{1+\cos(2x)}{2} \, dx = \frac{1}{2}\left[ x + \frac{\sin(2x)}{2} \right] + C$.
> 3. Separamos un $\cos$ y usamos $\cos^{2} = 1 - \sin^{2}$, con $u = \sin(x)$, $du = \cos(x)\,dx$:
> $$
> \begin{align}
> & \int \cos^{3}(x) \, dx \\[0.5em]
> &= \int (1 - \sin^{2}(x))\cos(x) \, dx \\[0.5em]
> &= \int (1-u^{2}) \, du \\[0.5em]
> &= \sin(x) - \frac{\sin^{3}(x)}{3} + C \tag*{$\blacksquare$}
> \end{align}
> $$

> [!theorem] **Fórmula de reducción.** ($\cos^{n}$)
>
> Para $n \geq 2$,
> $$
> \int \cos^{n}(x) \, dx = \frac{\cos^{n-1}(x)\sin(x)}{n} + \frac{n-1}{n}\int \cos^{n-2}(x) \, dx
> $$

> [!proof]- **Proof.**
>
> Partes con $u = \cos^{n-1}(x)$, $dv = \cos(x)\,dx$ ($du = -(n-1)\cos^{n-2}(x)\sin(x)\,dx$, $v = \sin(x)$):
> $$
> \begin{align}
> & \int \cos^{n}(x) \, dx \\[0.5em]
> &= \cos^{n-1}(x)\sin(x) + (n-1)\int \cos^{n-2}(x)\sin^{2}(x) \, dx \\[0.5em]
> &= \cos^{n-1}(x)\sin(x) \\[0.5em]
> &\quad + (n-1)\int \cos^{n-2}(x) \, dx - (n-1)\int \cos^{n}(x) \, dx \tag{$\sin^{2} = 1 - \cos^{2}$}
> \end{align}
> $$
> y despejando como con el seno, $n\int\cos^{n} = \cos^{n-1}\sin + (n-1)\int\cos^{n-2}$. $\blacksquare$

> [!theorem] **Inversa.** ($\cos^{-1}$)
>
> Para $\left| x \right| < 1$,
> $$
> \int \cos^{-1}(x) \, dx = x\cos^{-1}(x) - \sqrt{1-x^{2}} + C
> $$

> [!proof]- **Proof.**
>
> Partes con $u = \cos^{-1}(x)$, $dv = dx$ ($du = -\frac{dx}{\sqrt{1-x^{2}}}$, $v = x$):
> $$
> \int \cos^{-1}(x) \, dx = x\cos^{-1}(x) + \int \frac{x}{\sqrt{1-x^{2}}} \, dx = x\cos^{-1}(x) - \sqrt{1-x^{2}} + C
> $$
> (la última integral es la misma que en $\sin^{-1}$, con signo contrario). $\blacksquare$

## Tangente

> [!theorem] **Tangentes.**
>
> $$
> \begin{align}
> \int \tan(x) \, dx &= - \log \left|\cos(x)\right| + C = \log \left|\sec(x)\right| + C\\[0.5em]
> \int \tan^{2}(x) \, dx &= \tan(x) - x + C \\[0.5em]
> \int \tan^{3}(x) \, dx &= \frac{\tan^{2}(x)}{2} + \log\left| \cos(x) \right| + C
> \end{align}
> $$

> [!proof]- **Proof.**
>
> 1. $\displaystyle \int \frac{\sin(x)}{\cos(x)} \, dx = -\int \frac{du}{u} = -\log\left| u \right| + C = -\log\left| \cos(x) \right| + C$, con $u = \cos(x)$, $du = -\sin(x)\,dx$. Y $-\log\left| \cos \right| = \log\left| \frac{1}{\cos} \right| = \log\left| \sec \right|$.
> 2. $\displaystyle \int \tan^{2}(x) \, dx = \int (\sec^{2}(x) - 1) \, dx = \tan(x) - x + C$, pues $1 + \tan^{2} = \sec^{2}$.
> 3. Separamos un $\tan^{2} = \sec^{2} - 1$:
> $$
> \int \tan^{3}(x) \, dx = \int \tan(x)\sec^{2}(x) \, dx - \int \tan(x) \, dx = \frac{\tan^{2}(x)}{2} + \log\left| \cos(x) \right| + C
> $$
> con $u = \tan(x)$, $du = \sec^{2}(x)\,dx$ en la primera. $\blacksquare$

> [!note]- La "contradicción" con $\int \tan$
>
> Si intentamos partes con $u = \frac{1}{\cos(x)}$, $dv = \sin(x)\,dx$ ($v = -\cos(x)$, $du = \frac{\sin(x)}{\cos^{2}(x)}dx$):
> $$
> \int \tan(x) \, dx = \frac{-\cos(x)}{\cos(x)} - \int (-\cos(x))\frac{\sin(x)}{\cos^{2}(x)} \, dx = -1 + \int \tan(x) \, dx
> $$
> y "restando" $\int\tan$ de ambos lados, $0 = -1$. No hay contradicción: $\int \tan(x)\,dx$ es una **familia** de antiderivadas que difieren por una constante (la $+C$), y $-1 + (\text{familia}) = (\text{familia})$. Lo que es falso es restar $\int$ como si fuera un número.

> [!theorem] **Fórmula de reducción.** ($\tan^{n}$)
>
> Para $n \geq 2$,
> $$
> \int \tan^{n}(x) \, dx = \frac{\tan^{n-1}(x)}{n-1} - \int \tan^{n-2}(x) \, dx
> $$

> [!proof]- **Proof.**
>
> Aquí no hacen falta partes: separamos $\tan^{2} = \sec^{2} - 1$,
> $$
> \begin{align}
> & \int \tan^{n}(x) \, dx \\[0.5em]
> &= \int \tan^{n-2}(x)\sec^{2}(x) \, dx - \int \tan^{n-2}(x) \, dx \\[0.5em]
> &= \frac{\tan^{n-1}(x)}{n-1} - \int \tan^{n-2}(x) \, dx
> \end{align}
> $$
> con $u = \tan(x)$, $du = \sec^{2}(x)\,dx$ en la primera ($\int u^{n-2}\,du = \frac{u^{n-1}}{n-1}$). Con $n = 2$ y $n = 3$ se recuperan las de arriba. $\blacksquare$

> [!theorem] **Inversa.** ($\tan^{-1}$)
>
> $$
> \int \tan^{-1}(x) \, dx = x\tan^{-1}(x) - \frac{1}{2}\log\left( 1+x^{2} \right) + C
> $$

> [!proof]- **Proof.**
>
> Partes con $u = \tan^{-1}(x)$, $dv = dx$ ($du = \frac{dx}{1+x^{2}}$, $v = x$):
> $$
> \int \tan^{-1}(x) \, dx = x\tan^{-1}(x) - \int \frac{x}{1+x^{2}} \, dx = x\tan^{-1}(x) - \frac{1}{2}\log\left( 1+x^{2} \right) + C
> $$
> con $w = 1+x^{2}$, $dw = 2x\,dx$ (y $1 + x^{2} > 0$, así que no hace falta valor absoluto). $\blacksquare$

## Secante

> [!theorem] **Secantes.**
>
> $$
> \begin{align}
> \int \sec(x) \, dx &= \log\left| \sec(x) + \tan(x) \right| + C \\[0.5em]
> \int \sec^{2}(x) \, dx&= \tan(x) + C \\[0.5em]
> \int \sec^{3}(x) \, dx &= \frac{1}{2}\left[ \sec(x)\tan(x) + \log\left| \sec(x) + \tan(x) \right| \right] + C
> \end{align}
> $$

> [!proof]- **Proof.**
>
> 1. Multiplicamos por un 1 conveniente:
> $$
> \begin{align}
> & \int \sec(x) \left(\frac{\sec(x)+\tan(x)}{\sec(x)+\tan(x)}  \right) \, dx \\[0.5em]
> &= \int \frac{\sec^{2}(x) + \sec(x)\tan(x)}{\sec(x)+\tan(x)} \, dx \\[0.5em]
> &= \int \frac{du}{u} \\[0.5em]
> &= \log\left| \sec(x) + \tan(x) \right| + C
> \end{align}
> $$
> con $u = \sec(x)+\tan(x)$, pues $du = (\sec(x)\tan(x) + \sec^{2}(x))\,dx$ es justo el numerador.
> 2. $(\tan)' = \sec^{2}$.
> 3. Partes con $u = \sec(x)$, $dv = \sec^{2}(x)\,dx$ ($du = \sec(x)\tan(x)\,dx$, $v = \tan(x)$):
> $$
> \begin{align}
> \int \sec^{3}(x) \, dx &= \sec(x)\tan(x) - \int \sec(x)\tan^{2}(x) \, dx \\[0.5em]
> &= \sec(x)\tan(x) - \int \sec(x)(\sec^{2}(x) - 1) \, dx \tag{$\tan^{2} = \sec^{2}-1$} \\[0.5em]
> &= \sec(x)\tan(x) - \int \sec^{3}(x) \, dx + \int \sec(x) \, dx
> \end{align}
> $$
> Es una integral cíclica: pasando $\int \sec^{3}$ al otro lado, $\displaystyle 2\int \sec^{3}(x) \, dx = \sec(x)\tan(x) + \log\left| \sec(x)+\tan(x) \right| + C$. $\blacksquare$

> [!theorem] **Fórmula de reducción.** ($\sec^{n}$)
>
> Para $n \geq 2$,
> $$
> \int \sec^{n}(x) \, dx = \frac{\sec^{n-2}(x)\tan(x)}{n-1} + \frac{n-2}{n-1}\int \sec^{n-2}(x) \, dx
> $$

> [!proof]- **Proof.**
>
> Es la generalización de la prueba de $\sec^{3}$. Partes con $u = \sec^{n-2}(x)$, $dv = \sec^{2}(x)\,dx$ ($du = (n-2)\sec^{n-2}(x)\tan(x)\,dx$, $v = \tan(x)$):
> $$
> \begin{align}
> & \int \sec^{n}(x) \, dx \\[0.5em]
> &= \sec^{n-2}(x)\tan(x) - (n-2)\int \sec^{n-2}(x)\tan^{2}(x) \, dx \\[0.5em]
> &= \sec^{n-2}(x)\tan(x) \\[0.5em]
> &\quad - (n-2)\int \sec^{n}(x) \, dx + (n-2)\int \sec^{n-2}(x) \, dx \tag{$\tan^{2} = \sec^{2}-1$}
> \end{align}
> $$
> Pasando $(n-2)\int\sec^{n}$ al lado izquierdo, $(n-1)\int \sec^{n} = \sec^{n-2}\tan + (n-2)\int\sec^{n-2}$, y dividimos entre $n - 1 \neq 0$. $\blacksquare$

> [!theorem] **Inversa.** ($\sec^{-1}$)
>
> Para $\left| x \right| > 1$,
> $$
> \int \sec^{-1}(x) \, dx = x\sec^{-1}(x) - \operatorname{sgn}(x)\log\left| x + \sqrt{x^{2}-1} \right| + C
> $$
> (para $x > 1$, simplemente $x\sec^{-1}(x) - \log\left( x + \sqrt{x^{2}-1} \right) + C$).

> [!proof]- **Proof.**
>
> Partes con $u = \sec^{-1}(x)$, $dv = dx$ ($du = \frac{dx}{\left| x \right|\sqrt{x^{2}-1}}$, $v = x$):
> $$
> \begin{align}
> & \int \sec^{-1}(x) \, dx \\[0.5em]
> &= x\sec^{-1}(x) - \int \frac{x}{\left| x \right|\sqrt{x^{2}-1}} \, dx \\[0.5em]
> &= x\sec^{-1}(x) - \operatorname{sgn}(x)\int \frac{dx}{\sqrt{x^{2}-1}}
> \end{align}
> $$
> pues $\frac{x}{\left| x \right|} = \operatorname{sgn}(x)$ es constante en cada intervalo $(1,\infty)$ y $(-\infty,-1)$. La última integral es $\log\left| x + \sqrt{x^{2}-1} \right|$ (ver [[Fomulasos de Derivadas y Antiderivadas]]; sale con [[Sustitucion Trigonometrica]], Caso 3, o con [[Metodo de Euler]]). $\blacksquare$

## Cosecante

> [!theorem] **Cosecantes.**
>
> $$
> \begin{align}
> \int \csc(x) \, dx &= -\log\left| \csc(x) + \cot(x) \right| + C = \log\left| \csc(x) - \cot(x) \right| + C \\[0.5em]
> \int \csc^{2}(x) \, dx&= -\cot(x) + C \\[0.5em]
> \int \csc^{3}(x) \, dx &= -\frac{1}{2}\left[ \csc(x)\cot(x) + \log\left| \csc(x) + \cot(x) \right| \right] + C
> \end{align}
> $$

> [!proof]- **Proof.**
>
> Igual que con secantes, usando $(\csc)' = -\csc\cot$ y $(\cot)' = -\csc^{2}$:
> 1. Con $u = \csc(x) + \cot(x)$, $du = -(\csc(x)\cot(x) + \csc^{2}(x))\,dx$, ent. $\displaystyle \int \csc(x) \frac{\csc(x)+\cot(x)}{\csc(x)+\cot(x)} \, dx = -\int \frac{du}{u} = -\log\left| \csc(x)+\cot(x) \right| + C$. La segunda forma sale de $(\csc + \cot)(\csc - \cot) = \csc^{2} - \cot^{2} = 1$.
> 2. $(-\cot)' = \csc^{2}$.
> 3. Partes con $u = \csc(x)$, $dv = \csc^{2}(x)\,dx$ ($du = -\csc(x)\cot(x)\,dx$, $v = -\cot(x)$) y $\cot^{2} = \csc^{2} - 1$:
> $$
> \int \csc^{3}(x) \, dx = -\csc(x)\cot(x) - \int \csc^{3}(x) \, dx + \int \csc(x) \, dx
> $$
> y despejando como en $\sec^{3}$ sale el resultado. $\blacksquare$

> [!theorem] **Fórmula de reducción.** ($\csc^{n}$)
>
> Para $n \geq 2$,
> $$
> \int \csc^{n}(x) \, dx = -\frac{\csc^{n-2}(x)\cot(x)}{n-1} + \frac{n-2}{n-1}\int \csc^{n-2}(x) \, dx
> $$

> [!proof]- **Proof.**
>
> Partes con $u = \csc^{n-2}(x)$, $dv = \csc^{2}(x)\,dx$ ($du = -(n-2)\csc^{n-2}(x)\cot(x)\,dx$, $v = -\cot(x)$):
> $$
> \begin{align}
> & \int \csc^{n}(x) \, dx \\[0.5em]
> &= -\csc^{n-2}(x)\cot(x) - (n-2)\int \csc^{n-2}(x)\cot^{2}(x) \, dx \\[0.5em]
> &= -\csc^{n-2}(x)\cot(x) \\[0.5em]
> &\quad - (n-2)\int \csc^{n}(x) \, dx + (n-2)\int \csc^{n-2}(x) \, dx \tag{$\cot^{2} = \csc^{2}-1$}
> \end{align}
> $$
> y despejando, $(n-1)\int\csc^{n} = -\csc^{n-2}\cot + (n-2)\int\csc^{n-2}$. $\blacksquare$

> [!theorem] **Inversa.** ($\csc^{-1}$)
>
> Para $\left| x \right| > 1$,
> $$
> \int \csc^{-1}(x) \, dx = x\csc^{-1}(x) + \operatorname{sgn}(x)\log\left| x + \sqrt{x^{2}-1} \right| + C
> $$

> [!proof]- **Proof.**
>
> Igual que $\sec^{-1}$, ahora con $du = -\frac{dx}{\left| x \right|\sqrt{x^{2}-1}}$:
> $$
> \begin{align}
> & \int \csc^{-1}(x) \, dx \\[0.5em]
> &= x\csc^{-1}(x) + \operatorname{sgn}(x)\int \frac{dx}{\sqrt{x^{2}-1}} \\[0.5em]
> &= x\csc^{-1}(x) + \operatorname{sgn}(x)\log\left| x + \sqrt{x^{2}-1} \right| + C \tag*{$\blacksquare$}
> \end{align}
> $$

## Cotangente

> [!theorem] **Cotangentes.**
>
> $$
> \begin{align}
> \int \cot(x) \, dx &= \log\left| \sin(x) \right| + C \\[0.5em]
> \int \cot^{2}(x) \, dx &= -\cot(x) - x + C \\[0.5em]
> \int \cot^{3}(x) \, dx &= -\frac{\cot^{2}(x)}{2} - \log\left| \sin(x) \right| + C
> \end{align}
> $$

> [!proof]- **Proof.**
>
> 1. $\displaystyle \int \frac{\cos(x)}{\sin(x)} \, dx = \int \frac{du}{u} = \log\left| \sin(x) \right| + C$, con $u = \sin(x)$.
> 2. $\displaystyle \int \cot^{2}(x) \, dx = \int (\csc^{2}(x) - 1) \, dx = -\cot(x) - x + C$, pues $1 + \cot^{2} = \csc^{2}$.
> 3. Separamos $\cot^{2} = \csc^{2} - 1$, con $u = \cot(x)$, $du = -\csc^{2}(x)\,dx$ en la primera:
> $$
> \begin{align}
> & \int \cot^{3}(x) \, dx \\[0.5em]
> &= \int \cot(x)\csc^{2}(x) \, dx - \int \cot(x) \, dx \\[0.5em]
> &= -\frac{\cot^{2}(x)}{2} - \log\left| \sin(x) \right| + C \tag*{$\blacksquare$}
> \end{align}
> $$

> [!theorem] **Fórmula de reducción.** ($\cot^{n}$)
>
> Para $n \geq 2$,
> $$
> \int \cot^{n}(x) \, dx = -\frac{\cot^{n-1}(x)}{n-1} - \int \cot^{n-2}(x) \, dx
> $$

> [!proof]- **Proof.**
>
> Como con la tangente, separamos $\cot^{2} = \csc^{2} - 1$ y usamos $u = \cot(x)$, $du = -\csc^{2}(x)\,dx$:
> $$
> \begin{align}
> & \int \cot^{n}(x) \, dx \\[0.5em]
> &= \int \cot^{n-2}(x)\csc^{2}(x) \, dx - \int \cot^{n-2}(x) \, dx \\[0.5em]
> &= -\frac{\cot^{n-1}(x)}{n-1} - \int \cot^{n-2}(x) \, dx \tag*{$\blacksquare$}
> \end{align}
> $$

> [!theorem] **Inversa.** ($\cot^{-1}$)
>
> $$
> \int \cot^{-1}(x) \, dx = x\cot^{-1}(x) + \frac{1}{2}\log\left( 1+x^{2} \right) + C
> $$

> [!proof]- **Proof.**
>
> Partes con $u = \cot^{-1}(x)$, $dv = dx$ ($du = -\frac{dx}{1+x^{2}}$, $v = x$):
> $$
> \begin{align}
> & \int \cot^{-1}(x) \, dx \\[0.5em]
> &= x\cot^{-1}(x) + \int \frac{x}{1+x^{2}} \, dx \\[0.5em]
> &= x\cot^{-1}(x) + \frac{1}{2}\log\left( 1+x^{2} \right) + C \tag*{$\blacksquare$}
> \end{align}
> $$
