### Descripción
An attacker was able to intercept communications between a bank and a fintech company. They managed to get the [message](https://challenge-files.cylabacademy.net/library/0d44678c5a09bacc6d0ff4226f7ed3e66bc9f62c37de7a58fc588bad8eb76f88/secret.enc) (ciphertext) and the [password](https://challenge-files.cylabacademy.net/library/0d44678c5a09bacc6d0ff4226f7ed3e66bc9f62c37de7a58fc588bad8eb76f88/password.enc) that was used to encrypt the message. After some intensive reconassainance they found out that the bank has an oracle that was used to encrypt the password and can be found here `nc xebec.cylabacademy.net 23299`. Decrypt the password and use it to decrypt the message. The oracle can decrypt anything except the password.

	Hints
	1 Cryptography Threat models: chosen plaintext attack.
	2 OpenSSL can be used to decrypt the message. e.g `openssl enc -aes-256-cbc -d ...`
	3 The key to getting the flag is by sending a custom message to the server by taking advantage of the RSA encryption algorithm.
	4 Minimum requirements for a useful cryptosystem is CPA security.

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat password.enc
229790027447939649384780243053157276621760946675886654979990150188281873809819082258366413541859653254597024114291891290777358488784916151635421532417233

┌──(kali㉿kali)-[~]
└─$ nc xebec.cylabacademy.net 23299
*****************************************
****************THE ORACLE***************
*****************************************
what should we do for you? 
E --> encrypt D --> decrypt. 
E
enter text to encrypt (encoded length must be less than keysize): 
 

encoded cleartext as Hex m: 2

ciphertext (m ^ e mod n) 5067313465613043651275429665315895824157755779222372979446076012356324498190828210335763979330272318657269048435311897896433721115606764442199497891219230

what should we do for you? 
E --> encrypt D --> decrypt. 
D
Enter text to decrypt: 
1164418042456019556108197177579893922339598813247488059739504820257762699313204900742584164130097746208083610931558229415569429158309193796502264639908351543160840502267853110912185585098275528893910302324204481061986423984185124978949829986345672236968038758824191147572718105747683935266851609167731778941460

decrypted ciphertext as hex (c ^ d mod n): 6460666e66
decrypted ciphertext: d`fnf

what should we do for you? 
E --> encrypt D --> decrypt. 
^C

┌──(kali㉿kali)-[~]
└─$ python3 -c "
val = int('6460666e66', 16)
m = val // 2
print(bytes.fromhex(hex(m)[2:]).decode())
"
20373

┌──(kali㉿kali)-[~]
└─$ openssl enc -aes-256-cbc -d -in secret.enc -k 20373
*** WARNING : deprecated key derivation used.
Using -iter or -pbkdf2 would be better.
academy{su((3ss_(r@ck1ng_r3@_20373ec2}
```

### Notas adicionales
- Debido a la propiedad multiplicativa (homomórfica) de RSA sin relleno (*textbook RSA*):
  $$E(m_1) \times E(m_2) \equiv (m_1 \times m_2)^e \pmod n$$
- Como el oráculo se niega a desencriptar directamente el valor de `password.enc` ($c$), podemos pedirle que encripte un valor conocido como el byte `2` (lo que nos da $c_2 = 2^e \pmod n$).
- Multiplicamos ambos textos cifrados:
  $$c' = c \times c_2 = (m \times 2)^e \pmod n$$
- Enviamos $c'$ al oráculo para desencriptar. Al ser diferente de $c$, el oráculo lo desencripta sin restricción y devuelve el valor hexadecimal de $(2 \times m)$.
- Dividiendo el resultado entre 2 se recupera la contraseña en claro: `20373`.
- Finalmente, se descifra el archivo `secret.enc` mediante OpenSSL usando la contraseña obtenida.

### Referencias
- [RSA Chosen Ciphertext Attack](https://crypto.stackexchange.com/questions/2323/how-does-a-chosen-ciphertext-attack-on-rsa-work)
- [OpenSSL enc manual](https://www.openssl.org/docs/man1.1.1/man1/openssl-enc.html)
