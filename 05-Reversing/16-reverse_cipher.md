### Descripción
We have recovered a [binary](https://challenge-files.cylabacademy.net/library/3c06dee37ca661aa44d0cdd3193b89065bbed43cadb4663740d63c64b9d238c0/rev) and a [text file](https://challenge-files.cylabacademy.net/library/3c06dee37ca661aa44d0cdd3193b89065bbed43cadb4663740d63c64b9d238c0/rev_this). Can you reverse the flag.

	Hints
	1 objdump and Gihdra are some tools that could assist with this

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat rev_this
academy{w1{1wq8394=.>19}

┌──(kali㉿kali)-[~]
└─$ # Al desensamblar el binario 'rev', encontramos la lógica de transformación del texto:
└─$ # 1. Los primeros 8 caracteres (índices 0 a 7, 'academy{') se copian sin cambios.
└─$ # 2. Para los índices j desde 8 hasta 22:
└─$ #    - Si j es PAR:  cifrado[j] = flag[j] + 5  =>  flag[j] = cifrado[j] - 5
└─$ #    - Si j es IMPAR: cifrado[j] = flag[j] - 2  =>  flag[j] = cifrado[j] + 2
└─$ # 3. El último carácter (índice 23, '}') se copia directamente.

┌──(kali㉿kali)-[~]
└─$ python3 -c "
with open('rev_this') as f:
    c = f.read().strip()

prefix = c[:8]
suffix = c[-1]
mid = []
for j in range(8, len(c) - 1):
    val = ord(c[j])
    if j % 2 == 0:
        mid.append(chr(val - 5))
    else:
        mid.append(chr(val + 2))

print(prefix + ''.join(mid) + suffix)
"
academy{r3v3rs354680934}
```

### Notas adicionales
- El binario `rev` lee el archivo de la bandera original y genera `rev_this` mediante una serie de operaciones aritméticas en función del índice:
  - Los primeros 8 caracteres (`academy{`) se mantienen idénticos.
  - Para los índices de 8 a 22, si la posición es par se sumaron 5 unidades al valor ASCII del carácter, y si la posición es impar se restaron 2 unidades.
  - El delimitador final `}` se conserva sin modificaciones.
- Invirtiendo estas operaciones aritméticas (restando 5 en posiciones pares y sumando 2 en impares), se reconstruye la bandera original.

### Referencias
- [Ghidra SRE framework](https://ghidra-sre.org/)
- [objdump man page](https://linux.die.net/man/1/objdump)
