![Welcome](/images/link_layer/Hamming/binary_numbers.jpg)

# ✒️ Bug detection and correction ✒️

Solved the problem of beginning and end of the frame, the following problem is reached and it is how to ensure that the delivery of the frames is reliable.

Two techniques have basically been designed for handling errors.

- Include enough redundant information in each block to let the receiver know that an error has occurred.
  - **Error detection code techniques**

- Include redundant information to detect the error, the extra information is used to correct it.
  - **Error Correction Code Techniques**

To understand how to handle errors, it is necessary to study closely what an error is.

A frame consists of `m` data bits and `r` redundant or check bits. Then let the total length be $n = m + r$.

This unit is called **code word**.

Given any two codewords, `10001001` and `10110001`, in what way (*boolean operator*) can it be determined how many corresponding bits differ?

---

Exclusive OR (XOR) is used.

|    |    |    |    |    |    |    |    |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1  | 0  | 0  | 0  | 1  | 0  | 0  | 1  |
| 1  | 0  | 1  | 1  | 0  | 0  | 0  | 1  |
| \- | \- | \- | \- | \- | \- | \- | \- |
| 0  | 0  | 1  | 1  | 1  | 0  | 0  | 0  |

The number of bit positions by which two codewords differ is called the ***Hamming Distance***.

---

## Hamming Distance

For example, to convert the word **“Ball”** to a different word:

- “B**a**ll” en “B**e**ll” has changed one letter (one step), so the ***Hamming distance*** is **1**.
- “Ba**ll**” en “Ba**se**”, the ***Hamming distance*** is **2**.
- “B**all**” en “B**end**”, the ***Hamming distance*** is **3**.
- “**Ball**” en “**Girl**”, the ***Hamming distance*** is **4**.

For binary numbering, the ***Hamming distance*** is the bits that change from one bit group to another bit group.

---

## Hamming space

Hamming space is all combinations of bit strings of the same size. That is, they are all points of a dimension N.

For example, for binary there would be a total of $𝟐^𝑵$ dots/combinations in “*Hamming Space*”.

![Hamming Space 4 bits](/images/link_layer/Hamming/Hamming_Space_4_bits.png)

---

Taking into account the concepts of ***Hamming Distance*** and ***Hamming Space*** a diagram representing distance changes of 1 between different *r* bit codewords can be constructed.

With only 1 bit, the ***Hamming Space*** would be 2 and the relationship of these two words with respect to the ***Hamming Distance*** would be as shown in the following image:

![1 bit](/images/link_layer/Hamming/bits/1_bit.png)

With 2 bits, the ***Hamming Space*** would be 4 and the relationship of these two words with respect to the ***Hamming Distance*** would be as shown in the following image:

![2 bits](/images/link_layer/Hamming/bits/2_bits.png)

With 3 bits, the ***Hamming Space*** would be 8 and the relationship of these two words with respect to the ***Hamming Distance*** would be as shown in the following image:

![3 bits](/images/link_layer/Hamming/bits/3_bits.png)

With 4 bits, the ***Hamming Space*** would be 16 and the relationship of these two words with respect to the ***Hamming Distance*** would be as shown in the following image:

![4 bits](/images/link_layer/Hamming/bits/4_bits.png)

---

## Redundancy bits

They are extra bits of information to try to correct errors or at least check that everything is correct.

The original data plus the “redundancy bits” is known as the “Block Code”.

### Redundancy codes

- Parity
- Repetition
- Hamming codes

#### Parity

Parity consists of adding a bit, called the parity bit, which indicates whether the number of bits with the value `1` in the preceding data is even or odd.

If a single bit were to change by error in transmission, the message will change parity and the error can be detected (note that the bit where the error occurs can be the same parity bit).

The most common convention is that a parity value of `1` indicates that there are an odd number of 1s in the data, and a parity value of `0` indicates that there are an even number of 1s in the data.

| **Information code**      | **Quantity of "1" in the code**  | **Parity bit**     |
|:-------------------------:|:--------------------------------:|:------------------:|
| 0010010                   | 2                                | 0                  |
| 1110110                   | 5                                | 1                  |

| **7 data bits**      | **Even parity** | **Odd parity**    |
|:--------------------:|:---------------:|:-----------------:|
| 0000000              | 000000**0**     | 000000**1**       |
| 1010001              | 1010001**1**    | 1010001**0**      |
| 1101001              | 1101001**0**    | 1101001**1**      |
| 1111111              | 1111111**1**    | 1111111**0**      |

#### Repetition

Another code used was to repeat each bit of data several times to make sure the transmission was correct.

For example, if the data bit being sent were a 1, a repeat code with n=3 would send "111". If the three received bits were not identical, there was an error.

In a quiet environment, most of the time only one bit in each three-bit packet would change.

Therefore, data of type `001`, `010`, and `100` correspond to bit `0`, while `110`, `101`, and `011` correspond to bit `1`.

A code with this ability to reconstruct the original message in the presence of errors is known as an ***correcting code***.

On the other hand, the repetition code is extremely inefficient, reducing the transmission speed by three in our original example, and its efficiency drops drastically as the number of times each bit is repeated increases to detect and correct more errors.

#### Hamming codes

If more error-correcting bits are added alongside the message, and if those bits can be arranged so that different error bits produce different results, then the erroneous bits could be identified.

The bit string is made up of data bits and parity bits mixed together (but not scrambled 😉)

There are several nomenclatures for these codes:

-hamming(3,1)
-hamming(7,4)
-Hamming(15,11)
-Hamming(31,26)
- Etc…

Let's focus on “***Hamming(7,4)***”, which means that for every `7` bits that represent data there are `4` that are data bits and the remaining $7 – 4 = 3$ are “ ***parity bits***”.

##### Steps

1. All bits whose position is a power of two are used as parity bits (positions 1, 2, 4, 8, 16, 32, 64, etc.).
2. The bits in the rest of the positions are used as data bits (positions 3, 5, 6, 7, 9, 10, 11, 12, 13, 14, 15, 17, etc.).
3. Each parity bit is obtained by calculating the parity of one of the data bits

###### Example

Let's focus on “Hamming(7,4)”, which means that for every 7 bits that represent data there are 4 that are Data bits and the remaining $7 – 4 = $3 are “parity bits”.

**Unverified data**

| **1** | **0** | **1** | **1** |
|:-----:|:-----:|:-----:|:-----:|

To make the interpretation of the process easier, the following table is created following steps `1` and `2`:

1. All bits whose position is a power of two are used as parity bits (positions 1, 2, 4, 8, 16, 32, 64, etc.).
2. The bits in the rest of the positions are used as data bits (positions 3, 5, 6, 7, 9, 10, 11, 12, 13, 14, 15, 17, etc.).

In this example bits `1`, `2` and `4` are parity bits, while bits `3`, `5`, `6` and `7` are data bits.

Since the parity bits have not yet been calculated they are marked as `*`.

| **1** | **2** | **3** | **4** | **5** | **6** | **7** |
|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|
| *     | *     | 1     | *     | 0     | 1     | 1     |

With the data bits and parity bits located in the table, the process of calculating the parity bits can begin.

To carry out the process, each of the positions must be converted to its respective binary number as shown in the following table:

|                            |     |     |     |     |     |     |     |
|:--------------------------:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **Binary position**        | 001 | 010 | 011 | 100 | 101 | 110 | 111 |
| **Decimal position**       | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| **Unverified data**        | *   | *   | 1   | *   | 0   | 1   | 1   |

Now, apply step `3`.

3. Each parity bit is obtained by calculating the parity of one of the data bits

Let's start with the parity bit which is in the `1` position. The bits that will be used to calculate the parity bit that goes in this position are those whose position contains a `1` in the least significant bit.

In the case of the parity bit that is in position `1`, the data bits in the positions will be used:

- `3` (01**1**)
- `5` (10**1**)
- `7` (11**1**)

This means, that for this example, the parity bit that is in the `1` position will have the value of `0` under an even parity scheme (even amount of `1` in the word to be transmitted).

The parity bit that is in position `2` will be calculated in the same way, but using those data bits that are in positions that have a `1` in the second least significant bit.

In the case of the parity bit that is in position `1`, the data bits in the positions will be used:

- `3` (0**1**1)
- `6` (1**1**0)
- `7` (1**1**1)

This means, that for this example, the parity bit that is in position `2` will have the value of `1` under an even parity scheme (even amount of `1` in the word to be transmitted).

The parity bit that is in position `3` will be calculated in the same way, but using those data bits that are in positions that have a `1` in the most significant bit.

In the case of the parity bit that is in position `3`, the data bits in the positions will be used:

- `5` (**1**01)
- `6` (**1**10)
- `7` (**1**11)

This means, that for this example, the parity bit that is in position `3` will have the value of `0` under an even parity scheme (even quantity of `1` in the word to be transmitted).

With these parity bits already calculated, the table presented above can be completed; resulting in this:

|                            |     |     |     |     |     |     |     |
|:--------------------------:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **Posición binario**       | 001 | 010 | 011 | 100 | 101 | 110 | 111 |
| **Posición decimal**       | 1   | 2   | 3   | 4   | 5   | 6   | 7   |
| **Datos sin comprobación** | *0* | *1* | 1   | *0* | 0   | 1   | 1   |

---

