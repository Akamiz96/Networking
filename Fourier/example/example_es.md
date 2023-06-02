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

Explicacion de On

---

Calculo de los armónicos

--- 

Suma de armónicos

---

Generacion se;al completa 

---