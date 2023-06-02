# Example of application of Fourier's Theorem

It should be clarified that the method applied in this example is a step by step designed for engineers as this is their first approach to Fourier and the mathematics behind it.

This method is designed to find the various harmonic components next to the forward voltage value of a sequence of bits.

Use is made of the equations presented in [✒️ Fourier's Theorem ✒️](/Fourier/explanation/explanation_en.md)

---

For this example, the signal presented below will be used.

![Example](/images/Fourier/example/Ejemplo_Fourier.png)

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

![Example](/images/Fourier/example/Ejemplo_Fourier_Resaltado.png)

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

![Example](/images/Fourier/example/Ejemplo_Fourier.png)

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

![Example](/images/Fourier/example/Ejemplo_Fourier.png)

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

## Calculation of harmonics

Now with the values ​​of the different coefficients, the construction of the equations of each one of the harmonics can be carried out. For this, the following equation must be taken into account:

$$
\begin{align}
g(t) = dc + \sum _ { i = 1 } ^ { \infty } C_n * sin(2\pi n f t + \varphi_n)
\end{align}
$$

Being:
- *dc* indicates the value of the forward voltage component
- *n* indicates the number of the harmonic of the component
- *f* indicates the frequency of the fundamental harmonic
- *t* indicates time
- $\varphi_n$ indicates the initial phase of the sine signal

From this equation we already have the following calculated values:
- *dc* - [Calculation of dc value](https://github.com/Akamiz96/Networking/blob/main/Fourier/example/example_en.md#calculation-of-dc-value)
- $C_n$ - [Calculation of the coefficient](https://github.com/Akamiz96/Networking/blob/main/Fourier/example/example_en.md#calculation-of-the-coefficient-c_n)
- n - Depends on which harmonic is being calculated it will change between the values ​​1, 2, 3, 4, 5, 6, 7, ...
- *f* - It was calculated that, for this example, the fundamental frequency is: `0.125 Hz`, which is related to the equation:

$$ 
f = \frac {1} {T} 
$$

- $\varphi_n$ - [Calculation of the coefficient](https://github.com/Akamiz96/Networking/blob/main/Fourier/example/example_en.md#calculation-of-the-coefficient-varphi_n)

The only value that is missing within the equation is that of time ( *t* ). This is simply the time series on which each point of the different sine functions will be calculated for its graphing.

The following table lists the value at different times *t* for each of the 8 harmonics together with the value *dc*.

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

## Display of harmonics

With this table already completed, each of the harmonic components of the signal can be visualized.

Each one is shown below starting with the value *dc*.

![Example](/images/Fourier/example/signal/DC.png)

![Example](/images/Fourier/example/signal/g1(t).png)

![Example](/images/Fourier/example/signal/g2(t).png)

![Example](/images/Fourier/example/signal/g3(t).png)

![Example](/images/Fourier/example/signal/g4(t).png)

![Example](/images/Fourier/example/signal/g5(t).png)

![Example](/images/Fourier/example/signal/g6(t).png)

![Example](/images/Fourier/example/signal/g7(t).png)

---

## Sum of harmonics

However, to generate the desired signal, each of the harmonics must be added (including the *dc* value).

The following images show the different sums; starting only with the value *dc* and continuing with the sum of one in one of the different harmonics.

![Example](/images/Fourier/example/signal/DC.png)

![Example](/images/Fourier/example/signal/DC%2Bg1(t).png)

![Example](/images/Fourier/example/signal/DC%2Bg1(t)%2Bg2(t).png)

![Example](/images/Fourier/example/signal/DC%2Bg1(t)%2Bg2(t)%2Bg3(t).png)

![Example](/images/Fourier/example/signal/DC%2Bg1(t)%2Bg2(t)%2Bg3(t)%2Bg4(t).png)

![Example](/images/Fourier/example/signal/DC%2Bg1(t)%2Bg2(t)%2Bg3(t)%2Bg4(t)%2Bg5(t).png)

![Example](/images/Fourier/example/signal/DC%2Bg1(t)%2Bg2(t)%2Bg3(t)%2Bg4(t)%2Bg5(t)%2Bg6(t).png)

![Example](/images/Fourier/example/signal/DC+g1(t)+g2(t)+g3(t)+g4(t)+g5(t)+g6(t)+g7(t).png)

---