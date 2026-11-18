---
modified: 2026-11-17T21:38:33Z
publish: true
type: zettel
date: "2026-08-24"
status: seed
aliases:
tags:
 - probability
cssclasses: 
 - romana
---
# Medida de Probabilidad $P$

Ya tenemos qué resultados pueden pasar ($\Omega$) y a qué eventos les vamos a poder preguntar su probabilidad ($\mathcal{F}$, ver [[Sigma-algebra de eventos]]). Falta la función que contesta: a cada evento le asigna un número. Kolmogórov propuso pedirle solo tres cosas, y todo lo demás se demuestra.

> [!theorem] **Definición.** (Medida de Probabilidad)
>
> Dado un espacio medible constituido por $(\Omega, \mathcal{F})$, una **medida de probabilidad** es una función $P: \mathcal{F} \to \mathbb{R}$, i.e. asigna a cada $A \in \mathcal{F}$ un real, satisfaciendo los **Axiomas de Kolmogórov**:
> 1. $\forall A \in \mathcal{F} \ (P(A) \geq 0)$
> 2. $P(\Omega) = 1$
> 3. Sea $(A_{n})_{n=1}^{\infty}$ una sucesión de eventos en $\mathcal{F}$ tal que $A_{i}\cap A_{j} = \varnothing\quad \forall i,j \ (i\neq j)$, se tiene:
> $$
> P\left[ \bigcup_{i=1}^{\infty} A_{i} \right] = \sum_{i=1}^{\infty} P[A_{i}]
> $$

> [!Info]- **Nota!**
>
> $(i)$ **No negatividad:** Ninguna probabilidad es negativa. Que además $P(A) \leq 1$ **no** hace falta pedirlo: se demuestra (Propiedad 6).
> $(ii)$ **Normalización:** La probabilidad de que ocurra *algún* resultado del espacio muestral es exactamente la unidad.
> $(iii)$ $\sigma$**-aditividad:** La probabilidad de la unión de eventos ajenos es exactamente igual a la suma (*serie*) de sus probabilidades individuales. El axioma $(iii)$ de $\mathcal{F}$ es el que permite esto: garantiza que la unión está en $\mathcal{F}$.

De los tres axiomas salen las reglas que usamos todo el tiempo:

> [!theorem] **Teorema.** (Propiedades de $P$)
>
> Sean $A,B \in \mathcal{F}$.
> 1. $P[\varnothing]  = 0$
> 2. Aditividad finita: si $A_{1},\dots,A_{n} \in \mathcal{F}$ son ajenos dos a dos ($A_{i} \cap A_{j} = \varnothing$ si $i\neq j$),
> $$P\left[ \bigcup_{i=1}^{n} A_{i} \right] = \sum_{i=1}^{n}P[A_{i}]$$
> 3. $\displaystyle P[A^{c}] = 1 - P[A]$, i.e. $P[A] + P[A^{c}] = 1$.
> 4. $P[B \setminus A] = P[B] - P[B \cap A]$. En particular, si $A \subseteq B$, $P[B \setminus A] = P[B] - P[A]$.
> 5. Monotonía: si $A \subseteq B$, ent. $P(A) \leq P(B)$.
> 6. $P(A) \leq 1$.
> 7. $P(A \cup B) = P(A) + P(B) - P(A \cap B)$.

> [!proof]- **Proof.**
>
> 1. **P.D.** $P[\varnothing] = 0$
> Sea $A_{n} = \varnothing$ para todo $n \geq 1$. Son ajenos ($\varnothing \cap \varnothing = \varnothing$) y su unión es $\varnothing$, así que por el axioma $(iii)$,
> $$
> P(\varnothing) = \sum_{i=1}^{\infty} P(\varnothing) = \lim_{ n \to \infty } n\cdot P(\varnothing)
> $$
> Sup. $P(\varnothing) = \varepsilon > 0$. Ent. el lado derecho es $\displaystyle \lim_{ n \to \infty } n \cdot \varepsilon = \infty$, pero el izquierdo es un número real, $!$
> $$
> \therefore P(\varnothing) = 0 \tag*{$\blacksquare$}
> $$
> 2. **P.D.** $\displaystyle P\left[ \bigcup_{i=1}^{n} A_{i} \right] = \sum_{i=1}^{n}P[A_{i}]$
> Completamos la sucesión con vacíos: $A_{n+1} = A_{n+2} = \dots = \varnothing$. Sigue siendo una sucesión de eventos ajenos, y su unión es la misma. Ent.
> $$
> \begin{align}
> & P\left[ \bigcup_{i=1}^{n} A_{i} \right] \\[0.5em]
> &= P\left[ \bigcup_{i=1}^{\infty} A_{i} \right] = \sum_{i=1}^{\infty} P[A_{i}] \tag{axioma $(iii)$} \\[0.5em]
> &= \sum_{i=1}^{n} P[A_{i}] + \sum_{i=n+1}^{\infty} P[\varnothing] = \sum_{i=1}^{n} P[A_{i}] \tag*{$\blacksquare$}
> \end{align}
> $$
> 3. **P.D.** $P[A^{c}] = 1 - P[A]$
> Tenemos que $A \cup A^{c} = \Omega$ y $A \cap A^{c} = \varnothing$. Por 2 y el axioma $(ii)$,
> $$
> 1 = P[\Omega] = P[A \cup A^{c}] = P[A] + P[A^{c}]
> $$
> $$
> \therefore P[A^{c}] = 1 - P[A] \tag*{$\blacksquare$}
> $$
> 4. **P.D.** $P[B \setminus A] = P[B] - P[B \cap A]$
> $B = (B \setminus A) \cup (B \cap A)$, unión ajena. Por 2, $P[B] = P[B \setminus A] + P[B \cap A]$, y se despeja. Si $A \subseteq B$, $B \cap A = A$. $\blacksquare$
> 5. **P.D.** $P(A) \leq P(B)$
> Por 4 y el axioma $(i)$, $P[B] - P[A] = P[B\setminus A] \geq 0$. $\blacksquare$
> 6. Por 5 con $B = \Omega$: $P(A) \leq P(\Omega) = 1$. $\blacksquare$
> 7. **P.D.** $P[A \cup B] = P[A] + P[B] - P[A\cap B]$
> $A \cup B = A \cup (B \setminus A)$, unión ajena. Por 2 y 4,
> $$
> P[A \cup B] = P[A] + P[B \setminus A] = P[A] + P[B] - P[A\cap B] \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> En 7 se resta $P(A \cap B)$ porque al sumar $P(A) + P(B)$ la intersección se cuenta **dos** veces. Con más eventos hay que ir sumando y restando intersecciones: es el principio de inclusión-exclusión, y junto con la desigualdad de Boole y otras propiedades más finas está en [[Propiedades de la Medida de Probabilidad]].

---
Siguiente: [[Propiedades de la Medida de Probabilidad]].
