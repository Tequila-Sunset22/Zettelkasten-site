---
modified: 2026-11-15T14:18:14Z
publish: true
type: zettel
date: "2026-09-01"
status: seed
aliases:
tags:
 - calculus
cssclasses:
 - romana
---
# Definiendo $\int$

Queremos darle sentido al "área bajo la curva" de una función $f$ en un intervalo $[a,b]$. Antes de construirla, decidimos qué propiedades **debe** tener cualquier cosa que llamemos integral.

> Definimos la integral simplemente como un número que cumple esas dos propiedades:
> 
> *Aditividad:* Es que el área bajo la curva se puede dividir en pedazos.
> 
> *Acotación:* es el hecho, que el área bajo la curva está acotada entre el rectángulo *más grande* y el *más pequeño* posible del intervalo.


> [!theorem] **Definición.** (Integral, de forma axiomática)
>
> Dada una función $f : [a,b] \to \mathbb{R}$ en principio, continua.
> Dados $u,v \in [a,b]$ tales que $a \leq u\leq v \leq b$, se entiende a la **integral** de $f$ en $[u,v]$ como el *"número"* $\displaystyle \int_{u}^{v} f(x) \ dx$ que cumple las siguientes propiedades.
> - Aditividad o Acumulatividad: 
> $$
> \int_{a}^{u} f + \int_{u}^{v}f = \int_{a}^{v} f
> $$
> - Acotación o Intercalación:
> $$
> (v-u) \cdot \underset{[u,v]}{\min} \{ f \} \leq \int_{u}^{v} f(x) dx \leq (v-u)\cdot \underset{[u,v]}{\max} \{ f \}
> $$

> [!observation]+ **Observación.**
>
> Esto todavía **no** es una construcción: no dice si ese número existe, ni si es único. Lo construimos para $f$ continua con sumas inferiores y superiores en [[Integral de Darboux]], y ahí mismo probamos que cumple estas dos propiedades. Después, en [[Generalizando la Integral]], lo extendemos a funciones acotadas, cambiando $\min$/$\max$ por $\inf$/$\sup$.

### Particiones de un Intervalo

Para aproximar el área cortamos $[a,b]$ en pedazos.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Una partición es una forma de cortar $[a,b]$ en subintervalos. Al **refinarla** (agregar puntos) los pedazos se hacen más chicos; la *norma* mide el más grande de ellos.
>
> <img src="/videos/particion-refinamiento.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** (Partición $\mathcal{P}$)
>
> Sea $a < b$. Una **partición** del intervalo $[a,b]$ es una colección finita de puntos de $[a,b]$, uno de los cuales es $a$ y otro es $b$. Se enumeran de forma
> $$
> \mathcal{P}_{[a,b]} = \{ x_{0},x_{1},\dots,x_{n} \} \quad \text{ tal que } \quad a = x_{0} < x_{1} < \dots < x_{n-1} < x_{n} = b
> $$
> Los **subintervalos** de $\mathcal{P}$ son $[x_{k}, x_{k+1}]$, para $k \in \{ 0, \dots, n-1 \}$.
> 
> La **norma** de la partición es la longitud del subintervalo más grande:
> $$
> \Delta \mathcal{P} = \max_{0 \leq k \leq n-1} \{ x_{k+1} - x_{k} \}
> $$

> [!example]- Ejemplo. (Partición regular)
>
> Para $n \in \mathbb{N}^{+}$, la partición de $[a,b]$ en $n$ subintervalos iguales es
> $$
> \mathcal{P}_{n} = \left\{ x_{k} = a + \frac{k(b-a)}{n} \;\middle|\; k = 0, \dots, n \right\}, \qquad \Delta \mathcal{P}_{n} = \frac{b-a}{n}
> $$
> Por la Prop. Arquimediana, $\Delta \mathcal{P}_{n}$ se hace tan chica como queramos.

> Sea $\mathcal{P}$ partición, se puede cortar alguno de sus subintervalos para crear $\mathcal{P}'$, así tenemos $\mathcal{P} \subseteq \mathcal{P}'$.

> [!theorem] **Definición.** (Refinamiento de $\mathcal{P}$)
>
> Dados $[a,b] \subseteq \mathbb{R}$ y $\mathcal{P}_{[a,b]}$ decimos que $\mathcal{P}'_{[a,b]}$ es un **refinamiento** de $\mathcal{P}$ si
> $$
> \mathcal{P}_{[a,b]} \subseteq \mathcal{P}'_{[a,b]}
> $$

> [!observation]+ **Observación.**
>
> 1. $\Delta \mathcal{P}' \leq \Delta \mathcal{P}$. Esto es porque cada subintervalo de $\mathcal{P}'$ está contenido en algún subintervalo de $\mathcal{P}$: el refinamiento pudo haber partido al subintervalo más grande (y la norma baja) o no (y la norma sigue igual, $\Delta \mathcal{P} = \Delta \mathcal{P}'$).
> 2. Dadas dos particiones $\mathcal{P}_{1}, \mathcal{P}_{2}$ de $[a,b]$, $\mathcal{P}_{1} \cup \mathcal{P}_{2}$ es un refinamiento de **ambas** (un *refinamiento común*).

La palabra "partición" también se usa en conjuntos ([[Particion]]), con otro sentido: allá los bloques son disjuntos; aquí los subintervalos comparten extremos.
