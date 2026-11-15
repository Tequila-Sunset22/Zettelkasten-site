---
modified: 2026-11-15T14:17:13Z
title: "Generalizando la Integral"
publish: true
type: zettel
date: 2026-08-31
status: seed
aliases:
tags:
  - calculus
cssclasses:
  - romana
---
El objetivo ahora es construir una integral para funciones que no sean **necesariamente continuas**. Generalizamos para funciones **acotadas**.

Sea $f:[a,b] \to \mathbb{R}$ **acotada** y $\mathcal{P}_{[a,b]} = \{ x_{0} = a,x_{1},\dots,x_{n} = b \}$.
Dado que en una función acotada no sabemos de la existencia de mínimos y máximos, introducimos nuestras nuevas definiciones con la generalización de $\min$ y $\max$: $\inf$ y $\sup$.

> [!example]- ¿Por qué no hay mínimos y máximos?
>
> El [[Teorema de Weierstrass y de Acotación|Teorema de Weierstrass]] (que garantizaba $\min$ y $\max$) pide continuidad. Sin ella pueden no existir: con $f(x) = x$ en $[0,1)$ y $f(1) = 0$, $f$ está acotada en $[0,1]$ y $\sup_{[0,1]} \{ f \} = 1$, pero ningún punto vale $1$, así que no hay máximo. En cambio, $\inf$ y $\sup$ **siempre** existen para un cjto. acotado y no vacío (Axioma del Supremo, ver [[Supremo e Infimo]]).

<!-- ### Qué se conserva del caso continuo -->
<!---->
<!-- En [[Integral de Darboux]] hicimos todo para $f$ continua. Al cambiar $\min \to \inf$ y $\max \to \sup$: -->
<!---->
<!-- | Caso continuo ([[Integral de Darboux]]) | Caso acotado | ¿Cambia? | -->
<!-- |---|---|---| -->
<!-- | Sumas con $\min$ y $\max$ | Sumas con $\inf$ y $\sup$ ([[Suma Inferior y Superior]]) | solo la definición | -->
<!-- | Refinamiento, Proposición 2, Lemas 1 y 2 | Mismos enunciados | la prueba es la misma (solo usa que en un cjto. más chico el $\inf$ sube y el $\sup$ baja) | -->
<!-- | $\sup \mathcal{L} = \inf \mathcal{U}$ siempre (Lema 4) | Puede fallar (Dirichlet) | ahora es la **definición** de integrable ([[Integrabilidad]]) | -->
<!-- | Aditividad e Intercalación | Teorema 4 y Monotonía ([[Mas propiedades de la integral\|Propiedades de la Integral]]) | se prueban con el criterio $\varepsilon$ | -->
<!---->
<!-- Añadimos $f$ como parámetro por convención, la notación $L(f,\mathcal{P})$ es equivalente a $L(\mathcal{P})$, utilizada en muchos libros. -->

### Recorrido

1. [[Suma Inferior y Superior]]: las sumas con $\inf$ y $\sup$, e integrales inferior y superior.
2. [[Integrabilidad]]: cuándo $\underline{I} = \overline{I}$; el criterio $\varepsilon$, ejemplos, las continuas (el caso particular de [[Integral de Darboux]]) y las funciones con discontinuidades.
3. [[Mas propiedades de la integral|Propiedades de la Integral]]: aditividad, linealidad, monotonía, paridad.
4. [[Sumas de Riemann]] e [[Integral de Reimann|Integral de Riemann]], otra forma de def. la integral.
