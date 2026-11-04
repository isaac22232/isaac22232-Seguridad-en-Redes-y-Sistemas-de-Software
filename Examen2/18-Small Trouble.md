### Descripción
Everything seems secure; strong numbers, familiar parameters but something small might ruin it all. Can you recover the message? Download the [message](https://challenge-files.cylabacademy.net/library/3a16f68729491af8a7840a7cc2a1244c8d49b8da749f91330e5cf92516820f1f/message.txt). And source [code](https://challenge-files.cylabacademy.net/library/3a16f68729491af8a7840a7cc2a1244c8d49b8da749f91330e5cf92516820f1f/encryption.py)

	Hints
	1 This might be a job for Boneh-Durfee.

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat "encryption.py" | grep -E "getPrime|inverse"
p = getPrime(1048)
q = getPrime(1048)
d = getPrime(256)
e = inverse(d, phi)

┌──(kali㉿kali)-[~]
└─$ # El módulo n tiene 2096 bits pero d solo 256 bits (d < 1/3 * n^(1/4)), vulnerable al ataque de Wiener mediante fracciones continuadas:
┌──(kali㉿kali)-[~]
└─$ python3 -c "
import math
from Crypto.Util.number import long_to_bytes

with open('message (1).txt') as f:
    lines = dict(line.split(' = ') for line in f.read().splitlines() if ' = ' in line)

n = int(lines['n'])
e = int(lines['e'])
c = int(lines['c'])

def continued_fraction(num, den):
    res = []
    while den != 0:
        q = num // den
        res.append(q)
        num, den = den, num - q * den
    return res

def convergents(cf):
    n0, n1 = 0, 1
    d0, d1 = 1, 0
    for q in cf:
        n0, n1 = n1, q * n1 + n0
        d0, d1 = d1, q * d1 + d0
        yield n1, d1

for k, d in convergents(continued_fraction(e, n)):
    if k == 0 or (e * d - 1) % k != 0:
        continue
    phi = (e * d - 1) // k
    b = n - phi + 1
    discr = b * b - 4 * n
    if discr >= 0 and math.isqrt(discr)**2 == discr:
        m = pow(c, d, n)
        print(long_to_bytes(m).decode())
        break
"
academy{sm4ll_d_073963cb}
```

### Notas adicionales
- El script de generación utiliza primos de 1048 bits ($n \approx 2096$ bits), pero el exponente privado $d$ se generó con solo 256 bits (`d = getPrime(256)`).
- De acuerdo con el teorema de Wiener, si $d < \frac{1}{3} n^{1/4}$, las convergentes de la fracción continua de $\frac{e}{n}$ contienen la fracción $\frac{k}{d}$.
- Como $256 < \frac{2096}{4} = 524$ bits, el ataque de Wiener tiene éxito de forma instantánea, permitiendo recuperar $d$ y descifrar el mensaje cifrado $c$.

### Referencias
- [Wiener's attack on RSA](https://en.wikipedia.org/wiki/Wiener%27s_attack)
- [Cryptanalytic Attacks on RSA - Boneh](https://crypto.stanford.edu/~dabo/papers/rsa-survey.pdf)
