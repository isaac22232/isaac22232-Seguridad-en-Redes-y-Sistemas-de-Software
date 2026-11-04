### Descripción
A message was encrypted using a shared secret... but it looks like one side of the exchange leaked something. Can you piece together the secret and get the flag? Download the [message](https://challenge-files.cylabacademy.net/library/0c5716023de07c8f5e39852dad85c3c416bb8de0fb7fb3216ae79dd5bf1a58e3/message.txt). And source [code](https://challenge-files.cylabacademy.net/library/0c5716023de07c8f5e39852dad85c3c416bb8de0fb7fb3216ae79dd5bf1a58e3/encryption.py)

	Hints
	1 What do you get if you combine a public key with a known private one?

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat encryption.py | grep -E "shared|enc ="
shared = pow(A, b, p)
enc = bytes([x ^ (shared % 256) for x in flag])

┌──(kali㉿kali)-[~]
└─$ python3 -c "
with open('message.txt') as f:
    lines = dict(line.split(' = ') for line in f.read().splitlines() if ' = ' in line)

p = int(lines['p'])
A = int(lines['A'])
b = int(lines['b'])
enc = bytes.fromhex(lines['enc'])

shared = pow(A, b, p)
key = shared % 256
flag = bytes([x ^ key for x in enc])
print(flag.decode())
"
academy{dh_s3cr3t_913ddd75}
```

### Notas adicionales
- El reto implementa el intercambio de claves Diffie-Hellman:
  - Parámetros públicos: $g$, $p$.
  - Clave pública del servidor: $A \equiv g^a \pmod p$.
  - Clave privada del cliente: $b$.
- El archivo `message.txt` proporciona directamente los valores de $p$, $A$, $b$ y el texto cifrado `enc`.
- Con la clave pública del servidor $A$ y la clave privada del cliente $b$, se calcula el secreto compartido:
  $$\text{shared} \equiv A^b \pmod p$$
- La clave de cifrado simétrico es $\text{key} = \text{shared} \pmod{256}$, que al aplicarse mediante XOR contra los bytes de `enc` recupera la bandera en texto plano.

### Referencias
- [Diffie-Hellman key exchange](https://en.wikipedia.org/wiki/Diffie%E2%80%93Hellman_key_exchange)
