---
modified: 2026-11-15T18:17:46Z
title: "Integrales Impropias"
publish: true
type: zettel
date: "2026-10-01"
status: seed
aliases:
tags:
 - calculus
cssclasses: 
 - romana
---
> [!tip|idea]+ **Idea Intuitiva.**
>
> Un área sobre un intervalo infinito puede ser finita: integramos hasta $b$ (eso ya sabemos hacerlo) y vemos qué pasa al mandar $b \to \infty$. Si el área acumulada se estabiliza, la integral converge; si crece sin cota, diverge. Que $f \to 0$ no basta: depende de **qué tan rápido** se va a $0$.
>
> <img src="/videos/integral-impropia.avif" alt="center" width="720" loading="lazy">
>
> *Funciones:* $\frac{1}{x^{2}}$ (el área tiende a $1$) contra $\frac{1}{x}$ (el área es $\log(b) \to \infty$), las integrales $p$ de abajo con $p = 2$ y $p = 1$.

> [!theorem] **Definición 1.** (Integral Impropia de 1ra Clase)
>
> Sea $f: [a,\infty) \to \mathbb{R}$ tal que $f$ es integrable en $[a,b]$ para toda $b>a$. Definimos como
> $$
> \int_{a}^{\infty} f(x) \, dx = \lim_{b\to \infty } \int_{a}^{b} f(x) \, dx
> $$
> En caso de existir decimos que $\int_{a}^{\infty} f(x) \, dx$ es una **integral impropia de primera clase**.
>

> [!example]- Ejemplo.
>
> Calculamos: $\displaystyle \int_{0}^{\infty} \frac{1}{1+x^{2}} \, dx = ?$
> $$
> \int_{0}^{b} \frac{1}{1+x^{2}} \, dx  = \tan^{-1}(x) \bigg|_{0}^{b} = \tan^{-1}(b) - \tan^{-1}(0) = \tan^{-1}(b)
> $$
> Con esto. $\displaystyle \int_{0}^{\infty} \frac{dx}{1+x^{2}} = \lim_{b \to \infty} \tan^{-1}(b) = \frac{\pi}{2}$


> [!Info]- **¡Nótese!** 
>
> Dado lo anterior, el valor de $\displaystyle \pi = 2 \int_{0}^{\infty} \frac{1}{1+x^{2}} \, dx$


> [!theorem] **Definición 2.** (Integral Impropia de 2da Clase)
>
> Sea $f$ definida en $[a,b]$ excepto quizá en $b$ (i.e. $f: [a,b) \to \mathbb{R}$). Supongamos que $f$ es integrable en $[a,c]$ para toda $c \in  (a,b)$. Entonces definimos
> $$
> \int_{a}^{b} f(x) \, dx = \lim_{c \to b^{-}} \int_{a}^{c} f(x) \, dx
> $$
> De existir, decimos que $\int_{a}^{b} f(x) \, dx$ es una **integral impropia de segunda clase**.
>

> [!observation]+ **Observación.**
>
> Análogamente, sea $f$ definida en $[a,b]$ excepto quizá en $a$. Sup. $f$ integrable en $[c,b] \quad \forall c \in  (a,b)$. Entonces $\displaystyle \int_{a}^{b} f(x) \, dx = \lim_{c \to a^{+}} \int_{c}^{b} f(x) \, dx$.
>



> [!example]- Ejemplo.
>
> $\displaystyle \square \int_{0}^{1} \frac{1}{\sqrt{x}} \, dx = \lim_{c \to 0^{+}} \int_{c}^{1} \frac{1}{\sqrt{x}} \, dx = \lim_{c \to 0^{+}} 2\sqrt{x} \ \bigg|_{c}^{1}$. Así, $\displaystyle \lim_{c \to 0^{+}} (2\sqrt{1} - 2\sqrt{c}) = 2$

> [!example]- Ejemplo. (Integrales $p$)
>
> $\displaystyle \int_{1}^{\infty} \frac{dx}{x^{p}}$ converge $\iff p > 1$, y en ese caso vale $\frac{1}{p-1}$.
> - Si $p \neq 1$: $\displaystyle \int_{1}^{b} x^{-p} \, dx = \frac{b^{1-p} - 1}{1-p}$. Si $p > 1$, $b^{1-p} \to 0$ y el límite es $\frac{1}{p-1}$; si $p < 1$, $b^{1-p} \to \infty$ y diverge.
> - Si $p = 1$: $\displaystyle \int_{1}^{b} \frac{dx}{x} = \log(b) \to \infty$, diverge.
>
> En particular $\displaystyle \int_{1}^{\infty} \frac{dx}{x^{2}} = 1$ y $\displaystyle \int_{1}^{\infty} \frac{dx}{x}$ diverge (compárese con las [[P-Series]]).


> [!theorem] **Definición 3.**
>
> Supongamos que $f: \mathbb{R} \to \mathbb{R}$ es tal que $f$ es integrable para todo intervalo cerrado y acotado $[a,b] \subseteq \mathbb{R}$, sea $c \in \mathbb{R}$, definimos
> $$
> \int_{-\infty}^{\infty} f(x) \, dx = \int_{-\infty}^{c} f(x) \, dx + \int_{c}^{\infty} f(x) \, dx
> $$
> si estas dos últimas integrales existen, para algún $c \in \mathbb{R}$ (si existen para un $c$, existen para todos y el valor no depende de $c$, por aditividad de la integral).

Obsérvese que la *Def. 3* es una *integral impropia de 1ra clase*.

> [!theorem] **Definición 4.** (Valor Principal de Cauchy)
>
> Sea $f:\mathbb{R}\to \mathbb{R}$ integrable en todo $[a,b] \subseteq \mathbb{R}$. Definimos el **valor principal de Cauchy** como
> $$
> \lim_{c \to \infty} \int_{-c}^{c} f(x) \, dx
> $$

> [!observation]+ **Observación.**
>
> 1. Las definiciones 3 y 4 pueden confundirse, pero no son lo mismo. Si $\int_{-\infty}^{\infty} f(x)\,dx$ existe, entonces sí coinciden:
> $$
> \int_{-\infty}^{\infty} f(x) \, dx = \lim_{c \to \infty} \int_{-c}^{c} f(x) \, dx
> $$
> (pues $\int_{-c}^{c} f = \int_{-c}^{0} f + \int_{0}^{c} f$ y cada sumando converge a su integral impropia).
>
> 2. Puede existir el valor principal de Cauchy pero no existir la integral impropia $\int_{-\infty}^{\infty} f(x) \, dx$.
>
> > [!example]- Ejemplo. (Obs. 2)
> >
> > $f(x) = x$, $f: \mathbb{R}\to \mathbb{R}$
> > Def 4: $\displaystyle \int_{-c}^{c} x \, dx = \frac{x^{2}}{2}\bigg|_{-c}^{c} = \frac{c^{2}}{2} - \frac{c^{2}}{2} = 0 \overset{c \to  \infty}{\longrightarrow} 0$
> > Def 3: $\displaystyle \int_{0}^{c} x \, dx = \frac{x^{2}}{2} \ \bigg|_{0}^{c} = \frac{c^{2}}{2} \overset{c\to \infty}{\longrightarrow} \infty$
>
> 3. ¡El valor principal de Cauchy es simétrico! Usa los mismos límites $-c$ y $c$, por eso las áreas de una función impar se cancelan aunque cada lado diverja.


> [!theorem] **Definición 5.**
>
> Sea $f$ definida en $[a,b]$ excepto quizá en $c \in  (a,b)$. Definimos
> $$
> \int_{a}^{b} f(x) \, dx = \int_{a}^{c} f(x) \, dx + \int_{c}^{b} f(x) \, dx
> $$
> si estas dos últimas integrales existen. En este caso $\int_{a}^{b} f(x) \, dx$ **también es una integral impropia de 2da clase**.



