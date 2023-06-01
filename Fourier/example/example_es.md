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

En la ecuacion `(1)` se presenta la forma de calcular el valor de la componente de voltaje directo. 

En la ecuacion `(2)` se reemplaza el valor de `T` por *8* que es el periodo de la señal, asumiendo que cada bit tiene una duración de 1 segundo. 

Ahora bien, la integral $\int _ { 0 } ^ { 8 } g(t) dt$ se puede calcular a partir de la definición de una integral. 

> Dada una función `f(x)` de una variable real `x` y un intervalo `[a,b]` de la recta real, **la integral es igual al área de la región del plano `xy` limitada entre la gráfica de `f`, el eje `x`, y las líneas verticales `x=a` y `x=b`**, donde son negativas las áreas por debajo del eje `x`.

Teniendo en cuenta esto, la integral $\int _ { 0 } ^ { 8 } g(t) dt$ se reduce a calcular el área bajo la curva que en este caso es la señal. 

En resumen, el área sería el resaltado a continuación: 

![Example](/images/Fourier/ejemplo/Ejemplo_Fourier_Resaltado.png)

En este ejemplo y con las condiciones propuestas (Periodo = 8 segundos), el área resaltada es `3`. Por ende, la ecuación quedaría:

$$
\begin{equation}
dc = \frac {1} {8} * 3 \\
dc = 0.375
\end{equation}
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
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(0.25 \pi n t)dt \\
\end{align}
$$

Siendo:
- *T* el periodo de la señal que se quiere transformar
- *f* indica la frecuencia del armónico fundamental 
- *t* indica el tiempo

En la ecuación `8` se reemplazan los valores de `T` y `f`, siendo estos, `8` (Periodo de la señal) y `0.125` ( $\frac{1}{T}$ )correspondientemente. 

A partir de este punto, se puede empezar a calcular el coeficiente $a_n$ para cada armónico (1,2,3,4,5,6,7...). Este ejemplo se realizará con 7 armónicos. 

### Para el armónico 1

$$
\begin{align}
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(0.25 \pi * 1 * t)dt \\
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(0.25 \pi  t)dt
\end{align}
$$

Aquí se reemplaza la variable `n` por `1` que es el armónico que se quiere calcular. Con esto, se obtiene la ecuación `11` donde se puede calcular la integral. 

Teniendo en cuenta que: 

$$
\begin{align}
\int sin(x)dx = - cos(x) + C
\end{align}
$$

Se puede reestructurar la ecuación `11` como: 

$$
\begin{align}
a_n = - \frac{0.25}{0.25 * \pi} * g(t) * cos(0.25 \pi  t)|^8_0 \\
a_n = - \frac{1}{\pi} * g(t) * cos(0.25 \pi  t)|^8_0 \\
\end{align}
$$

El siguiente paso requiere el realizar el reemplazo de los límites. En este proceso hay que entender que la función `g(t)` es una función a trozos. Por ende, el cálculo de $a_n$ sería: 

$$
\begin{equation}
a_n = - \frac{1}{\pi} * ( 0 * cos(0.25 \pi  t)|^1_0 ) + ( 1 * cos(0.25 \pi  t)|^2_1 ) 
+ ( 0 * cos(0.25 \pi  t)|^3_2 ) + ( 0 * cos(0.25 \pi  t)|^4_3 ) + \\
( 0 * cos(0.25 \pi  t)|^5_4) + ( 1 * cos(0.25 \pi  t)|^6_5 ) + \\
( 1 * cos(0.25 \pi  t)|^7_6 ) + ( 0 * cos(0.25 \pi  t)|^8_7 )\\
\end{equation}
$$