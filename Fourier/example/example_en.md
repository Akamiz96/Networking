# Example of application of Fourier's Theorem

It should be clarified that the method applied in this example is a step by step designed for engineers as this is their first approach to Fourier and the mathematics behind it.

This method is designed to find the various harmonic components next to the forward voltage value of a sequence of bits.

Use is made of the equations presented in [✒️ Fourier's Theorem ✒️](/Fourier/explanation/explanation_en.md)

---

For this example, the signal presented below will be used.

![Example](/images/Fourier/ejemplo/Ejemplo_Fourier.png)

This signal has a logic `1` voltage of 1 volt and a logic `0` voltage of 0 volts.

The period `T` is defined by the number of bits, in this case 8 bits; which will mean a period of 8 seconds to simplify the calculations. In case the period of the signal is different, the equations must be adjusted accordingly.

---

The first step is to calculate the *dc* value of the signal. For that, the following equation is used.

## Calculation of *dc* value

$$
\begin{align}
dc = \frac {1} {T} * \int _ { 0 } ^ { T } g(t) dt \\
dc = \frac {1} {8} * \int _ { 0 } ^ { 8 } g(t) dt
\end{align}
$$

In equation `(1)` the way to calculate the value of the direct voltage component is presented.

In equation `(2)` the value of `T` is replaced by *8*, which is the period of the signal, assuming that each bit has a duration of 1 second.

Now, the integral $\int _ { 0 } ^ { 8 } g(t) dt$ can be calculated from the definition of an integral.

> Given a function `f(x)` of a real variable `x` and an interval `[a,b]` of the real line, **the integral is equal to the area of ​​the region of the `xy` plane bounded between the graph of `f`, the `x` axis, and the vertical lines `x=a` and `x=b`**, where the areas below the `x` axis are negative.

Taking this into account, the integral $\int _ { 0 } ^ { 8 } g(t) dt$ reduces to computing the area under the curve, which in this case is the signal.

In short, the area would be highlighted below:

![Example](/images/Fourier/ejemplo/Ejemplo_Fourier_Resaltado.png)

In this example and with the proposed conditions (Period = 8 seconds), the highlighted area is `3`. Therefore, the equation would be:

$$
\begin{align}
dc = \frac {1} {8} * 3 \\
dc = 0.375
\end{align}
$$

---

Now, the next step is to calculate the Fourier coefficients $a_n$ and $b_n$. This is because the coefficients $C_n$ and $\varphi_n$ depend on these two, as shown below.

## Calculation of the coefficient $C_n$

$$
\begin{align}
C_n = \sqrt{a_n^2 + b_n^2} 
\end{align}
$$

Being:
- *a_n* one of the Fourier coefficients
- *b_n* one of the Fourier coefficients

## Calculation of the coefficient $\varphi_n$

$$
\begin{align}
\varphi_n = arctan (\frac {b_n} {a_n})
\end{align}
$$

Being:
- *a_n* one of the Fourier coefficients
- *b_n* one of the Fourier coefficients

---
Starting with $a_n$:

## Calculation of the coefficient $a_n$

$$
\begin{align}
a_n = \frac{2}{T} \int _ {0} ^{T} g(t) sin(2 \pi n f t)dt \\
a_n = \frac{2}{8} \int _ {0} ^{8} g(t) sin(2 \pi * 0.125 * n t)dt \\
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(0.25 \pi n t)dt \\
\end{align}
$$

Being:
- *T* the period of the signal to be transformed
- *f* indicates the frequency of the fundamental harmonic
- *t* indicates time

In the formula `8` the values ​​of `T` and `f` are replaced, these being `8` (Signal period) and `0.125` ( $\frac{1}{T}$ )correspondingly.

From this point, you can start calculating the coefficient $a_n$ for each harmonic (1,2,3,4,5,6,7...). This example is done with 7 harmonics.

### For the 1st harmonic

$$
\begin{align}
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(0.25 \pi * 1 * t)dt \\
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(0.25 \pi t)dt
\end{align}
$$

Here the variable `n` is replaced by `1`, which is the harmonic to be calculated. With this, the equation `11` is obtained where the integral can be calculated.

Taking into account that:

$$
\begin{align}
\int sin(x)dx = - cos(x) + C
\end{align}
$$

Formula `11` can be restructured as: 

$$
\begin{align}
a_n = - \frac{0.25}{0.25 * \pi} * cos(0.25 \pi  t)|^8_0 \\
a_n = - \frac{1}{\pi} * cos(0.25 \pi  t)|^8_0
\end{align}
$$
