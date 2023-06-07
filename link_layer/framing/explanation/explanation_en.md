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

