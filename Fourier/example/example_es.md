# Ejemplo de aplicación del Teorema de Fourier

Cabe aclarar que método aplicado en este ejemplo, es un paso a paso diseñado para ingenieros que este es su primer acercamiento a Fourier y a la matemática detrás de este. 

Este método está diseñado para encontrar las distintas componentes armónicas junto al valor de voltaje directo de una secuencia de bits. 

Se hace uso de las ecuaciones presentadas en [✒️ Teorema de Fourier ✒️](/Fourier/explanation/explanation_es.md)

---

Para este ejemplo, se usará la señal presentada a continuación. 

![Example](/images/Fourier/ejemplo/Ejemplo_Fourier.png)

Esta señal cuenta con un voltaje de `1` lógico de 1 voltio y un voltaje de `0` lógico de 0 voltios. 

El periodo `T` está definido por la cantidad de bits, en este caso 8 bits; lo que significará un periodo de 8 segundos para simplificar los cálculos. En dado caso que el periodo de la señal sea diferente, las ecuaciones deben ser ajustadas acorde. 

---

El primer paso es calcular el valor *dc* de la señal. Para eso se utiliza la siguiente ecuación. 

## Cálculo del valor *dc*

$$
\begin{align}
dc = \frac {1} {T} * \int _ { 0 } ^ { T } g(t) dt \\
dc = \frac {1} {8} * \int _ { 0 } ^ { 8 } g(t) dt
\end{align}
$$

En la primera ecuación ecuacion se presenta la forma de calcular el valor de la componente de voltaje directo. 

En la segunda ecuacion se reemplaza el valor de `T` por *8* que es el periodo de la señal, asumiendo que cada bit tiene una duración de 1 segundo. 

Ahora bien, la integral $\int _ { 0 } ^ { 8 } g(t) dt$ se puede calcular a partir de la definición de una integral. 

> Dada una función `f(x)` de una variable real `x` y un intervalo `[a,b]` de la recta real, **la integral es igual al área de la región del plano `xy` limitada entre la gráfica de `f`, el eje `x`, y las líneas verticales `x=a` y `x=b`**, donde son negativas las áreas por debajo del eje `x`.

Teniendo en cuenta esto, la integral $\int _ { 0 } ^ { 8 } g(t) dt$ se reduce a calcular el área bajo la curva que en este caso es la señal. 

En resumen, el área sería el resaltado a continuación: 

![Example](/images/Fourier/ejemplo/Ejemplo_Fourier_Resaltado.png)

En este ejemplo y con las condiciones propuestas (Periodo = 8 segundos), el área resaltada es `3`. Por ende, la ecuación quedaría:

$$
\begin{align}
dc = \frac {1} {8} * 3 \\
dc = 0.375
\end{align}
$$

---

Ahora, el siguiente paso radica en el cálculo de los coeficientes de Fourier $a_n$ y $b_n$. Esto ya que los coeficientes $C_n$ y $\varphi_n$ dependen de estos dos, como se muestra a continuación. 

## Cálculo del coeficiente $C_n$

$$
\begin{align}
C_n = \sqrt{a_n^2 + b_n^2} 
\end{align}
$$

Siendo:
- *a_n* uno de los coeficientes de Fourier
- *b_n* uno de los coeficientes de Fourier

## Cálculo del coeficiente $\varphi_n$

$$
\begin{align}
\varphi_n = arctan (\frac {b_n} {a_n})
\end{align}
$$

Siendo:
- *a_n* uno de los coeficientes de Fourier
- *b_n* uno de los coeficientes de Fourier

---
Empezando con $a_n$: 

## Cálculo del coeficiente $a_n$

$$
\begin{align}
a_n = \frac{2}{T} \int _ {0} ^ {T} g(t) sin(2 \pi n f t)dt \\
a_n = \frac{2}{8} \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * n t)dt \\
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * n t)dt \\
\end{align}
$$

Siendo:
- *T* el periodo de la señal que se quiere transformar
- *f* indica la frecuencia del armónico fundamental 
- *t* indica el tiempo

En la ecuación `2` del bloque anterior, se reemplazan los valores de `T` y `f`, siendo estos, `8` (Periodo de la señal) y `0.125` ( $\frac{1}{T}$ )correspondientemente. 

A partir de este punto, se puede empezar a calcular el coeficiente $a_n$ para cada armónico (1,2,3,4,5,6,7...). Este ejemplo se realizará con 7 armónicos. 

### Para el armónico 1

$$
\begin{align}
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * 1 * t)dt \\
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * t)dt
\end{align}
$$

Aquí se reemplaza la variable `n` por `1` que es el armónico que se quiere calcular. Con esto, se obtiene la segunda ecuación del bloque anterior donde se puede calcular la integral. 

Teniendo en cuenta que: 

$$
\begin{align}
\int sin(x)dx = - cos(x) + C
\end{align}
$$

Se puede reestructurar la ecuación de $a_n$ como: 

$$
\begin{align}
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * t)dt \\
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * g(t) * cos(2 \pi * 0.125 * t)|^8_0 \\
\end{align}
$$

El siguiente paso requiere el realizar el reemplazo de los límites. En este proceso hay que entender que la función `g(t)` es una función a trozos. Por ende, el cálculo de $a_n$ sería: 

$$
\begin{align}
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * (( 0 * cos(2 \pi * 0.125 * t)|^1_0 ) + \\
( 1 * cos(2 \pi * 0.125 * t)|^2_1 ) + ( 0 * cos(2 \pi * 0.125 * t)|^3_2 ) + \\
( 0 * cos(2 \pi * 0.125 * t)|^4_3 ) + ( 0 * cos(2 \pi * 0.125 * t)|^5_4) + \\
( 1 * cos(2 \pi * 0.125 * t)|^6_5 ) + ( 1 * cos(2 \pi * 0.125 * t)|^7_6 ) + \\
( 0 * cos(2 \pi * 0.125 * t)|^8_7 )) \\
\end{align}
$$

![Example](/images/Fourier/ejemplo/Ejemplo_Fourier.png)

Cada uno de los segmentos de la señal es separado en la solución de la integral y se multiplica cada función coseno por el valor del voltaje de la señal en ese tramo. 

Reduciendo los términos que se vean multiplicados por `0`, la ecuación que determina el coeficiente $a_n$ sería: 

$$
\begin{align}
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * (( 1 * cos(2 \pi * 0.125 * t)|^2_1 ) + \\
( 1 * cos(2 \pi * 0.125 * t)|^6_5 ) + \\
( 1 * cos(2 \pi * 0.125 * t)|^7_6 )) \\
\end{align}
$$

Ahora, el siguiente paso es el cálculo de los límites de cada uno de los cosenos de la siguiente forma (se eliminan los `1` para que la fórmula sea más simple de escribir): 

$$
\begin{align}
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * (( cos(2 \pi * 0.125 * 2) - cos(2 \pi * 0.125 * 1) ) + \\
( cos(2 \pi * 0.125 * 6) - cos(2 \pi * 0.125 * 5) ) + \\
( cos(2 \pi * 0.125 * 7) - cos(2 \pi * 0.125 * 6) )) \\
\end{align}
$$

Resolviendo cada uno de las funciones cosenos: 

$$
\begin{align}
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * (( 0.0000 - 0.7071 ) + \\
( 0.0000 - (-0.7071) ) + \\
( 0.7071 - 0.0000 )) \\
\end{align}
$$

Simplificando: 

$$
\begin{align}
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * (-0.7071 + 0.7071 + 0.7071 ) \\
a_n = - \frac{-1}{\pi} * (-0.7071 + 0.7071 + 0.7071 ) \\
a_n = - \frac{-1}{\pi} * ( 0.7071 ) \\
a_n = - 0.2250 \\
\end{align}
$$

Este sería el coeficiente $a_n$ para el armónico `1`. 

Este proceso tiene que ser repetido para cada uno de los armónicos con los que se quiera trabajar. 

---

Siguiendo con $b_n$: 

## Cálculo del coeficiente $b_n$

$$
\begin{align}
b_n = \frac{2}{T} \int _ {0} ^ {T} g(t) cos(2 \pi n f t)dt \\
b_n = \frac{2}{8} \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * n t)dt \\
b_n = 0.25 * \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * n t)dt \\
\end{align}
$$

Siendo:
- *T* el periodo de la señal que se quiere transformar
- *f* indica la frecuencia del armónico fundamental 
- *t* indica el tiempo

En la ecuación `2` del bloque anterior, se reemplazan los valores de `T` y `f`, siendo estos, `8` (Periodo de la señal) y `0.125` ( $\frac{1}{T}$ )correspondientemente. 

A partir de este punto, se puede empezar a calcular el coeficiente $b_n$ para cada armónico (1,2,3,4,5,6,7...). Este ejemplo se realizará con 7 armónicos. 

### Para el armónico 1

$$
\begin{align}
b_n = 0.25 * \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * 1 * t)dt \\
b_n = 0.25 * \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * t)dt
\end{align}
$$

Aquí se reemplaza la variable `n` por `1` que es el armónico que se quiere calcular. Con esto, se obtiene la segunda ecuación del bloque anterior donde se puede calcular la integral. 

Teniendo en cuenta que: 

$$
\begin{align}
\int cos(x)dx = sin(x) + C
\end{align}
$$

Se puede reestructurar la ecuación de $b_n$ como: 

$$
\begin{align}
b_n = 0.25 * \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * t)dt \\
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * g(t) * sin(2 \pi * 0.125 * t)|^8_0 \\
\end{align}
$$

El siguiente paso requiere el realizar el reemplazo de los límites. En este proceso hay que entender que la función `g(t)` es una función a trozos. Por ende, el cálculo de $a_n$ sería: 

$$
\begin{align}
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * (( 0 * sin(2 \pi * 0.125 * t)|^1_0 ) + \\
( 1 * sin(2 \pi * 0.125 * t)|^2_1 ) + ( 0 * sin(2 \pi * 0.125 * t)|^3_2 ) + \\
( 0 * sin(2 \pi * 0.125 * t)|^4_3 ) + ( 0 * sin(2 \pi * 0.125 * t)|^5_4) + \\
( 1 * sin(2 \pi * 0.125 * t)|^6_5 ) + ( 1 * sin(2 \pi * 0.125 * t)|^7_6 ) + \\
( 0 * sin(2 \pi * 0.125 * t)|^8_7 )) \\
\end{align}
$$

![Example](/images/Fourier/ejemplo/Ejemplo_Fourier.png)

Cada uno de los segmentos de la señal es separado en la solución de la integral y se multiplica cada función coseno por el valor del voltaje de la señal en ese tramo. 

Reduciendo los términos que se vean multiplicados por `0`, la ecuación que determina el coeficiente $a_n$ sería: 

$$
\begin{align}
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * (( 1 * sin(2 \pi * 0.125 * t)|^2_1 ) + \\
( 1 * sin(2 \pi * 0.125 * t)|^6_5 ) + \\
( 1 * sin(2 \pi * 0.125 * t)|^7_6 )) \\
\end{align}
$$

Ahora, el siguiente paso es el cálculo de los límites de cada uno de los cosenos de la siguiente forma (se eliminan los `1` para que la fórmula sea más simple de escribir): 

$$
\begin{align}
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * (( sin(2 \pi * 0.125 * 2) - sin(2 \pi * 0.125 * 1) ) + \\
( sin(2 \pi * 0.125 * 6) - sin(2 \pi * 0.125 * 5) ) + \\
( sin(2 \pi * 0.125 * 7) - sin(2 \pi * 0.125 * 6) )) \\
\end{align}
$$

Resolviendo cada uno de las funciones cosenos: 

$$
\begin{align}
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * (( 1.0000 - 0.7071 ) + \\
( -1.0000 - (-0.7071) ) + \\
( -0.7071 - (-1.0000) )) \\
\end{align}
$$

Simplificando: 

$$
\begin{align}
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * ( 0.2929 - 0.2929 + 0.2929 ) \\
b_n = - \frac{1}{\pi} * ( 0.2929 - 0.2929 + 0.2929 ) \\
b_n = - \frac{1}{\pi} * ( 0.2929 ) \\
b_n = 0.0932 \\
\end{align}
$$

Este sería el coeficiente $b_n$ para el armónico `1`. 

Este proceso tiene que ser repetido para cada uno de los armónicos con los que se quiera trabajar. 

---

Al repetir este proceso con cada uno de los siete armónicos que se deseen utilizar se obtienen los siguientes coeficientes: 

| **Armónicos n** | **$a_n$**     | **$b_n$**      |
|:---------------:|:-------------:|:--------------:|
| **1**           | \-0,225079079 | 0,093230807    |
| **2**           | 0,159154943   | \-0,477464829  |
| **3**           | 0,07502636    | \-0,181129655  |
| **4**           | \-0,159154943 | \-9,74942E\-18 |
| **5**           | 0,045015816   | 0,108677793    |
| **6**           | 0,053051648   | 0,159154943    |
| **7**           | \-0,032154154 | \-0,013318687  |

---

## Cálculo del coeficiente $C_n$

Para calcular el coeficiente $C_n$ a partir de los coeficientes $a_n$ y $b_n$ solo se debe seguir la siguiente fórmula: 

$$
\begin{align}
C_n = \sqrt{a_n^2 + b_n^2} 
\end{align}
$$

Siendo:
- *a_n* uno de los coeficientes de Fourier
- *b_n* uno de los coeficientes de Fourier

Siguiendo la ecuación anterior, la tabla se complementaría con una columna adicional de la siguiente forma: 

| **Armónicos n** | **$a_n$**     | **$b_n$**      | **$C_n$**   |
|:---------------:|:-------------:|:--------------:|:-----------:|
| **1**           | \-0,225079079 | 0,093230807    | 0,24362384  |
| **2**           | 0,159154943   | \-0,477464829  | 0,503292121 |
| **3**           | 0,07502636    | \-0,181129655  | 0,196053326 |
| **4**           | \-0,159154943 | \-9,74942E\-18 | 0,159154943 |
| **5**           | 0,045015816   | 0,108677793    | 0,117631996 |
| **6**           | 0,053051648   | 0,159154943    | 0,16776404  |
| **7**           | \-0,032154154 | \-0,013318687  | 0,034803406 |


--- 

## Cálculo del coeficiente $\varphi_n$

Para calcular el coeficiente $\varphi_n$ a partir de los coeficientes $a_n$ y $b_n$ solo se debe seguir la siguiente fórmula: 

$$
\begin{align}
\varphi_n = arctan (\frac {b_n} {a_n})
\end{align}
$$

Siendo:
- *a_n* uno de los coeficientes de Fourier
- *b_n* uno de los coeficientes de Fourier

Siguiendo la ecuación anterior, la tabla se complementaría con una columna adicional de la siguiente forma: 

| **Armónicos n** | **$a\_n$**    | **$b\_n$**     | **$C\_n$**  | **$\\varphi\_n$** |
|:---------------:|:-------------:|:--------------:|:-----------:|:-----------------:|
| **1**           | \-0,225079079 | 0,093230807    | 0,24362384  | 2,748893572       |
| **2**           | 0,159154943   | \-0,477464829  | 0,503292121 | \-1,249045772     |
| **3**           | 0,07502636    | \-0,181129655  | 0,196053326 | \-1,178097245     |
| **4**           | \-0,159154943 | \-9,74942E\-18 | 0,159154943 | \-3,141592654     |
| **5**           | 0,045015816   | 0,108677793    | 0,117631996 | 1,178097245       |
| **6**           | 0,053051648   | 0,159154943    | 0,16776404  | 1,249045772       |
| **7**           | \-0,032154154 | \-0,013318687  | 0,034803406 | \-2,748893572     |

---

## Cálculo de los armónicos

Ya con los valores de los distintos coeficientes, se puede realizar la construcción de las ecuaciones de cada uno de los armónicos. Para esto se debe tener en cuenta la siguiente ecuación: 

$$
\begin{align}
g(t) = dc + \sum _ { i = 1 } ^ { \infty } C_n * sin(2\pi n f t + \varphi_n)
\end{align}
$$

Siendo: 
- *dc* indica el valor de la componente de voltaje directo
- $C_n$ indica el coeficiente de la función seno
- *n* indica el número del armónico de la componente
- *f* indica la frecuencia del armónico fundamental 
- *t* indica el tiempo
- $\varphi_n$ indica la fase inicial de la señal seno 

De esta ecuación ya contamos con los siguientes valores calculados: 
- *dc* - [ Cálculo del valor dc ](https://github.com/Akamiz96/Networking/blob/main/Fourier/example/example_es.md#c%C3%A1lculo-del-valor-dc)
- $C_n$ - [ Cálculo del coeficiente ](https://github.com/Akamiz96/Networking/blob/main/Fourier/example/example_es.md#c%C3%A1lculo-del-coeficiente-c_n-1)
- n - Depende cuál armónico se está calculando cambiará entre los valores 1, 2, 3, 4, 5, 6, 7, ...
- *f* - Se calculó que, para este ejemplo la frecuencia fundamental es: `0.125 Hz`, la cual se encuentra relacionada con la ecuación:

$$ 
f = \frac {1} {T} 
$$

- $\varphi_n$ - [ Cálculo del coeficiente ](https://github.com/Akamiz96/Networking/blob/main/Fourier/example/example_es.md#c%C3%A1lculo-del-coeficiente-varphi_n)

El único valor que hace falta dentro de la ecuación es el del tiempo ( *t* ). Este simplemente es la serie de tiempo sobre la cual se calculará cada punto de las distintas funciones seno para su graficación. 

En la siguiente tabla se enuncia el valor en diferentes tiempos *t* para cada uno de los 8 armónicos junto con el valor *dc*. 

| **t**   | **g0(t)** | **g1(t)**    | **g2(t)**    | **g3(t)**    | **g4(t)**    | **g5(t)**    | **g6(t)**    | **g7(t)**    |
|:-------:|:---------:|:------------:|:------------:|:------------:|:------------:|:------------:|:------------:|:------------:|
| **0**   | 0,375     | 0,093230807  | -0,477464829 | -0,181129655 | -1,94988E-17 | 0,108677793  | 0,159154943  | -0,013318687 |
| **0,1** | 0,375     | 0,075283907  | -0,446689127 | -0,158610472 | -0,049181582 | 0,117631996  | 0,165893037  | -0,028156547 |
| **0,2** | 0,375     | 0,056872856  | -0,404914455 | -0,12732645  | -0,093548928 | 0,108677793  | 0,136468613  | -0,034696118 |
| **0,3** | 0,375     | 0,038111165  | -0,353169446 | -0,089006347 | -0,128759054 | 0,083178382  | 0,077295812  | -0,031010062 |
| **0,4** | 0,375     | 0,019114506  | -0,292728233 | -0,04576774  | -0,151365346 | 0,045015816  | 0,001273533  | -0,01818473  |
| **0,5** | 0,375     | 2,98475E-17  | -0,225079079 | -8,70652E-17 | -0,159154943 | -1,42306E-16 | -0,07502636  | 1,54558E-16  |
| **0,6** | 0,375     | -0,019114506 | -0,151887731 | 0,04576774   | -0,151365346 | -0,045015816 | -0,134971485 | 0,01818473   |
| **0,7** | 0,375     | -0,038111165 | -0,074956404 | 0,089006347  | -0,128759054 | -0,083178382 | -0,165494588 | 0,031010062  |
| **0,8** | 0,375     | -0,056872856 | 0,003820599  | 0,12732645   | -0,093548928 | -0,108677793 | -0,15994203  | 0,034696118  |
| **0,9** | 0,375     | -0,075283907 | 0,082503526  | 0,158610472  | -0,049181582 | -0,117631996 | -0,119524196 | 0,028156547  |
| **1**   | 0,375     | -0,093230807 | 0,159154943  | 0,181129655  | -7,0679E-17  | -0,108677793 | -0,053051648 | 0,013318687  |
| **1,1** | 0,375     | -0,110602909 | 0,231887437  | 0,193639584  | 0,049181582  | -0,083178382 | 0,024985468  | -0,005444452 |
| **1,2** | 0,375     | -0,127293107 | 0,298910092  | 0,195448959  | 0,093548928  | -0,045015816 | 0,097576078  | -0,022603004 |
| **1,3** | 0,375     | -0,1431985   | 0,358572589  | 0,186457793  | 0,128759054  | 1,80133E-16  | 0,148896376  | -0,033100006 |
| **1,4** | 0,375     | -0,158221027 | 0,409405839  | 0,16716294   | 0,151365346  | 0,045015816  | 0,167759206  | -0,033841785 |
| **1,5** | 0,375     | -0,172268069 | 0,450158158  | 0,138630636  | 0,159154943  | 0,083178382  | 0,150052719  | -0,024609724 |
| **1,6** | 0,375     | -0,185253021 | 0,479826089  | 0,102437581  | 0,151365346  | 0,108677793  | 0,099636697  | -0,008124694 |
| **1,7** | 0,375     | -0,197095826 | 0,49767911   | 0,06058381   | 0,128759054  | 0,117631996  | 0,027501175  | 0,010754844  |
| **1,8** | 0,375     | -0,207723471 | 0,503277619  | 0,015382167  | 0,093548928  | 0,108677793  | -0,050629244 | 0,026464717  |
| **1,9** | 0,375     | -0,217070431 | 0,496483763  | -0,030669497 | 0,049181582  | 0,083178382  | -0,117723149 | 0,034374918  |
| **2**   | 0,375     | -0,225079079 | 0,477464829  | -0,07502636  | -2,63217E-16 | 0,045015816  | -0,159154943 | 0,032154154  |
| **2,1** | 0,375     | -0,23170004  | 0,446689127  | -0,115237254 | -0,049181582 | -3,74678E-16 | -0,165893037 | 0,020456929  |
| **2,2** | 0,375     | -0,236892494 | 0,404914455  | -0,149080119 | -0,093548928 | -0,045015816 | -0,136468613 | 0,002730644  |
| **2,3** | 0,375     | -0,240624426 | 0,353169446  | -0,174684792 | -0,128759054 | -0,083178382 | -0,077295812 | -0,015800416 |
| **2,4** | 0,375     | -0,242872829 | 0,292728233  | -0,190636357 | -0,151365346 | -0,108677793 | -0,001273533 | -0,029674782 |
| **2,5** | 0,375     | -0,24362384  | 0,225079079  | -0,196053326 | -0,159154943 | -0,117631996 | 0,07502636   | -0,034803406 |
| **2,6** | 0,375     | -0,242872829 | 0,151887731  | -0,190636357 | -0,151365346 | -0,108677793 | 0,134971485  | -0,029674782 |
| **2,7** | 0,375     | -0,240624426 | 0,074956404  | -0,174684792 | -0,128759054 | -0,083178382 | 0,165494588  | -0,015800416 |
| **2,8** | 0,375     | -0,236892494 | -0,003820599 | -0,149080119 | -0,093548928 | -0,045015816 | 0,15994203   | 0,002730644  |
| **2,9** | 0,375     | -0,23170004  | -0,082503526 | -0,115237254 | -0,049181582 | 5,69223E-16  | 0,119524196  | 0,020456929  |
| **3**   | 0,375     | -0,225079079 | -0,159154943 | -0,07502636  | 5,26434E-16  | 0,045015816  | 0,053051648  | 0,032154154  |
| **3,1** | 0,375     | -0,217070431 | -0,231887437 | -0,030669497 | 0,049181582  | 0,083178382  | -0,024985468 | 0,034374918  |
| **3,2** | 0,375     | -0,207723471 | -0,298910092 | 0,015382167  | 0,093548928  | 0,108677793  | -0,097576078 | 0,026464717  |
| **3,3** | 0,375     | -0,197095826 | -0,358572589 | 0,06058381   | 0,128759054  | 0,117631996  | -0,148896376 | 0,010754844  |
| **3,4** | 0,375     | -0,185253021 | -0,409405839 | 0,102437581  | 0,151365346  | 0,108677793  | -0,167759206 | -0,008124694 |
| **3,5** | 0,375     | -0,172268069 | -0,450158158 | 0,138630636  | 0,159154943  | 0,083178382  | -0,150052719 | -0,024609724 |
| **3,6** | 0,375     | -0,158221027 | -0,479826089 | 0,16716294   | 0,151365346  | 0,045015816  | -0,099636697 | -0,033841785 |
| **3,7** | 0,375     | -0,1431985   | -0,49767911  | 0,186457793  | 0,128759054  | -9,72724E-16 | -0,027501175 | -0,033100006 |
| **3,8** | 0,375     | -0,127293107 | -0,503277619 | 0,195448959  | 0,093548928  | -0,045015816 | 0,050629244  | -0,022603004 |
| **3,9** | 0,375     | -0,110602909 | -0,496483763 | 0,193639584  | 0,049181582  | -0,083178382 | 0,117723149  | -0,005444452 |
| **4**   | 0,375     | -0,093230807 | -0,477464829 | 0,181129655  | -7,89651E-16 | -0,108677793 | 0,159154943  | 0,013318687  |
| **4,1** | 0,375     | -0,075283907 | -0,446689127 | 0,158610472  | -0,049181582 | -0,117631996 | 0,165893037  | 0,028156547  |
| **4,2** | 0,375     | -0,056872856 | -0,404914455 | 0,12732645   | -0,093548928 | -0,108677793 | 0,136468613  | 0,034696118  |
| **4,3** | 0,375     | -0,038111165 | -0,353169446 | 0,089006347  | -0,128759054 | -0,083178382 | 0,077295812  | 0,031010062  |
| **4,4** | 0,375     | -0,019114506 | -0,292728233 | 0,04576774   | -0,151365346 | -0,045015816 | 0,001273533  | 0,01818473   |
| **4,5** | 0,375     | -5,96951E-17 | -0,225079079 | 7,20583E-17  | -0,159154943 | -8,647E-17   | -0,07502636  | -2,17446E-16 |
| **4,6** | 0,375     | 0,019114506  | -0,151887731 | -0,04576774  | -0,151365346 | 0,045015816  | -0,134971485 | -0,01818473  |
| **4,7** | 0,375     | 0,038111165  | -0,074956404 | -0,089006347 | -0,128759054 | 0,083178382  | -0,165494588 | -0,031010062 |
| **4,8** | 0,375     | 0,056872856  | 0,003820599  | -0,12732645  | -0,093548928 | 0,108677793  | -0,15994203  | -0,034696118 |
| **4,9** | 0,375     | 0,075283907  | 0,082503526  | -0,158610472 | -0,049181582 | 0,117631996  | -0,119524196 | -0,028156547 |
| **5**   | 0,375     | 0,093230807  | 0,159154943  | -0,181129655 | -9,26143E-16 | 0,108677793  | -0,053051648 | -0,013318687 |
| **5,1** | 0,375     | 0,110602909  | 0,231887437  | -0,193639584 | 0,049181582  | 0,083178382  | 0,024985468  | 0,005444452  |
| **5,2** | 0,375     | 0,127293107  | 0,298910092  | -0,195448959 | 0,093548928  | 0,045015816  | 0,097576078  | 0,022603004  |
| **5,3** | 0,375     | 0,1431985    | 0,358572589  | -0,186457793 | 0,128759054  | 1,35462E-15  | 0,148896376  | 0,033100006  |
| **5,4** | 0,375     | 0,158221027  | 0,409405839  | -0,16716294  | 0,151365346  | -0,045015816 | 0,167759206  | 0,033841785  |
| **5,5** | 0,375     | 0,172268069  | 0,450158158  | -0,138630636 | 0,159154943  | -0,083178382 | 0,150052719  | 0,024609724  |
| **5,6** | 0,375     | 0,185253021  | 0,479826089  | -0,102437581 | 0,151365346  | -0,108677793 | 0,099636697  | 0,008124694  |
| **5,7** | 0,375     | 0,197095826  | 0,49767911   | -0,06058381  | 0,128759054  | -0,117631996 | 0,027501175  | -0,010754844 |
| **5,8** | 0,375     | 0,207723471  | 0,503277619  | -0,015382167 | 0,093548928  | -0,108677793 | -0,050629244 | -0,026464717 |
| **5,9** | 0,375     | 0,217070431  | 0,496483763  | 0,030669497  | 0,049181582  | -0,083178382 | -0,117723149 | -0,034374918 |
| **6**   | 0,375     | 0,225079079  | 0,477464829  | 0,07502636   | 2,92465E-15  | -0,045015816 | -0,159154943 | -0,032154154 |
| **6,1** | 0,375     | 0,23170004   | 0,446689127  | 0,115237254  | -0,049181582 | -2,62277E-15 | -0,165893037 | -0,020456929 |
| **6,2** | 0,375     | 0,236892494  | 0,404914455  | 0,149080119  | -0,093548928 | 0,045015816  | -0,136468613 | -0,002730644 |
| **6,3** | 0,375     | 0,240624426  | 0,353169446  | 0,174684792  | -0,128759054 | 0,083178382  | -0,077295812 | 0,015800416  |
| **6,4** | 0,375     | 0,242872829  | 0,292728233  | 0,190636357  | -0,151365346 | 0,108677793  | -0,001273533 | 0,029674782  |
| **6,5** | 0,375     | 0,24362384   | 0,225079079  | 0,196053326  | -0,159154943 | 0,117631996  | 0,07502636   | 0,034803406  |
| **6,6** | 0,375     | 0,242872829  | 0,151887731  | 0,190636357  | -0,151365346 | 0,108677793  | 0,134971485  | 0,029674782  |
| **6,7** | 0,375     | 0,240624426  | 0,074956404  | 0,174684792  | -0,128759054 | 0,083178382  | 0,165494588  | 0,015800416  |
| **6,8** | 0,375     | 0,236892494  | -0,003820599 | 0,149080119  | -0,093548928 | 0,045015816  | 0,15994203   | -0,002730644 |
| **6,9** | 0,375     | 0,23170004   | -0,082503526 | 0,115237254  | -0,049181582 | 3,89092E-15  | 0,119524196  | -0,020456929 |
| **7**   | 0,375     | 0,225079079  | -0,159154943 | 0,07502636   | -4,64045E-15 | -0,045015816 | 0,053051648  | -0,032154154 |
| **7,1** | 0,375     | 0,217070431  | -0,231887437 | 0,030669497  | 0,049181582  | -0,083178382 | -0,024985468 | -0,034374918 |
| **7,2** | 0,375     | 0,207723471  | -0,298910092 | -0,015382167 | 0,093548928  | -0,108677793 | -0,097576078 | -0,026464717 |
| **7,3** | 0,375     | 0,197095826  | -0,358572589 | -0,06058381  | 0,128759054  | -0,117631996 | -0,148896376 | -0,010754844 |
| **7,4** | 0,375     | 0,185253021  | -0,409405839 | -0,102437581 | 0,151365346  | -0,108677793 | -0,167759206 | 0,008124694  |
| **7,5** | 0,375     | 0,172268069  | -0,450158158 | -0,138630636 | 0,159154943  | -0,083178382 | -0,150052719 | 0,024609724  |
| **7,6** | 0,375     | 0,158221027  | -0,479826089 | -0,16716294  | 0,151365346  | -0,045015816 | -0,099636697 | 0,033841785  |
| **7,7** | 0,375     | 0,1431985    | -0,49767911  | -0,186457793 | 0,128759054  | -5,15907E-15 | -0,027501175 | 0,033100006  |
| **7,8** | 0,375     | 0,127293107  | -0,503277619 | -0,195448959 | 0,093548928  | 0,045015816  | 0,050629244  | 0,022603004  |
| **7,9** | 0,375     | 0,110602909  | -0,496483763 | -0,193639584 | 0,049181582  | 0,083178382  | 0,117723149  | 0,005444452  |
| **8**   | 0,375     | 0,093230807  | -0,477464829 | -0,181129655 | 6,35624E-15  | 0,108677793  | 0,159154943  | -0,013318687 |


--- 

Suma de armónicos

---

Generacion se;al completa 

---