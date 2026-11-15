---
modified: 2026-11-15T17:42:06Z
title: "Memorial de Integrales y Derivadas"
publish: true
type: zettel
date: 2026-09-18
status: seed
aliases:
tags:
  - calculus
cssclasses:
  - romana
---
Integración directa, denotaremos por $\displaystyle \int f(x) \, dx$ a **la** antiderivada (en su concepto más general). En todas las integrales se sobreentiende el $+\,C$. Las pruebas están en las notas enlazadas.

## Derivadas

> [!theorem] **Reglas de derivación**
>
> | Regla | Fórmula | Condición |
> |:--|:--:|:--|
> | Linealidad | $\left[ \alpha f + \beta g \right]' = \alpha f' + \beta g'$ | |
> | Leibniz (producto) | $(fg)' = f'g + fg'$ | |
> | Cociente | $\left(\dfrac{f}{g}\right)' = \dfrac{f'g - fg'}{g^{2}}$ | $g(x) \neq 0$ |
> | Cadena | $(f \circ g)'(x) = f'(g(x))\,g'(x)$ | |
> | Inversa | $\left(f^{-1}\right)'(x) = \dfrac{1}{f'(f^{-1}(x))}$ | $f'(f^{-1}(x)) \neq 0$ |
> | Derivación logarítmica | $\left(f^{g}\right)' = f^{g}\left[ g' \log(f) + g\dfrac{f'}{f} \right]$ | $f(x) > 0$ |

> [!theorem] **Derivadas comunes**
>
> | $f(x)$ | $f'(x)$ | Condición |
> |:--:|:--:|:--|
> | $x^{n}$ | $nx^{n-1}$ | |
> | $e^{x}$ | $e^{x}$ | |
> | $a^{x}$ | $a^{x}\log(a)$ | $a>0,\ a\neq 1$ |
> | $\log(x)$ | $\dfrac{1}{x}$ | $x > 0$ |
> | $\log_{a}(x)$ | $\dfrac{1}{x\log(a)}$ | $x>0,\ a>0,\ a\neq 1$ |

> [!theorem] **Trigonométricas y sus inversas**
>
> | $f(x)$ | $f'(x)$ | | $f(x)$ | $f'(x)$ | Condición |
> |:--:|:--:|:--:|:--:|:--:|:--|
> | $\sin(x)$ | $\cos(x)$ | | $\sin^{-1}(x)$ | $\dfrac{1}{\sqrt{1-x^{2}}}$ | $\lvert x \rvert < 1$ |
> | $\cos(x)$ | $-\sin(x)$ | | $\cos^{-1}(x)$ | $-\dfrac{1}{\sqrt{1-x^{2}}}$ | $\lvert x \rvert < 1$ |
> | $\tan(x)$ | $\sec^{2}(x)$ | | $\tan^{-1}(x)$ | $\dfrac{1}{1+x^{2}}$ | |
> | $\cot(x)$ | $-\csc^{2}(x)$ | | $\cot^{-1}(x)$ | $-\dfrac{1}{1+x^{2}}$ | |
> | $\sec(x)$ | $\sec(x)\tan(x)$ | | $\sec^{-1}(x)$ | $\dfrac{1}{\lvert x \rvert\sqrt{x^{2}-1}}$ | $\lvert x \rvert > 1$ |
> | $\csc(x)$ | $-\csc(x)\cot(x)$ | | $\csc^{-1}(x)$ | $-\dfrac{1}{\lvert x \rvert\sqrt{x^{2}-1}}$ | $\lvert x \rvert > 1$ |

> [!theorem] **Hiperbólicas y sus inversas**
>
> | $f(x)$ | $f'(x)$ | | $f(x)$ | $f'(x)$ | Condición |
> |:--:|:--:|:--:|:--:|:--:|:--|
> | $\sinh(x)$ | $\cosh(x)$ | | $\sinh^{-1}(x)$ | $\dfrac{1}{\sqrt{x^{2}+1}}$ | |
> | $\cosh(x)$ | $\sinh(x)$ | | $\cosh^{-1}(x)$ | $\dfrac{1}{\sqrt{x^{2}-1}}$ | $x > 1$ |
> | $\tanh(x)$ | $\operatorname{sech}^{2}(x)$ | | $\tanh^{-1}(x)$ | $\dfrac{1}{1-x^{2}}$ | $\lvert x \rvert < 1$ |
>
> Más en [[Funciones Hiperbolicas]].

## Integrales

> [!theorem] **Reglas de integración**
>
> | Regla | Fórmula | Nota |
> |:--|:--:|:--|
> | Linealidad | $\displaystyle\int \left[ \alpha f + \beta g \right] dx = \alpha \int f\,dx + \beta \int g\,dx$ | |
> | Partes | $\displaystyle\int u \, dv = uv - \int v \, du$ | [[Integracion por Partes]] |
> | Cambio de variable | $\displaystyle\int f(g(x))g'(x) \, dx = \int f(u) \, du,\ u = g(x)$ | [[Cambio de Variable]] |
> | T.F.C. 1 | $\displaystyle\frac{d}{dx}\int_{a}^{x} f(t) \, dt = f(x)$ | $f$ continua |
> | T.F.C. 2 | $\displaystyle\int_{a}^{b} f(x) \, dx = F(b) - F(a)$ | $F' = f$ |
> | T.V.M. (integrales) | $\displaystyle\int_{a}^{b} f(x) \, dx = f(c)(b-a)$ para algún $c \in (a,b)$ | $f$ continua |

> [!theorem] **Integrales comunes**
>
> | $f(x)$ | $\displaystyle\int f(x)\,dx$ | Condición |
> |:--:|:--:|:--|
> | $1$ | $x$ | |
> | $x^{m}$ | $\dfrac{x^{m+1}}{m+1}$ | $m \neq -1$ |
> | $\dfrac{1}{x^{m}}$ | $\dfrac{1}{(1-m)\,x^{m-1}}$ | $m > 1$ |
> | $\dfrac{1}{x}$ | $\log\lvert x \rvert$ | $x \neq 0$ |
> | $e^{x}$ | $e^{x}$ | |
> | $a^{x}$ | $\dfrac{a^{x}}{\log(a)}$ | $a>0,\ a\neq 1$ |
> | $\log(x)$ | $x\log(x) - x$ | $x > 0$ (por partes) |

> [!theorem] **Trigonométricas (pruebas en [[Integrales Trigonometricas]])**
>
> | $f(x)$ | $\displaystyle\int f(x)\,dx$ | | $f(x)$ | $\displaystyle\int f(x)\,dx$ |
> |:--:|:--:|:--:|:--:|:--:|
> | $\sin(x)$ | $-\cos(x)$ | | $\sin^{2}(x)$ | $\dfrac{x}{2} - \dfrac{\sin(2x)}{4}$ |
> | $\cos(x)$ | $\sin(x)$ | | $\cos^{2}(x)$ | $\dfrac{x}{2} + \dfrac{\sin(2x)}{4}$ |
> | $\tan(x)$ | $\log\lvert\sec(x)\rvert = -\log\lvert\cos(x)\rvert$ | | $\tan^{2}(x)$ | $\tan(x) - x$ |
> | $\cot(x)$ | $\log\lvert\sin(x)\rvert$ | | $\cot^{2}(x)$ | $-\cot(x) - x$ |
> | $\sec(x)$ | $\log\lvert\sec(x) + \tan(x)\rvert$ | | $\sec^{2}(x)$ | $\tan(x)$ |
> | $\csc(x)$ | $\log\lvert\csc(x) - \cot(x)\rvert$ | | $\csc^{2}(x)$ | $-\cot(x)$ |
> | $\sin^{3}(x)$ | $-\cos(x) + \dfrac{\cos^{3}(x)}{3}$ | | $\sec^{3}(x)$ | $\dfrac{\sec(x)\tan(x) + \log\lvert\sec(x)+\tan(x)\rvert}{2}$ |
> | $\cos^{3}(x)$ | $\sin(x) - \dfrac{\sin^{3}(x)}{3}$ | | $\csc^{3}(x)$ | $-\dfrac{\csc(x)\cot(x) + \log\lvert\csc(x)+\cot(x)\rvert}{2}$ |
> | $\tan^{3}(x)$ | $\dfrac{\tan^{2}(x)}{2} + \log\lvert\cos(x)\rvert$ | | $\cot^{3}(x)$ | $-\dfrac{\cot^{2}(x)}{2} - \log\lvert\sin(x)\rvert$ |

> [!theorem] **Fórmulas de reducción ($n \geq 2$)**
>
> | $f(x)$ | $\displaystyle\int f(x)\,dx$ |
> |:--:|:--:|
> | $\sin^{n}(x)$ | $\displaystyle -\frac{\sin^{n-1}(x)\cos(x)}{n} + \frac{n-1}{n}\int \sin^{n-2}(x)\,dx$ |
> | $\cos^{n}(x)$ | $\displaystyle \frac{\cos^{n-1}(x)\sin(x)}{n} + \frac{n-1}{n}\int \cos^{n-2}(x)\,dx$ |
> | $\tan^{n}(x)$ | $\displaystyle \frac{\tan^{n-1}(x)}{n-1} - \int \tan^{n-2}(x)\,dx$ |
> | $\cot^{n}(x)$ | $\displaystyle -\frac{\cot^{n-1}(x)}{n-1} - \int \cot^{n-2}(x)\,dx$ |
> | $\sec^{n}(x)$ | $\displaystyle \frac{\sec^{n-2}(x)\tan(x)}{n-1} + \frac{n-2}{n-1}\int \sec^{n-2}(x)\,dx$ |
> | $\csc^{n}(x)$ | $\displaystyle -\frac{\csc^{n-2}(x)\cot(x)}{n-1} + \frac{n-2}{n-1}\int \csc^{n-2}(x)\,dx$ |

> [!theorem] **Inversas trigonométricas**
>
> | $f(x)$ | $\displaystyle\int f(x)\,dx$ | Condición |
> |:--:|:--:|:--|
> | $\sin^{-1}(x)$ | $x\sin^{-1}(x) + \sqrt{1-x^{2}}$ | $\lvert x \rvert < 1$ |
> | $\cos^{-1}(x)$ | $x\cos^{-1}(x) - \sqrt{1-x^{2}}$ | $\lvert x \rvert < 1$ |
> | $\tan^{-1}(x)$ | $x\tan^{-1}(x) - \frac{1}{2}\log(1+x^{2})$ | |
> | $\cot^{-1}(x)$ | $x\cot^{-1}(x) + \frac{1}{2}\log(1+x^{2})$ | |
> | $\sec^{-1}(x)$ | $x\sec^{-1}(x) - \operatorname{sgn}(x)\log\lvert x + \sqrt{x^{2}-1} \rvert$ | $\lvert x \rvert > 1$ |
> | $\csc^{-1}(x)$ | $x\csc^{-1}(x) + \operatorname{sgn}(x)\log\lvert x + \sqrt{x^{2}-1} \rvert$ | $\lvert x \rvert > 1$ |

> [!theorem] **Hiperbólicas**
>
> | $f(x)$ | $\displaystyle\int f(x)\,dx$ |
> |:--:|:--:|
> | $\sinh(x)$ | $\cosh(x)$ |
> | $\cosh(x)$ | $\sinh(x)$ |
> | $\tanh(x)$ | $\log(\cosh(x))$ |
> | $\operatorname{sech}(x)$ | $\tan^{-1}(\sinh(x))$ |

> [!theorem] **Formas racionales e irracionales especiales**
>
> | $f(x)$ | $\displaystyle\int f(x)\,dx$ | Condición |
> |:--:|:--:|:--|
> | $\dfrac{1}{x^{2}+a^{2}}$ | $\dfrac{1}{a}\tan^{-1}\left(\dfrac{x}{a}\right)$ | $a \neq 0$ |
> | $\dfrac{1}{\sqrt{1-x^{2}}}$ | $\sin^{-1}(x)$ | $\lvert x \rvert < 1$ |
> | $\dfrac{1}{\sqrt{a^{2}-x^{2}}}$ | $\sin^{-1}\left(\dfrac{x}{a}\right)$ | $a > 0,\ \lvert x \rvert < a$ |
> | $\dfrac{1}{x\sqrt{x^{2}-a^{2}}}$ | $\dfrac{1}{a}\sec^{-1}\left(\dfrac{\lvert x \rvert}{a}\right)$ | $a > 0,\ \lvert x \rvert > a$ |
> | $\dfrac{1}{a^{2}-x^{2}}$ | $\dfrac{1}{2a}\log\left\lvert \dfrac{a+x}{a-x} \right\rvert$ | $\lvert x \rvert \neq a$ |
> | $\dfrac{1}{x^{2}-a^{2}}$ | $\dfrac{1}{2a}\log\left\lvert \dfrac{x-a}{x+a} \right\rvert$ | $\lvert x \rvert \neq a$ |
> | $\dfrac{1}{\sqrt{x^{2}\pm a^{2}}}$ | $\log\left\lvert x + \sqrt{x^{2}\pm a^{2}} \right\rvert$ | |
>
> Las de raíces salen por [[Sustitucion Trigonometrica]] (o [[Metodo de Euler]]) y las de cocientes por [[Fracciones Parciales]].

