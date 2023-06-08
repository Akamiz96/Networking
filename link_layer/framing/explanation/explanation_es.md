# ✒️ Entramado ✒️

La unidad de intercambio de información en los protocolos de enlace de datos es la **trama**.

Una trama es un bloque de datos que además contiene información de control, empleada por el protocolo para identificar a la trama.

Cuando el método de transmisión utilizado está orientado a bloques (como muchas transmisiones síncronas) la sincronización de trama ya está resuelta por el método de transmisión. 

Por el contrario, al usar métodos de transmisión orientados a caracteres, como la transmisión serie asíncrona, la sincronización de trama debe ser resuelta por algún procedimiento adicional.

## Métodos para detectar el inicio / final de trama.

### Conteo de caracteres

En este método se agrega un campo en la cabecera, para especificar el número de caracteres en la trama. 

![Character Count without errors](/images/link_layer/framing/character_count_1.png)

En el momento en el cual la capa de enlace ve, en el extremo destinatario, la cuenta de caracteres, se entera del número de caracteres que siguen y, por consiguiente, donde termina la trama. 

El problema de este algoritmo es que la cuenta puede distorsionarse por un error de transmisión.

![Character Count with errors](/images/link_layer/framing/character_count_2.png)

El hecho de enviar una trama incorrecta al extremo origen para solicitarle que retransmita, tampoco ayuda de manera significativa, dado que el extremo destinatario no sabe cuántos caracteres debe omitir para llegar al inicio de la retransmisión.

### Secuencia de bits

El procedimiento consiste en insertar la secuencia **`01111110`** al inicio y fin de cada marco (conocida como byte indicador).

Añadir información de control para delimitar las tramas se emplea con frecuencia, pero presenta el problema de que las mismas combinaciones utilizadas podrían aparecer en el menseja a transmitir, generándose un conflicto de interpretación en el receptor al detectar un falso final de trama.

Para evitar que esta secuencia se repita dentro de los datos, si se encuentran **5 unos consecutivos**, se inserta automáticamente un `0`. Con ello, el byte indicador no se presentará en los datos.

#### Ejemplo

Se desea transmitir la siguiente trama: 

| 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | 0 | 0 |
|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|

Siguiendo lo descrito enteriormente la secuencia quedaría: 

| **0** | **1** | **1** | **1** | **1** | **1** | **1** | **0** | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | **0** | 1 | 0 | 0 | 0 | 1 | 1 | 1 | 0 | 1 | 1 | 1 | 1 | 1 | **0** | 0 | 0 | **0** | **1** | **1** | **1** | **1** | **1** | **1** | **0** |
|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-----:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-:|:-----:|:-:|:-:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|:-----:|

![Sequence of bits](/images/link_layer/framing/sequence_of_bits.png)

### Violaciones del código

Para señalizar las condiciones de principio y final de trama, estas violaciones consisten en condiciones anormales de la transmisión. 

Por ejemplo, la codificación *Manchester* establece la existencia de una transición **alto-bajo** o **bajo-alto** para la codificación de los bits. 

La utilización de combinaciones sin transición **bajo-bajo** o **alto-alto** (y por tanto inválidas bajo el esquema *Manchester*) permite encapsular claramente las tramas, y no requieren el proceso de inserción del método anterior.

![Code Violations](/images/link_layer/framing/code_violations.png)
