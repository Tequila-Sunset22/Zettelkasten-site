---
modified: 2026-11-15T04:19:31Z
publish: true
---
---
---
# Continuidad en un Conjunto
La continuidad es definida en puntos.

> [!theorem] **Definition.** 
>
> Sea $f: A \to \mathbb{R}$. Entonces $f$ es **continua** si $f$ es continua en cada punto de $A$.

Si queremos probar directamente desde esta definición, obvio, sería probar que es continua $\forall x_{0} \in A$. En ocasiones es más sencillo usar la siguiente caracterización **global**.

> [!Info]- **Nota!** (Abierto relativo)
>
> Un cjto. $U \subseteq A$ es **abierto relativo a** $A$ si para cada $x \in U$ existe $\delta > 0$ tal que $(x - \delta, x + \delta) \cap A \subseteq U$. Un cjto. $V \subseteq \mathbb{R}$ es **abierto** si es abierto relativo a $\mathbb{R}$, i.e. todos sus puntos son [[Punto Interior|puntos interiores]].

> [!theorem] **Teorema.** 
>
> Sea $f: A \to \mathbb{R}$. Entonces $f$ es **continua** si y sólo si para todo **conjunto abierto** $V \subset \mathbb{R}$, el conjunto $f^{-1}(V) = \{  x \in A : f(x) \in V \}$ es abierto (relativo a $A$).

> [!proof]- **Proof.** 
>
> ($\implies$) Sea $V$ abierto y $x_{0} \in f^{-1}(V)$. Como $f(x_{0}) \in V$ y $V$ es abierto, existe $\varepsilon > 0$ con $(f(x_{0}) - \varepsilon, f(x_{0}) + \varepsilon) \subseteq V$. Por continuidad en $x_{0}$ existe $\delta > 0$ tal que si $x \in A$ y $\lvert x - x_{0} \rvert < \delta$, ent. $\lvert f(x) - f(x_{0}) \rvert < \varepsilon$, i.e. $f(x) \in V$. Así $(x_{0} - \delta, x_{0} + \delta) \cap A \subseteq f^{-1}(V)$.
>
> ($\impliedby$) Sea $x_{0} \in A$ y $\varepsilon > 0$. $V = (f(x_{0}) - \varepsilon, f(x_{0}) + \varepsilon)$ es abierto y $x_{0} \in f^{-1}(V)$, que por hip. es abierto relativo a $A$. Ent. existe $\delta > 0$ con $(x_{0} - \delta, x_{0} + \delta) \cap A \subseteq f^{-1}(V)$, i.e. si $x \in A$ y $\lvert x - x_{0} \rvert < \delta$, ent. $\lvert f(x) - f(x_{0}) \rvert < \varepsilon$.
> $$
> \tag*{$\blacksquare$}
> $$
> (Ver también pag 316 de *Elementary Analysis*.)

> [!theorem] **Corolario.** 
>
> Sea $f:A\to \mathbb{R}$. $f$ es **continua** si y sólo si para cada intervalo $(\alpha,\beta)$, $f^{-1}((\alpha,\beta))$ es abierto (relativo a $A$).

> [!proof]- **Proof.** 
>
> ($\implies$) Todo intervalo abierto $(\alpha,\beta)$ es un cjto. abierto; aplicamos el teorema.
>
> ($\impliedby$) En la prueba de ($\impliedby$) del teorema solo usamos conjuntos $V$ de la forma $(f(x_{0}) - \varepsilon, f(x_{0}) + \varepsilon)$, que son intervalos.
> $$
> \tag*{$\blacksquare$}
> $$
