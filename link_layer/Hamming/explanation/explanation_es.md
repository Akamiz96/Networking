![Welcome](/images/link_layer/Hamming/binary_numbers.jpg)

# ✒️ Detección y corrección de errores ✒️ 

Resuelto el problema de inicio y fin de trama, se llega al siguiente problema y es como asegurar que le entrega de las tramas sea confiable.

Para el manejo de errores se han diseñado básicamente dos técnicas 

- Incluir suficiente información redundante en cada bloque para permitir que el receptor sepa que ha ocurrido un error. 
  - **Técnicas de códigos de detección de errores**

- Incluir información redundante para detectar el error, la información extra sirve para corregir. 
  - **Técnicas de códigos de corrección de errores**

Para entender la manera de manejar errores, es necesario estudiar de cerca lo que es un error.

Una trama consiste en `m` bits de datos y `r` bits redundantes o de verificación. Entonces sea la longitud total $n = m + r$.

A esta unidad se le llama **palabra codificada**.

Dadas dos palabras codificadas  cualesquiera, `10001001` y `10110001`, de que manera (*operador booleano*) es posible determinar cuántos bits correspondientes difieren.

---

Se utiliza el OR exclusivo (XOR).

|    |    |    |    |    |    |    |    |
|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| 1  | 0  | 0  | 0  | 1  | 0  | 0  | 1  |
| 1  | 0  | 1  | 1  | 0  | 0  | 0  | 1  |
| \- | \- | \- | \- | \- | \- | \- | \- |
| 0  | 0  | 1  | 1  | 1  | 0  | 0  | 0  |

La cantidad de posiciones de bits en la que difieren dos palabras codificadas se llama ***Distancia de Hamming***.

---

## Distancia de Hamming

Por ejemplo, para convertir la palabra **“Casa”** en otra palabra diferente:

- “**C**asa” en “**M**asa” ha cambiado una letra (un paso), por lo que la ***distancia de Hamming*** es **1**.
- “**C**a**s**a” en “**M**a**p**a”, la ***distancia de Hamming*** es de **2**.
- “**Cas**a” en “**Mop**a”, la ***distancia de Hamming*** es de **3**.
- “**Casa**” en “**Moví**”, la ***distancia de Hamming*** es de **4**.

Para la numeración binaria, la ***distancia de Hamming*** son los bits que cambian de un grupo de bits a otro grupo de bits.

---

## Espacio de Hamming 

El espacio de Hamming son todas las combinaciones de cadenas de bits del mismo tamaño. Es decir, son todos los puntos de una dimensión N.

Por ejemplo, para binario habría un total de $𝟐^𝑵$ puntos/combinaciones en el “*Espacio de Hamming*”.

![Hamming Space 4 bits](/images/link_layer/Hamming/Hamming_Space_4_bits.png)

---

Teniendo en cuenta los conceptos de ***Distancia de Hamming*** y ***Espacio de Hamming*** se puede construir un diagrama que representa cambios de distancia de 1 entre distintas palabras codificadas de *r* bits.

Con solo 1 bit, el ***Espacio de Hamming*** sería de 2 y la relación de estas dos palabras con respecto a la ***Distancia de Hamming*** sería como se muesta en la imagen siguiente: 

![1 bit](/images/link_layer/Hamming/bits/1_bit.png)

Con 2 bits, el ***Espacio de Hamming*** sería de 4 y la relación de estas dos palabras con respecto a la ***Distancia de Hamming*** sería como se muesta en la imagen siguiente: 

![2 bits](/images/link_layer/Hamming/bits/2_bits.png)

Con 3 bits, el ***Espacio de Hamming*** sería de 8 y la relación de estas dos palabras con respecto a la ***Distancia de Hamming*** sería como se muesta en la imagen siguiente: 

![3 bits](/images/link_layer/Hamming/bits/3_bits.png)

Con 4 bits, el ***Espacio de Hamming*** sería de 16 y la relación de estas dos palabras con respecto a la ***Distancia de Hamming*** sería como se muesta en la imagen siguiente: 

![4 bits](/images/link_layer/Hamming/bits/4_bits.png)



