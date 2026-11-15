---
modified: 2026-11-15T20:21:24Z
title: "Centros de masa (Físicos)"
publish: true
type: zettel
date: "2026-09-01"
status: budding
aliases:
tags:
 - calculus
cssclasses:
 - romana
---
### Caso discreto

> [!tip|idea]+ **Idea Intuitiva.**
>
> Supongamos que tenemos $n$ cuerpos $X = \{ x_{1},\dots,x_{n} \}$ con masas asociadas $M = \{ m_{1},\dots,m_{n} \}$, cuerpos alineados.
> El momento de masa respecto al origen representa, el **torque** o fuerza de rotación de un sistema alrededor de un eje o en este caso, un punto (*el origen*). Como es un sistema donde se aplican diferentes fuerzas (*los pesos $m_{i}g$*, cada uno a distancia $x_{i}$), el torque "*total*" es la suma $\sum m_{i}g\,x_{i}$; el momento de masa es ese torque total dividido entre $g$.
> El centroide representa dónde está el centro de masa, dadas todas las masas, en tal sistema.
> 
> ![[Pasted image 20261029152713.png|center|400]]
>
> Si apoyamos el sistema en un punto $p$, cada masa empuja con su "brazo" $x_{i} - p$: si la suma $\sum m_{i}(x_{i}-p)$ es positiva el sistema se va a la derecha, si es negativa a la izquierda, y solo en un punto queda en equilibrio. Ese punto es el centroide.
>
> <img src="/videos/centroide-discreto.avif" alt="center" width="720" loading="lazy">
>
> *Masas:* $m = 3, 1, 2$ en $x = 1, 3, 6$; el apoyo se mueve hasta $\bar{x} = 3$, donde el momento es $0$.


> [!theorem] **Definición.** (Momento)
>
> Dado lo anterior, el **momento** o **momento de masa** de $(X, M)$ respecto al origen es:
> $$
> \sum_{i=1}^{n} m_{i}x_{i}
> $$
> El momento respecto a otro punto $z$ diferente del origen es,
> $$
> \sum_{i=1}^{n} m_{i}(x_{i} - z)
> $$


> [!theorem] **Definición.** (Centroide o centro de masa)
>
> El **centroide** de $(X, M)$ denotado $\bar{x}$ es:
> $$
> \bar{x} = \frac{\displaystyle \sum_{i=1}^{n} m_{i}x_{i}}{\displaystyle \sum_{i=1}^{n} m_{i}}
> $$


Es interesante ver que el momento respecto al centroide es nulo; físicamente esto significa que si sostenemos al sistema solo desde el centroide, estará en equilibrio. Calculamos el momento respecto a $\bar{x}$,
$$
\begin{align}
& \sum_{i=1}^{n} m_{i} \left( x_{i} - \frac{\displaystyle \sum_{k=1}^{n} m_{k}x_{k}}{\displaystyle \sum_{k=1}^{n} m_{k}}  \right) = \dots \\[0.5em]
\dots &= \sum_{i=1}^{n} m_{i} \frac{\displaystyle \left( \left(\sum_{k=1}^{n} m_{k}  \right)x_{i} - \sum_{k=1}^{n} m_{k}x_{k}  \right)}{\displaystyle \sum_{k=1}^{n} m_{k}} \tag{común denom.} \\[0.5em]
&= \frac{1}{\displaystyle  \sum_{k=1}^{n} m_{k}} \cdot  \sum_{i=1}^{n} m_{i} \left( \left(\sum_{k=1}^{n} m_{k}\right)x_{i} - \sum_{k=1}^{n} m_{k}x_{k}  \right) \tag{factor.} \\[0.5em]
&= \frac{1}{\displaystyle \sum_{k=1}^{n} m_{k}} \cdot \sum_{i=1}^{n} m_{i} \left( \sum_{k=1}^{n} m_{k} (x_{i} - x_{k})  \right) \tag{$x_{i}$ entra a la suma} \\[0.5em]
&= \frac{1}{\sum_{k=1}^{n} m_{k}} \cdot \left( \sum_{i=1}^{n} \sum_{k=1}^{n} m_{i}m_{k} (x_{i} - x_{k})   \right) \tag{dist.} \\[0.5em]
&= \frac{1}{\sum_{k=1}^{n} m_{k}} \cdot  \sum_{i,k=1}^{n} m_{i} m_{k}(x_{i}- x_{k}) \tag{Obs.} \\[0.5em]
&= 0
\end{align}
$$

> [!observation]+ **Observación.**
>
> La suma con doble índice anterior es $= 0$, pues observamos que $\forall i,k \in \{ 1,\dots,n \}$, por ejemplo, si $i = 1, k= 2 \implies m_{1}m_{2}(x_{1}-x_{2})$, y si lo invertimos,
> $i = 2, k =1 \implies  m_{2}m_{1}(x_{2}-x_{1})$, lo cual es lo mismo que el anterior pero con signo opuesto, si lo sumamos se cancela. Y si $i = k$, el término es $m_{i}^{2} \cdot 0 = 0$.
>
> **NOTA**. Los físicos dicen que un sistema está equilibrado si se sostiene justo desde su centroide.

> [!note]- Otra forma (más directa)
>
> Por la definición de $\bar{x}$, $\displaystyle \bar{x} \sum_{i=1}^{n} m_{i} = \sum_{i=1}^{n} m_{i}x_{i}$, ent.
> $$
> \sum_{i=1}^{n} m_{i}(x_{i} - \bar{x}) = \sum_{i=1}^{n} m_{i}x_{i} - \bar{x}\sum_{i=1}^{n} m_{i} = \sum_{i=1}^{n} m_{i}x_{i} - \sum_{i=1}^{n} m_{i}x_{i} = 0
> $$

> [!example]- Ejemplo.
>
> Masas $m_{1} = 3$, $m_{2} = 1$, $m_{3} = 2$ en $x_{1} = 1$, $x_{2} = 3$, $x_{3} = 6$ (las de la animación):
> $$
> \bar{x} = \frac{3(1) + 1(3) + 2(6)}{3 + 1 + 2} = \frac{18}{6} = 3
> $$
> y en efecto, el momento respecto a $3$ es $3(1-3) + 1(3-3) + 2(6-3) = -6 + 0 + 6 = 0$.

Ahora, supongamos que el sistema "vive" en $\mathbb{R}^{2}$ y que no está necesariamente alineado. En este caso se definen dos momentos de masa,

![[IMG_7010.jpeg|center|250]]

> [!theorem] **Definición.** (Momentos y centroide en $\mathbb{R}^{2}$)
>
> Dados puntos $(x_{i}, y_{i})$ con masas $m_{i}$, $i = 1,\dots,n$, sus momentos respecto a los ejes son
> $$
> \underset{\text{ Respecto al eje X }}{M_{X} = \sum_{i=1}^{n} m_{i}y_{i}} \quad , \quad \underset{\text{ Respecto al eje Y }}{M_{Y} = \sum_{i=1}^{n} m_{i}x_{i}}
> $$
> y el centroide es $\displaystyle (\bar{x}, \bar{y}) = \left( \frac{M_{Y}}{\sum_{i=1}^{n} m_{i}}, \frac{M_{X}}{\sum_{i=1}^{n} m_{i}} \right)$.

> [!observation]+ **Observación.**
>
> Ojo con los nombres: $M_{X}$ (respecto al eje $X$) usa las **alturas** $y_{i}$, pues mide qué tan lejos del eje $X$ están las masas; por eso da la coordenada $\bar{y}$. Y al revés con $M_{Y}$.

### Momento Continuo (varilla)
Supongamos que tenemos una varilla, podemos discretizar la varilla. El problema, es que si pensamos la varilla puntualmente, los pesos de cada punto van a ser nulos, como lo es el área de una recta o longitud de un punto, esa medida está en otra dimensión.


![[IMG_7012.jpeg|center|300]]

Entonces, introducimos el concepto de **densidad** (lineal), en este caso denotada con $\rho$, ent. la densidad de la varilla es masa sobre longitud: $\displaystyle \frac{m}{\ell} = \rho \implies m = \rho \cdot \ell$ (si $\rho$ es constante; por eso aproximamos tramo por tramo).
Pensemos la varilla como el intervalo $[a,b]$ y tomemos una partición $\mathcal{P} = \{ a = x_{0} < x_{1} < \dots < x_{n} = b \}$: la varilla queda cortada en $n$ **tramos** $[x_{i}, x_{i+1}]$, $i = 0, \dots, n-1$. Supongamos que por cada tramo de la varilla existe un punto, llamémosle $\xi_{i} \in [x_{i}, x_{i+1}]$ en el cual se concentra toda la masa del tramo. La masa aproximada es,
$$
m_{i} = \rho (\xi_{i})(x_{i+1}- x_{i})
$$
Entonces, para el problema de $n$ cuerpos (en la varilla) tenemos por aproximación del momento (respecto al origen) a:
$$
\sum_{i=0}^{n-1} m_{i}\xi_{i} = \sum_{i=0}^{n-1} \rho (\xi_{i})(x_{i+1}-x_{i})\xi_{i}
$$
pues toda la masa del tramo está en $\xi_{i}$.
Obs. que el lado derecho de la ecuación es una [[Sumas de Riemann|suma de Riemann]] para $\rho(x)\cdot x$.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Partimos la varilla en $n$ tramos y concentramos la masa de cada uno en un punto $\xi_{i}$: eso ya es el caso discreto, que sabemos resolver, y da un centroide aproximado $\bar{x}_{n}$. Al aumentar $n$ (refinar la partición), $\bar{x}_{n}$ se acerca a un valor, y ese límite es el centroide de la varilla. Donde la varilla es más densa (color más intenso), las masas pesan más y jalan el centroide hacia allá.
>
> <img src="/videos/centroide-varilla.avif" alt="center" width="720" loading="lazy">
>
> *Varilla:* $[0,4]$ con densidad $\rho(x) = 1 + x$ (el ejemplo de abajo). La masa de cada tramo se concentra en su extremo izquierdo, $\xi_{i} = x_{i}$; con $n = 2, 4, 8, 16, 32$ tramos, $\bar{x}_{n} = 1.5,\ 2,\ 2.23,\ 2.34,\ 2.39 \to \bar{x} = \frac{22}{9} \approx 2.44$ (en rojo, lo que falta). Empieza a la izquierda porque cada masa queda en el extremo más ligero y más a la izquierda de su tramo; con el punto medio la aproximación es casi exacta desde $n = 4$.

> [!theorem] **Definición.** (Momento respecto al origen)
>
> El momento de una varilla sobre $[a,b]$ con densidad $\rho$ continua es:
> $$
> \int_{a}^{b} x \rho(x) \, dx
> $$
> de esta forma, el momento depende de la densidad.

> [!theorem] **Definición.** (Centroide caso Continuo)
>
> El centroide de una varilla es,
> $$
> \bar{x} = \frac{\displaystyle \int_{a}^{b} x \rho(x) \, dx}{ \displaystyle \int_{a}^{b} \rho(x) \, dx}
> $$

> [!observation]+ **Observación.**
>
> Si $\rho = k$, i.e. es constante, $\displaystyle \bar{x} = \frac{\displaystyle \rho \int_{a}^{b} x \, dx}{\displaystyle  \rho \int_{a}^{b}  \, dx} = \frac{\displaystyle \rho \left(\frac{b^{2}-a^{2}}{2}  \right)}{\rho (b-a)} = \frac{b+a}{2}$ (dif. de cuadrados)
> Lo cual tiene sentido, el centroide de una varilla con densidad constante, es el punto medio.

> [!example]- Ejemplo.
>
> Varilla en $[0,4]$ con densidad $\rho(x) = 1 + x$ (más pesada a la derecha):
> $$
> \bar{x} = \frac{\displaystyle\int_{0}^{4} x(1+x) \, dx}{\displaystyle\int_{0}^{4} (1+x) \, dx} = \frac{\left[ \frac{x^{2}}{2} + \frac{x^{3}}{3} \right]_{0}^{4}}{\left[ x + \frac{x^{2}}{2} \right]_{0}^{4}} = \frac{8 + \frac{64}{3}}{4 + 8} = \frac{88/3}{12} = \frac{22}{9} \approx 2.44
> $$
> mayor que el punto medio $2$, como esperábamos.

### Centroide de una región (lámina)

Ahora la masa está repartida en una figura plana: la región bajo la gráfica de $f:[a,b]\to\mathbb{R}$ continua, con $f \geq 0$, hecha de un material con densidad (de área) constante $\rho$.

Tomemos una partición $\mathcal{P}$ de $[a,b]$ y $z_{k}$ el punto medio de $[x_{k}, x_{k+1}]$. Aproximamos la región por franjas: rectángulos de base $[x_{k}, x_{k+1}]$ y altura $f(z_{k})$. Cada franja
- tiene masa $m_{k} = \rho\, f(z_{k})(x_{k+1}-x_{k})$ (densidad por área),
- y su centroide está en su centro, $\left( z_{k}, \frac{f(z_{k})}{2} \right)$, por simetría del rectángulo.

Pensando cada franja como una masa puntual en su centro, estamos en el caso discreto en $\mathbb{R}^{2}$:
$$
\begin{align}
M_{Y} &\approx \sum_{k=0}^{n-1} z_{k}\, \rho f(z_{k})(x_{k+1}-x_{k}) && \text{suma de Riemann de } \rho\, x f(x) \\[0.5em]
M_{X} &\approx \sum_{k=0}^{n-1} \frac{f(z_{k})}{2}\, \rho f(z_{k})(x_{k+1}-x_{k}) && \text{suma de Riemann de } \tfrac{\rho}{2} f^{2}(x) \\[0.5em]
M &\approx \sum_{k=0}^{n-1} \rho f(z_{k})(x_{k+1}-x_{k}) && \text{suma de Riemann de } \rho f(x)
\end{align}
$$
y como $f$ es continua, al refinar las tres convergen a sus integrales ([[Integral de Reimann|Integral de Riemann]]).

> [!tip|idea]+ **Idea Intuitiva.**
>
> Cada franja se comporta como una masa puntual en su centro (a media altura). Su "brazo" respecto al eje $Y$ es $z_{k}$ y respecto al eje $X$ es $\frac{f(z_{k})}{2}$. El centroide de esos puntos se estabiliza al refinar: la recta vertical $x = \bar{x}$ sale de $M_{Y}$ y la horizontal $y = \bar{y}$ de $M_{X}$, y la figura se equilibra sobre cualquiera de las dos.
>
> <img src="/videos/centroide-region.avif" alt="center" width="720" loading="lazy">
>
> *Región:* bajo $f(x) = \frac{x^{2}}{4}$ en $[0,3]$ (la región $R_{1}$ del ejemplo de abajo, con $a = 3$, $b = \frac{9}{4}$), partida en $n = 1, 2, 4, 8, 16$ franjas. El centroide de los centros (rojo) va de $(1.5,\ 0.28)$ a $(2.10,\ 0.58)$ y se acerca al centroide exacto $\left( \frac{9}{4}, \frac{27}{40} \right) = (2.25,\ 0.675)$ (verde); el segmento rojo es lo que falta.

> [!theorem] **Definición.** (Centroide de una región)
>
> Sea $f:[a,b]\to\mathbb{R}$ continua con $f \geq 0$ y $A = \int_{a}^{b} f(x)\,dx > 0$ el área bajo su gráfica. Con densidad constante, los momentos de la región respecto a los ejes son
> $$
> M_{Y} = \rho\int_{a}^{b} x f(x) \, dx, \qquad M_{X} = \frac{\rho}{2}\int_{a}^{b} f^{2}(x) \, dx,
> $$
> su masa es $\rho A$, y su centroide (la $\rho$ se cancela) es
> $$
> \bar{x} = \frac{\displaystyle \int_{a}^{b} xf(x) \, dx }{A}, \qquad \bar{y} = \frac{\displaystyle \int_{a}^{b} f^{2}(x) \, dx}{2A}
> $$

> [!theorem] **Corolario.** (Región entre dos gráficas)
>
> Si la región está entre $f \geq g$ en $[a,b]$ (densidad constante), con $A = \int_{a}^{b} [f(x)-g(x)]\,dx$,
> $$
> \bar{x} = \frac{\displaystyle\int_{a}^{b} x[f(x) - g(x)] \, dx}{A}, \qquad \bar{y} = \frac{\displaystyle\int_{a}^{b} [f^{2}(x) - g^{2}(x)] \, dx}{2A}
> $$

> [!proof]- **Proof.**
>
> Ahora cada franja va de $g(z_{k})$ a $f(z_{k})$: tiene masa $\rho[f(z_{k})-g(z_{k})](x_{k+1}-x_{k})$ y su centro está a la altura $\frac{f(z_{k})+g(z_{k})}{2}$. Así $M_{X} = \rho\int_{a}^{b} \frac{f+g}{2}(f-g)\,dx = \frac{\rho}{2}\int_{a}^{b} (f^{2}-g^{2})\,dx$ (dif. de cuadrados), y $M_{Y} = \rho\int_{a}^{b} x(f-g)\,dx$. $\blacksquare$

> [!example]- Ejemplo.
>
> La región bajo $f(x) = \frac{x^{2}}{4}$ en $[0,3]$ (la de la animación): $A = \int_{0}^{3} \frac{x^{2}}{4}\,dx = \frac{9}{4}$, y
> $$
> \bar{x} = \frac{1}{A}\int_{0}^{3} \frac{x^{3}}{4} \, dx = \frac{4}{9}\cdot \frac{81}{16} = \frac{9}{4}, \qquad \bar{y} = \frac{1}{2A}\int_{0}^{3} \frac{x^{4}}{16} \, dx = \frac{2}{9}\cdot \frac{243}{80} = \frac{27}{40}
> $$
> **Caso general.** Si un rectángulo $[0,a]\times[0,b]$ se divide con el arco de parábola $y = \frac{b}{a^{2}}x^{2}$ (vértice en una esquina, pasa por la opuesta), la parte de abajo $R_{1}$ tiene área $\frac{ab}{3}$ y centroide $\left( \frac{3a}{4}, \frac{3b}{10} \right)$, y la de arriba $R_{2}$ tiene área $\frac{2ab}{3}$ y centroide $\left( \frac{3a}{8}, \frac{3b}{5} \right)$ (con $g = \frac{b}{a^{2}}x^{2}$ y $f = b$ en el Corolario). Comprobación: el promedio de los dos, ponderado por las áreas, es el centro del rectángulo $\left( \frac{a}{2}, \frac{b}{2} \right)$.

### Curvas paramétricas (varilla curvada)

<div style="display: flex; gap: 20px;">
  <div style="flex: 1;">
    Pensemos ahora que la varilla está curveada.
    Procediendo similarmente al caso anterior con la existencia de 
    <span class="math-inline">
      \{ \xi_{i} \}
    </span>
    <div style="text-align: center; width: 100%; margin: 15px 0;">
      <span class="math-inline">
        m_{i} = \rho(\xi_{i}) \displaystyle \int_{t_{i}}^{t_{i+1}} \sqrt{(\gamma_{1}'(t))^{2} + (\gamma_{2}'(t))^{2}} \, dt
      </span>
    </div>
    Suponiendo que
    <span class="math-inline">
      \gamma
    </span>
    es de clase C¹ (derivable con derivada continua),
    tenemos, usando el T.V.M. de integrales:
  </div>
  <div style="flex: 1; padding: 10px; border-radius: 5px;">
     <img src="/images/IMG_7013.jpeg" width="270">

  </div>
</div>

$$
m_{i} = \rho (\xi_{i}) \cdot (t_{i+1}-t_{i}) \sqrt{(\gamma_{1}'(c_{i}))^{2} + (\gamma_{2}'(c_{i}))^{2}}
$$
Así, una aproximación del momento respecto a, Eje $X$:
$$
\sum_{i=0}^{n-1} \gamma_{2}(\xi_{i}) \cdot  \rho (\xi_{i})(t_{i+1}-t_{i})\sqrt{(\gamma_{1}'(c_{i}))^{2} + (\gamma_{2}'(c_{i}))^{2}}
$$
y respecto al eje $Y$,
$$
\sum_{i=0}^{n-1} \gamma_{1}(\xi_{i}) \cdot  \rho (\xi_{i})(t_{i+1}-t_{i})\sqrt{(\gamma_{1}'(c_{i}))^{2} + (\gamma_{2}'(c_{i}))^{2}}
$$
Como $\xi_{i}$ y $c_{i}$ no son necesariamente el mismo punto, estas no son exactamente sumas de Riemann; sin embargo, por [[Continuidad Uniforme|continuidad uniforme]] convergen a las integrales siguientes.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Es la varilla otra vez, pero doblada: partimos la curva en arcos, concentramos la masa de cada arco en un punto $\gamma(\xi_{i})$ (la masa es la densidad por la **longitud del arco**), y promediamos. Ojo: el centroide de una curva casi nunca está sobre la curva.
>
> <img src="/videos/centroide-curva.avif" alt="center" width="720" loading="lazy">
>
> *Curva:* alambre semicircular $\gamma(t) = (2\cos(t), 2\sin(t))$, $t \in [0,\pi]$, con densidad constante, partido en $n = 1, 2, 4, 8, 16$ arcos (cada punto es el punto medio de su arco). Con un arco el centroide está sobre el alambre ($\bar{y}_{1} = 2$); al refinar baja ($1.41,\ 1.31,\ 1.28, \dots$) hasta $\left( 0, \frac{2r}{\pi} \right) = \left( 0, \frac{4}{\pi} \right) \approx (0,\ 1.27)$, dentro del semicírculo.

> [!theorem] **Definición.** (Momento de función paramétrica)
>
> Los momentos de una varilla dada por $\gamma(t) = \left( \gamma_{1}(t), \gamma_{2}(t)  \right)$, $t \in [a,b]$, de clase $C^{1}$ son:
> $$
> \begin{align}
> M_{X} &= \int_{a}^{b} \gamma_{2}(t)\rho(t) \sqrt{(\gamma_{1}'(t))^{2} + (\gamma_{2}'(t))^{2}} \, dt \\[0.5em]
> M_{Y} &= \int_{a}^{b} \gamma_{1}(t)\rho(t) \sqrt{(\gamma_{1}'(t))^{2} + (\gamma_{2}'(t))^{2}} \, dt
> \end{align}
> $$

> [!theorem] **Definición.** (Centroide paramétrico)
>
> Las coordenadas del centroide de una curva dada por $\gamma(t) = (\gamma_{1}(t), \gamma_{2}(t))$ son, donde $\displaystyle M_{T} = \int_{a}^{b} \rho(t)\sqrt{(\gamma_{1}'(t))^{2} + (\gamma_{2}'(t))^{2}} \, dt$ es la masa total
> $$
> \begin{align}
> \bar{y} &= \frac{M_{X}}{M_{T}} = \frac{\displaystyle \int_{a}^{b} \gamma_{2}(t) \rho(t)  \sqrt{(\gamma_{1}'(t))^{2} + (\gamma_{2}'(t))^{2}}\, dt}{\displaystyle\int_{a}^{b} \rho(t)\sqrt{(\gamma_{1}'(t))^{2} + (\gamma_{2}'(t))^{2}} \, dt} \\[0.5em]
> \bar{x} &= \frac{M_{Y}}{M_{T}} = \frac{\displaystyle \int_{a}^{b} \gamma_{1}(t) \rho(t) \sqrt{(\gamma_{1}'(t))^{2} + (\gamma_{2}'(t))^{2}} \, dt}{\displaystyle\int_{a}^{b} \rho(t)\sqrt{(\gamma_{1}'(t))^{2} + (\gamma_{2}'(t))^{2}} \, dt}
> \end{align}
> $$

> [!example]- Ejemplo. (Alambre semicircular)
>
> $\gamma(t) = (r\cos(t), r\sin(t))$, $t \in [0,\pi]$, con $\rho = k$ constante. Como $\sqrt{(\gamma_{1}')^{2} + (\gamma_{2}')^{2}} = \sqrt{r^{2}\sin^{2}(t) + r^{2}\cos^{2}(t)} = r$,
> $$
> \begin{gather}
> M_{T} = \int_{0}^{\pi} k r \, dt = k\pi r \\[0.5em]
> M_{X} = \int_{0}^{\pi} r\sin(t)\, k r \, dt = 2kr^{2} \\[0.5em]
> M_{Y} = \int_{0}^{\pi} r\cos(t)\, kr \, dt = 0
> \end{gather}
> $$
> Así $\displaystyle (\bar{x}, \bar{y}) = \left( 0, \frac{2r}{\pi} \right)$: está sobre el eje de simetría, a $\frac{2}{\pi} \approx 0.64$ del radio, y **no** sobre el alambre.

De aquí, el caso más sencillo por estudiar será cuando
$\rho = k$ y $\gamma(t) = (\gamma_{1}(t), \gamma_{2}(t)) \equiv  (x,f(x))$ (la gráfica de una función). En este caso, con $\gamma(t) = (t, f(t))$ se tiene $\gamma'(t) = (1, f'(t))$, y la constante $k$ se cancela,
$$
\bar{y} =  \frac{\displaystyle\int_{a}^{b} f(x)\sqrt{1 + (f'(x))^{2}} \, dx}{\ell_{\operatorname{graf}(f)}}
$$

$$
\bar{x} =  \frac{\displaystyle\int_{a}^{b} x\sqrt{1 + (f'(x))^{2}} \, dx}{\ell_{\operatorname{graf}(f)}}
$$
y continuamos declarando el [[Teorema de Pappus]].

### Simetría

Muchas veces el centroide se encuentra sin integrar: si la figura es simétrica respecto a un eje, el centroide **tiene** que estar sobre ese eje.

> [!theorem] **Proposición.** (Simetría del centroide)
>
> Con densidad constante:
> 1. Si $f:[-c,c] \to \mathbb{R}$ es **par** con derivada continua, el centroide de su gráfica cumple $\bar{x} = 0$ (está sobre el eje $Y$).
> 2. Si la región entre $f \geq g$ en $[-c,c]$ tiene $f$ y $g$ pares, su centroide cumple $\bar{x} = 0$.
> 3. Si la región es simétrica respecto al eje $X$ (entre $f \geq 0$ y $g = -f$), su centroide cumple $\bar{y} = 0$. Igual para una curva $\gamma$ en $[-c,c]$ con $\gamma_{1}$ par y $\gamma_{2}$ impar.

> [!proof]- **Proof.**
>
> Todo se reduce a que **la integral de una función impar en un intervalo simétrico es $0$** (ver [[Mas propiedades de la integral|Propiedades de la Integral]], paridad).
> 1. Si $f$ es par, $f'$ es impar (derivando $f(-x) = f(x)$: $-f'(-x) = f'(x)$), así que $f'(x)^{2}$ es par y $x\sqrt{1 + f'(x)^{2}}$ es impar. Ent.
> $$
> \bar{x} = \frac{\int_{-c}^{c} x\sqrt{1 + f'(x)^{2}}\,dx}{\ell_{\operatorname{graf}(f)}} = \frac{0}{\ell_{\operatorname{graf}(f)}} = 0
> $$
> 2. $x\left( f(x) - g(x) \right)$ es impar (impar por par), así que $M_{Y} = \int_{-c}^{c} x(f-g)\,dx = 0$.
> 3. $f^{2} - g^{2} = f^{2} - f^{2} = 0$, así que $M_{X} = \frac{1}{2}\int (f^{2}-g^{2})\,dx = 0$. Para la curva, $\gamma_{2}$ es impar y $\sqrt{(\gamma_{1}')^{2} + (\gamma_{2}')^{2}}$ es par ($\gamma_{1}'$ impar, $\gamma_{2}'$ par), así que el integrando de $M_{X}$ es impar. $\blacksquare$

> [!observation]+ **Observación.**
>
> La gráfica de una **función** no puede ser simétrica respecto al eje $X$ (salvo $f \equiv 0$): si $(x,y)$ y $(x,-y)$ están en la gráfica, $y = f(x) = -y$. Por eso, para curvas simétricas respecto al eje $X$ hay que usar curvas paramétricas (inciso 3), como la circunferencia. El alambre semicircular de arriba es el inciso 1 con $\bar{x} = 0$.

Ver también [[Centros de Masa para Actuarios]], donde se observa que $\operatorname{E}[X] = \bar{x}$.
