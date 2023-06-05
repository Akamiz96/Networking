# 🧑‍💻 Ejemplos de aplicación capacidad máxima del canal 🧑‍💻

---

> Si se tiene un canal que usa ancho de banda de 1 Mhz que está expuesto al ruido. Considerando una SNR de 40dB, calcular la capacidad del canal.

Teniendo en cuenta que se considera un enlace con ruido, se aplica la tasa de Shannon, esto es:

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

Para este caso, se sabe que:

$$
H = 10^6 [Hz]
$$

$$
SNR = 40 [db]
$$

Para poder determinar la relación señal ruido ($\frac{S}{N}$) en términos de potencia, se debe aplicar la siguiente ecuación: 

$$
(\frac{S}{N})_{db} = 10 * log(\frac{S}{N}) \\
$$

Reemplazando: 

$$
\begin{align} 
40 = 10 * log(\frac{S}{N}) \\
\frac{40}{10} = log(\frac{S}{N}) \\
4 = log(\frac{S}{N}) \\
10^4 = \frac{S}{N} \\
\end{align} 
$$

Ahora bien, con este valor, ya se puede calcular la capacidad máxima del canal:

$$
\begin{align} 
C_{bps} = H * Log_2(1 + \frac{S}{N}) \\
C_{bps} = 10^6 * Log_2(1 + 10^4) \\
C_{bps} = 10^6 * 13.28 \\
C_{bps} = 13.28 [Mbps] \\
\end{align} 
$$

---

> Suponga un canal con una capacidad proyectada de 20 Mbps. El ancho de banda del canal es de 3Mhz. ¿Cuál es la relación S/N requerido para obtener dicha capacidad?

Teniendo en cuenta que se considera un enlace con ruido, se aplica la tasa de Shannon, esto es:

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

Para este caso, se sabe que:

$$
C_{bps} = 20 [Mbps]
$$

$$
H = 3 [Mhz]
$$

Ahora bien, con estos valores, ya se puede calcular la relación S/N:

$$
\begin{align} 
C_{bps} = H * Log_2(1 + \frac{S}{N}) \\
20 * 10^6 = 3 * 10^6 * Log_2(1 + \frac{S}{N}) \\
\frac{20}{3} = Log_2(1 + \frac{S}{N}) \\
2^{\frac{20}{3}} = 1 + \frac{S}{N} \\
2^{\frac{20}{3}} - 1 = \frac{S}{N} \\
100.6 [db] = \frac{S}{N}
\end{align} 
$$

---

> Conociendo que la señal voz en un canal telefónico contiene  frecuencias  máximas  del  orden  de  los  4  KHz  (4000Hz),  indique  la 
velocidad mínima para transmitir la señal por un canal de voz digital (explique). Además, si esas muestras se cuantifican en 128 niveles, qué velocidad de flujo de datos se requiere en el canal para poder transmitir las muestras. 

Teniendo en cuenta los valores provistos por el problema, se puede utilizar la tasa de Nyquist para solucionar el problema:

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
C_{bps} = 2 * 4000 * Log_2(128) \\
C_{bps} = 8000 * Log_2(128) \\
C_{bps} = 8000 * 7 \\
C_{bps} = 56000 \\
\end{aligned} 
$$

