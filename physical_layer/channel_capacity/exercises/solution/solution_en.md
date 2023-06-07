![Welcome](/images/physical_layer/channel_capacity/math_banner_solution.jpg)

# Solution
---

> Assume that the spectrum of a channel is located between 3Mhz and 4 MHz and that the SNR is 24 dB.

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

Since the signal noise ratio is expressed in *db*, it must be applied first:

$$
\begin{aligned} 
(\frac{S}{N})_{db} = 10 * log(\frac{S}{N}) \\
24 = 10 * log(\frac{S}{N}) \\
\frac{24}{10} = log(\frac{S}{N}) \\
2.4 = log(\frac{S}{N}) \\
10^{2.4} = \frac{S}{N}
\end{aligned}
$$

With this already calculated, the channel capacity can be calculated:

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

> A telephone channel has a bandwidth of 3 kHz and a signal/noise ratio of 30 dB. What is the maximum data capacity that a modem can produce for this wired channel and expect errors not to become irreparable?

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

Since the signal noise ratio is expressed in *db*, the following equation must first be applied:

$$
\begin{aligned} 
(\frac{S}{N})_{db} = 10 * log(\frac{S}{N}) \\
30 = 10 * log(\frac{S}{N}) \\
\frac{30}{10} = log(\frac{S}{N}) \\
3 = log(\frac{S}{N}) \\
10^{3} = \frac{S}{N}
\end{aligned}
$$

With this already calculated, the channel capacity can be calculated:

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
 
> If we assume that a voice channel with a bandwidth of 3100 Hz is used with a modem to transmit digital data ( levels), what would be the capacity of the channel?

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
C_{bps} = 2 * 3100 * Log_2(2) \\
C_{bps} = 6200 * Log_2(2) \\
C_{bps} = 6200 * 1 \\
C_{bps} = 6200 \\
\end{aligned} 
$$

---

> A TV channel has a bandwidth of 6 *MHz*. Calculate the maximum data transfer rate that could be carried on a TV channel by means of a 16-level code. Ignore the noise.

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
C_{bps} = 2 * 6 * 10^6 * Log_2(16) \\
C_{bps} = 12 * 10^6 * Log_2(16) \\
C_{bps} = 12 * 10^6 * 4 \\
C_{bps} = 48 * 10^6 \\
C_{bps} = 48 Mbps \\
\end{aligned} 
$$

---

> What will be the maximum transmission speed through a digital channel without noise, if its bandwidth is 100 Khz and 16 different voltage levels are used to represent the information?

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
C_{bps} = 2 * 100 * 10^3 * Log_2(16) \\
C_{bps} = 200 * 10^3 * Log_2(16) \\
C_{bps} = 200 * 10^6 * 4 \\
C_{bps} = 800 * 10^3 \\
C_{bps} = 800 kbps \\
\end{aligned} 
$$

---

> What will be the channel capacity of a wired transmission medium if its bandwidth is 1 *Mhz* and the signal/noise ratio is 20 *dB*. What will be the maximum achievable speed in said channel if the power of the signal is 3 *mW*.?

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

Since the signal noise ratio is expressed in *db*, the following equation must first be applied:

$$
\begin{aligned} 
(\frac{S}{N})_{db} = 10 * log(\frac{S}{N}) \\
20 = 10 * log(\frac{S}{N}) \\
\frac{20}{10} = log(\frac{S}{N}) \\
2 = log(\frac{S}{N}) \\
10^{2} = \frac{S}{N}
\end{aligned}
$$

With this already calculated, the channel capacity can be calculated:

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