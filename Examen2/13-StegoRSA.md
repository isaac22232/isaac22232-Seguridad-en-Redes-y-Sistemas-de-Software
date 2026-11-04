### Descripción
A message has been encrypted using RSA. The public key is gone… but someone might have been careless with the private key. Can you recover it and decrypt the message? Download the [flag](https://challenge-files.cylabacademy.net/library/43fe409039addd5ea8db54dde7c2716afeaaac4275047cbfb23f6d5f81fb3ba4/flag.enc) and [image](https://challenge-files.cylabacademy.net/library/43fe409039addd5ea8db54dde7c2716afeaaac4275047cbfb23f6d5f81fb3ba4/image.jpg).

	Hints
	1 Metadata can tell you more than you expect.
	2 Hex can be turned back into a key file.

### Solución
```
┌──(kali㉿kali)-[~]
└─$ strings image.jpg | grep -E "2d2d2d2d2d" | head -n 1
R2d2d2d2d2d424547494e2050524956415445204b45592d2d2d2d2d0a4d494945765149424144414e...

┌──(kali㉿kali)-[~]
└─$ # La cadena en hexadecimal comienza con 2d2d2d2d2d ('-----') y 424547494e ('BEGIN')
┌──(kali㉿kali)-[~]
└─$ python3 -c "
with open('image.jpg', 'rb') as f:
    data = f.read()
import re
match = re.search(b'2d2d2d2d2d424547494e[0-9a-fA-F]+', data).group()
with open('private.key', 'wb') as out:
    out.write(bytes.fromhex(match.decode()))
"

┌──(kali㉿kali)-[~]
└─$ openssl pkeyutl -decrypt -inkey private.key -in flag.enc
academy{rs4_k3y_1n_1mg_21d0a083}
```

### Notas adicionales
- Al inspeccionar los metadatos y cadenas imprimibles dentro de `image.jpg`, se descubre un bloque hexadecimal extenso.
- Los bytes `2d 2d 2d 2d 2d 42 45 47 49 4e 20 50 52 49 56 41 54 45 20 4b 45 59` corresponden en ASCII a `-----BEGIN PRIVATE KEY`.
- Se convierte la cadena hexadecimal a texto plano obteniendo el archivo PEM de la clave privada (`private.key`).
- Con OpenSSL (`pkeyutl -decrypt -inkey private.key -in flag.enc`) se descifra `flag.enc`, revelando la bandera.

### Referencias
- [OpenSSL pkeyutl](https://www.openssl.org/docs/man1.1.1/man1/pkeyutl.html)
