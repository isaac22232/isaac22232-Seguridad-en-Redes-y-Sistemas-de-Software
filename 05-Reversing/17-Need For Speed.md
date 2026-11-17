### Descripción
The name of the game is [speed](https://www.youtube.com/watch?v=8piqd2BWeGI). Are you quick enough to solve this problem and keep it above 50 mph? [need-for-speed](https://challenge-files.cylabacademy.net/library/6dfc63d7e4ee66dec270d4f50ae9e6c2b1ed3c6364b723c94f23210d2ab91740/need-for-speed)

	Hints
	1 What is the final key?

### Solución
```
┌──(kali㉿kali)-[~]
└─$ chmod +x need-for-speed

┌──(kali㉿kali)-[~]
└─$ ./need-for-speed
Keep this thing over 50 mph!
============================

Creating key...
Not fast enough. BOOM!

┌──(kali㉿kali)-[~]
└─$ # Al analizar el binario con GDB u objdump:
└─$ # - La función 'set_timer' programa una alarma con SIGALRM que interrumpe el programa.
└─$ # - La función 'calculate_key' ejecuta un bucle decremental deliberadamente lento que siempre finaliza retornando 0xdf489ce8.
└─$ # - La función 'decrypt_flag' aplica una operación XOR entre el arreglo cifrado en .data y los bytes de la clave (incrementando la clave en 1 cada 3 posiciones).

┌──(kali㉿kali)-[~]
└─$ # Podemos extraer la bandera directamente emulando decrypt_flag con la clave final 0xdf489ce8:
┌──(kali㉿kali)-[~]
└─$ python3 -c "
with open('need-for-speed', 'rb') as f:
    data = f.read()

# Arreglo cifrado ubicado en la sección .data (offset 0x3020, 55 bytes)
flag_enc = data[0x3020 : 0x3020 + 0x37]
key = 0xdf489ce8

res = []
for i in range(len(flag_enc)):
    key_byte = key.to_bytes(4, 'little')[i % 2]
    res.append(chr(flag_enc[i] ^ key_byte))
    if i % 3 == 2:
        key = (key + 1) & 0xffffffff

print(''.join(res))
"
academy{Good job keeping bus #31b86b76 speeding along!}
```

### Notas adicionales
- El binario implementa un temporizador mediante `alarm()` que detiene el proceso si no termina en un segundo.
- La función `calculate_key()` realiza un bucle decreciente de 32 bits repetido 8 veces, cuyo resultado fijo al terminar la comparación es `0xdf489ce8` (resolviendo la pista *What is the final key?*).
- La rutina `decrypt_flag(key)` recorre los 55 bytes de la bandera cifrada en la sección `.data`, aplicando XOR con los bytes en little-endian de la clave alternando según `i % 2`, e incrementando `key` en `1` cada vez que `i % 3 == 2`.
- Al reproducir el algoritmo en Python o parchear el binario para omitir la alarma y saltar directamente al cálculo, se obtiene la bandera.

### Referencias
- [SIGALRM and alarm(2)](https://man7.org/linux/man-pages/man2/alarm.2.html)
- [GDB Breakpoints and Execution](https://sourceware.org/gdb/current/onlinedocs/gdb.html)
