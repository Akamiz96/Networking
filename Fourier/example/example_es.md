# Ejemplo de aplicación del Teorema de Fourier

Cabe aclarar que método aplicado en este ejemplo, es un paso a paso diseñado para ingenieros que este es su primer acercamiento a Fourier y a la matemática detrás de este. 

Este método está diseñado para encontrar las distintas componentes armónicas junto al valor de voltaje directo de una secuencia de bits. 

Se hace uso de las ecuaciones presentadas en [✒️ Teorema de Fourier ✒️](Fourier/explanation/explanation_es.md)

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
\begin{align}
dc = \frac {1} {8} * 3 \\
dc = 0.375
\end{align}
$$

---

Ahora, el siguiente paso radica en el cálculo de los coeficientes de Fourier $a_n$ y $b_n$. Esto ya que los coeficientes $C_n$ y $\varphi_n$ dependen de estos dos, como se muestra a continuación. 

## Cálculo del coeficiente *$C_n$*

$$
\begin{align}
C_n = \sqrt{a_n^2 + b_n^2} 
\end{align}
$$

Siendo:
- *a_n* uno de los coeficientes de Fourier
- *b_n* uno de los coeficientes de Fourier

## Cálculo del coeficiente *$\varphi_n$*

$$
\begin{align}
\varphi_n = arctan (\frac {b_n} {a_n})
\end{align}
$$

Siendo:
- *a_n* uno de los coeficientes de Fourier
- *b_n* uno de los coeficientes de Fourier