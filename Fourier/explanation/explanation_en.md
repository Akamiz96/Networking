![Welcome](/images/Fourier/Banner_Ondas.jpg)

# ✒️ Fourier's theorem ✒️ 

The French physicist and mathematician [Jean–Baptiste Joseph Fourier](https://es.wikipedia.org/wiki/Joseph_Fourier) (1768−1830) formulated a theorem in 1807 stating that:

> Any **periodic signal** *g(t)* defined in time, can be decomposed into a component of **Forward Voltage** *(dc)* and an **infinite number of sine and cosine signals** *(harmonics)*.

That is, a periodic signal can be built with an **infinite sum of sine and cosine signals**.

![Ejemplo](/images/Fourier/Ejemplo_Fourier.gif)
Image taken from: [eMe - apuntes de acústica](https://www.eumus.edu.uy/eme/ensenanza/acustica/presentaciones/fisica/frecuencia/fourier1.html)

## ➗ Theoretical bases ➗

A sinusoidal signal is represented mathematically by:

$$
\begin{align}
f_1(t) = a * sin(2\pi f t + \varphi)
\end{align}
$$

where:
- *a* indicates the amplitude of the sine signal
- *f* indicates the frequency of the sine signal
- *t* indicates time
- $\varphi$ indicates the initial phase of the sine signal

Example of a sine signal is below $y = sin(x)$:

![Sine Wave](/images/Fourier/sine.png)

---
A cosine signal is represented mathematically by:

$$
\begin{align}
f_1(t) = a * sin(2\pi f t + \varphi)
\end{align}
$$

where:
- *a* indicates the amplitude of the cosine signal
- *f* indicates the frequency of the cosine signal
- *t* indicates time
- $\varphi$ indicates the initial phase of the cosine signal

Example of a cosine signal is below $y = sin(x)$:

![Cosine Wave](/images/Fourier/cosine.png)

---
The relationship between the sine signal and the cosine signal lies in:

$$
\begin{align}
sin(\theta)=cos(90^∘−\theta)
\end{align}
$$

For this reason, Fourier's Theorem can be rewritten as:

> Any **periodic signal** *g(t)* defined in time, can be decomposed into a component of **Forward Voltage** *(dc)* and an **infinite number of sine signals** *( harmonics)*.

---

### ➕ Fourier's Theorem Definition ➕

The theorem says that any curve can be reproduced by superposing properly chosen simple harmonics.
Consequently, any sound, no matter how complex it may be – from the voice of a singer to a bus changing gears-,
it can be analyzed by decomposing it into its pure tones and can be reproduced exactly with a pure sound source (for example, a tuning fork).

$$
\begin{align}
g(t) = dc + \sum _ { i = 1 } ^ { \infty } sin(2\pi n f t + \varphi_n)
\end{align}
$$

Being:
- *dc* indicates the value of the forward voltage component
- *n* indicates the number of the harmonic of the component
- *f* indicates the frequency of the fundamental harmonic
- *t* indicates time
- $\varphi_n$ indicates the initial phase of the sine signal

To calculate the variable values ​​of this equation, the following operations must be carried out.

#### Calculation of the *dc* value

$$
\begin{align}
dc = \frac {1} {T} * \int _ { 0 } ^ { T } g(t) dt
\end{align}
$$

Being:
- *T* the period of the signal to be transformed
- *g(t)* the periodic function to be transformed

#### Calculation of the coefficient $C_n$

$$
\begin{align}
C_n = \sqrt{a_n^2 + b_n^2} 
\end{align}
$$

Being:
- *a_n* one of the Fourier coefficients
- *b_n* one of the Fourier coefficients

#### Calculation of the coefficient $\varphi_n$

$$
\begin{align}
\varphi_n = arctan (\frac {b_n} {a_n})
\end{align}
$$

Being:
- *a_n* one of the Fourier coefficients
- *b_n* one of the Fourier coefficients

##### Calculation of the coefficient $a_n$

$$
\begin{align}
a_n = \frac{2}{T} \int _ {0} ^ {T} g(t) sin(2 \pi n f t)dt
\end{align}
$$

Being:
- *T* the period of the signal to be transformed
- *f* indicates the frequency of the fundamental harmonic
- *t* indicates time

##### Calculation of the coefficient $b_n$

$$
\begin{align}
b_n = \frac{2}{T} \int _ {0} ^ {T} g(t) cos(2 \pi n f t)dt
\end{align}
$$

Being:
- *T* the period of the signal to be transformed
- *f* indicates the frequency of the fundamental harmonic
- *t* indicates time