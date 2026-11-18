---
modified: 2026-11-18T16:47:12Z
title: "Distribuciones de Probabilidad"
publish: true
type: zettel
date: "2026-09-01"
status: seed
aliases:
tags:
 - probability
cssclasses:
 - romana
---
Muchos experimentos distintos producen v.a.s con la **misma** distribución: el núm. de águilas en $10$ volados y el núm. de piezas defectuosas en un lote de $10$ (si cada una falla indep. con proba. $\frac{1}{2}$) se comportan igual. Por eso conviene estudiar las distribuciones como objetos propios, con nombre, organizadas en **familias paramétricas**: una fórmula que depende de unos pocos parámetros, y que da una distribución para cada valor de ellos.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> Una familia paramétrica es una fórmula para $f$ con perillas.

Se escribe $X \sim \operatorname{Bin}(n,p)$, donde $\sim$ se lee "se distribuye como" o "tiene distribución". Recordemos que lo único que importa de una v.a. para su distribución es $P_{X}$ (ver [[Variable Aleatoria]]): dos v.a.s con la misma distribución son intercambiables para cualquier cálculo de probabilidades, aunque vengan de experimentos completamente distintos.

> [!Info]- **Nota!**
>
> A todas las distribuciones se les puede sacar función de probabilidad (o densidad) y función de distribución; el nombre de la familia no cambia eso. Se clasifican en **discretas** (dan $f(x) = P(X = x)$ en una cantidad numerable de puntos) y **continuas** (dan una densidad), ver [[Funcion de Masa de Probabilidad]] y [[Funcion de Densidad de Probabilidad]].

Las familias no son independientes entre sí: casi todas se obtienen de otras sumando, tomando límites o transformando. Ese mapa es lo que conviene tener en la cabeza, más que cada fórmula.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Cada flecha es un resultado que está en la nota de la distribución de llegada; las punteadas cruzan de discretas a continuas.
> ![[mapa-distribuciones.svg|center|700]]

| Discretas | Modelan | Continuas | Modelan |
|---|---|---|---|
| [[Distribucion Uniforme Discreta\|Uniforme]] | $n$ resultados igual de probables | [[Distribucion Uniforme Continua\|Uniforme]] | un punto al azar en $(a,b)$ |
| [[Distribucion de Bernoulli\|Bernoulli]] | un ensayo éxito/fracaso | [[Distribucion Exponencial\|Exponencial]] | espera sin memoria |
| [[Distribucion Binomial\|Binomial]] | éxitos en $n$ ensayos | [[Distribucion Gamma\|Gamma]] | espera de $\alpha$ eventos |
| [[Distribucion Geometrica\|Geométrica]] | fracasos antes del primer éxito | [[Distribucion Beta\|Beta]] | una proporción |
| [[Distribucion Binomial Negativa\|Binomial negativa]] | fracasos antes del $r$-ésimo éxito | [[Distribucion Weibull\|Weibull]] | vida con desgaste |
| [[Distribucion Hipergeometrica\|Hipergeométrica]] | muestreo sin reemplazo | [[Distribucion Normal\|Normal]] | suma de muchos efectos |
| [[Distribucion de Poisson\|Poisson]] | conteo de eventos raros | [[Distribucion ji-cuadrada\|ji-cuadrada]], [[Distribucion t\|t]], [[Distribucion F\|F]] | estadística de muestras normales |

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 3 (pp. 204–289). <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
