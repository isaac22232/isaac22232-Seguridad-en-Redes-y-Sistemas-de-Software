### Descripción
Our data got corrupted on the way here. Luckily, nothing got replaced, but every block of 3 got scrambled around! The first word seems to be three letters long, maybe you can use that to recover the rest of the message. Download the corrupted message [here](https://challenge-files.cylabacademy.net/library/304dc08e455ad3c33cf532bb41f44a7e939e8e2ad161d9c9012b8375dee48829/message.txt).

	Hints
	1 Split the message up into blocks of 3 and see how the first block isscrambled

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat "message (1).txt"
heTfl g as icaaemd{7y4NRP051N5_16_35P3X51N3_V1CCA2B2}A

┌──(kali㉿kali)-[~]
└─$ # En el primer bloque 'heT', la palabra original es 'The', lo que indica que el tercer carácter (índice 2) pasa a la primera posición: (c2, c0, c1)
┌──(kali㉿kali)-[~]
└─$ python3 -c "
with open('message (1).txt') as f:
    text = f.read()

res = []
for i in range(0, len(text), 3):
    b = text[i:i+3]
    if len(b) == 3:
        res.append(b[2] + b[0] + b[1])
    else:
        res.append(b)

print(''.join(res))
"
The flag is academy{7R4N5P051N6_15_3XP3N51V3_C1CBA2A2}
```

### Notas adicionales
- El mensaje fue transpuesto en bloques independientes de 3 caracteres.
- Al analizar el primer bloque `heT` y compararlo con la palabra en inglés esperada `"The"`, se deduce la permutación inversa: el carácter en la posición 2 pasa al frente, seguido por los caracteres en las posiciones 0 y 1 (`block[2] + block[0] + block[1]`).
- Al aplicar esta misma permutación a cada bloque de 3 caracteres de la cadena, se reconstruye el texto original y la bandera.

### Referencias
- [Transposition cipher](https://en.wikipedia.org/wiki/Transposition_cipher)
