---
modified: 2026-11-15T14:36:08Z
title: "Sumas de Riemann"
publish: true
type: zettel
date: "2026-11-14"
status: seed
aliases:
tags:
 - calculus
cssclasses:
 - romana
---
En las [[Suma Inferior y Superior|sumas inferior y superior]] la altura de cada rectángulo es el $\inf$ o el $\sup$ de $f$ en el subintervalo. Riemann deja escoger **cualquier** punto del subintervalo para dar la altura.

> [!tip|idea]+ **Idea Intuitiva.**
>
> En cada subintervalo escogemos un punto $z_{k}$ (la *etiqueta*) y usamos $f(z_{k})$ como altura. Movamos los $z_{k}$ como movamos, el rectángulo queda entre el de la suma inferior y el de la superior: toda suma de Riemann $R$ está atrapada entre $L$ y $U$.
>
> <img src="/videos/sumas-riemann.avif" alt="center" width="720" loading="lazy">
>
> *Función:* $f(x) = 1 + 0.8x - 0.15x^{2}$ en $[0,4]$; las etiquetas $z_{k}$ se mueven dentro de cada subintervalo.

> [!theorem] **Definición.** (Suma de Riemann)
>
> Dada $f:[a,b] \to \mathbb{R}$ acotada y $\mathcal{P} = \{ x_{0}, \dots, x_{n} \}$ partición de $[a,b]$, una **suma de Riemann** es una expresión
> $$
> R(f,\mathcal{P},z) = \sum_{k=0}^{n-1} f(z_{k})(x_{k+1}-x_{k})
> $$
> en donde $z_{k} \in [x_{k},x_{k+1}]$, para todo $k$. A los $z_{k}$ se les llama **etiquetas** (o puntos muestra); muchas veces escribimos solo $R(f,\mathcal{P})$ o $R$.

> [!observation]+ **Observación.**
>
> Como $m_{k} \leq f(z_{k}) \leq M_{k}$ para cualquier $z_{k} \in [x_{k}, x_{k+1}]$, multiplicando por $x_{k+1} - x_{k}$ y sumando,
> $$
> L(f,\mathcal{P}) \leq R(f,\mathcal{P},z) \leq U(f,\mathcal{P})
> $$
> para cualquier elección de etiquetas. Si $f$ es continua, $L$ y $U$ son ellas mismas sumas de Riemann (con $z_{k}$ donde $f$ alcanza su mínimo o su máximo en el subintervalo); si $f$ no es continua, en general no lo son, pero hay sumas de Riemann tan cerca de ellas como queramos.

> [!example]- Ejemplo. (Sumas más usadas)
>
> Con la partición regular $x_{k} = a + k\,\Delta x$, $\Delta x = \frac{b-a}{n}$:
> - **Por la izquierda:** $z_{k} = x_{k}$, $\displaystyle R_{\text{izq}} = \Delta x \sum_{k=0}^{n-1} f(x_{k})$.
> - **Por la derecha:** $z_{k} = x_{k+1}$, $\displaystyle R_{\text{der}} = \Delta x \sum_{k=0}^{n-1} f(x_{k+1})$.
> - **Punto medio:** $z_{k} = \frac{x_{k} + x_{k+1}}{2}$, $\displaystyle R_{\text{med}} = \Delta x \sum_{k=0}^{n-1} f\left( \frac{x_{k} + x_{k+1}}{2} \right)$.
>
> Si $f$ es creciente, $R_{\text{izq}} = L$ y $R_{\text{der}} = U$ (y al revés si es decreciente). Estas sumas son la base de los [[Metodos numericos de Integracion|métodos numéricos de integración]].

Cuándo las sumas de Riemann "convergen" a la integral, y cómo usarlas para calcularla, está en [[Integral de Reimann|Integral de Riemann]].
