# 🧑‍💻 Example of application maximum channel capacity 🧑‍💻

If you have a channel that uses 1 MHz bandwidth that is exposed to noise. Considering an SNR of 40dB, calculate the channel capacity.

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
