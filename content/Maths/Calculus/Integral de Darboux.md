---
modified: 2026-11-15T19:03:03Z
title: "Integral de Darboux"
publish: true
type: zettel
date: "2026-09-07"
status: seed
aliases:
 - epsilon particion
tags:
 - calculus
cssclasses: 
 - romana
---
> [!Info]- **Nota!** (Caso particular: $f$ continua)
>
> Aquí construimos la integral **solo para funciones continuas**, como lo vimos primero en clase. Como $f$ es continua, en cada subintervalo alcanza su mínimo y su máximo ([[Teorema de Weierstrass y de Acotación|Teorema de Weierstrass]]), y eso simplifica todo. Después, en [[Generalizando la Integral]], hacemos lo mismo para funciones **acotadas**, cambiando $\min$ por $\inf$ y $\max$ por $\sup$; las pruebas de esta nota se reusan allá.

> Es la suma de cada "*área rectangular*" que se forma al multiplicar la longitud del subintervalo $(x_{k+1} - x_{k})$ por algún valor de la función $f(x)$ en el mismo subintervalo, como lo es $\min \left\{f\right\}$ y $\max \left\{f\right\}$ para definir los rectángulos más pequeños y más grandes de cada subintervalo.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Con una [[Definiendo la Integral|partición]] dibujamos rectángulos **por debajo** de la gráfica (altura = el mínimo de $f$ en cada subintervalo) y **por encima** (altura = el máximo). El área "real" queda atrapada entre las dos sumas. Al refinar la partición, la suma inferior sube, la superior baja, y la brecha $U - L$ se cierra.
>
> <img src="/videos/sumas-darboux.avif" alt="center" width="720" loading="lazy">
>
> *Función:* $f(x) = 1 + 0.8x - 0.15x^{2}$ en $[0,4]$, con particiones regulares de $2, 4, 8$ y $16$ subintervalos.

> [!theorem] **Definición.** (Sumas de Darboux Superiores e Inferiores)
>
> Sea $f: [a,b] \to \mathbb{R}$ continua y $\mathcal{P} = \{ x_{0}, \dots, x_{n} \}$ partición de $[a,b]$. Para $k \in \{ 0, \dots, n-1 \}$ sean
> $$
> m_{k} = \underset{[x_{k},x_{k+1}]}{\min }\{ f \}, \qquad M_{k} = \underset{[x_{k},x_{k+1}]}{\max }\{ f \}
> $$
> y
> $$
> \begin{align}
> L(f,\mathcal{P}) &= \sum_{k=0}^{n-1} m_{k} \cdot(x_{k+1} - x_{k}) \\[0.5em]
> U(f,\mathcal{P}) &= \sum_{k=0}^{n -1} M_{k} \cdot (x_{k+1}-x_{k})
> \end{align}
> $$
> A $L$ se le llama **suma inferior** y a $U$ **suma superior**.


> [!observation]+ **Observación.**
>
> Tenemos que, para cualquier partición,
> $$
> L(f,\mathcal{P})\leq U(f,\mathcal{P})
> $$
> pues $m_{k} \leq M_{k}$ para cada $k$. Además, si $\mathcal{P}'$ es un refinamiento de $\mathcal{P}$
> $$
> L(f,\mathcal{P}) \leq L(f,\mathcal{P}') \leq U(f,\mathcal{P}') \leq U(f,\mathcal{P})
> $$
> Bueno, ahora vamos a probarlo.

### Refinamiento

> El refinamiento de una partición siempre va a tener sumas más próximas, es decir, **refinar** aumenta (o deja igual) cualquier $L$ y disminuye (o deja igual) cualquier $U$.


> [!theorem] **Proposición.** (Refinamiento)
>
> Sea $\mathcal{P}$ una partición, y $\mathcal{P}'$ un refinamiento de $\mathcal{P}$ tenemos que
> $$
> L(f,\mathcal{P}) \leq L(f,\mathcal{P}') \leq U(f,\mathcal{P}') \leq U(f,\mathcal{P})
> $$

> [!proof]+ **Proof.** 
>
> Consideremos primero el caso especial (figura) en donde $\mathcal{P}'$ contenga solamente un punto $y$ más que $\mathcal{P}$:
> 
> ![[Pasted image 20260702093950.png|center]]
> $$
> \begin{align}
> \mathcal{P} &= \{  x_{0},\dots,x_{j},x_{j+1},\dots,x_{n} \} \\[0.5em]
> \mathcal{P'} &= \{ x_{0},\dots,x_{j},y,x_{j+1},\dots,x_{n} \}
> \end{align}
> $$ 
> con $x_{j} < y < x_{j+1}$. Sus sumas tienen los mismos sumandos excepto el del subintervalo $[x_{j}, x_{j+1}]$:
> $$
> \begin{align}
> L(f,\mathcal{P}) &= \sum_{k\neq j} m_{k}(x_{k+1}-x_{k}) + \underset{[x_{j},x_{j+1}]}{\min }\{ f \} (x_{j+1}-x_{j}) \\[0.5em]
> L(f,\mathcal{P}') &= \sum_{k\neq j} m_{k}(x_{k+1}-x_{k}) + \underset{[x_{j},y]}{\min }\{ f \} (y-x_{j}) + \underset{[y,x_{j+1}]}{\min }\{ f \} (x_{j+1}-y)
> \end{align}
> $$
> En especial, observamos
> $$
> \underset{[x_{j},x_{j+1}]}{\min } \{ f \} (x_{j+1}-x_{j}) = \underset{[x_{j},x_{j+1}]}{\min } \{ f \}(x_{j+1}-y) +\underset{[x_{j},x_{j+1}]}{\min }\{ f \}(y-x_{j}) \tag{1}
> $$
> Además, como $[x_{j},y] \subseteq [x_{j},x_{j+1}]$, el mínimo en el cjto. más chico es mayor o igual. Ent. 
> $$
> \underset{[x_{j},y]}{\min} \{ f \} \geq \underset{[x_{j},x_{j+1}]}{\min} \{ f \}
> $$
> Igualmente, como $[y,x_{j+1}] \subseteq [x_{j},x_{j+1}]$, ent.
> $$
> \underset{[y,x_{j+1}]}{\min} \{ f \}  \geq \underset{[x_{j},x_{j+1}]}{\min} \{ f \} 
> $$
> Por lo que en $(1)$
> $$
> \underset{[x_{j},x_{j+1}]}{\min } \{ f \} (x_{j+1}-x_{j}) \leq \underset{[x_{j},y]}{\min }\{ f \} (y-x_{j}) + \underset{[y,x_{j+1}]}{\min }\{ f \} (x_{j+1}-y)
> $$
> y sumando los demás sumandos (que son iguales), $L(f,\mathcal{P}) \leq L(f,\mathcal{P}')$. Con el $\max$ es igual, con la desigualdad al revés (en un cjto. más chico el máximo es menor o igual): $U(f,\mathcal{P}') \leq U(f,\mathcal{P})$.
>
> Ahora puede deducirse fácilmente el caso general. La partición $\mathcal{P}'$ puede obtenerse a partir de $\mathcal{P}$ añadiendo un punto cada vez; en otras palabras, existe una sucesión finita de particiones
> $$
> \mathcal{P} = \mathcal{P}_{0}, \mathcal{P}_{1},\dots, \mathcal{P}_{r} = \mathcal{P}'
> $$
> tales que $\mathcal{P}_{s+1}$ contiene exactamente un punto más que $\mathcal{P}_{s}$. Luego
> $$
> L(f,\mathcal{P}_{0}) \leq L(f,\mathcal{P}_{1}) \leq \dots \leq L(f,\mathcal{P}_{r}) \qquad \text{y} \qquad U(f,\mathcal{P}_{0}) \geq \dots \geq U(f,\mathcal{P}_{r}).
> $$
> La desigualdad de en medio, $L(f,\mathcal{P}') \leq U(f,\mathcal{P}')$, es la observación de arriba.
> $$
> \tag*{$\blacksquare$}
> $$

> De hecho, siempre se cumple que $L \leq U$, no importa qué particiones.

> [!theorem] **Proposición 2.** 
>
> Sean $\mathcal{P}_{1}$ y $\mathcal{P}_{2}$ cualesquiera particiones,
> $$
> L(f,\mathcal{P}_{1}) \leq U(f,\mathcal{P}_{2})
> $$

> [!proof]- **Proof.** 
>
> Sea $\mathcal{P}= \mathcal{P}_{1} \cup \mathcal{P}_{2}$. Observemos que $\mathcal{P}$ es un refinamiento de $\mathcal{P}_{1}$ y de $\mathcal{P}_{2}$. Así, por la Proposición (Refinamiento),
> $$
> L(f,\mathcal{P}_{1})\leq L(f,\mathcal{P})\leq U(f,\mathcal{P})\leq U(f,\mathcal{P}_{2}) \tag*{$\blacksquare$}
> $$

Generalizamos la *Proposición 2* con este *Lema*:
> Cualquier $U$ es una cota superior del conjunto de sumas inferiores, y cualquier $L$ es una cota inferior del conjunto de sumas superiores. Y como son reales acotados, es claro que tenemos $\inf$ y $\sup$.

> [!theorem] **Lema 1.** (Acotación de las Sumas de Darboux)
>
> Dada $f:[a,b] \to \mathbb{R}$ continua. Definimos los conjuntos de todas las sumas inferiores y superiores como:
> $$
> \begin{gather}
> \mathcal{L} = \{ L(f,\mathcal{P}) \mid \mathcal{P} \text{ es partición de } [a,b] \} \\[0.5em]
> \mathcal{U} = \{ U(f,\mathcal{P}) \mid \mathcal{P} \text{ es partición de } [a,b] \}
> \end{gather}
> $$
> Entonces, para cualquier partición $\mathcal{P}_2$ fija, el número real $U(f,\mathcal{P}_2)$ es una cota superior para el conjunto $\mathcal{L}$, y para cualquier partición $\mathcal{P}_1$ fija, el número real $L(f,\mathcal{P}_1)$ es una cota inferior para el conjunto $\mathcal{U}$.

> [!proof]- **Proof.**
>
> Es la Proposición 2, leída con $\mathcal{P}_{2}$ fija (o con $\mathcal{P}_{1}$ fija).
> $$
> \tag*{$\blacksquare$}
> $$

> [!theorem] **Lema 2.** (Existencia de la Integral Inferior y Superior)
>
> Dada $f:[a,b] \to \mathbb{R}$ continua, existen $\sup \mathcal{L}$ e $\inf \mathcal{U}$, y $\sup \mathcal{L} \leq \inf \mathcal{U}$.

> [!proof]- **Proof.**
>
> Como el conjunto $\mathcal{L}$ es no vacío y está acotado superiormente (por cualquier suma superior, según el *Lema 1*), por el Axioma del Supremo, $\sup \mathcal{L}$ existe en $\mathbb{R}$.
> Como el conjunto $\mathcal{U}$ es no vacío y está acotado inferiormente (por cualquier suma inferior, según el *Lema 1*), por el Axioma del Ínfimo, $\inf \mathcal{U}$ existe en $\mathbb{R}$.
> Además, cada $U(f,\mathcal{P}_{2})$ es cota superior de $\mathcal{L}$, así que $\sup \mathcal{L} \leq U(f,\mathcal{P}_{2})$ (es la menor); ent. $\sup \mathcal{L}$ es cota inferior de $\mathcal{U}$ y $\sup \mathcal{L} \leq \inf \mathcal{U}$ (es la mayor).
> $$
> \tag*{$\blacksquare$}
> $$

### $\varepsilon$-particiones

> Una $\varepsilon$-partición garantiza que la función no "brinque" ni varíe más de $\varepsilon$ de altura dentro de ningún subintervalo.

> [!tip|idea]+ **Idea Intuitiva.** 
>
> En cada subintervalo dibujamos la "caja" que va del mínimo al máximo de $f$. La partición es una $\varepsilon$-partición si **todas** las cajas miden menos que $\varepsilon$ de alto (verdes). Si alguna se pasa (roja), refinamos. Al pedir un $\varepsilon$ más chico, vuelven a aparecer cajas rojas y hay que refinar más.
>
> <img src="/videos/epsilon-particion.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** ($\varepsilon$-partición)
>
> Dada $f:[a,b]\to \mathbb{R}$ continua y $\varepsilon > 0$, sea $\mathcal{P} = \{ a =x_{0},\dots,x_{n} =b \}$.
> Decimos que $\mathcal{P}$ es una $\varepsilon$**-partición**,  si para todo $k \in  \{ 0,\dots,n-1 \}$, para cualesquiera $p,q \in [x_{k},x_{k+1}]$ se tiene que
> $$
> \lvert f(p)-f(q) \rvert <\varepsilon
> $$

Recuerda que "para cualquier" es lo mismo que "para todo", evita confusiones!

> Por el Teorema de Heine-Cantor ([[Continuidad Uniforme]]), nuestra función $f:[a,b]\to \mathbb{R}$ continua es unif. continua. Este hecho garantiza la existencia de las $\varepsilon$-particiones.

> [!theorem] **Lema 3.** 
>
> Para $f:[a,b]\to \mathbb{R}$ continua, existen las $\varepsilon$-particiones. Más aún, cualquier partición con norma suficientemente chica lo es.

> [!proof]- **Proof.** 
>
> Como $f: [a,b] \to \mathbb{R}$ es continua, ent. es unif. continua.
> Fijando $\varepsilon$ tendremos una $\delta$ "fija" que cumple la definición: si $x,y \in [a,b]$ y $\lvert x-y \rvert<\delta$, ent. $\lvert f(x)-f(y) \rvert<\varepsilon$. Sea $\mathcal{P}$ cualquier partición con $\Delta \mathcal{P} < \delta$; p. ej., por la Prop. Arquimediana tomamos $N \in \mathbb{N}^{+}$ tal que $\frac{b-a}{N}< \delta$, y sea la partición
> $$
> \mathcal{P} = \left\{  x_{0}= a , x_{1} = a + \frac{b-a}{N} , x_{2} = a+ \frac{2(b-a)}{N}, \dots, x_{N} =b \right\}
> $$
> Por **ejemplo.** $\displaystyle x_{1}-x_{0} = \frac{b-a}{N}< \delta$.
> Así, para cualesquiera $p,q \in [x_{0},x_{1}]$ se cumple que $\lvert p-q \rvert \leq x_{1} - x_{0} <\delta$ y; por continuidad uniforme, $\lvert f(p)-f(q) \rvert<\varepsilon$.
> Lo mismo pasa para cualquier subintervalo $[x_{k},x_{k+1}]$.
> $$
> \tag*{$\blacksquare$}
> $$

> [!observation]+ **Observación.**
>
> Podemos pensar al Lema 3 como una máquina, le metes un número de tolerancia (cualquier número positivo) y la máquina te fabrica y te entrega una partición $\mathcal{P}$ de $[a,b]$ garantizada. La garantía de esa partición es que, en cualquiera de sus subintervalos, la diferencia entre el punto más alto de la función y el punto más bajo será estrictamente menor que ese número de tolerancia que le metiste.

El Lema 3, implica el Lema 4:

> Puedes acercar $U$ y a $L$ tanto como quieras!

> [!theorem] **Lema 4.** 
>
> Si $f: [a,b] \to \mathbb{R}$ es continua, ent. para todo $\varepsilon > 0$ existe una partición $\mathcal{P}$ tal que
> $$
> U(f,\mathcal{P}) - L(f,\mathcal{P}) < \varepsilon
> $$

> [!proof]- **Proof.** 
>
> Sea $\varepsilon > 0$ y sea $\mathcal{P} = \{ x_{0}, \dots, x_{n} \}$ una $\left( \frac{\varepsilon}{2(b-a)} \right)$-partición (la cual existe por **Lema 3**). Recordemos que
> $$
> \begin{align}
> L(f,\mathcal{P}) &= \sum_{k=0}^{n-1} m_{k} \cdot (x_{k+1}- x_{k}) \\[0.5em]
> U(f,\mathcal{P})  &= \sum_{k=0}^{n-1} M_{k} \cdot (x_{k+1}-x_{k}).
> \end{align}
> $$
> Entonces, $\displaystyle U-L = \sum_{k=0}^{n-1}(x_{k+1}-x_{k})(M_{k}-m_{k})$.
> Como $f$ alcanza su máximo y su mínimo en $[x_{k},x_{k+1}]$, $M_{k} = f(q)$ y $m_{k} = f(p)$ con $p,q \in [x_{k},x_{k+1}]$, así que $M_{k} - m_{k} < \frac{\varepsilon}{2(b-a)}$. Ent.
> $$
> \begin{align}
> U - L &< \sum_{k=0}^{n-1} (x_{k+1}-x_{k})\left(  \frac{\varepsilon}{2(b-a)} \right) \\[0.5em]
> &= \left( \frac{\varepsilon}{2(b-a)} \right)\left( \sum_{k=0}^{n-1} (x_{k+1}-x_{k}) \right) \\[0.5em]
> &=\frac{\varepsilon}{2(b-a)}(b-a) = \frac{\varepsilon}{2} < \varepsilon \tag*{$\blacksquare$}
> \end{align}
> $$

**OJO!** Observamos que estos Lemas dependen por hip. de que la función sea continua (en un intervalo **cerrado**, para tener Heine-Cantor).

### La integral

> [!theorem] **Definición.** (Integral de Darboux)
>
> Sea $f:[a,b] \to \mathbb{R}$ continua, se define a la Integral de Darboux como el supremo del conjunto de todas las sumas inferiores $\mathcal{L}$, es decir,
> $$
> \int_{a}^{b} f(x) \, dx  = \sup_{\mathcal{P}} \{ L(f,\mathcal{P}) \mid \mathcal{P} \text{ es partición de } [a,b] \}
> $$

> [!Info]- **Nota!**
>
> El símbolo $\int$ originalmente era una $s$ alargada que significaba "suma"; los números $a,b$ se denominan *límites de integración inferior y superior*. La $x$ de $dx$ es muda: $\int_{a}^{b} f(x)\,dx = \int_{a}^{b} f(z)\,dz$.

> [!observation]+ **Observación.**
>
> Daba igual usar el $\sup$ de las inferiores o el $\inf$ de las superiores: por el Lema 2, $0 \leq \inf \mathcal{U} - \sup \mathcal{L} \leq U(f,\mathcal{P}) - L(f,\mathcal{P})$ para toda $\mathcal{P}$, y por el Lema 4 esto es $< \varepsilon$ para todo $\varepsilon > 0$. Ent.
> $$
> \sup \mathcal{L} = \int_{a}^{b} f(x) \, dx = \inf \mathcal{U}, \qquad L(f,\mathcal{P}) \leq \int_{a}^{b} f(x) \, dx \leq U(f,\mathcal{P}) \text{ para toda } \mathcal{P}
> $$
> y es el **único** número entre todas las sumas inferiores y todas las superiores. En el caso general esta igualdad ya no es automática: es la definición de *integrable* ([[Integrabilidad]]).

> Para que sea una integral tiene que cumplir las propiedades: *Aditividad* e *Intercalación* de [[Definiendo la Integral]]. Esto hay que demostrarlo:

> [!theorem] **Teorema.** (La integral de Darboux cumple los axiomas)
>
> Sea $f:[a,b] \to \mathbb{R}$ continua y $a \leq u \leq v \leq b$. Entonces
> 1. **Aditividad:** $\displaystyle \int_{a}^{u} f(x) \, dx + \int_{u}^{v} f(x) \, dx = \int_{a}^{v} f(x) \, dx$.
> 2. **Intercalación:** $\displaystyle (v-u)\underset{[u,v]}{\min } \{ f \} \leq \int_{u}^{v} f(x) \, dx \leq (v-u)\underset{[u,v]}{\max } \{ f \}$.

> [!proof]- **Proof.** 
>
> **Nota.** Si $f$ es continua en $[a,b]$, también lo es en $[u,v] \quad \forall u,v \in [a,b]$, así que todas estas integrales tienen sentido. Sup. $u < v$ (si $u = v$, ver la Propiedad 3 abajo).
>
> **Propiedad 2. Intercalación:**
> Observamos que, para $f\mid_{[u,v]}$ (*restringida*), $\mathcal{P}=\{ u,v \}$ es una partición de $[u,v]$. Además, por la Observación de arriba,
> $$
> L(f,\mathcal{P}) = (v-u)\cdot \underset{[u,v]}{\min \{ f \}} \leq \int_{u}^{v} f(x) \, dx \leq U(f,\mathcal{P}) = (v-u)\underset{[u,v]}{\max } \{ f \}
> $$
> En conclusión, para toda $u,v \in [a,b]$ tal que $u\leq v$:
> $$
> (v-u)\underset{[u,v]}{\min } \{ f \} \leq \int_{u}^{v} f(x) \, dx \leq (v-u)\underset{[u,v]}{\max } \{ f \}
> $$
> 
> **Propiedad 1. Aditividad:**
> **P.D.** $\displaystyle \int_{a}^{u} f(x) \, dx + \int_{u}^{v} f(x) \, dx = \int_{a}^{v} f(x) \, dx$
> Sea $\varepsilon > 0$. Por el Lema 4, como $f$ es continua en $[a,u]$ y en $[u,v]$, existen particiones $\mathcal{P}_1$ (de $[a,u]$) y $\mathcal{P}_2$ (de $[u,v]$) tales que sus sumas cumplen:
> $$
> U_1 - L_1 < \frac{\varepsilon}{2} \quad \text{y} \quad U_2 - L_2 < \frac{\varepsilon}{2}
> $$
> Tomamos $\mathcal{P} = \mathcal{P}_1 \cup \mathcal{P}_2$, la cual es partición de $[a,v]$.
>
> **Nota.** Sus subintervalos son los de $\mathcal{P}_{1}$ y los de $\mathcal{P}_{2}$, así que $L = L_{1} + L_{2}$ es su suma inferior y $U =U_{1}+U_{2}$ es su suma superior.
> 
> Notamos que, por la Observación de arriba en cada intervalo:
> $$
> \begin{align}
> L_{1} \leq \int_{a}^{u} f(x) \, dx \leq U_{1} \tag{1} \\[0.5em]
> L_{2} \leq \int_{u}^{v} f(x) \, dx \leq U_{2} \tag{2}
> \end{align}
> $$
> Entonces, sumando,
> $$
> L \leq \int_{a}^{u} f(x) \, dx  + \int_{u}^{v} f(x)  \, dx \leq U
> $$
> Además, $\displaystyle L \leq \int_{a}^{v}  f(x) \, dx \leq U$.
> Con esto, restando las dos desigualdades:
> $$
> L-U \leq \int_{a}^{u} f(x) \, dx +\int_{u}^{v} f(x) \, dx - \int_{a}^{v} f(x) \, dx \leq U -L
> $$
> Esto quiere decir,
> $$
> \left\lvert  \int_{a}^{u} f(x) \, dx +\int_{u}^{v} f(x) \, dx - \int_{a}^{v} f(x) \, dx   \right\rvert \leq U - L 
> $$
> y tenemos
> $$
> U- L= U_{1} - L_{1} + U_{2} - L_{2} < \frac{\varepsilon}{2} + \frac{\varepsilon}{2} = \varepsilon \tag{Lema 4}
> $$
> para todo $\varepsilon > 0$.
> $$
> \therefore \int_{a}^{u} f(x) \, dx + \int_{u}^{v} f(x) \, dx = \int_{a}^{v} f(x) \, dx \tag*{$\blacksquare$}
> $$

> [!theorem] **Proposición.** (Propiedad 3)
>
> $$
> \int_{a}^{a} f(x) \, dx  = 0
> $$

> [!proof]- **Proof.** 
>
> Por Propiedad 1 (con $u = v = a$),
> $$
> \int_{a}^{a} f(x) \, dx + \int_{a}^{a} f(x) \, dx = \int_{a}^{a} f(x) \, dx 
> $$
> Esto implica,
> $$
> \int_{a}^{a} f(x) \, dx = 0 \tag*{$\blacksquare$}
> $$
> (Aquí $\int_{a}^{a}$ se entiende como la convención de "área de un intervalo de longitud $0$"; ver también [[Mas propiedades de la integral|Propiedades de la Integral]].)

Con esto ya podemos probar el [[Teorema Fundamental de Cálculo]]. Para funciones que no son continuas, ver [[Generalizando la Integral]].
