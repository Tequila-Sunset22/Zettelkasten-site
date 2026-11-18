---
modified: 2026-11-17T20:06:25Z
title: "Sólidos de Revolución"
publish: true
type: zettel
date: "2026-10-23"
status: seed
aliases:
tags:
 - calculus
cssclasses: 
 - romana
---
### Volumen, método de discos

Sea $f:[a,b]\to \mathbb{R}$ continua con gráfica como se muestra. Consideramos la revolución de la gráfica de $f$ alrededor del eje $x$, lo que determina su superficie.

¿Cómo calculamos su volumen?

- La propuesta es, $\displaystyle 2\pi \int_{a}^{b} f(x) \, dx$, ¿será? pues intuitivamente tiene sentido, simplemente rotar la función...

Conociendo el volumen de un cilindro, recordando, $V = \pi r^{2}h$,  donde $h$ es la altura del cilindro y $r$ el radio de su circunferencia. ¿Cómo podemos aproximar el cilindro para que represente el volumen de nuestra función $f$? Podemos ver el volumen de un cilindro dentro de la gráfica de la función como



$$
V = \pi f(z)^{2} (x_{2}-x_{1})
$$
con $z \in [x_{1}, x_{2}]$.
Considerando una partición en el intervalo $[a,b]$, una aproximación al volumen del sólido de revolución es:


$$
\sum_{k=0}^{n-1} \pi f(z_{k})^{2} (x_{k+1} - x_{k})
$$
con $z_{k} \in [x_{k}, x_{k+1}]$, lo cual es una Suma de Riemann para $\pi f^{2}$.

Así, la propuesta inicial no era correcta: el volumen no depende de $f$, sino de $f^{2}$, pues cada disco tiene volumen $\pi r^{2}h$ con $r = f(z)$.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Cada rectángulo de la suma de Riemann, al girar alrededor del eje $x$, barre un disco (un cilindro muy delgado) de radio $f(z_{k})$ y grosor $x_{k+1}-x_{k}$. Los discos apilados aproximan el sólido, y al refinar su volumen total tiende al volumen del sólido.
>
> <img src="/videos/discos.avif" alt="center" width="720" loading="lazy">
>
> *Sólido:* la esfera de radio $2$ (el ejemplo de abajo), con $n = 6$ y $12$ discos: $V_{n} = 33.98,\ 33.63 \to \frac{4}{3}\pi(2)^{3} \approx 33.51$.

> [!theorem] **Definición.** (Volumen de un Sólido de Revolución)
>
> El volumen del sólido de revolución generado a partir de $f:[a,b] \to \mathbb{R}$ es
> $$
> \pi \int_{a}^{b} f^{2}(x) \, dx
> $$

> [!example]- Ejemplo.
>
> $\square$ Calcula el volumen de una esfera de radio $r$.
> Recordando la función de una media luna positiva (de cuando sacamos el área del círculo en [[Aplicaciones de la Integral]]), $f(x)= \sqrt{r^{2} - x^{2}}$. Ent. el volumen es,
> $$
> \begin{align}
>   V &= \pi \int_{-r}^{r} (r^{2}-x^{2}) \, dx \\[0.5em]
>    &=  \pi \left[ \int_{-r}^{r} r^{2} \, dx - \int_{-r}^{r} x^{2} \, dx  \right] \tag{linealidad} \\[0.5em]
>     &= \pi \left[ 2r^{3} - \frac{2r^{3}}{3}  \right] \tag{T.F.C.} \\[0.5em]
>     &= \boxed{\frac{4}{3}\pi r^{3}}
> \end{align}
> $$


### Área

> [!example]- Ejemplo. 
>
> $\square$ Calcula el área lateral (sin la base) de un cono de altura $h$, generatriz $l$ y radio $r$.
>
> El área de un sector de radio $p$ es
> $$
> \frac{p^{2} \theta}{2} = \frac{l^{2} \theta}{2}
> $$
> pues al desenrollar el cono, el radio del sector es $p = l$.
> El arco del sector mide $2\pi r$ (la circunferencia de la base), y la longitud de arco es proporcional al ángulo, por lo que $2\pi r$ es a $\theta$ como $2\pi l$ (círculo completo) es a $2\pi$.
> Tenemos la conversión siguiente,
> $$
> \frac{2\pi r}{ \theta} = \frac{ 2\pi l}{ 2\pi} \implies \theta = \frac{2\pi r}{l}
> $$
> Así, el área del cono (de helado) es: $\displaystyle \frac{l^{2} \theta}{2} = \frac{l^{2}\left(\frac{2\pi r}{l}  \right)}{2} = \boxed{\pi  r l}$


> [!example]- Ejemplo. 
>
> Calcula el área lateral de un cono truncado con un corte perpendicular respecto a la altura.
> 
> Claramente, el área está dada por: $A = A_{C} - A' = \pi r_{1} l - \pi r_{2} l'$, donde $A_{C}$ es el área del cono completo, y $A'$ es el área del cono que buscamos cortar.
>
> Por semejanza de triángulos se tiene: $\displaystyle \frac{r_{1}}{r_{2}} = \frac{l}{l'} \implies l' = \frac{lr_{2}}{r_{1}}$.
> Entonces,
> $$
> \begin{align}
> A &= \pi r_{1} l - \pi r_{2} \frac{l r_{2}}{r_{1}} = \pi l \left[ r_{1} - \frac{r_{2}^{2}}{r_{1}}  \right] \tag{sust. $l'$} \\[0.5em]
>  &= \frac{\pi l [ r_{1} + r_{2}] [r_{1} - r_{2}]}{r_{1}} \tag{dif. de cuadrados}
> \end{align}
> $$
> Por semejanza del mismo triángulo, $\displaystyle \frac{r_{2}}{r_{1}} = \frac{l'}{l}$; restando ambos lados de 1: $\displaystyle \frac{r_{1} - r_{2}}{r_{1}} = \frac{l - l'}{l}$
> Así,
> $$
> \begin{align}
> A &= \pi l (r_{1} + r_{2}) \frac{(l - l')}{l} \tag{sust.} \\[0.5em]
>  &= \boxed{\pi ( r_{1} + r_{2}) (l - l')} \tag{se cancela $l$}
> \end{align}
> $$
> donde $l-l'$ es el lado del cono truncado.



Supongamos que $f: [a,b] \to  \mathbb{R}^{+}$ continua tal que su gráfica se ve como sigue,

![[Guia para escribir en tiempo real con nvim y obsidian 20261101112625.jpg|center|300]]

Revolucionemos la curva dada por la gráfica de $f$ alrededor del eje $x$.
Dado el ejemplo anterior, tenemos que el área del cono truncado construido a partir de $(x_{1}, f(x_{1}))$ y $(x_{2}, f(x_{2}))$ es:
$$
\pi (f(x_{1}) + f(x_{2})) \sqrt{(x_{2}-x_{1})^{2} + (f(x_{2}) - f(x_{1}))^{2}}
$$
Tomando una partición $P$ de $[a,b]$ obtenemos una aproximación al área del sólido por medio de
$$
\sum_{k=0}^{n-1} \pi (f(x_{k+1}) + f(x_{k})) \sqrt{(x_{k+1} - x_{k})^{2} + (f(x_{k+1}) - f(x_{k}))^{2}}
$$
$$
= \sum_{k=0}^{n-1} \pi (f(x_{k+1}) + f(x_{k})) (x_{k+1} - x_{k}) \sqrt{ 1 + \frac{(f(x_{k+1}) - f(x_{k}))^{2}}{(x_{k+1} - x_{k})^{2}}} \tag{factor.}
$$
donde $(x_{k+1}-x_{k})$ sale de la raíz sin v.a. pues $x_{k+1} > x_{k}$.
Suponiendo que $f$ es derivable tenemos, por T.V.M. en $[x_{k}, x_{k+1}]$, que existe $c_{k}$ tal que $\displaystyle f'(c_{k}) = \frac{f(x_{k+1})-f(x_{k})}{x_{k+1}-x_{k}}$, ent.
$$
\sum_{k=0}^{n-1} \pi (f(x_{k+1})+f(x_{k})) (x_{k+1} - x_{k}) \sqrt{1 + f'(c_{k})^{2}}
$$

Además, a consecuencia del Teorema del Valor Intermedio, va a existir un $d_{k}$ tal que $f(x_{k+1}) + f(x_{k}) = 2 f(d_{k})$, pues el promedio $\frac{f(x_{k+1})+f(x_{k})}{2}$ está entre $f(x_{k})$ y $f(x_{k+1})$, y $f$ es continua, ent.
$$
\sum_{k=0}^{n-1} \pi (2f(d_{k})) ( x_{k+1} - x_{k}) \sqrt{1 + f'(c_{k})^{2}}
$$
con $c_{k}, d_{k} \in  [x_{k}, x_{k+1}]$, son puntos intermedios del intervalo.

Notemos que, como $c_{k}$ y $d_{k}$ no son necesariamente el mismo punto, esta no es exactamente una suma de Riemann; sin embargo, si $f'$ es continua, por continuidad uniforme la suma converge a la integral de $2\pi f(x)\sqrt{1+f'(x)^{2}}$ (Teorema de Bliss/Duhamel).

Un área es necesariamente positiva, por lo que añadimos v.a. a $f(x)$.


> [!tip|idea]+ **Idea Intuitiva.**
>
> Aproximamos la curva con una poligonal, como para la longitud de arco. Cada segmento, al girar alrededor del eje $x$, barre un **cono truncado** (una banda inclinada, no un cilindro), cuya área ya conocemos: $\pi(f(x_{k}) + f(x_{k+1}))$ por el largo del segmento. Al refinar, las bandas se pegan a la superficie.
>
> <img src="/videos/superficie-x.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Definición.** (Área de una superficie de revolución sobre el eje X)
>
> El área de la superficie de revolución generada por la gráfica de $f:[a,b]\to \mathbb{R}$, con $f'$ continua, es,
> $$
> 2\pi \int_{a}^{b}  \left| f(x) \right| \sqrt{1 + f'(x)^{2}} \, dx
> $$

> [!observation]+ **Observación.**
>
> ¿Cuál es el área del cilindro? $A = 2\pi r \cdot h$,
> Sabemos que $\int_{a}^{b} \sqrt{1+f'(x)^{2}} \, dx$ es la longitud de la gráfica de $f(x)$.
> Así, observamos que la fórmula del área de una superficie de revolución generaliza de alguna manera el concepto de área de un cilindro recto con base circular.
> En efecto, si $f(x) = r$ constante, entonces $f'(x) = 0$ y $\displaystyle 2\pi \int_{a}^{b} r \, dx = 2\pi r (b-a) = 2\pi r h$.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Lo mismo, pero girando alrededor del eje vertical: ahora cada banda tiene **radio** $x_{k}$ (la distancia al eje $Y$), no $f(x_{k})$. Por eso en el formulazo aparece $\left| x \right|$ en lugar de $\left| f(x) \right|$.
>
> <img src="/videos/superficie-y.avif" alt="center" width="720" loading="lazy">

> [!theorem] **Corolario.** (Área de una superficie de revolución sobre el eje Y)
>
> Sea $f:[a,b]\to \mathbb{R}$ con $f'$ continua y $a \geq 0$ (o $b \leq 0$, para que la curva no cruce el eje $Y$). El área de la superficie que se genera al girar la gráfica de $f$ alrededor del eje $Y$ es
> $$
> 2\pi \int_{a}^{b} \left| x \right| \sqrt{1 + f'(x)^{2}} \, dx
> $$

> [!proof]- **Proof.**
>
> Es la misma construcción que sobre el eje $X$, cambiando el papel de los radios: al girar alrededor del eje $Y$, el punto $(x_{k}, f(x_{k}))$ describe una circunferencia de radio $\left| x_{k} \right|$ (su distancia al eje $Y$). El cono truncado entre $(x_{k}, f(x_{k}))$ y $(x_{k+1}, f(x_{k+1}))$ tiene área $\pi (\left| x_{k} \right| + \left| x_{k+1} \right|)\sqrt{(x_{k+1}-x_{k})^{2} + (f(x_{k+1}) - f(x_{k}))^{2}}$, y con T.V.M., T.V.I. y continuidad uniforme, igual que arriba, la suma converge a la integral. $\blacksquare$

> [!observation]+ **Observación.**
>
> Cuando rotamos sobre el eje $Y$ podemos resolver de dos formas: expresando todo en términos de la función inversa $x(y)$ (si existe), o simplemente tomando $\left| x \right|$ en lugar de $\left| f(x) \right|$ en el formulazo:
> $$
> 2\pi \int_{y_{1}}^{y_{2}} \left| x(y) \right| \sqrt{1 + x'(y)^{2}} \, dy = S = 2\pi \int_{a}^{b} \left| x \right| \sqrt{1  + f'(x)^{2}} \, dx
> $$

> [!example]- Ejemplo. (Disco parabólico)
>
> Un disco para satélite tiene la forma de $y = ax^{2}$ girada alrededor del eje $Y$, con $10$ ft de diámetro y $2$ ft de profundidad. El borde está en $x = 5$ a altura $2$, así que $2 = 25a$ y $a = \frac{2}{25}$. Con $f'(x) = 2ax$ y $x \geq 0$,
> $$
> \begin{align}
> & S = 2\pi\int_{0}^{5} x\sqrt{1 + 4a^{2}x^{2}} \, dx \\[0.5em]
> &= \frac{\pi}{4a^{2}}\int_{1}^{1+100a^{2}} \sqrt{u} \, du \tag{$u = 1 + 4a^{2}x^{2}$} \\[0.5em]
> &= \frac{\pi}{6a^{2}}\left[ (1+100a^{2})^{\frac{3}{2}} - 1 \right] = \frac{5\pi\left( 41\sqrt{41} - 125 \right)}{24} \approx 90.01 \text{ ft}^{2}
> \end{align}
> $$


### Método de los casquillos


> [!tip|idea]+ **Idea Intuitiva.**
>
> Ya sabemos cómo calcular volúmenes de cilindros, ¿no? Bueno, como es habitual, el proceso es aproximar el volumen de otra cosa que no conocemos por medio de volúmenes que ya conocemos, como un pan de muerto agujerado o una piedra taladrada, por medio de volúmenes de cilindros agujerados.
>
> Una franja de la región, al girar alrededor del eje $Y$, barre un casquillo (cilindro agujerado). Si lo cortamos y lo desenrollamos, es casi una placa de **largo** $2\pi x'$ (la circunferencia), **alto** $f(x')$ y **grosor** $x_{2}-x_{1}$:
>
> <img src="/videos/casquillos.avif" alt="center" width="720" loading="lazy">
>
> *Región:* bajo $f(x) = 0.5 + 4(x-0.4)(1.6-x)$ en $[0.4, 1.6]$, girada alrededor del eje $Y$ (el pan de muerto agujerado, en gris).

Sea $f:[a,b]\to \mathbb{R}^{+}$ continua con $a\geq 0$, cuya gráfica es como sigue.

![[Pasted image 20261029161221.png|center]]

Consideremos los segmentos de recta que van de $(a,0)$ a $(a,f(a))$ y $(b,0)$ a $(b,f(b))$.
La región $A$ determinada por la gráfica de $f$, el eje $x$ y dichos segmentos la revolucionamos alrededor del eje $Y$ para obtener nuestro pan de muerto agujerado.

¿Cómo obtenemos el volumen $V$ de eso?

Recordando el volumen de un cilindro: $\pi r^{2} h$
Sea $\displaystyle x' = \frac{x_{1}+x_{2}}{2}$ (punto medio). El sólido generado por el rectángulo con base $\overline{x_{1}x_{2}}$ y altura $f(x')$, revolucionado alrededor del eje $Y$, tiene por volumen (*de un cilindro agujerado*: el cilindro de radio $x_{2}$ menos el hueco de radio $x_{1}$):
$$
\begin{align}
\pi x_{2}^{2} \cdot f(x') - \pi x_{1}^{2} \cdot f(x') &= \pi f(x') \left[ x_{2}^{2} - x_{1}^{2}\right] && \text{factor común} \\[0.5em]
&= \pi f(x') \left(\frac{(x_{2}+x_{1})}{2}\right)(x_{2}-x_{1})\cdot 2 && \text{dif. de cuadrados, } \cdot\tfrac{2}{2} \\[0.5em]
&= 2\pi f(x')\cdot x'(x_{2}-x_{1}) && x' = \tfrac{x_{1}+x_{2}}{2}
\end{align}
$$

> [!note]- Intuición
>
> $2\pi x' \cdot f(x') \cdot (x_{2}-x_{1})$ es *circunferencia × altura × grosor*: si cortamos el casquillo verticalmente y lo "desenrollamos", obtenemos (aproximadamente) una placa de largo $2\pi x'$, alto $f(x')$ y grosor $x_{2}-x_{1}$.

Así, una aproximación al volumen de $V$ será
$$
\sum_{k=0}^{n-1} 2\pi f(x'_{k})x'_{k}(x_{k+1}-x_{k})
$$
con $x'_{k}$ el punto medio de $[x_{k}, x_{k+1}]$, dada una partición $\mathcal{P}_{[a,b]}$ la cual es una suma de Riemann para $2\pi x f(x)$.


> [!theorem] **Definición.** (Volumen de S.R. sobre el eje Y)
>
> El volumen $V$, con sus hipótesis, es,
> $$
> 2\pi \int_{a}^{b} x f(x) \, dx
> $$

