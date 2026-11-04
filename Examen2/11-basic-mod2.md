### Descripción
A new modular challenge! Download the message [here](https://challenge-files.cylabacademy.net/library/4f25bc41d739375d13732691063a72f372cc433988ff76ad620c458a792b5c9e/message.txt).

Take each number mod 41 and find the modular inverse for the result. Then map to the following character set: 1-26 are the alphabet, 27-36 are the decimal digits, and 37 is an underscore.

Wrap your decrypted message in the academy flag format (i.e. `academy{decrypted_message}`)

	Hints
	1 Do you know what the modular inverse is?
	2 The inverse modulo _z_ of _x_ is the number, _y_ that when multiplied by _x_       is 1 modulo _z_
	3 It's recommended to use a tool to find the modular inverses

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat message.txt
104 126 274 231 262 378 108 352 64 338 77 209 139 441 297 168 158 309 329 415 186 145 186

┌──(kali㉿kali)-[~]
└─$ python3 -c "
with open('message.txt') as f:
    nums = [int(x) for x in f.read().split()]

invs = [pow(x % 41, -1, 41) for x in nums]

def map_char(v):
    if 1 <= v <= 26:
        return chr(ord('a') + v - 1)
    elif 27 <= v <= 36:
        return chr(ord('0') + v - 27)
    elif v == 37:
        return '_'
    return '?'

msg = ''.join(map_char(v) for v in invs)
print(f'academy{{{msg}}}')
"
academy{1nv3r53ly_h4rd_471a6111}
```

### Notas adicionales
- Para cada número $n_i$, se calcula primero su residuo módulo 41 ($r_i = n_i \pmod{41}$).
- Luego se obtiene el inverso modular multiplicativo: $x \equiv r_i^{-1} \pmod{41}$, es decir, tal que $(r_i \cdot x) \equiv 1 \pmod{41}$.
- En Python 3.8+, la función nativa `pow(r, -1, 41)` calcula este inverso eficientemente mediante el algoritmo de Euclides extendido.
- Siguiendo el mapeo del enunciado (1-26: `a-z`, 27-36: `0-9`, 37: `_`), se decodifica la cadena y se envuelve en el formato `academy{}`.

### Referencias
- [Modular multiplicative inverse](https://en.wikipedia.org/wiki/Modular_multiplicative_inverse)
- [Python pow() function](https://docs.python.org/3/library/functions.html#pow)
