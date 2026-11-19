---
modified: 2026-11-18T17:37:35Z
title: "Falacias"
publish: true
type: zettel
date: "2026-11-18"
status: seed
aliases:
 - Falacia del Apostador
 - Problema de Monty Hall
 - Paradoja de los Cumpleaños
tags:
 - probability
cssclasses:
 - romana
---
La intuición sobre el azar falla de formas muy predecibles: creer que el azar "se compensa", leer una condicional al revés, ignorar la información que da quien escoge, subestimar cuántos pares hay en un grupo, confiar en un promedio que no existe. En cada caso la teoría que ya tenemos da la respuesta correcta, y entender **por qué** falla la intuición es la mejor forma de no caer.<sup><a href="#user-content-fn-inline-1" id="user-content-fnref-inline-1" data-footnote-ref class="internal">1</a></sup>

> El azar no tiene memoria, no lee las condicionales al revés, y cuenta pares, no personas.

### La falacia del apostador

Después de cinco soles seguidos en volados justos, mucha gente siente que "ya toca" águila. Es falso: los lanzamientos son [[Independencia de Eventos|independientes]], así que el pasado no cambia nada.

> [!theorem] **Proposición.**
>
> En volados justos e indep., para cualquier sucesión de resultados previos $R$ de los primeros $n$ lanzamientos,
> $$
> P(\text{el lanzamiento } n+1 \text{ es águila} \mid R) = \frac{1}{2}.
> $$

> [!proof]- **Proof.**
>
> Por independencia, $P(\text{águila en } n+1 \cap R) = P(\text{águila en } n+1)P(R) = \frac{1}{2}P(R)$, y se divide entre $P(R) = \frac{1}{2^{n}} > 0$ ([[Probabilidad Condicional]]). $\blacksquare$

La falacia suele venir de una mala lectura de la ley de los grandes números: "la frecuencia tiende a $\frac{1}{2}$, así que si hubo de más soles tienen que venir águilas". Lo que de verdad pasa es que el exceso se **diluye**, no se corrige.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Con $S_{n}$ = núm. de águilas en $n$ volados, $S_{n} - \frac{n}{2}$ es cuántas águilas "sobran" respecto a la mitad, y $\#\text{águilas} - \#\text{soles} = 2\left( S_{n} - \frac{n}{2} \right)$. Su tamaño típico es su desviación estándar, $\frac{\sqrt{ n }}{2}$ (la banda punteada), que **crece**: el atraso no se cierra. Lo que se va a $0$ es ese atraso **dividido entre $n$**, i.e. la frecuencia menos $\frac{1}{2}$, cuyo tamaño típico es $\frac{1}{2\sqrt{ n }}$.
> ![[falacia-apostador.svg|center|650]]

> [!theorem] **Proposición.**
>
> Sea $S_{n}$ el núm. de águilas en $n$ volados justos e indep., $S_{n} \sim \operatorname{Bin}(n, \frac{1}{2})$. Ent.
> $$
> \operatorname{Var}\left( S_{n} - \frac{n}{2} \right) = \frac{n}{4} \to \infty, \qquad \operatorname{Var}\left( \frac{S_{n}}{n} \right) = \frac{1}{4n} \to 0.
> $$

> [!proof]- **Proof.**
>
> $\operatorname{Var}(S_{n}) = n\cdot\frac{1}{2}\cdot\frac{1}{2}$ ([[Distribucion Binomial]]), recorrer no cambia la varianza, y $\operatorname{Var}(cX) = c^{2}\operatorname{Var}(X)$ con $c = \frac{1}{n}$ ([[Varianza]]). Sacando raíz, las desviaciones estándar son $\frac{\sqrt{ n }}{2}$ y $\frac{1}{2\sqrt{ n }}$. $\blacksquare$

> [!example]- **Ejemplo 1.**
>
> En $10\,000$ volados, la frecuencia de águilas típicamente queda a $\pm\frac{1}{2\sqrt{ 10\,000 }} = \pm 0.005$ de $\frac{1}{2}$, pero el **número** de águilas queda típicamente a $\pm\frac{\sqrt{ 10\,000 }}{2} = \pm 50$ de $5000$, i.e. unas $100$ águilas más (o menos) que soles. Un atraso así es normal, y nada lo obliga a cerrarse.

### Leer la condicional al revés

$P(A \mid B)$ y $P(B \mid A)$ pueden ser muy distintas, y confundirlas es probablemente el error más caro de la probabilidad aplicada (diagnósticos, juicios, filtros de spam). El [[Teorema de Bayes]] es la forma correcta de pasar de una a la otra, y la diferencia la hace la proba. a priori.

> [!example]- **Ejemplo 2.** (Prueba médica)
>
> Una enfermedad la tiene el $1\%$ de la población. Una prueba detecta al $99\%$ de los enfermos, y da falso positivo en el $5\%$ de los sanos. Si sales positivo, ¿qué tan probable es que estés enfermo? Con $E$ = "enfermo" y $+$ = "prueba positiva",
> $$
> P(E \mid +) = \frac{P(+ \mid E)P(E)}{P(+ \mid E)P(E) + P(+ \mid E^{c})P(E^{c})} = \frac{0.99 \cdot 0.01}{0.99 \cdot 0.01 + 0.05 \cdot 0.99} = \frac{1}{6}.
> $$
> La prueba "acierta el $99\%$", pero un positivo solo significa $\frac{1}{6}$ de proba. de estar enfermo: los sanos son tantos que sus falsos positivos ($5\%$ de $99\%$) superan a los verdaderos ($99\%$ de $1\%$).

> [!observation]+ **Observación.**
>
> La **falacia del fiscal** es la misma confusión en un juicio: "si fuera inocente, la proba. de esta evidencia sería $1$ en un millón, ent. la proba. de que sea inocente es $1$ en un millón". Es confundir $P(\text{evidencia} \mid \text{inocente})$ con $P(\text{inocente} \mid \text{evidencia})$; la segunda depende de cuántos inocentes podrían haber producido la misma evidencia.

### Monty Hall: la información de quien escoge

Hay tres puertas y un premio detrás de una. Escoges una; el presentador, que **sabe** dónde está el premio, abre otra puerta sin premio y te ofrece cambiar. La respuesta intuitiva ("quedan dos puertas, da igual") es falsa: cambiar gana con proba. $\frac{2}{3}$.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Quedarte gana solo si acertaste al principio ($\frac{1}{3}$). Si no acertaste ($\frac{2}{3}$), el presentador está obligado a abrir la única otra puerta vacía, y cambiar te lleva justo al premio.
> ![[monty-hall.svg|center|600]]

> [!theorem] **Proposición.**
>
> Si el presentador siempre abre una puerta sin premio distinta de la tuya (al azar si hay dos), ent. quedarse gana con proba. $\frac{1}{3}$ y cambiar con proba. $\frac{2}{3}$, sin importar qué puerta abrió.

> [!proof]- **Proof.**
>
> S.p.g. escogiste $A$ y el presentador abrió $B$. Sean $A, B, C$ también los eventos "el premio está ahí", cada uno con proba. $\frac{1}{3}$, y $B^{*}$ = "el presentador abre $B$". Ent. $P(B^{*} \mid A) = \frac{1}{2}$ (puede abrir $B$ o $C$), $P(B^{*} \mid B) = 0$ y $P(B^{*} \mid C) = 1$ (está obligado). Por Bayes,
> $$
> P(A \mid B^{*}) = \frac{\frac{1}{2}\cdot\frac{1}{3}}{\frac{1}{2}\cdot\frac{1}{3} + 0 + 1\cdot\frac{1}{3}} = \frac{1}{3},
> $$
> y $P(C \mid B^{*}) = 1 - P(A \mid B^{*}) - P(B \mid B^{*}) = 1 - \frac{1}{3} - 0 = \frac{2}{3}$. $\blacksquare$

> [!observation]+ **Observación.**
>
> Lo que hace funcionar el truco es que el presentador **no** abre al azar: su elección depende de dónde está el premio, así que da información. Si abriera una puerta al azar y por suerte no tuviera premio, quedarse y cambiar valdrían $\frac{1}{2}$ cada uno. Es el mismo fenómeno que el **problema de los tres prisioneros**: si el celador le dice a $A$ cuál de los otros dos sale libre (escogiendo al azar cuando el condenado es $A$), la proba. de $A$ sigue siendo $\frac{1}{3}$, y la del otro prisionero sube a $\frac{2}{3}$.

El mismo error aparece cuando se cuentan casos que no son igual de probables:

> [!example]- **Ejemplo 3.** (La caja de Bertrand)
>
> Hay tres cajas: $C_{1}$ con dos monedas de oro, $C_{2}$ con una de oro y una de plata, $C_{3}$ con dos de plata. Se escoge una caja al azar y de ella una moneda al azar, y resulta de oro. ¿Proba. de que la caja sea $C_{1}$?
> "Quedan $C_{1}$ y $C_{2}$, ent. $\frac{1}{2}$" es falso: hay tres monedas de oro igual de probables, y dos de ellas están en $C_{1}$. Con Bayes,
> $$
> P(C_{1} \mid \text{oro}) = \frac{1 \cdot \frac{1}{3}}{1 \cdot \frac{1}{3} + \frac{1}{2}\cdot\frac{1}{3} + 0} = \frac{2}{3}.
> $$
> Es la misma trampa que tomar las sumas de dos dados como equiprobables (Ejemplo 2 de [[Medida de Probabilidad Clasica]]).

### Los cumpleaños: contar pares, no personas

¿Cuántas personas hacen falta para que sea más probable que no que dos cumplan años el mismo día? La intuición dice algo como $180$; la respuesta es $23$.

> [!tip|idea]+ **Idea Intuitiva.**
>
> Con $23$ personas no hay $23$ oportunidades de coincidir, hay $\binom{23}{2} = 253$ pares, y cada uno coincide con proba. $\frac{1}{365}$.
> ![[cumpleanos.svg|center|550]]

> [!theorem] **Proposición.**
>
> Con $n \leq 365$ personas y cumpleaños indep. y uniformes en $365$ días,
> $$
> P(\text{al menos dos coinciden}) = 1 - \frac{365 \cdot 364 \cdots (365 - n + 1)}{365^{n}}.
> $$

> [!proof]- **Proof.**
>
> Es el complemento de "todos distintos". Hay $365^{n}$ listas de cumpleaños igual de probables, y las que no repiten son las ordenaciones sin repetición $365 \cdot 364 \cdots (365-n+1)$ ([[Ordenaciones sin Repeticion]], [[Medida de Probabilidad Clasica]]). $\blacksquare$

> [!example]- **Ejemplo 4.**
>
> Con $n = 23$ la proba. es $\approx 0.507$; con $n = 50$, $\approx 0.970$; con $n = 70$, $\approx 0.9992$. Ojo: la proba. de que alguien cumpla **el mismo día que tú** sí es chica ($1 - (364/365)^{22} \approx 0.06$ con $22$ personas más): esa es la pregunta que la intuición está contestando.

### Cuando la esperanza engaña

La [[Esperanza]] se usa como "precio justo" de un juego. Pero ese uso depende de que la esperanza exista y de que sea representativa, y puede fallar de forma espectacular.

> [!example]- **Ejemplo 5.** (Paradoja de San Petersburgo)
>
> Se lanza una moneda justa hasta que sale sol; si sale en el lanzamiento $n$, ganas $2^{n}$. Como el primer sol sale en el $n$-ésimo con proba. $\frac{1}{2^{n}}$,
> $$
> \operatorname{E}(\text{premio}) = \sum_{n=1}^{\infty} 2^{n}\cdot\frac{1}{2^{n}} = \sum_{n=1}^{\infty} 1 = \infty.
> $$
> Por el criterio de la esperanza, cualquier precio de entrada sería un buen negocio, y sin embargo casi nadie pagaría ni $20$: la mitad de las veces se gana $2$, y la esperanza infinita viene de premios enormes con proba. ínfima.

> [!observation]+ **Observación.**
>
> Basta que la banca tenga un límite para que el resultado sea razonable: si el premio máximo es $2^{20} \approx 10^{6}$ (lo demás se paga igual a $2^{20}$), la esperanza es $\sum_{n=1}^{20} 1 + \sum_{n > 20} 2^{20}\cdot 2^{-n} = 20 + 1 = 21$. La esperanza infinita era un artefacto de suponer una banca infinita.

> [!Info]- **Nota!** (Otras confusiones que ya vimos)
>
> - Ajenos no es lo mismo que independientes: [[Eventos Independientes vs. Ajenos]].
> - $\operatorname{E}(1/X) \neq 1/\operatorname{E}(X)$ y en general $\operatorname{E}(\varphi(X)) \neq \varphi(\operatorname{E}X)$: [[Desigualdad de Jensen]].
> - "Media", "mediana" y "valor más probable" no son lo mismo: [[Moda]].
> - Una prueba que "acierta casi siempre" puede ser casi inútil si el evento es raro: Ejemplo 2.

---
Volver a [[Probabilidad]].

<section data-footnotes class="footnotes"><h2 class="sr-only" id="footnote-label">Notas</h2>
<ol>
<li id="user-content-fn-inline-1">

Luis Rincón, *Introducción a la probabilidad*, cap. 1, Ejs. 71 y 124–126 (pp. 65–87), y cap. 2, §2.6, Ej. 222. <a href="#user-content-fnref-inline-1" data-footnote-backref class="data-footnote-backref internal">↩</a>

</li>
</ol>
</section>
