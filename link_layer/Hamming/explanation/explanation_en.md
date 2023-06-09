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