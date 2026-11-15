---
modified: 2026-11-15T18:09:48Z
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
# Aplicaciones de la Integral $\displaystyle \int$

Dadas dos funciones $f,g: [a,b] \to \mathbb{R}$ como se muestran:

![[area-entre-curvas.svg|center|600]]

¿Cómo calcular el área determinada por $f$ y $g$ en $[a,b]$?
Si $f \geq g$ en $[a,b]$ (y ambas son integrables), por medio de $\displaystyle A_{f,g} = \int_{a}^{b} (f(x) - g(x)) \, dx$.

¿Y si ocurre que $g \geq f$? $\displaystyle A_{f,g} = \int_{a}^{b} (g(x) -f(x)) \, dx$

Pero, ¿y si $f$ y $g$ se cruzan? En general, el área es $\displaystyle A_{f,g} = \int_{a}^{b} \left| f(x) - g(x) \right| dx$, y para calcularla partimos $[a,b]$ en los puntos donde se cruzan.

![[area-curvas-cruzadas.svg|center|600]]


Por ejemplo, si $f \geq g$ en $[a,w]$, $g \geq f$ en $[w,y]$ y $f \geq g$ en $[y,b]$:

$$
\int_{a}^{b} \left| f(x) - g(x)\right| \, dx = \int_{a}^{w} (f-g)(x) \, dx + \int_{w}^{y} (g-f)(x) \, dx + \int_{y}^{b} (f-g)(x) \, dx = A_{f,g}
$$
donde $w,y$ son los puntos de intersección entre $f$ y $g$.

Veamos un ejemplo

> [!example]- Ejemplo.
>
> $\square$ Calcula el área comprendida entre $f(x) = \sqrt{1+x^{2}} + 2x - x^{2}$ y $g(x) = \sqrt{1+x^{2}} - 3x + 2$.
>
> Para esto, calculamos los puntos de intersección entre $f$ y $g$.
> Y solo calcularemos el área del intervalo de tales puntos, pues más allá, el área es indefinida (infinita).
> $$
> f(x) - g(x) = 2x - x^{2} + 3x - 2 = -x^{2} + 5x - 2 \tag{las raíces se cancelan}
> $$
> que se anula en $\displaystyle x_{\pm} = \frac{5 \pm \sqrt{17}}{2}$, y entre ellas es positiva (parábola que abre hacia abajo).
> Para quitar un valor absoluto hay que ver que la función es positiva en nuestro intervalo, ¡lo cual pasa en esta integral!
> $$
> \begin{align}
> A &= \int_{x_{-}}^{x_{+}} (-x^{2} + 5x - 2) \, dx = \int_{x_{-}}^{x_{+}} (x_{+} - x)(x - x_{-}) \, dx \tag{factor.} \\[0.5em]
> &= \frac{(x_{+} - x_{-})^{3}}{6} = \frac{(\sqrt{17})^{3}}{6} = \boxed{\frac{17\sqrt{17}}{6}}
> \end{align}
> $$
> (La segunda igualdad: con $x = x_{-} + s$ y $h = x_{+}-x_{-}$, queda $\int_{0}^{h} (h - s)s \, ds = \frac{h^{3}}{2} - \frac{h^{3}}{3} = \frac{h^{3}}{6}$.)


> [!example]- Ejemplo. (Área de un Círculo)
>
> $\square$ Calcular el área del Círculo!
> **PD.** $A_{0} = \pi r^{2}$
>
> $$
> x^{2} + y ^{2} = r^{2} \implies  y = \pm \sqrt{r^{2} - x^{2}}
> $$
> Entonces definimos $f(x) = \sqrt{r^{2} - x^{2}}$ y $g(x) = -\sqrt{r^{2} - x^{2}}$
> y vemos que estan definidas como $f,g: [-r,r] \to \mathbb{R}$.
> Así,
> $$
> \begin{align}
> & A_{0} \\[0.5em]
> &= \int_{-r}^{r} (f(x) - g(x)) \, dx \\[0.5em]
> &= \int_{-r}^{r} 2\sqrt{r^{2}-x^{2}} \, dx \\[0.5em]
> &= 2\int_{-\frac{\pi}{2}}^{\frac{\pi}{2}} r\cos(\theta)\cdot r\cos(\theta) \, d\theta \tag{$x = r\sin(\theta)$} \\[0.5em]
> &= 2r^{2}\left[ \frac{\theta}{2} + \frac{\sin(2\theta)}{4} \right]_{-\frac{\pi}{2}}^{\frac{\pi}{2}} \\[0.5em]
> &= 2r^{2}\cdot \frac{\pi}{2} \\[0.5em]
> &= \boxed{\pi r^{2}}
> \end{align}
> $$
> (La sustitución es el Caso 1 de [[Sustitucion Trigonometrica]], y $\int\cos^{2}$ está en [[Integrales Trigonometricas]].)


> [!example]- Ejemplo. 
>
> $\square$ Calcular el área encerrada entre $f(x) = r\cos(x)$ y el eje $x$, con $r > 0$, en $[0, 2\pi]$.
>
> Observamos la gráfica de $r\cos(x)$ entre $x= 0$ y $x = 2\pi$: cambia de signo en $\frac{\pi}{2}$ y $\frac{3\pi}{2}$, así que partimos ahí.
> $$
> \begin{align}
> & A \\[0.5em]
> &= \int_{0}^{2\pi} \left| r\cos(x) \right| dx \\[0.5em]
> &= r\left[ \int_{0}^{\frac{\pi}{2}} \left| \cos(x) \right| \, dx + \int_{\frac{\pi}{2}}^{\frac{3\pi}{2}} \left| \cos(x) \right| \, dx + \int_{\frac{3\pi}{2}}^{2\pi} \left| \cos(x) \right| \, dx \right] \\[0.5em]
> &= r\left[ \int_{0}^{\frac{\pi}{2}} \cos(x)  \, dx + \int_{\frac{\pi}{2}}^{\frac{3\pi}{2}} - \cos(x) \, dx + \int_{\frac{3\pi}{2}}^{2\pi}  \cos(x)  \, dx \right] \\[0.5em]
> &= r\left[ \sin(x)\bigg|_{0}^{\frac{\pi}{2}} + \left( -\sin(x)\bigg|_{\frac{\pi}{2}}^{\frac{3\pi}{2}} \right) + \sin(x)\bigg|_{\frac{3\pi}{2}}^{2\pi} \right] \\[0.5em]
> &= r(1 + 2 + 1) \\[0.5em]
> &= 4r
> \end{align}
> $$

> [!example]- Ejemplo. (Área de un sector del círculo)
>
> Sector de radio $r$ y ángulo $\theta \in \left[ 0, \frac{\pi}{2} \right]$: área del triángulo + integral del intervalo de $r\cos(\theta )$ a $r$.
> Después de visualizar una gráfica para identificar las áreas a calcular, determinamos que necesitamos la suma de un triángulo y una parte del área del círculo:
> $$
> \begin{align}
>   A_{1} &= \frac{r\cos(\theta)r\sin(\theta)}{2}\\[0.5em]
>   A_{2} &= \int_{r\cos(\theta)}^{r} \sqrt{r^{2}-x^{2}} \, dx
> \end{align}
> $$
> Resolvemos la integral con sust. trig. $x = r\cos(\alpha)$, $dx = -r\sin(\alpha)\,d\alpha$ ($x = r\cos(\theta) \mapsto \alpha = \theta$, $x = r \mapsto \alpha = 0$, y $\sqrt{r^{2}-x^{2}} = r\sin(\alpha)$):
> $$
> A_{2} = -r^{2}\int_{\theta}^{0} \sin^{2}(\alpha) \, d\alpha = r^{2}\int_{0}^{\theta} \sin^{2}(\alpha) \, d\alpha = \frac{r^{2}}{2}\cdot \left( \theta - \frac{\sin(2\theta)}{2}  \right)
> $$
> Así, el área del sector es: $\displaystyle A_{\mathcal{S}} = A_{1} + A_{2} = \frac{r^{2}\sin(2\theta)}{4} + \frac{r^{2}\theta}{2} - \frac{r^{2}\sin(2\theta)}{4}$ (pues $\sin\theta\cos\theta = \frac{\sin 2\theta}{2}$)
> $$
> \boxed{A_{\mathcal{S}} = \frac{r^{2}\theta}{2}}
> $$

## Cambio de Coordenadas
Los cambios de coordenadas son transformaciones $T: \mathbb{R}^{2} \to  \mathbb{R}^{2}$ continuas y diferenciables ("*bonitas*").



### Coordenadas polares
Intuitivamente sabemos que un punto en coordenadas polares (radio $\rho$, ángulo $\theta$) es, en cartesianas,
$$
x = \rho\cos(\theta), \qquad y = \rho\sin(\theta)
$$

Voy a tomar la transformación,
$$
T(\theta,\rho) = (\rho \cos(\theta), \rho \sin(\theta))
$$

Nos estamos moviendo, ahora, con radios $\rho$ y ángulos $\theta$, sobre un **radar**.


![[IMG_6971.jpeg|416|center|432]]
El objetivo ahora es calcular el área de funciones que tengan como parámetro un ángulo $\theta$ (*coordenadas polares*).

![[IMG_6972.jpeg|center|627]]

Sea $f: [\theta_{1},\theta_{2}] \to \mathbb{R}$ continua con $f \geq 0$ y $\theta_{2} - \theta_{1} \leq 2\pi$. Recordando que un sector de radio $\rho$ y ángulo $\theta_{2}-\theta_{1}$ tiene área $\frac{\rho^{2}(\theta_{2}-\theta_{1})}{2}$ (ejemplo del sector, arriba), el área de $f(\theta)$ se encuentra entre la pizza amarilla y la roja, lo que nos lleva a:
$$
\min \left\{f\right\}^{2} \frac{(\theta_{2} - \theta_{1})}{2} \leq A_{f(\theta)}\leq  \max \left\{f\right\}^{2} \frac{(\theta_{2}-\theta_{1})}{2}
$$
Ent.
$$
L\left(\frac{f^{2}(\theta)}{2}\right) = \frac{\min \left\{f(\theta)\right\}^{2} }{2}(\theta_{2}-\theta_{1}) \leq A_{f(\theta)} \leq  \frac{\max \left\{f(\theta)\right\}^{2} }{2}(\theta_{2}-\theta_{1}) = U\left( \frac{f^{2}(\theta)}{2}  \right)
$$



<div style="display: flex; gap: 20px; align-items: center;">
  <div style="flex: 1;">
    Si retomamos nuestra pizza, entonces tenemos que considerar una partición de tal intervalo.
    Al ser
    <span class="math-inline">
        A_{f(\theta)}
    </span>
    acotada por sumas inferiores y superiores asociadas a la función
    <span class="math-inline">
        \displaystyle \frac{f^{2}(\theta)}{2}
    </span>
     definimos el área de una curva en coordenadas polares en
    <span class="math-inline">
        [\theta_{1},\theta_{2}]
    </span>
     por:
    <div style="text-align: center; width: 100%; margin: 15px 0;">
      <span class="math-inline">
          \boxed{\int_{\theta_{1}}^{\theta_{2}} \frac{f^{2}(\theta)}{2} \, d\theta}
      </span>
    </div>
  </div>
  <div style="flex: 1; text-align: center;"> <!-- 💡 Opcional: Centrar también la imagen en su columna -->
      <img src="/images/IMG_6973.jpeg" width="250">

  </div>
</div>

> [!example]- Ejemplo.
>
> $\square$ Dibuja la curva generada por $\rho = 2 \cos(2\theta)$ y determina el área que encierra.
>
> Es una rosa de 4 pétalos: $\rho$ vale $2$ en $\theta = 0, \frac{\pi}{2}, \pi, \frac{3\pi}{2}$ y se anula a la mitad entre ellos. Al recorrer $\theta \in [0,2\pi]$ se dibuja cada pétalo una vez (cuando $\cos(2\theta) < 0$, el punto cae en el pétalo opuesto), así que
> $$
> \begin{align}
> A &= \int_{0}^{2\pi} \frac{(2\cos(2\theta))^{2}}{2} \, d\theta = 2\int_{0}^{2\pi} \cos^{2}(2\theta) \, d\theta \\[0.5em]
> &= 2\left[ \frac{\theta}{2} + \frac{\sin(4\theta)}{8} \right]_{0}^{2\pi} = \boxed{2\pi}
> \end{align}
> $$
> Así, el área encerrada por la curva es $2\pi$ (cada pétalo mide $\frac{\pi}{2}$).




Es el tema de métodos de integración pero con otros formulazos.




