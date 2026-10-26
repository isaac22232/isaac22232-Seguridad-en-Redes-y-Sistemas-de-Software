### Descripción
A message has come in but it seems to be all scrambled. Luckily it seems to have the key at the beginning. Can you crack this substitution cipher? Download the message [here](https://challenge-files.cylabacademy.net/library/ba4dc472a6e0784e2ec4ad7184bdbe107b432edfc1464d836433b8eb16279406/message.txt).

### Solución
```
Este es un cifrado de sustitución simple donde cada letra del alfabeto estándar (A-Z) fue reemplazada por la letra correspondiente en la misma posición de la llave.

El mapeo para descifrar el mensaje es el siguiente:

- **Llave (Texto cifrado):** `K C X Z U N D A O Y V R H W L G F S I M Q P T E B J`
    
- **Alfabeto (Texto plano):** `A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`
    

Si observamos la última línea del archivo, encontramos la cadena `kxkzuhb{5QC5717Q710W_3P0RQ710W_1ZZN0Z6X}`. Al sustituir cada letra cifrada por su correspondiente en texto plano (respetando los números y guiones bajos que no cambian):

TXT

- `kxkzuhb` se traduce como `academy` (ej. K->A, X->C, Z->D, U->E, H->M, B->Y).
    
- `5QC5717Q710W` se traduce como `5UB5717U710N` (Q->U, C->B, W->N).
    
- `3P0RQ710W` se traduce como `3V0LU710N` (P->V, R->L, Q->U, W->N).
    
- `1ZZN0Z6X` se traduce como `1DDF0D6C` (Z->D, N->F, X->C).
    

Uniendo todas las partes, la bandera final es:

**`academy{5UB5717U710N_3V0LU710N_1DDF0D6C}`**
```

### Notas adicionales


### Referencias
