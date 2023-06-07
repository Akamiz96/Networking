# Framing

The unit of exchange of information in data link protocols is the **frame**.

A frame is a block of data that also contains control information, used by the protocol to identify the frame.

When the transmission method used is block oriented (such as many synchronous transmissions) the frame synchronization is already resolved by the transmission method.

On the contrary, when using character-oriented transmission methods, such as asynchronous serial transmission, frame synchronization must be resolved by some additional procedure.

## Methods to detect the beginning / end of frame.

### Character Count

In this method a field is added in the header, to specify the number of characters in the frame.

![Character Count without errors](/images/link_layer/character_count_1.png)

By the time the link layer sees, at the receiving end, the character count, it learns the number of characters that follow, and therefore where the frame ends.

The problem with this algorithm is that the account can be distorted by a transmission error.

![Character Count with errors](/images/link_layer/character_count_2.png)

El hecho de enviar una trama incorrecta al extremo origen para solicitarle que retransmita, tampoco ayuda de manera significativa, dado que el extremo destinatario no sabe cuántos caracteres debe omitir para llegar al inicio de la retransmisión.

### Sequence of bits

The procedure consists of inserting the sequence **`01111110`** at the start and end of each frame (known as the indicator byte).

Adding control information to delimit the frames is frequently used, but it presents the problem that the same combinations used could appear in the message to be transmitted, generating an interpretation conflict in the receiver when detecting a false end of the frame.

To prevent this sequence from repeating itself within the data, if **5 consecutive ones** are found, a `0` is automatically inserted. Thus, the flag byte will not be present in the data.

#### Example

You want to transmit the following frame:

| 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

Following what was previously described, the sequence would be:

| **0** | **1** | **1** | **1** | **1** | **1** | **1** | **0** | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | **0** | 1 | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | **0** | 0 | 0 | **0** | **1** | **1** | **1** | **1** | **1** | **1** | **0** |
|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-----:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-----:|:-:|:-:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|

### Code Violations

To signal the frame start and end conditions, these violations consist of abnormal transmission conditions.

For example, the *Manchester* encoding establishes the existence of a **high-low** or **low-high** transition for the encoding of the bits.

The use of transitionless combinations **low-low** or **high-high** (and therefore invalid under the *Manchester* scheme) allows frames to be clearly encapsulated, and does not require the insertion process of the previous method.

![Code Violations](/images/link_layer/code_violations.png)