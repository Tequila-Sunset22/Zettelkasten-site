---
modified: 2026-11-17T21:59:52Z
title: "Teorema del Valor Intermedio"
publish: true
type: zettel
date: 2026-09-04
status: seed
aliases:
  - Teorema de Bolzano
tags:
  - calculus
cssclasses:
  - romana
---
> [!tip|idea]- **Idea Intuitiva.**
>
> Si $f$ cambia de signo en $[a,b]$, partimos $[a,b]$ a la mitad y nos quedamos con la mitad donde $f$ sigue cambiando de signo. Repitiendo, los intervalos se encogen a un punto $c$, y por continuidad $f(c)$ no puede ser ni positivo ni negativo.

> [!theorem] **Teorema.** (Teorema de Bolzano)
>
> Si $f: [a,b] \to  \mathbb{R}$ es continua y $f(a)$ y $f(b)$ tienen signos opuestos, es decir, $f(a)f(b) < 0$, entonces existe al menos un $c \in  (a,b)$ tal que $f(c) = 0$.

Ojo: no confundir con el [[Teorema del Bolzano-Weierstrass]] (el de subsucesiones).

> [!proof]- **Proof.**
>
> S.p.g. $f(a) < 0 < f(b)$ (si no, aplicamos lo siguiente a $-f$).
> Construimos por inducción intervalos $[a_{n}, b_{n}]$: sea $[a_{0}, b_{0}] = [a,b]$. Dado $[a_{n}, b_{n}]$ con $f(a_{n}) < 0 < f(b_{n})$, sea $m = \frac{a_{n} + b_{n}}{2}$:
> - si $f(m) = 0$, ya encontramos $c = m \in (a,b)$;
> - si $f(m) < 0$, sea $[a_{n+1}, b_{n+1}] = [m, b_{n}]$;
> - si $f(m) > 0$, sea $[a_{n+1}, b_{n+1}] = [a_{n}, m]$.
>
> Si nunca caemos en el primer caso, obtenemos sucesiones con $f(a_{n}) < 0 < f(b_{n})$, $\{ a_{n} \}$ creciente, $\{ b_{n} \}$ decreciente, $a \leq a_{n} < b_{n} \leq b$ y
> $$
> b_{n} - a_{n} = \frac{b-a}{2^{n}}
> $$
> 1. $\{ a_{n} \}$ es creciente y acot. sup. por $b$, ent. converge a algún $c$ (Criterio 4 de [[Criterios de Convergencia de Sucesiones]]), y $c \in [a,b]$ (Conservación de Desigualdades).
> 2. $b_{n} = a_{n} + (b-a)\left( \frac{1}{2} \right)^{n} \to c + 0 = c$ (álgebra de límites y Potencias, ver [[Limites de Sucesiones]]).
> 3. Como $f$ es continua en $c$, por Continuidad por Sucesiones ([[Limites de Sucesiones]]) $f(a_{n}) \to f(c)$ y $f(b_{n}) \to f(c)$.
> 4. Como $f(a_{n}) < 0$ para todo $n$, $f(c) \leq 0$; como $f(b_{n}) > 0$, $f(c) \geq 0$ (Conservación de Desigualdades). Ent. $f(c) = 0$.
>
> Finalmente $c \neq a$ y $c \neq b$, porque $f(a) \neq 0 \neq f(b)$. Ent. $c \in (a,b)$.
> $$
> \tag*{$\blacksquare$}
> $$

Equivalentemente, vamos generalizando para una constante $k$. El siguiente corolario representa la misma idea pero con los dos casos posibles en cuanto al orden de $f(a)$ y $f(b)$.

> [!theorem] **Corolario.** (Teorema del Valor Intermedio)
>
> Sea $f: [a,b] \to \mathbb{R}$ continua y sea $k \in \mathbb{R}$. Si $f(a) < k < f(b)$ o $f(b) < k < f(a)$, entonces existe $c \in (a,b)$, tal que $f(c) = k$.

> [!proof]- **Proof.**
>
> Sea $g(x) = f(x) - k$, que es continua por ser diferencia de continuas. En ambos casos $g(a)$ y $g(b)$ tienen signos opuestos, i.e. $g(a)g(b) < 0$. Por el Teorema de Bolzano existe $c \in (a,b)$ con $g(c) = 0$, i.e. $f(c) = k$.
> $$
> \tag*{$\blacksquare$}
> $$

### Algunas consecuencias

- La imagen de una función continua en $[a,b]$ es un intervalo cerrado $[m,M]$ (Corolario en [[Teorema de Weierstrass y de Acotación]]).
- Todo $a > 0$ tiene raíz $n$-ésima positiva ([[Teorema de Existencia de Raices]]).
- Se usa (con el Corolario $\operatorname{Im} f = [m,M]$) en la prueba del Teorema del Valor Medio para integrales ([[Teorema del Valor Medio]]).

La propiedad local de que una función continua conserva su signo cerca de un punto (Conservación del Signo para funciones) está en [[Continuidad]].
