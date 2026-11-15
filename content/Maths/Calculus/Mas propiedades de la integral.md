---
modified: 2026-11-15T05:26:27Z
title: "Propiedades de la Integral"
publish: true
---
Aquí $f, g$ son **integrables** ([[Integrabilidad]]); no hace falta que sean continuas. Son las propiedades del caso continuo ([[Integral de Darboux]]) extendidas a funciones acotadas ([[Generalizando la Integral]]).

### Aditividad respecto al intervalo

> [!theorem] **Teorema 4.** (Propiedad Acumulativa)
>
> Sea $f$ acotada en $[a,b]$ y $a<c<b$. Si $f$ es integrable en $[a,b]$, entonces $f$ es integrable en $[a,c]$ y en $[c,b]$. Recíprocamente, si $f$ es integrable en $[a,c]$ y en $[c,b]$, entonces $f$ es integrable en $[a,b]$. Finalmente, en cualquier caso,
> $$
> \int_{a}^{b} f = \int_{a}^{c} f+ \int_{c}^{b} f. 
> $$

> [!proof]- **Proof.** 
>
> Si $\mathcal{P}'$ es partición de $[a,c]$ y $\mathcal{P}''$ de $[c,b]$, ent. $\mathcal{P} = \mathcal{P}' \cup \mathcal{P}''$ es partición de $[a,b]$ que contiene a $c$, y sus subintervalos son los de $\mathcal{P}'$ y los de $\mathcal{P}''$, así que
> $$
> \begin{align}
> L(f,\mathcal{P}) = L(f,\mathcal{P}') + L(f,\mathcal{P}''), \\[0.5em]
> U(f,\mathcal{P}) = U(f,\mathcal{P}') + U(f,\mathcal{P}''). \tag{1}
> \end{align}
> $$
> $(\implies)$
> Supongamos que $f$ es integrable en $[a,b]$. Si $\varepsilon>0$, existe una partición $\mathcal{P}= \{ x_{0},\dots,x_{n} \}$ de $[a,b]$ tal que
> $$
> U(f,\mathcal{P}) - L(f,\mathcal{P}) < \varepsilon.
> $$
> Podemos suponer que $c = x_{j}$ para algún $j$. (En otro caso, sea $\mathcal{Q} = \mathcal{P} \cup \{ c \}$; entonces $\mathcal{Q}$ refina a $\mathcal{P}$, de manera que $U(f,\mathcal{Q})- L(f,\mathcal{Q}) \leq U(f,\mathcal{P})-L(f,\mathcal{P}) < \varepsilon$, por el Lema de Refinamiento de [[Suma Inferior y Superior]]). Así, $\mathcal{P}' = \{ x_{0},\dots,x_{j} \}$ es una partición de $[a,c]$ y $\mathcal{P}'' = \{ x_{j},\dots,x_{n} \}$ es una partición de $[c,b]$. Por $(1)$,
> $$
> [U(f,\mathcal{P}')-L(f,\mathcal{P}')] + [U(f,\mathcal{P}'')- L(f,\mathcal{P}'')] = U(f,\mathcal{P}) - L(f,\mathcal{P}) <\varepsilon.
> $$
> Como cada uno de los términos entre corchetes es no negativo, cada uno de ellos debe ser menor que $\varepsilon$. Esto demuestra que $f$ es integrable en $[a,c]$ y en $[c,b]$ (Teorema 2).
>
> $(\impliedby)$
> Supongamos ahora que $f$ es integrable en $[a,c]$ y en $[c,b]$. Si $\varepsilon >0$, existe una partición $\mathcal{P}'$ de $[a,c]$ y una partición $\mathcal{P}''$ de $[c,b]$ tal que
> $$
> \begin{align}
> U(f,\mathcal{P}') - L(f,\mathcal{P}') < \varepsilon / 2, \\[0.5em]
> U(f,\mathcal{P}'') - L(f,\mathcal{P}'') < \varepsilon / 2.
> \end{align}
> $$
> Con $\mathcal{P} = \mathcal{P}' \cup \mathcal{P}''$, por $(1)$,
> $$
> U(f,\mathcal{P}) - L(f,\mathcal{P}) = [U(f,\mathcal{P}')-L(f,\mathcal{P}')] + [U(f,\mathcal{P}'') - L(f,\mathcal{P}'')] < \varepsilon.
> $$
> **La igualdad.** En ambos casos $f$ es integrable en los tres intervalos. Para particiones $\mathcal{P}', \mathcal{P}''$ cualesquiera de $[a,c]$ y $[c,b]$,
> $$
> \begin{align}
> L(f,\mathcal{P}') \leq \int_{a}^{c} f \leq U(f,\mathcal{P}'), \\[0.5em]
> L(f,\mathcal{P}'') \leq \int_{c}^{b} f \leq U(f,\mathcal{P}''),
> \end{align}
> $$
> de manera que, sumando y por $(1)$,
> $$
> L(f,\mathcal{P}) \leq \int_{a}^{c} f + \int_{c}^{b} f \leq U(f,\mathcal{P}).
> $$
> Como $\int_{a}^{b} f$ también está entre $L(f,\mathcal{P})$ y $U(f,\mathcal{P})$, y por el $(\impliedby)$ podemos tomar $\mathcal{P}', \mathcal{P}''$ con $U(f,\mathcal{P}) - L(f,\mathcal{P}) < \varepsilon$ para cualquier $\varepsilon > 0$, ambos números están a distancia menor que $\varepsilon$ para todo $\varepsilon$, i.e.
> $$
> \int_{a}^{c} f + \int_{c}^{b} f = \int_{a}^{b} f. \tag*{$\blacksquare$}
> $$

> [!theorem] **Corolario.**
>
> 1. Si $f$ es integrable en $[a,b]$, entonces $f$ es integrable en todo $[c,d] \subseteq [a,b]$.
> 2. Dados $f: [a,b] \to  \mathbb{R}$ acotada y $\mathcal{P} = \{ c_{0} = a,c_{1},\dots, c_{n} = b \}$ partición de $[a,b]$, $f$ es integrable en $[a,b]$ si y sólo si $f$ es integrable en $[c_{i}, c_{i+1}]$ para todo $i \in  \{ 0,\dots,n-1 \}$, y en ese caso
> $$
> \int_{a}^{b} f(x) \, dx = \sum_{i=0}^{n-1} \int_{c_{i}}^{c_{i+1}} f(x) \, dx 
> $$

> [!proof]- **Proof.**
>
> 1. Si $a < c$, por el Teorema 4 $f$ es integrable en $[c,b]$; si además $d < b$, otra vez por el Teorema 4 (ahora en $[c,b]$), es integrable en $[c,d]$. (Si $c = a$ o $d = b$, nos saltamos el paso.)
> 2. Por inducción sobre $n$, aplicando el Teorema 4 en $[c_{0}, c_{n-1}]$ y $[c_{n-1}, c_{n}]$.
> $$
> \tag*{$\blacksquare$}
> $$

El Teorema 4 permite justificar algunas convenciones de notación. Añadiendo las definiciones:
$$
\int_{a}^{a} f = 0 \quad \text{ y } \quad \int_{a}^{b} f = -\int_{b}^{a} f \quad \text{si } a > b.
$$

> [!observation]+ **Observación.**
>
> 1. Las convenciones no son arbitrarias: si queremos que $\int_{a}^{u} f + \int_{u}^{v} f = \int_{a}^{v} f$ valga siempre, con $u = v = a$ queda $\int_{a}^{a} f + \int_{a}^{a} f = \int_{a}^{a} f$, ent. $\int_{a}^{a} f = 0$; y con $v = a$, $\int_{a}^{u} f + \int_{u}^{a} f = 0$.
> 2. Con esto, la igualdad del Teorema 4 se verifica para todo $a,b,c$ (en un intervalo donde $f$ es integrable), incluso sin $a<c<b$. La demostración es por casos; p. ej., si $c < a < b$, por el Teorema 4 $\int_{c}^{b} f = \int_{c}^{a} f + \int_{a}^{b} f$, ent. $\int_{a}^{b} f = \int_{c}^{b} f - \int_{c}^{a} f = \int_{a}^{c} f + \int_{c}^{b} f$. Los demás casos son iguales.

### Linealidad

> [!theorem] **Proposición.** (Suma)
>
> Sean $f,g: [a,b]\to \mathbb{R}$ integrables. Entonces $f+g$ es integrable y
> $$
> \int_{a}^{b} (f+g)(x) \, dx  = \int_{a}^{b} f(x) \, dx + \int_{a}^{b} g(x) \, dx 
> $$

> [!proof]- **Proof.**
>
> En cada subintervalo $[x_{k}, x_{k+1}]$ de una partición $\mathcal{P}$, para todo $x$ ahí, $f(x) + g(x) \geq \inf f + \inf g$, ent. $\inf (f+g) \geq \inf f + \inf g$; análogamente $\sup(f+g) \leq \sup f + \sup g$. Multiplicando por $x_{k+1} - x_{k}$ y sumando,
> $$
> L(f,\mathcal{P}) + L(g,\mathcal{P}) \leq L(f+g,\mathcal{P}) \leq U(f+g,\mathcal{P}) \leq U(f,\mathcal{P}) + U(g,\mathcal{P}) \tag{2}
> $$
> Sea $\varepsilon > 0$. Existen $\mathcal{P}_{1}, \mathcal{P}_{2}$ con $U - L < \frac{\varepsilon}{2}$ para $f$ y para $g$ respectivamente; con $\mathcal{P} = \mathcal{P}_{1} \cup \mathcal{P}_{2}$ (refinamiento) siguen valiendo. Por $(2)$,
> $$
> U(f+g,\mathcal{P}) - L(f+g,\mathcal{P}) \leq [U(f,\mathcal{P}) - L(f,\mathcal{P})] + [U(g,\mathcal{P}) - L(g,\mathcal{P})] < \varepsilon
> $$
> así que $f + g$ es integrable (Teorema 2). Además, $\int (f+g)$ y $\int f + \int g$ están ambos en el intervalo $[L(f,\mathcal{P}) + L(g,\mathcal{P}), \ U(f,\mathcal{P}) + U(g,\mathcal{P})]$, de longitud $< \varepsilon$. Como $\varepsilon$ es arbitrario, son iguales.
> $$
> \tag*{$\blacksquare$}
> $$

Sea $f:[a,b]\to \mathbb{R}$ integrable. ¿Cuál es la integral de $-f$?
> [!theorem] **Proposición.** (Negativo)
>
> $-f$ es integrable y
> $$
> \int_{a}^{b} -f(x) \, dx  = - \int_{a}^{b} f(x) \, dx 
> $$

> [!proof]- **Proof.**
>
> Sea $\mathcal{P}$ partición de $[a,b]$. Como $\inf_{A} \{ f \} = -\sup_{A} \{ -f \}$ para todo cjto. $A$ ([[Supremo e Infimo]]),
> $$
> \begin{align}
>   L(f,\mathcal{P}) &= \sum_{k=0}^{n-1} \underset{[x_{k},x_{k+1}]}{\inf \left\{f\right\} } (x_{k+1}-x_{k}) \\[0.5em]
>    &= \sum_{k=0}^{n -1} - \underset{[x_{k},x_{k+1}]}{\sup \left\{-f\right\} }(x_{k+1}-x_{k}) \\[0.5em]
>     &= -\sum_{k=0}^{n-1} \underset{[x_{k},x_{k+1}]}{\sup \left\{-f\right\} } (x_{k+1}-x_{k}) = -U(-f,\mathcal{P})
> \end{align}
> $$
> Análogamente $U(f,\mathcal{P}) = -L(-f,\mathcal{P})$. En consecuencia,
> $$
>  \sup \left\{L(f,\mathcal{P})\right\} = \sup \left\{-U(-f,\mathcal{P})\right\} = - \inf \left\{U(-f,\mathcal{P})\right\} 
> $$
> y del mismo modo $\inf \{ U(f,\mathcal{P}) \} = -\sup \{ L(-f,\mathcal{P}) \}$. Como $f$ es integrable, los lados izquierdos son iguales a $\int_{a}^{b} f$, así que la integral inferior y la superior de $-f$ valen ambas $-\int_{a}^{b} f$. Lo que implica que $-f$ es integrable y
> $$
> \int_{a}^{b} -f(x) \, dx  = -\int_{a}^{b} f(x) \, dx \tag*{$\blacksquare$}
> $$

> [!theorem] **Proposición.** (Homogeneidad)
>
> Si $\lambda \in \mathbb{R}$, $\lambda f$ es integrable y
> $$
> \int_{a}^{b} \lambda f(x) \, dx  = \lambda \int_{a}^{b} f(x) \, dx 
> $$

> [!proof]- **Proof.**
>
> Si $\lambda \geq 0$, en cada subintervalo $\inf (\lambda f) = \lambda \inf f$ y $\sup (\lambda f) = \lambda \sup f$, ent. $L(\lambda f,\mathcal{P}) = \lambda L(f,\mathcal{P})$ y $U(\lambda f,\mathcal{P}) = \lambda U(f,\mathcal{P})$ para toda $\mathcal{P}$. Así, $\sup \{ L(\lambda f,\mathcal{P}) \} = \lambda \sup \{ L(f,\mathcal{P}) \} = \lambda \int_{a}^{b} f$ y lo mismo con $\inf \{ U \}$.
> Si $\lambda < 0$, $\lambda f = -(\lvert \lambda \rvert f)$, y usamos el caso anterior y la Proposición (Negativo).
> $$
> \tag*{$\blacksquare$}
> $$

Al ser $\displaystyle  \int_{a}^{b} (\cdot) \, dx$ aditiva y homogénea, se dice que $\displaystyle  \int_{a}^{b} (\cdot) \, dx$ es un **operador lineal**:
$$
\int_{a}^{b} \left[ \alpha f(x) + \beta g(x) \right] dx = \alpha \int_{a}^{b} f(x) \, dx + \beta \int_{a}^{b} g(x) \, dx
$$

> [!observation]+ **Observación.**
>
> Ojo, para continuas hay una prueba rápida: como su integral existe, tienen antiderivada, y usamos el Teorema Fundamental del Cálculo 2 ([[Teorema Fundamental de Cálculo]]): si $F' = f$ y $G' = g$, ent. $(F + G)' = f + g$ y $(cF)' = cf$. Pero las pruebas de arriba valen para cualquier integrable.

### Orden

> [!theorem] **Teorema.** (Monotonía)
>
> Sean $f,g$ funciones integrables en $[a,b]$:
> 1. Si $f \geq  0$ entonces, $\displaystyle \int_{a}^{b} f(x) \, dx \geq  0$.
> 2. Si $f \geq  g$ entonces, $\displaystyle \int_{a}^{b} f(x) \, dx \geq \int_{a}^{b} g(x) \, dx$
> 3. $\displaystyle m(b-a) \leq  \int_{a}^{b} f(x) \, dx \leq  M(b-a)$ donde $m$ y $M$ son cotas inferior y superior de $f$ respectivamente.

> [!proof]- **Proof.** 
>
> 1. Cualquier suma superior de $f$ es no negativa, pues $f\geq 0 \implies \sup_{[x_{k},x_{k+1}]}\{ f \} \geq 0$. De esta manera, $0$ es cota inferior de $\{ U \mid  U \text{ es suma superior }\}$, y $\inf \left\{U \mid  U \text{ es suma superior }\right\} = \overline{I} = I \geq 0$ para $\displaystyle  I = \int_{a}^{b} f(x) \, dx$.
> 2. Si $f\geq g$, $f - g \geq  0$ y por $(1)$, $\displaystyle \int_{a}^{b} (f-g)(x) \, dx \geq  0$. Al ser $\displaystyle \int_{a}^{b} (\cdot) \, dx$ lineal,
> $$
> \begin{align}
>   \int_{a}^{b} (f-g)(x) \, dx  &=  \int_{a}^{b} f(x) \, dx  - \int_{a}^{b} g(x) \,  dx \geq  0 \\[0.5em]
>    &\implies \int_{a}^{b} f(x) \, dx \geq \int_{a}^{b} g(x) \, dx  
> \end{align}
> $$
> 3. Con la partición $\{ a, b \}$, como $m \leq \inf_{[a,b]} \{ f \}$ y $\sup_{[a,b]} \{ f \} \leq M$,
> $$
> m(b-a) \leq L(f,\{ a,b \}) \leq \int_{a}^{b} f(x) \, dx \leq U(f,\{ a,b \}) \leq M(b-a) \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Las dos propiedades que pedimos en [[Definiendo la Integral]] ya las probamos para $f$ continua en [[Integral de Darboux]]. Aquí quedan generalizadas: la **Aditividad** es el Teorema 4 (con las convenciones), y la **Intercalación** es el inciso (3) de Monotonía con $m = \inf_{[u,v]} \{ f \}$ y $M = \sup_{[u,v]} \{ f \}$.

### Paridad

> [!theorem] **Lema.** (Reflexión)
>
> Si $f$ es integrable en $[a,b]$ y $g(x) = f(-x)$, ent. $g$ es integrable en $[-b,-a]$ y $\displaystyle \int_{-b}^{-a} g = \int_{a}^{b} f$.

> [!proof]- **Proof.**
>
> Si $\mathcal{P} = \{ x_{0}, \dots, x_{n} \}$ es partición de $[a,b]$, ent. $-\mathcal{P} = \{ -x_{n} < \dots < -x_{0} \}$ es partición de $[-b,-a]$, y toda partición de $[-b,-a]$ es de esta forma. En $[-x_{k+1}, -x_{k}]$, $g$ toma exactamente los mismos valores que $f$ en $[x_{k}, x_{k+1}]$, y el subintervalo mide lo mismo. Ent. $L(g, -\mathcal{P}) = L(f,\mathcal{P})$ y $U(g,-\mathcal{P}) = U(f,\mathcal{P})$: los cjtos. de sumas inferiores y superiores de $g$ y de $f$ son los mismos, así que sus $\sup$ e $\inf$ coinciden.
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Proposición.** (Funciones pares e impares)
>
> Sea $a > 0$ y $f$ integrable en $[-a,a]$ (ver [[Paridad]]).
> 1. Si $f$ es **par**, $\displaystyle \int_{-a}^{a} f = 2 \int_{0}^{a} f$.
> 2. Si $f$ es **impar**, $\displaystyle \int_{-a}^{a} f = 0$.

> [!proof]- **Proof.**
>
> Por el Teorema 4, $\int_{-a}^{a} f = \int_{-a}^{0} f + \int_{0}^{a} f$. Por el Lema (Reflexión) en $[0,a]$, con $g(x) = f(-x)$, $\int_{-a}^{0} g = \int_{0}^{a} f$.
> 1. Si $f$ es par, $g = f$, ent. $\int_{-a}^{0} f = \int_{0}^{a} f$ y $\int_{-a}^{a} f = 2\int_{0}^{a} f$.
> 2. Si $f$ es impar, $g = -f$, ent. $-\int_{-a}^{0} f = \int_{0}^{a} f$ (Proposición (Negativo)) y $\int_{-a}^{a} f = 0$.
> $$
> \tag*{$\blacksquare$}
> $$
