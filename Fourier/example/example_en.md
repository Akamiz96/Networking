# Example of application of Fourier's Theorem

It should be clarified that the method applied in this example is a step by step designed for engineers as this is their first approach to Fourier and the mathematics behind it.

This method is designed to find the various harmonic components next to the forward voltage value of a sequence of bits.

Use is made of the equations presented in [✒️ Fourier's Theorem ✒️](Fourier/explanation/explanation_en.md)

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
