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

In the first equation the way to calculate the value of the direct voltage component is presented.

In the second equation the value of `T` is replaced by *8*, which is the period of the signal, assuming that each bit has a duration of 1 second.

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
a_n = \frac{2}{T} \int _ {0} ^ {T} g(t) sin(2 \pi n f t)dt \\
a_n = \frac{2}{8} \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * n t)dt \\
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * n t)dt \\
\end{align}
$$

Being:
- *T* the period of the signal to be transformed
- *f* indicates the frequency of the fundamental harmonic
- *t* indicates time

In the formula `2` of the previous block the values ​​of `T` and `f` are replaced, these being `8` (Signal period) and `0.125` ( $\frac{1}{T}$ )correspondingly.

From this point, you can start calculating the coefficient $a_n$ for each harmonic (1,2,3,4,5,6,7...). This example is done with 7 harmonics.

### For the 1st harmonic

$$
\begin{align}
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * 1 * t)dt \\
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * t)dt
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
a_n = 0.25 * \int _ {0} ^ {8} g(t) sin(2 \pi * 0.125 * t)dt \\
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * g(t) * cos(2 \pi * 0.125 * t)|^8_0 \\
\end{align}
$$

The next step requires performing the boundary replacement. In this process we must understand that the function `g(t)` is a piecewise function. Finally, the calculation of $a_n$ would be:

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

Each of the segments of the signal is separated in the solution of the integral and each cosine function is multiplied by the value of the voltage of the signal in that segment.

Reducing the terms that are multiplied by `0`, the equation that determines the coefficient $a_n$ would be:

$$
\begin{align}
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * (( 1 * cos(2 \pi * 0.125 * t)|^2_1 ) + \\
( 1 * cos(2 \pi * 0.125 * t)|^6_5 ) + \\
( 1 * cos(2 \pi * 0.125 * t)|^7_6 )) \\
\end{align}
$$

Now, the next step is to calculate the limits of each of the cosines as follows (the `1` are removed to make the formula easier to write):

$$
\begin{align}
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * (( cos(2 \pi * 0.125 * 2) - cos(2 \pi * 0.125 * 1) ) + \\
( cos(2 \pi * 0.125 * 6) - cos(2 \pi * 0.125 * 5) ) + \\
( cos(2 \pi * 0.125 * 7) - cos(2 \pi * 0.125 * 6) )) \\
\end{align}
$$

Solving each of the cosine functions:

$$
\begin{align}
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * (( 0.0000 - 0.7071 ) + \\
( 0.0000 - (-0.7071) ) + \\
( 0.7071 - 0.0000 )) \\
\end{align}
$$

Simplifying:

$$
\begin{align}
a_n = 0.25 * \frac{-1}{2 \pi * 0.125} * (-0.7071 + 0.7071 + 0.7071 ) \\
a_n = - \frac{-1}{\pi} * (-0.7071 + 0.7071 + 0.7071 ) \\
a_n = - \frac{-1}{\pi} * ( 0.7071 ) \\
a_n = - 0.2250 \\
\end{align}
$$

This would be the coefficient $a_n$ for the `1` harmonic.

This process has to be repeated for each of the harmonics with which you want to work.

---

Continuing with $b_n$:

## Cálculo del coeficiente $b_n$

$$
\begin{align}
b_n = \frac{2}{T} \int _ {0} ^ {T} g(t) cos(2 \pi n f t)dt \\
b_n = \frac{2}{8} \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * n t)dt \\
b_n = 0.25 * \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * n t)dt \\
\end{align}
$$

Being:
- *T* the period of the signal to be transformed
- *f* indicates the frequency of the fundamental harmonic
- *t* indicates time

In the equation `2` of the previous block, the values ​​of `T` and `f` are replaced, these being `8` (Signal period) and `0.125` ( $\frac{1}{T}$ )correspondingly.

From this point, you can start calculating the coefficient $b_n$ for each harmonic (1,2,3,4,5,6,7...). This example will be done with 7 harmonics.

### For the 1st harmonic

$$
\begin{align}
b_n = 0.25 * \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * 1 * t)dt \\
b_n = 0.25 * \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * t)dt
\end{align}
$$

Here the variable `n` is replaced by `1`, which is the harmonic to be calculated. With this, the second equation of the previous block is obtained where the integral can be calculated.

Taking into account that:

$$
\begin{align}
\int cos(x)dx = sin(x) + C
\end{align}
$$

The equation of $b_n$ can be restructured as:

$$
\begin{align}
b_n = 0.25 * \int _ {0} ^ {8} g(t) cos(2 \pi * 0.125 * t)dt \\
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * g(t) * sin(2 \pi * 0.125 * t)|^8_0 \\
\end{align}
$$

The next step requires performing the boundary replacement. In this process we must understand that the function `g(t)` is a piecewise function. Therefore, the calculation of $a_n$ would be:

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

Each of the segments of the signal is separated in the solution of the integral and each cosine function is multiplied by the value of the voltage of the signal in that segment.

Reducing the terms that are multiplied by `0`, the equation that determines the coefficient $a_n$ would be:

$$
\begin{align}
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * (( 1 * sin(2 \pi * 0.125 * t)|^2_1 ) + \\
( 1 * sin(2 \pi * 0.125 * t)|^6_5 ) + \\
( 1 * sin(2 \pi * 0.125 * t)|^7_6 )) \\
\end{align}
$$

Now, the next step is to calculate the limits of each of the cosines as follows (the `1` are removed to make the formula easier to write):

$$
\begin{align}
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * (( sin(2 \pi * 0.125 * 2) - sin(2 \pi * 0.125 * 1) ) + \\
( sin(2 \pi * 0.125 * 6) - sin(2 \pi * 0.125 * 5) ) + \\
( sin(2 \pi * 0.125 * 7) - sin(2 \pi * 0.125 * 6) )) \\
\end{align}
$$

Solving each of the cosine functions:

$$
\begin{align}
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * (( 1.0000 - 0.7071 ) + \\
( -1.0000 - (-0.7071) ) + \\
( -0.7071 - (-1.0000) )) \\
\end{align}
$$

Simplifying:

$$
\begin{align}
b_n = 0.25 * \frac{1}{2 \pi * 0.125} * ( 0.2929 - 0.2929 + 0.2929 ) \\
b_n = - \frac{1}{\pi} * ( 0.2929 - 0.2929 + 0.2929 ) \\
b_n = - \frac{1}{\pi} * ( 0.2929 ) \\
b_n = 0.0932 \\
\end{align}
$$

This would be the coefficient $b_n$ for the `1` harmonic.

This process has to be repeated for each of the harmonics with which you want to work.

---

By repeating this process with each of the seven harmonics to be used, the following coefficients are obtained:

| **Harmonics n** | **$a_n$**     | **$b_n$**      |
|:---------------:|:-------------:|:--------------:|
| **1**           | \-0,225079079 | 0,093230807    |
| **2**           | 0,159154943   | \-0,477464829  |
| **3**           | 0,07502636    | \-0,181129655  |
| **4**           | \-0,159154943 | \-9,74942E\-18 |
| **5**           | 0,045015816   | 0,108677793    |
| **6**           | 0,053051648   | 0,159154943    |
| **7**           | \-0,032154154 | \-0,013318687  |

---

## Calculation of the coefficient $C_n$

To calculate the coefficient $C_n$ from the coefficients $a_n$ and $b_n$, just follow the following formula:

$$
\begin{align}
C_n = \sqrt{a_n^2 + b_n^2} 
\end{align}
$$

Being:
- *a_n* one of the Fourier coefficients
- *b_n* one of the Fourier coefficients

Following the previous equation, the table would be complemented with an additional column as follows:

| **Harmonics n** | **$a_n$**     | **$b_n$**      | **$C_n$**   |
|:---------------:|:-------------:|:--------------:|:-----------:|
| **1**           | \-0,225079079 | 0,093230807    | 0,24362384  |
| **2**           | 0,159154943   | \-0,477464829  | 0,503292121 |
| **3**           | 0,07502636    | \-0,181129655  | 0,196053326 |
| **4**           | \-0,159154943 | \-9,74942E\-18 | 0,159154943 |
| **5**           | 0,045015816   | 0,108677793    | 0,117631996 |
| **6**           | 0,053051648   | 0,159154943    | 0,16776404  |
| **7**           | \-0,032154154 | \-0,013318687  | 0,034803406 |

---

## Calculation of the coefficient $\varphi_n$

To calculate the coefficient $C_n$ from the coefficients $a_n$ and $b_n$, just follow the following formula:

$$
\begin{align}
\varphi_n = arctan (\frac {b_n} {a_n})
\end{align}
$$

Being:
- *a_n* one of the Fourier coefficients
- *b_n* one of the Fourier coefficients

Following the previous equation, the table would be complemented with an additional column as follows:

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
