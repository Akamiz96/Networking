![Welcome](/images/physical_layer/Fourier/banner_waves.jpg)

# ✒️ Capacidad máxima del canal ✒️ 

La capacidad de canal es la cantidad de información que puede ser relativamente transmitida sobre canales de comunicación. 

La capacidad del canal se mide en bits por segundo (bps) y depende de su ancho de banda y de la relación S/N (Relación señal/ruido). 

La capacidad del canal limita la cantidad de información (se denomina régimen binario y se mide en bits por segundo, bps) que puede trasmitir la señal que se envía a través de él. 

Aprender a calcular la capacidad del canal es fundamental para optimizar la transmisión de datos y asegurar una comunicación eficiente y efectiva.

Existen dos criterios importantes para calcular la capacidad del canal: el criterio de Nyquist y el criterio de Shannon. Ambos criterios se basan en la comprensión de la señal y su relación con el ruido.

## Tasa de Nyquist

$$
C_{bps} = 2 * H * Log_2(V)
$$

Siendo: 
- C_{bps} la capacidad máxima del canal en bits por segundo.
- *H* ancho de banda del canal de comunicación en Hertz *Hz*. 
- *V* número de niveles de amplitud de la señal.

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

### Nota: 

If the signal-to-noise ratio is expressed in decibels *db*, in order to apply the aforementioned equation, it is necessary to carry out the transformation described below:

$$
(\frac{S}{N})_{db} = 10 * log_{10}(\frac{Potencia\_señal}{Potencia\_ruido})  \\
(\frac{S}{N})_{db} = 10 * log_{10}(\frac{S}{N}) \\
$$