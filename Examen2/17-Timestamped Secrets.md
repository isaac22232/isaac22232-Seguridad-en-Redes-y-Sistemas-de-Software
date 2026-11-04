### Descripción
Someone encrypted a message using AES in ECB mode but they weren’t very careful with their key. Turns out it’s derived from something as simple as the current time! Can you uncover the key and decrypt the flag? Download the encrypted message: [message](https://challenge-files.cylabacademy.net/library/b74f8dcd392af52aae4e0f5332824faf5d93398362f1db228d4ad4b507e6c632/message.txt)  
You may also find the encryption script helpful: [code](https://challenge-files.cylabacademy.net/library/b74f8dcd392af52aae4e0f5332824faf5d93398362f1db228d4ad4b507e6c632/encryption.py)

	Hints
	1 `encryption.py` is a redacted example of the program

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat message.txt
Hint: The encryption was done around 1790147509 UTC
Ciphertext (hex): e24b9c357ad38df368104cc83fd235607bdac8f0f83123b38a89f459e46a3db2

┌──(kali㉿kali)-[~]
└─$ python3 -c "
from hashlib import sha256
from Crypto.Cipher import AES
from Crypto.Util.Padding import unpad

target = bytes.fromhex('e24b9c357ad38df368104cc83fd235607bdac8f0f83123b38a89f459e46a3db2')
ts = 1790147509

key = sha256(str(ts).encode()).digest()[:16]
cipher = AES.new(key, AES.MODE_ECB)
pt = unpad(cipher.decrypt(target), AES.block_size)
print(pt.decode())
"
academy{sa3S_sEc9t_f9ccd007}
```

### Notas adicionales
- El script de cifrado genera la clave AES de 128 bits calculando el hash SHA-256 de la marca de tiempo Unix (`timestamp`) convertida a cadena, tomando los primeros 16 bytes: `sha256(str(timestamp).encode()).digest()[:16]`.
- Dado que `message.txt` proporciona la marca de tiempo exacta (`1790147509 UTC`), se deriva la clave directamente con SHA-256.
- Al descifrar el bloque con `AES.MODE_ECB` y remover el relleno (*padding* PKCS#7), se recupera la bandera en claro.

### Referencias
- [AES ECB Mode](https://en.wikipedia.org/wiki/Block_cipher_mode_of_operation#Electronic_codebook_(ECB))
- [PyCryptodome AES documentation](https://pycryptodome.readthedocs.io/en/latest/src/cipher/aes.html)
