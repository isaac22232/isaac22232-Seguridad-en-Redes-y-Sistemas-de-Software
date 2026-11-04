### Descripción
You will find the flag after decrypting this file Download the encrypted flag [here](https://challenge-files.cylabacademy.net/library/87b38d23d72ad6f1aa572b3fb1ba217ddb7476a432e8810b51a3ff40caad8ac1/encrypted.txt).

	Hints
	1 Sometimes rotation is right

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat encrypted.txt
ikilmug{z0bib1wv_l3kzgxb3l_69m10560}

┌──(kali㉿kali)-[~]
└─$ # Sabiendo que el prefijo debe ser 'academy', la primera letra 'i' se desplaza a 'a' (shift de -8 o rotación 18):
┌──(kali㉿kali)-[~]
└─$ python3 -c "
s = 'ikilmug{z0bib1wv_l3kzgxb3l_69m10560}'
res = []
for c in s:
    if 'a' <= c <= 'z':
        res.append(chr((ord(c) - ord('a') - 8) % 26 + ord('a')))
    elif 'A' <= c <= 'Z':
        res.append(chr((ord(c) - ord('A') - 8) % 26 + ord('A')))
    else:
        res.append(c)
print(''.join(res))
"
academy{r0tat1on_d3crypt3d_69e10560}
```

### Notas adicionales
- Se trata de un cifrado César (rotación alfabética).
- Comparando el texto cifrado `ikilmug` con el formato esperado `academy`, se observa que cada letra está desplazada 8 posiciones hacia adelante (`'i' - 8 = 'a'`, `'k' - 8 = 'c'`).
- Aplicando un desplazamiento de $-8$ (o $+18$) únicamente a los caracteres alfabéticos, se obtiene la bandera descifrada.

### Referencias
- [Caesar cipher](https://en.wikipedia.org/wiki/Caesar_cipher)
