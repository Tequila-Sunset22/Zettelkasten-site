---
modified: 2026-11-15T03:56:02Z
title: "Criterios de Convergencia de Sucesiones"
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
### Cociente de polinomios

> [!theorem] **Teorema.** (Cociente de Polinomios)
>
> Sea $\{ x_{n} \}$ y $\{ y_{n} \}$ sucesiones determinadas por:
> $$
> \begin{align}
> x_{n} &= a_{p}n^{p} + a_{p-1}n^{p-1} + \dots + a_{0}\\[0.5em]
> y_{n} &= b_{q}n^{q} + b_{q-1}n^{q-1} + \dots + b_{0}
> \end{align}
> $$
> donde $p,q \in \mathbb{N}$, $a_{p}\neq 0, b_{q}\neq 0$ y $y_{n} \neq 0$ para todo $n \in \mathbb{N}$. Entonces:
> $$
> \lim_{n \to \infty} \frac{x_{n}}{y_{n}} = \begin{cases}
>   \frac{a_{p}}{b_{q}} & \text{ si } p = q \\[0.5em]
>   0 & \text{ si } p<q \\[0.5em]
>   \infty & \text{ si } p>q \text{ y } \frac{a_{p}}{b_{q}}>0 \\[0.5em]
>   -\infty & \text{ si } p>q \text{ y } \frac{a_{p}}{b_{q}}<0
> \end{cases}
> $$

> [!proof]- **Proof.**
>
> (Caso $p=q$) Para $n \geq 1$, dividimos entre $n^{p}$:
> $$
> \frac{x_{n}}{y_{n}} = \frac{\frac{1}{n^{p}}x_{n}}{\frac{1}{n^{p}}y_{n}} = \frac{a_{p} + \frac{a_{p-1}}{n}+ \dots + \frac{a_{0}}{n^{p}}}{b_{q} + \frac{b_{q-1}}{n} + \dots + \frac{b_{0}}{n^{p}}} \implies \lim_{n \to \infty} \frac{x_{n}}{y_{n}} = \frac{a_{p}}{b_{q}}
> $$
> por álgebra de límites, pues $\frac{1}{n^{j}} \to 0$ y $b_{q} \neq 0$ (ver [[Limites de Sucesiones]]).
>
> (Caso $p<q$)
> Sea $x'_{n} = n^{q} + x_{n}$ para $n \geq 1$. Como $p < q$, $x'_{n}$ es un polinomio de grado $q$ con coeficiente principal $1$, igual que $n^{q}$. Ent. $\displaystyle \frac{x'_{n}}{y_{n}} = \frac{n^{q}}{y_{n}} + \frac{x_{n}}{y_{n}}$
> $$
> \implies \lim_{n \to \infty} \frac{x_{n}}{y_{n}} = -\lim_{n \to \infty} \frac{n^{q}}{y_{n}} + \lim_{n \to \infty} \frac{x'_{n}}{y_{n}} = \underbrace{-\frac{1}{b_{q}} + \frac{1}{b_{q}}}_{\text{ por el caso } p = q} = 0
> $$
> (Caso $p>q$)
> Sea $r = p-q > 0$. Dividiendo el numerador entre $n^{p}$ y el denominador entre $n^{q}$,
> $$
> \implies \lim \frac{x_{n}}{y_{n}} = \lim \underbrace{n^{r}}_{\to \infty} \cdot \underbrace{\frac{a_{p} + \frac{a_{p-1}}{n} + \dots + \frac{a_{0}}{n^{p}}}{b_{q} + \frac{b_{q-1}}{n} + \dots + \frac{b_{0}}{n^{q}}}}_{\to \frac{a_{p}}{b_{q}} \neq 0} = \pm \infty
> $$
> por la Proposición ($c \cdot \infty$) de [[Limites de Sucesiones]], con el signo de $\frac{a_{p}}{b_{q}}$ ($n^{r} \geq n \to \infty$ por Comparación).
> $$
> \tag*{$\blacksquare$}
> $$

> [!example]- Ejemplos.
>
> 1. $\displaystyle  \lim\frac{5n^{8} - n^{4} + 3}{2n^{8} + n^{3} + n -2} = \frac{5}{2}$
> 2. $\displaystyle \lim \frac{n^{14} + n^{20} + 2n + 1}{n^{17} + 3n + 2} = \infty$
> 3. $\displaystyle  \lim \frac{4n^{3} - n^{2} + 2}{n^{4} + n - 4} = 0$
>
> El truco de dividir entre la mayor potencia, paso a paso, está en el Ejemplo 1 de [[Limites de Sucesiones]].

### Criterio de la razón

> [!theorem] **Criterio de la Razón** (D'Alembert)
>
> Sea $\{ x_{n} \}$ una sucesión de términos positivos. Supongamos que $\lim \frac{x_{n+1}}{x_{n}} = \alpha$,
> 1. Si $\alpha < 1 \implies \{ x_{n} \}$ es nula.
> 2. Si $\alpha>1 \implies \{ x_{n} \}$ diverge (de hecho, $x_{n} \to \infty$).
> 3. Si $\alpha = 1$, ent. no hay información.

> [!proof]- **Proof.**
>
> Como $\frac{x_{n+1}}{x_{n}} > 0$, por Conservación del Signo $\alpha \geq 0$.
> 1. Existe $b \in \mathbb{R}$ tal que $0 \leq \alpha < b <1$ (p. ej. $b = \frac{\alpha + 1}{2}$). Ahora tomemos $\varepsilon = b-\alpha$ y como $\displaystyle \lim \frac{x_{n+1}}{x_{n}} = \alpha$, existe $N \in \mathbb{N}$ tal que $\displaystyle \alpha - b < \frac{x_{n+1}}{x_{n}} -\alpha < b-\alpha$ para $n \geq N$.
> De esta manera tenemos que: $0< x_{n+1} < bx_{n}$ y sucesivamente, por inducción, para $n \geq N$,
> $$
> 0 < x_{n} \leq b^{n-N}x_{N} = \frac{x_{N}}{b^{N}} \, b^{n}
> $$
> Como $0 < b < 1$, $b^{n} \to 0$ (Potencias en [[Limites de Sucesiones]]), y $\frac{x_{N}}{b^{N}}$ es constante, ent. por Sándwich $x_{n} \to 0$.
> 2. Existe $b$ tal que $1 < b < \alpha$. Con $\varepsilon = \alpha - b$, existe $N$ tal que $\frac{x_{n+1}}{x_{n}} > \alpha - \varepsilon = b$ para $n \geq N$, ent. $x_{n+1} > bx_{n}$ y por inducción
> $$
> x_{n} \geq b^{n-N}x_{N} = \frac{x_{N}}{b^{N}} \, b^{n} \quad \text{ si } n \geq N
> $$
> Como $b > 1$, $b^{n} \to \infty$ (Ejemplo 5 de [[Limites de Sucesiones]]); multiplicando por la constante $\frac{x_{N}}{b^{N}} > 0$ y por Comparación, $x_{n} \to \infty$.
> 3. Con $x_{n} = \frac{1}{n}$, $\frac{x_{n+1}}{x_{n}} = \frac{n}{n+1} \to 1$ y converge; con $x_{n} = n$, $\frac{x_{n+1}}{x_{n}} = \frac{n+1}{n} \to 1$ y diverge.
> $$
> \tag*{$\blacksquare$}
> $$


> [!example]- Ejemplos.
>
> 1. $\displaystyle \left\{  \frac{n}{(1+x)^{n}}  \right\}_{n=1}^{\infty}$ con $x>0$: $\displaystyle \lim \left[ \frac{\frac{n+1}{(1+x)^{n+1}}}{\frac{n}{(1+x)^{n}}}  \right] = \lim \frac{(n+1)(1+x)^{n}}{n(1+x)^{n+1}} = \lim \frac{n+1}{n} \cdot \frac{1}{1+x} = \frac{1}{1+x} < 1$, ent. es nula.
> 2. $\displaystyle \left\{\frac{2^{n}}{n}  \right\}_{n=1}^{\infty}$: $\displaystyle \lim \frac{2^{n+1}}{n+1} \cdot \frac{n}{2^{n}} = \lim \frac{2n}{n+1} = 2 > 1$, ent. $\frac{2^{n}}{n} \to \infty$.

### Sucesiones monótonas

Para [[Sucesiones Monotonas|sucesiones monótonas]], estar [[Sucesiones Acotadas|acotada]] **sí** basta para converger. Aquí es donde se usa el Axioma del Supremo (ver [[Supremo e Infimo]]).

> [!theorem] **Criterio 4.** (Convergencia de Sucesiones Crecientes)
>
> Sea $\{ x_{n} \}$ una sucesión creciente, ent. $\{ x_{n} \}$ converge sii está acotada superiormente. En este caso
> $$
> \lim x_{n} = \sup \left\{x_{n} \mid n \in \mathbb{N}\right\}
> $$

> [!proof]- **Proof.**
>
> ($\implies$) Si converge, está acotada (Proposición de [[Sucesiones Convergentes]]), en particular superiormente.
>
> ($\impliedby$) Supongamos que $\{ x_{n} \}$ está acot. sup, entonces existe el supremo del conjunto $S = \{ x_{n} \mid  n \in \mathbb{N} \}$ que denotaremos por $\alpha$ (por Axm. del Sup.)
> Sea $\varepsilon >0$ y consideramos $\alpha-\varepsilon$. Esta no es cota sup. del cjto. $S$; entonces existe un elemento $x_{N}$ tal que $\alpha - \varepsilon  < x_{N} \leq \alpha$ y para $n \geq N$, como es creciente, $\alpha- \varepsilon  < x_{N} \leq x_{n} \leq \alpha$, donde $\left| x_{n} -\alpha \right| = \alpha - x_{n} < \varepsilon$
> $$
> \therefore \lim x_{n} = \alpha \tag*{$\blacksquare$}
> $$


> [!theorem] **Criterio 5.** (Convergencia de Sucesiones Decrecientes)
>
> Sea $\{ x_{n} \}$ sucesión decreciente. $\{ x_{n} \}$ converge sii está acotada inferiormente y en este caso
> $$
> \lim x_{n} = \inf \left\{x_{n} \mid  n \in \mathbb{N}\right\}
> $$

> [!proof]- **Proof.**
>
> $\{ -x_{n} \}$ es creciente (Observación de [[Sucesiones Monotonas]]), y está acot. sup. sii $\{ x_{n} \}$ está acot. inf. Por el Criterio 4 y álgebra de límites, $x_{n} = -(-x_{n}) \to -\sup \{ -x_{n} \} = \inf \{ x_{n} \}$.
> $$
> \tag*{$\blacksquare$}
> $$


> [!theorem] **Teorema.** (Tarea)
>
> Sea $\{ x_{n} \}$ monótona ent.
> $$
> \lim x_{n} = \begin{cases}
>   \infty & \text{ si } \{ x_{n} \} \text{ es creciente y no acot. sup. }\\[0.5em]
>   -\infty & \text{ si } \{ x_{n} \} \text{ es decreciente y no acot. inf. }
> \end{cases}
> $$

> [!proof]- **Proof.**
>
> Sup. $\{ x_{n} \}$ creciente y no acot. sup. Sea $M \in \mathbb{R}$. Como $M$ no es cota sup., existe $N$ tal que $x_{N} > M$, y para $n \geq N$, $x_{n} \geq x_{N} > M$. Ent. $x_{n} \to \infty$.
> El caso decreciente sale aplicando lo anterior a $\{ -x_{n} \}$.
> $$
> \tag*{$\blacksquare$}
> $$

Así, una sucesión monótona **siempre** tiene límite (finito o $\pm\infty$).

> [!example]- Ejemplos. (Sucesiones recursivas)
>
> 1. Sea $x_{0} = 1$ y  $x_{n} = \sqrt{1+x_{n-1}}$ para $n\geq 1$.
> **Creciente.** Por Ind.: $x_{1} = \sqrt{ 2 } > 1 = x_{0}$; si $x_{n} > x_{n-1}$, ent. $x_{n+1} = \sqrt{ 1 + x_{n} } > \sqrt{ 1 + x_{n-1} } = x_{n}$.
> **Acot. por $2$.** Por Ind.: $x_{0} = 1 < 2$; si $x_{n} < 2$, ent. $x_{n+1} < \sqrt{ 3 } < 2$.
> Por el Criterio 4 el límite $\alpha$ de esta sucesión existe, y el de cualquiera de sus subsucesiones existe y es igual a $\alpha$ ([[Subsucesiones]]); en particular $x_{n+1} \to \alpha$. Por Raíz Cuadrada y álgebra de límites $\sqrt{ 1 + x_{n} } \to \sqrt{ 1 + \alpha }$, y de aquí se tiene
> $$
> x_{n+1} = (1+x_{n})^{\frac{1}{2}} \implies  \alpha = (1+\alpha)^{\frac{1}{2}} \implies \alpha^{2} - \alpha - 1 = 0 \implies \alpha = \frac{1\pm \sqrt{1+4}}{2}
> $$
> y tomamos $+$ ya que $\alpha \geq x_{0} = 1 > 0$ (es creciente y por Conservación de Desigualdades), mientras que $\frac{1-\sqrt{ 5 }}{2} < 0$. Ent. $\alpha = \frac{1+\sqrt{5}}{2}$.
> 2. Sea $x_{0} = 2$ y $x_{n} = \sqrt{2x_{n-1}-1}$ si $n\geq 1$.
> **Bien definida y acot. inf. por $1$.** Por Ind.: $x_{0} = 2 \geq 1$; si $x_{n} \geq 1$, ent. $2x_{n} - 1 \geq 1$ y $x_{n+1} = \sqrt{ 2x_{n} - 1 } \geq 1$.
> **Decreciente.** Por Ind.: $x_{1} = \sqrt{ 3 } < 2 = x_{0}$; si $x_{n} < x_{n-1}$, ent. $2x_{n} - 1 < 2x_{n-1} - 1$ y $x_{n+1} < x_{n}$.
> Procediendo en forma análoga al anterior (ahora con el Criterio 5), $\alpha$ debe satisfacer
> $$
> \alpha = \sqrt{ 2\alpha - 1 } \implies \alpha^{2} - 2\alpha + 1 = 0 \implies (\alpha - 1)^{2} = 0 \implies \alpha = 1
> $$

Otro criterio importante, que no necesita conocer el límite, es el [[Sucesiones de Cauchy|criterio de Cauchy]].
