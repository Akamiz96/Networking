![Welcome](/images/physical_layer/channel_capacity/math_banner.jpg)

# 🧑‍💻 Examples of application maximum channel capacity 🧑‍💻

---

> If you have a channel that uses 1 MHz bandwidth that is exposed to noise. Considering an SNR of 40dB, calculate the channel capacity.

Taking into account that a noisy link is considered, the Shannon's rate is applied, that is:

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

For this case, it is known that:

$$
H = 10^6 [Hz]
$$

$$
SNR = 40 [db]
$$

In order to determine the signal to noise ratio ($\frac{S}{N}$) in terms of power, the following equation must be applied:

$$
(\frac{S}{N})_{db} = 10 * log(\frac{S}{N}) \\
$$

Replacing: 

$$
\begin{align} 
40 = 10 * log(\frac{S}{N}) \\
\frac{40}{10} = log(\frac{S}{N}) \\
4 = log(\frac{S}{N}) \\
10^4 = \frac{S}{N} \\
\end{align}
$$

Now, with this value, the maximum capacity of the channel can already be calculated:

$$
\begin{align} 
C_{bps} = H * Log_2(1 + \frac{S}{N}) \\
C_{bps} = 10^6 * Log_2(1 + 10^4) \\
C_{bps} = 10^6 * 13.28 \\
C_{bps} = 13.28 [Mbps] \\
\end{align}
$$

---

> Assume a channel with a projected capacity of 20 Mbps. The channel bandwidth is 3Mhz. What is the S/N ratio required to obtain such a capacity?

Taking into account that a noisy link is considered, the Shannon's rate is applied, that is:

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

For this case, it is known that:

$$
C_{bps} = 20 [Mbps]
$$

$$
H = 3 [Mhz]
$$

Now, with these values, the S/N ratio can now be calculated:

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

> Knowing that the voice signal in a telephone channel contains maximum frequencies of the order of 4 KHz (4000Hz), indicate the
minimum speed to transmit the signal over a digital voice channel (explain). Also, if those samples are quantized to 128 levels, what data rate is required on the channel to be able to transmit the samples.

Taking into account the values ​​provided by the problem, the Nyquist rate can be used to solve the problem:

## Nyquist's rate

$$
C_{bps} = 2 * H * Log_2(V)
$$

Being:
- C_{bps} the maximum capacity of the channel in bits per second.
- *H* bandwidth of the communication channel in Hertz *Hz*.
- *V* number of amplitude levels of the signal.

Substituting the values ​​given in the statement:

$$
\begin{aligned} 
C_{bps} = 2 * H * Log_2(V) \\
C_{bps} = 2 * 4000 * Log_2(128) \\
C_{bps} = 8000 * Log_2(128) \\
C_{bps} = 8000 * 7 \\
C_{bps} = 56000 \\
\end{aligned} 
$$

---

