---
modified: 2026-11-18T16:48:25Z
title: "Probabilidad"
publish: true
type: moc
url: 
tags:
 - moc
 - probability
aliases:
 - Probability
---
> **¿Qué es el azar?**

¿Qué es la probabilidad? $\to$ Estudio de fenómenos aleatorios
¿Fenómeno aleatorio? $\to$ Experimento cuyo resultado no se puede predecir.

##### [[Algebra de Conjuntos]]
Como previo es extremadamente importante saber conjuntos y dominar propiedades.

## [[Combinatoria]]
El *análisis combinatorio* juega un papel importante en el juego de la probabilidad.
## [[Espacio de Probabilidad]]
- [[Sigma-algebra de eventos]] (propiedades de cerradura, $\mathcal{P}(\Omega)$ y la trivial)
  - [[Sigma-algebra de Borel]] ($\sigma$-álgebra generada, intervalos y puntos)
- [[Medida de Probabilidad]] (axiomas de Kolmogórov, propiedades básicas)
	- [[Propiedades de la Medida de Probabilidad]] (inclusión-exclusión, Boole, Bonferroni, $\vartriangle$)
	- [[Medida de Probabilidad Clasica]]
		- [[Cartas de Poker]]
- [[Probabilidad Condicional]] (es medida de probabilidad, regla de la multiplicación)
- [[Independencia de Eventos]] (complementos, independencia de $n$ eventos)
	- [[Eventos Independientes vs. Ajenos]] (cuándo son las dos cosas, los cuatro casos, depende de $P$)
- [[Probablidad Total]]
- [[Teorema de Bayes]]
- [[Continuidad de la Probabilidad]] (límites de eventos monótonos)


## [[Variable Aleatoria]]
- [[Funcion de Masa de Probabilidad]] (función de probabilidad, soporte)
- [[Funcion de Distribucion Acumulada]] (propiedades, calcular con $F$, discreta y mixta)
- [[Funcion de Densidad de Probabilidad]] (y función de distribución continua)
- [[Cambio de Variable Aleatoria]] (caso discreto y continuo, no monótono)
- [[Independencia de Variables Aleatorias]] (discretas y continuas)

A continuación, a cualquier v.a. se le puede calcular las siguientes cantidades númericas, las cuales revelan características de la v.a. o de su distribución.

- [[Esperanza]] (estadístico inconsciente, linealidad, independencia, fórmula del área)
	- [[Desigualdad de Jensen]] (recta de soporte, $1/X$, media geométrica)
- [[Varianza]] (propiedades, suma de independientes, $\bar{X}$, mejor predicción)
- [[Momentos]] (centrales y absolutos, existencia, simetría)
- [[Cuantiles]] (existencia, caso continuo, mediana, función cuantil)
	- [[Metodo de la Transformada Inversa]] (simulación, $F(X)$ uniforme)
- [[Moda]] (existencia, moda contra mediana contra media)
- [[Funcion Generadora de Probabilidad]] (inversión, momentos factoriales, sumas indep.)
- [[Funcion Generadora de Momentos]] (momentos derivando, sumas indep., caracterización)

- [[Falacias]]
falacia del apostador

#### [[Distribuciones de Probabilidad]] (mapa de relaciones)
Distribuciones Discretas:
- [[Distribucion Uniforme Discreta]] (valores consecutivos)
- [[Distribucion de Bernoulli]] (indicadora de un evento)
- [[Distribucion Binomial]] (suma de Bernoullis, f.g.m., suma de binomiales)
- [[Distribucion Geometrica]] (pérdida de memoria)
- [[Distribucion Binomial Negativa]] (suma de geométricas, $F$ con la binomial)
- [[Distribucion Hipergeometrica]] (Vandermonde, corrección por población finita)
- [[Distribucion de Poisson]] (suma, límite de la binomial)

Distribuciones Continuas:
- [[Distribucion Uniforme Continua]] (propiedades, transformación lineal)
- [[Distribucion Exponencial]] (pérdida de memoria, parte entera geométrica)
- [[Distribucion Gamma]] (Erlang, sumas, relación con Poisson)
	- [[Funcion Gamma]] ($\Gamma(n+1) = n!$, $\Gamma(\frac{1}{2}) = \sqrt{ \pi }$)
- [[Distribucion Beta]] (forma según $a$ y $b$, cociente de gammas)
	- [[Funcion Beta]] (relación con $\Gamma$, propiedades)
- [[Distribucion Weibull]] (relación con la exponencial, tasa de falla)
- [[Distribucion Normal]] (estandarización, $\Phi$ y $z_{\alpha}$, sumas, cotas de la cola, lognormal)
	- [[Integral Gaussiana]]
- [[Distribucion ji-cuadrada]] ($Z^{2}$, sumas de cuadrados, varianza muestral)
- [[Distribucion t]] (momentos, Cauchy, $\bar{X}$ con $S$, convergencia a la normal)
- [[Distribucion F]] (momentos, recíproco y tablas, $t^{2}$)

**Profesor:** Daniel Cervantes Filoteo

-----

fenómeno aleatorio en lugar de hablar de una población. 
esto es la conexion con la estadistica. en ML se privilegia mucho la capacidad predictiva, pero de alguna manero va a ser fundamental poder cunatificar esa incertidumbre (inferencia estadistica). 
Variable aleatoria, asumir que estos datos se pueden describir con una variable alatoria.
Necesitamos cuatificar la incertidumbre, una pequeña muestra, proba e inferencia, clasificacion, regresion, estimacion de parametros. en ML con interesa la estimacion por intervalos. 

Motivación

Fenómenos aleatorios, variabilidad e incertidumbre...

Modelos deterministas vs modelos probabilisticos...

inestabilidad del algoritmo, se le puede meter una regularización. 

FA general datos, este fenomeno se puede  describir como una variabla aleatoria... 
modelo de recoleccion, variables aleatorias independientes distribuidas?... tambien se pueden procesos estocasticos, series de tiempos... pero esto es mas complejo.

espacios muestrales, conjuntos, proba 1. vectores aleatorios...
experimento aleatorio... (lanzamiento de la moneda)

resultado, espacio muestra, evento.
Cardinalidad
Teoria de conjuntos. operaciones con conjuntos
Probabilidad super basica lol
Proba coomo función P... axiomas de Kolmogórov
no hay pecs con el $\infty$. 


You can simulate and see empirically who is right.


![[Pasted image 20260408193641.png]]


---
## Demás Recursos:
- 
