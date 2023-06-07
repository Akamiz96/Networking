![Welcome](/images/physical_layer/channel_capacity/math_banner_solution.jpg)

# Solución 
---

> Supóngase que el espectro de un canal está situado entre 3Mhz y 4 MHz y que la SNR es de 24 dB. ¿Cuál sería la capacidad del canal?

## Tasa de Shannon

$$
C_{bps} = H * Log_2(1 + \frac{S}{N})
$$

Siendo:
- C_{bps} la capacidad máxima del canal en bits por segundo.
- *H* ancho de banda del canal de comunicación en Hertz *Hz*. 
- $\frac{S}{N}$ Relación señal ruido.
  - *S* potencia de la señal útil, que puede estar expresada en vatios *W*
  - *N* potencia del ruido presente en el canal que trata de enmascarar a la señal útil.

Como la relacion señal ruido está expresada en *db* se debe aplicar primero: 

$$
\begin{aligned} 
(\frac{S}{N})_{db} = 10 * log(\frac{S}{N}) \\
24 = 10 * log(\frac{S}{N}) \\
\frac{24}{10} = log(\frac{S}{N}) \\
2.4 = log(\frac{S}{N}) \\
10^{2.4} = \frac{S}{N}
\end{aligned}
$$

Con esto ya calculado, se puede calcular la capacidad del canal: 

$$
\begin{aligned}
C_{bps} = H * Log_2(1 + \frac{S}{N}) \\
C_{bps} = (3 * 10^6 - 4 * 10^6) * Log_2(1 + 10^{2.4}) \\
C_{bps} = (1 * 10^6) * Log_2(1 + 10^{2.4}) \\ 
C_{bps} = (1 * 10^6) * 7.98 \\ 
C_{bps} = 7.98 Mbps
\end{aligned}
$$

---

> Un canal telefónico tiene un ancho de banda de 3 kHz y una relación señal/ruido de 30 dB. ¿Cuál es la capacidad máxima de datos que un módem puede producir para este canal alámbrico y esperar que los errores no se vuelvan irreparables?.

## Tasa de Shannon

$$
C_{bps} = H * Log_2(1 + \frac{S}{N})
$$

Siendo:
- C_{bps} la capacidad máxima del canal en bits por segundo.
- *H* ancho de banda del canal de comunicación en Hertz *Hz*. 
- $\frac{S}{N}$ Relación señal ruido.
  - *S* potencia de la señal útil, que puede estar expresada en vatios *W*
  - *N* potencia del ruido presente en el canal que trata de enmascarar a la señal útil.

Como la relacion señal ruido está expresada en *db* se debe aplicar primero la ecuación siguiente: 

$$
\begin{aligned} 
(\frac{S}{N})_{db} = 10 * log(\frac{S}{N}) \\
30 = 10 * log(\frac{S}{N}) \\
\frac{30}{10} = log(\frac{S}{N}) \\
3 = log(\frac{S}{N}) \\
10^{3} = \frac{S}{N}
\end{aligned}
$$

Con esto ya calculado, se puede calcular la capacidad del canal: 

$$
\begin{aligned}
C_{bps} = H * Log_2(1 + \frac{S}{N}) \\
C_{bps} = (3 * 10^3) * Log_2(1 + 10^{3}) \\
C_{bps} = (3 * 10^3) * Log_2(1 + 10^{3}) \\ 
C_{bps} = (3 * 10^3) * 13.29 \\ 
C_{bps} = 39.87 kbps
\end{aligned}
$$

---

> Si suponemos que un canal de voz con un ancho de banda de 3100 Hz se utiliza con un módem para transmitir datos digitales ( niveles), ¿cuál sería la capacidad del canal? 

## Tasa de Nyquist

$$
C_{bps} = 2 * H * Log_2(V)
$$

Siendo: 
- C_{bps} la capacidad máxima del canal en bits por segundo.
- *H* ancho de banda del canal de comunicación en Hertz *Hz*. 
- *V* número de niveles de amplitud de la señal.

Reemplazando los valores dados en el enunciado: 

$$
\begin{aligned} 
C_{bps} = 2 * H * Log_2(V) \\
C_{bps} = 2 * 3100 * Log_2(2) \\
C_{bps} = 6200 * Log_2(2) \\
C_{bps} = 6200 * 1 \\
C_{bps} = 6200 bps \\
\end{aligned} 
$$

---

> Un canal de TV tiene un ancho de banda de 6 *MHz*. Calcule la tasa de transferencia de datos máxima que podría llevarse en un canal de TV por medio de un código de 16 niveles. Ignore el ruido. 

## Tasa de Nyquist

$$
C_{bps} = 2 * H * Log_2(V)
$$

Siendo: 
- C_{bps} la capacidad máxima del canal en bits por segundo.
- *H* ancho de banda del canal de comunicación en Hertz *Hz*. 
- *V* número de niveles de amplitud de la señal.

Reemplazando los valores dados en el enunciado: 

$$
\begin{aligned} 
C_{bps} = 2 * H * Log_2(V) \\
C_{bps} = 2 * 6 * 10^6 * Log_2(16) \\
C_{bps} = 12 * 10^6 * Log_2(16) \\
C_{bps} = 12 * 10^6 * 4 \\
C_{bps} = 48 * 10^6 \\
C_{bps} = 48 Mbps \\
\end{aligned} 
$$

---

> ¿Cuál será la máxima velocidad de transmisión a través de un canal digital sin ruido, si el ancho de banda del mismo es de 100 Khz y se utilizan 16 niveles de tensión distintos para representar la información?

## Tasa de Nyquist

$$
C_{bps} = 2 * H * Log_2(V)
$$

Siendo: 
- C_{bps} la capacidad máxima del canal en bits por segundo.
- *H* ancho de banda del canal de comunicación en Hertz *Hz*. 
- *V* número de niveles de amplitud de la señal.

Reemplazando los valores dados en el enunciado: 

$$
\begin{aligned} 
C_{bps} = 2 * H * Log_2(V) \\
C_{bps} = 2 * 100 * 10^3 * Log_2(16) \\
C_{bps} = 200 * 10^3 * Log_2(16) \\
C_{bps} = 200 * 10^6 * 4 \\
C_{bps} = 800 * 10^3 \\
C_{bps} = 800 kbps \\
\end{aligned} 
$$

---

> Cuál será la capacidad de canal de un medio de transmisión cableado si el ancho de banda del mismo es de 1 Mhz y la relación señal/ruido es de 20 dB. ¿Cuál será la máxima velocidad alcanzable en dicho canal si la potencia de la señal es de 3 mW.?

## Tasa de Shannon

$$
C_{bps} = H * Log_2(1 + \frac{S}{N})
$$

Siendo:
- C_{bps} la capacidad máxima del canal en bits por segundo.
- *H* ancho de banda del canal de comunicación en Hertz *Hz*. 
- $\frac{S}{N}$ Relación señal ruido.
  - *S* potencia de la señal útil, que puede estar expresada en vatios *W*
  - *N* potencia del ruido presente en el canal que trata de enmascarar a la señal útil.

Como la relacion señal ruido está expresada en *db* se debe aplicar primero la ecuación siguiente: 

$$
\begin{aligned} 
(\frac{S}{N})_{db} = 10 * log(\frac{S}{N}) \\
20 = 10 * log(\frac{S}{N}) \\
\frac{20}{10} = log(\frac{S}{N}) \\
2 = log(\frac{S}{N}) \\
10^{2} = \frac{S}{N}
\end{aligned}
$$

Con esto ya calculado, se puede calcular la capacidad del canal: 

$$
\begin{aligned}
C_{bps} = H * Log_2(1 + \frac{S}{N}) \\
C_{bps} = (1 * 10^6) * Log_2(1 + 10^{2}) \\
C_{bps} = (1 * 10^6) * Log_2(1 + 10^{2}) \\ 
C_{bps} = (1 * 10^6) * 6.66 \\ 
C_{bps} = 6.66 Mbps
\end{aligned}
$$

---

