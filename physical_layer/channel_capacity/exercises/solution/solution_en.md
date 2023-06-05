# Solution
---

> Assume that the spectrum of a channel is located between 3Mhz and 4 MHz and that the SNR is 24 dB.

---

> The telephone channel has a bandwidth of 3 kHz and a signal/noise ratio greater than 30 dB (at least they promise this a lot). The maximum data rate that a modem can produce for this wired channel and expect errors not to become rampant is capacity.

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