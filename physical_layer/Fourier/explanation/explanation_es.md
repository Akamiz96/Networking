![Welcome](/images/physical_layer/Fourier/banner_waves.jpg)

# ✒️ Teorema de Fourier ✒️

El físico y matemático francés [Jean–Baptiste Joseph Fourier](https://es.wikipedia.org/wiki/Joseph_Fourier) (1768−1830) formuló en 1807 un teorema que afirma que: 

> Cualquier **señal periódica** *g(t)* definida en el tiempo, puede ser descompuesta en una componente de **Voltaje Directo** *(dc)*  y un **número infinito de señales seno y coseno** *(armónicos)*.

Es decir, una señal periódica se puede construir con una **suma infinita de señales seno y coseno**.

![Ejemplo](/images/physical_layer/Fourier/example_Fourier.gif)
Imagen tomada de: [eMe - apuntes de acústica](https://www.eumus.edu.uy/eme/ensenanza/acustica/presentaciones/fisica/frecuencia/fourier1.html)

## ➗ Bases teóricas ➗

Una señal sinusoidal está representada matemáticamente por:

$$
\begin{align}
f_1(t) = a * sin(2\pi f t + \varphi)
\end{align}
$$

donde: 
- *a* indica la amplitud de la señal seno
- *f* indica la frecuencia de la señal seno
- *t* indica el tiempo
- $\varphi$ indica la fase inicial de la señal seno 

Ejemplo de una señal seno se encuentra a continuación $y = sin(x)$: 

![Sine Wave](/images/physical_layer/Fourier/sine.png)

---
Una señal cosenoidal está representada matemáticamente por:

$$
\begin{align}
f_1(t) = a * cos(2\pi f t + \varphi)
\end{align}
$$

donde: 
- *a* indica la amplitud de la señal coseno
- *f* indica la frecuencia de la señal coseno
- *t* indica el tiempo
- $\varphi$ indica la fase inicial de la señal coseno 

Ejemplo de una señal coseno se encuentra a continuación $y = sin(x)$: 

![Cosine Wave](/images/physical_layer/Fourier/cosine.png)

---
La relación entre la señal seno y la señal coseno radica en: 

$$
\begin{align}
sin(\theta)=cos(90^∘−\theta)
\end{align}
$$

Por esta razón el Teorema de Fourier se puede reescribir como:

> Cualquier **señal periódica** *g(t)* definida en el tiempo, puede ser descompuesta en una componente de **Voltaje Directo** *(dc)*  y un **número infinito de señales seno** *(armónicos)*.

---

### ➕ Definición Teorema de Fourier ➕

El teorema dice que cualquier curva se puede reproducir mediante la superposición de armónicos simples escogidos adecuadamente. 
En consecuencia, cualquier sonido, por complejo que sea – desde la voz de un cantante hasta un bus cambiando de marcha-, 
se puede analizar descomponiéndolo en sus tonos puros y se puede reproducir exactamente con una fuente de sonidos puros (por ejemplo, un diapasón).

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

Para calcular los valores variables de esta ecuación hay que realizar las siguientes operaciones. 

#### Cálculo del valor *dc*

$$
\begin{align}
dc = \frac {1} {T} * \int _ { 0 } ^ { T } g(t) dt
\end{align}
$$

Siendo:
- *T* el periodo de la señal que se quiere transformar
- *g(t)* la función periódica que se quiere transformar

#### Cálculo del coeficiente $C_n$

$$
\begin{align}
C_n = \sqrt{a_n^2 + b_n^2} 
\end{align}
$$

Siendo:
- *a_n* uno de los coeficientes de Fourier
- *b_n* uno de los coeficientes de Fourier

#### Cálculo del coeficiente $\varphi_n$

$$
\begin{align}
\varphi_n = arctan (\frac {b_n} {a_n})
\end{align}
$$

Siendo:
- *a_n* uno de los coeficientes de Fourier
- *b_n* uno de los coeficientes de Fourier

##### Cálculo del coeficiente $a_n$

$$
\begin{align}
a_n = \frac{2}{T} \int _ {0} ^ {T} g(t) sin(2 \pi n f t)dt
\end{align}
$$

Siendo:
- *T* el periodo de la señal que se quiere transformar
- *f* indica la frecuencia del armónico fundamental 
- *t* indica el tiempo

##### Cálculo del coeficiente $b_n$

$$
\begin{align}
b_n = \frac{2}{T} \int _ {0} ^ {T} g(t) cos(2 \pi n f t)dt
\end{align}
$$

Siendo:
- *T* el periodo de la señal que se quiere transformar
- *f* indica la frecuencia del armónico fundamental 
- *t* indica el tiempo