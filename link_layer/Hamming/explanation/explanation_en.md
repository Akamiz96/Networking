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

For example, to convert the word **“Ball”** to a different word:

- “B**a**ll” en “B**e**ll” has changed one letter (one step), so the ***Hamming distance*** is **1**.
- “Ba**ll**” en “Ba**se**”, the ***Hamming distance*** is **2**.
- “B**all**” en “B**end**”, the ***Hamming distance*** is **3**.
- “**Ball**” en “**Girl**”, the ***Hamming distance*** is **4**.

For binary numbering, the ***Hamming distance*** is the bits that change from one bit group to another bit group.

---