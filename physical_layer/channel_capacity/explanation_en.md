![Welcome](/images/physical_layer/Fourier/banner_waves.jpg)

# ✒️ Maximum channel capacity ✒️

Channel capacity is the amount of information that can be relatively transmitted over communication channels.

Channel capacity is measured in bits per second (bps) and depends on its bandwidth and S/N (Signal to Noise Ratio).

The channel capacity limits the amount of information (called bit rate and is measured in bits per second, bps) that can be transmitted by the signal sent through it.

Learning to calculate channel capacity is essential to optimize data transmission and ensure efficient and effective communication.

There are two important criteria for calculating channel capacity: the Nyquist criterion and the Shannon criterion. Both criteria are based on the understanding of the signal and its relation to noise.

## Nyquist's rate

$$
C_{bps} = 2 * H * Log_2(V)
$$

Being:
- C_{bps} the maximum capacity of the channel in bits per second.
- *H* bandwidth of the communication channel in Hertz *Hz*.
- *V* number of amplitude levels of the signal.

## Shannon's rate

$$
C_{bps} = H * Log_2(1 + \frac{S}{N})
$$

Being:
- C_{bps} the maximum capacity of the channel in bits per second.
- *H* bandwidth of the communication channel in Hertz *Hz*.
- $\frac{S}{N}$ Signal to noise ratio.
  - *S* useful signal power, which can be expressed in watts *W*
  - *N* power of the noise present in the channel that tries to mask the useful signal.

### Note: 

If the signal-to-noise ratio is expressed in decibels *db*, in order to apply the aforementioned equation, it is necessary to carry out the transformation described below:

$$
(\frac{S}{N})_{db} = 10 * log_{10}(\frac{Potencia señal}{Potencia ruido}) = 10 * log_{10}(\frac{S}{N})
$$