### Descripción
Can you get sense of this code file and write the function that will decode the given encrypted file content.

Find the encrypted file here [flag_info](https://challenge-files.cylabacademy.net/library/a64f108f8534cf5cfda7934a1fe672109591409a2ed883345371cdd5d03b281f/enc_flag) and [code file](https://challenge-files.cylabacademy.net/library/a64f108f8534cf5cfda7934a1fe672109591409a2ed883345371cdd5d03b281f/custom_encryption.py) might be good to analyze and get the flag.

	Hints
	1 Understanding encryption algorithm to come up with decryption algorithm.

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat enc_flag
a = 94
b = 25
cipher is: [120357, 869245, 213968, 1243689, 1243689, 1123332, 949483, 294206, 855872, 561666, 0, 1109959, 280833, 66865, 909364, 0, 294206, 1150078, 13373, 829126, 320952, 361071, 80238, 80238, 227341, 80238, 347698, 160476, 334325, 307579, 227341, 66865, 80238, 0]

┌──(kali㉿kali)-[~]
└─$ python3 -c "
p = 97
g = 31
a = 94
b = 25
cipher = [120357, 869245, 213968, 1243689, 1243689, 1123332, 949483, 294206, 855872, 561666, 0, 1109959, 280833, 66865, 909364, 0, 294206, 1150078, 13373, 829126, 320952, 361071, 80238, 80238, 227341, 80238, 347698, 160476, 334325, 307579, 227341, 66865, 80238, 0]

# 1. Recuperar clave compartida Diffie-Hellman
u = pow(g, a, p)
v = pow(g, b, p)
shared_key = pow(v, a, p)

# 2. Invertir la multiplicación: cipher = ord(char) * shared_key * 311
factor = shared_key * 311
semi_cipher = ''.join([chr(c // factor) for c in cipher])

# 3. Invertir dynamic_xor_encrypt con la clave 'trudeau'
text_key = 'trudeau'
key_len = len(text_key)
reversed_plain = []
for i, char in enumerate(semi_cipher):
    key_char = text_key[i % key_len]
    reversed_plain.append(chr(ord(char) ^ ord(key_char)))

plain = ''.join(reversed_plain)[::-1]
print(plain)
"
academy{custom_d2cr0pt6d_2b2589e3}
```

### Notas adicionales
- El algoritmo realiza dos capas de cifrado:
  1. `dynamic_xor_encrypt`: invierte la cadena (`plaintext[::-1]`) y aplica XOR cíclico con la clave `"trudeau"`.
  2. `encrypt`: multiplica el valor ordinal de cada carácter por `shared_key * 311`, donde `shared_key` se genera mediante Diffie-Hellman con $p=97$ y $g=31$.
- Como $a=94$ y $b=25$ están en `enc_flag`, calculamos `shared_key = pow(pow(31, 25, 97), 94, 97) = 43`.
- Dividiendo cada valor del arreglo entre $(43 \times 311)$ se recupera el texto intermedio, y aplicando XOR con `"trudeau"` e invirtiendo la cadena se obtiene la bandera.

### Referencias
- [Diffie-Hellman key exchange](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)
