# 🧑‍💻 Ejemplo de aplicación capacidad máxima del canal 🧑‍💻

Si se tiene un canal que usa ancho de banda de 1 Mhz que está expuesto al ruido. Considerando una SNR de 40dB, calcular la capacidad del canal.

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
40 = 10 * log(\frac{S}{N}) \\
\frac{40}{10} = log(\frac{S}{N}) \\
4 = log(\frac{S}{N}) \\
10^4 = \frac{S}{N}
$$

Ahora bien, con este valor, ya se puede calcular la capacidad máxima del canal:

$$
C_{bps} = H * Log_2(1 + \frac{S}{N}) \\
C_{bps} = 10^6 * Log_2(1 + 10^4) \\
C_{bps} = 10^6 * 13.28 \\
C_{bps} = 13.28 [Mbps]
$$