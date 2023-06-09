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