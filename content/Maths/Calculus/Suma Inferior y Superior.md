---
modified: 2026-11-15T19:03:03Z
title: "Suma Inferior y Superior"
publish: true
type: zettel
date: "2026-07-02"
aliases:
tags: 
 - calculus
cssclasses: 
 - romana
---
> Es la suma de cada "*área rectangular*" que se forma al multiplicar la longitud del subintervalo $(x_{k+1} - x_{k})$ por algún valor de la función $f(x)$ en el mismo subintervalo, como lo es $\inf \left\{f\right\}$ y $\sup \left\{f\right\}$ para definir los rectángulos más pequeños y más grandes de cada subintervalo.

> [!tip|idea]- **Idea Intuitiva.**
>
> Son los mismos rectángulos por debajo y por encima de la gráfica que en el caso continuo ([[Integral de Darboux]], con animación), pero como $f$ ya no tiene por qué alcanzar su mínimo y su máximo en cada subintervalo, usamos lo más parecido que siempre existe: el $\inf$ y el $\sup$ ([[Generalizando la Integral]]).

> [!theorem] **Definición.** (Suma Inferior y Superior)
>
> Supongamos que $f$ está acotada en $[a,b]$ y que $\mathcal{P} = \{ x_{0},\dots, x_{n} \}$ es una partición de $[a,b]$. Para $k \in \{ 0, \dots, n-1 \}$, sea
> $$
> \begin{align}
> m_{k} &= \inf\{ f(x) : x_{k}\leq x\leq x_{k+1} \}, \\[0.5em]
> M_{k} &= \sup \{ f(x) : x_{k} \leq x \leq x_{k+1} \}.
> \end{align}
> $$
> La **suma inferior** de $f$ respecto a $\mathcal{P}$, representada mediante $L(f,\mathcal{P})$ se define como
> $$
> L(f,\mathcal{P}) = \sum_{k=0}^{n-1} m_{k}(x_{k+1}-x_{k}).
> $$
> La **suma superior** de $f$ respecto a $\mathcal{P}$, representada mediante $U(f,\mathcal{P})$, se define como
> $$
> U(f,\mathcal{P}) = \sum_{k=0}^{n-1} M_{k}(x_{k+1}-x_{k}).
> $$

> [!Info]- **Nota!** (Otras notaciones)
>
> En otros libros cambian los nombres pero no la idea:
> - **Spivak** escribe $P = \{ t_{0}, \dots, t_{n} \}$ y numera los subintervalos $[t_{i-1}, t_{i}]$ con $i = 1, \dots, n$, i.e. $L(f,P) = \sum_{i=1}^{n} m_{i}(t_{i} - t_{i-1})$. Es nuestra suma con $i = k+1$. Las figuras de [[Integral de Darboux]] vienen de ahí.
> - Muchos escriben $L(P)$, $L_{\mathcal{P}}$ o $L(P,f)$ en vez de $L(f,\mathcal{P})$, $s(f,P)$ y $S(f,P)$, o $\underline{S}$ y $\overline{S}$.
> - A $L$ y $U$ también se les llama **sumas de Darboux**.

> [!observation]+ **Observación**
>
> 1. A pesar de la motivación geométrica, estas sumas se han definido de manera precisa, sin invocar ningún concepto de "área".
> 2. El requisito que $f$ esté acotada en $[a,b]$ es esencial para que los $m_{k}$ y $M_{k}$ estén bien definidos (existen por el Axioma del Supremo, ver [[Supremo e Infimo]]). Usamos ínfimos y supremos y no mínimos y máximos, ya que no se supone que $f$ sea continua.
> 3. Si $f$ **es** continua, por el [[Teorema de Weierstrass y de Acotación|Teorema de Weierstrass]] $f$ alcanza su mínimo y su máximo en cada $[x_{k}, x_{k+1}]$, así que $m_{k} = \min_{[x_{k},x_{k+1}]} \{ f \}$ y $M_{k} = \max_{[x_{k},x_{k+1}]} \{ f \}$. Así, para $f$ continua, son exactamente las sumas de [[Integral de Darboux]].

- Un resultado evidente es que $L(f,\mathcal{P}) \leq U(f,\mathcal{P})$, ya que para cada $k$ se verifica $m_{k}(x_{k+1}-x_{k})\leq M_{k}(x_{k+1}-x_{k})$.

### Refinamiento

Los resultados del caso continuo ([[Integral de Darboux]]) se conservan con las mismas pruebas.

> [!theorem] **Lema.** (Refinamiento)
>
> Si $\mathcal{P}'$ es un refinamiento de $\mathcal{P}$ (i.e. $\mathcal{P} \subseteq \mathcal{P}'$), entonces
> $$
> L(f,\mathcal{P}) \leq L(f,\mathcal{P}') \leq U(f,\mathcal{P}') \leq U(f,\mathcal{P})
> $$

> [!proof]- **Proof.** 
>
> Es la prueba de la Proposición (Refinamiento) de [[Integral de Darboux]], cambiando $\min$ por $\inf$ y $\max$ por $\sup$: lo único que se usa ahí es que si $A \subseteq B$, ent. $\inf_{A} \{ f \} \geq \inf_{B} \{ f \}$ y $\sup_{A} \{ f \} \leq \sup_{B} \{ f \}$, que también vale para $\inf$ y $\sup$ (todo elemento de $f(A)$ está en $f(B)$, ver [[Supremo e Infimo]]).
> $$
> \tag*{$\blacksquare$}
> $$

> De hecho, siempre se cumple que $L \leq U$, no importa qué particiones.

> [!theorem] **Teorema 1.** 
>
> Sean $\mathcal{P}_{1}$ y $\mathcal{P}_{2}$ particiones de $[a,b]$, y sea $f$ una función acotada en $[a,b]$.
> Entonces
> $$
> L(f,\mathcal{P}_{1}) \leq U(f,\mathcal{P}_{2})
> $$

> [!proof]- **Proof.** 
>
> Sea $\mathcal{P} = \mathcal{P}_{1} \cup \mathcal{P}_{2}$, que es un refinamiento de $\mathcal{P}_{1}$ y de $\mathcal{P}_{2}$ (ver [[Definiendo la Integral]]). Según el lema anterior, 
> $$
> L(f,\mathcal{P}_{1}) \leq L(f,\mathcal{P}) \leq U(f,\mathcal{P}) \leq U(f,\mathcal{P}_{2}). \tag*{$\blacksquare$}
> $$

### Integral inferior y superior

> Cualquier $U$ es una cota superior del conjunto de sumas inferiores, y cualquier $L$ es una cota inferior del conjunto de sumas superiores. Y como son reales acotados, es claro que tenemos $\sup$ e $\inf$.

> [!theorem] **Corolario.** (Integral Inferior y Superior)
>
> Sea $f$ acotada en $[a,b]$ y sean
> $$
> \begin{gather}
> \mathcal{L} = \{ L(f, \mathcal{P}) \mid \mathcal{P} \text{ es partición de } [a,b] \} \\[0.5em]
> \mathcal{U} = \{ U(f, \mathcal{P}) \mid \mathcal{P} \text{ es partición de } [a,b] \}
> \end{gather}
> $$
> Entonces existen
> $$
> \underline{I} = \sup \mathcal{L} \qquad \text{y} \qquad \overline{I} = \inf \mathcal{U}
> $$
> llamadas la **integral inferior** y la **integral superior** de $f$, y para toda partición $\mathcal{P}'$
> $$
> L(f,\mathcal{P}') \leq \underline{I} \leq \overline{I} \leq U(f,\mathcal{P}')
> $$

> [!proof]- **Proof.**
>
> Es la prueba de los Lemas 1 y 2 de [[Integral de Darboux]], con el Teorema 1 en lugar de la Proposición 2: cada $U(f,\mathcal{P}')$ es cota superior de $\mathcal{L}$ (no vacío), así que existe $\underline{I} = \sup \mathcal{L} \leq U(f,\mathcal{P}')$; ent. $\underline{I}$ es cota inferior de $\mathcal{U}$, existe $\overline{I} = \inf \mathcal{U}$ y $\underline{I} \leq \overline{I}$.
> $$
> \tag*{$\blacksquare$}
> $$

En el caso continuo siempre $\underline{I} = \overline{I}$ (Lema 4 de [[Integral de Darboux]]); en general no, y cuando sí, decimos que $f$ es integrable: ver [[Integrabilidad]].
