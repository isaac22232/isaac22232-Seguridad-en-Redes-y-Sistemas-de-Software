### Descripción
Oops! I have a typo in my first message so i sent it again! I used RSA twice so this is secure right? [chall.py](https://challenge-files.cylabacademy.net/library/d33371f1a01fd9671ac08d9ce0a486325fd0e8ed66ce83fc97ee9a5a07a64cb9/chall.py) [output.txt](https://challenge-files.cylabacademy.net/library/d33371f1a01fd9671ac08d9ce0a486325fd0e8ed66ce83fc97ee9a5a07a64cb9/output.txt)

	Hints
	1 How are the two messages related?
	2 Franklin Reiter _______ _______ attack.

### Solución
```
┌──(kali㉿kali)-[~]
└─$ cat chall.py
from Crypto.Util.number import getPrime, inverse, bytes_to_long, long_to_bytes, GCD

Message = bytes_to_long(b"[redacted]")
Message_fixed = bytes_to_long(b"[redacted]")
e = 0x11
p = getPrime(1024)
q = getPrime(1024)
phi = (p-1) * (q-1)
d = inverse(e, phi)
N = p*q

ciphertext = pow(Message, e, N)
ciphertext2 = pow(Message_fixed, e, N)

print(ciphertext, ciphertext2)
print(Message - Message_fixed)
print(N)

┌──(kali㉿kali)-[~]
└─$ # Ataque Franklin-Reiter para mensajes relacionados: f1(x) = x^e - c1, f2(x) = (x - diff)^e - c2
┌──(kali㉿kali)-[~]
└─$ python3 -c "
import math
from Crypto.Util.number import long_to_bytes

with open('output.txt') as f:
    lines = f.read().splitlines()

c1 = int(lines[0])
c2 = int(lines[1])
diff = int(lines[2])  # -3
N = int(lines[3])
e = 17

f1 = [0] * (e + 1)
f1[0] = 1
f1[-1] = (-c1) % N

f2 = [0] * (e + 1)
delta = (-diff) % N
for k in range(e + 1):
    f2[k] = (math.comb(e, k) * pow(delta, k, N)) % N
f2[-1] = (f2[-1] - c2) % N

def poly_clean(p):
    while len(p) > 1 and p[0] % N == 0:
        p = p[1:]
    return [c % N for c in p]

def poly_divmod(a, b):
    a = poly_clean(a)
    b = poly_clean(b)
    if len(a) < len(b): return [0], a
    inv_b = pow(b[0], -1, N)
    rem = list(a)
    while len(rem) >= len(b):
        factor = (rem[0] * inv_b) % N
        for i in range(len(b)):
            rem[i] = (rem[i] - factor * b[i]) % N
        rem = poly_clean(rem)
        if len(rem) == 1 and rem[0] == 0: break
    return [], rem

def poly_gcd(a, b):
    while len(b) > 1 or (len(b) == 1 and b[0] != 0):
        _, rem = poly_divmod(a, b)
        a, b = b, rem
    return a

g = poly_gcd(f1, f2)
m = (-g[1] * pow(g[0], -1, N)) % N

# Message_fixed = Message - diff = Message + 3
m_fixed = m - diff
print(long_to_bytes(m_fixed).decode())
"
academy{m3ssage_w1th_typ0}
```

### Notas adicionales
- Se trata del ataque de mensajes relacionados de Franklin-Reiter (*Franklin-Reiter Related Message Attack*).
- Dos mensajes relacionados linealmente ($M_2 = M_1 + \delta$, donde $\delta = -\text{diff} = 3$) fueron cifrados con la misma clave pública RSA ($N, e=17$).
- Definimos los polinomios en $\mathbb{Z}_N[x]$:
  $$f_1(x) = x^e - c_1 \pmod N$$
  $$f_2(x) = (x + 3)^e - c_2 \pmod N$$
- El máximo común divisor $\gcd(f_1, f_2)$ en $\mathbb{Z}_N[x]$ resulta en un polinomio lineal mónico $x - M_1 \pmod N$.
- Evaluando la raíz encontramos $M_1 = \text{academy\{m3ssage\_w1th\_typ0z}$ y sumando $\delta=3$ corregimos el error tipográfico (`z` $\to$ `}`), obteniendo la bandera final: `academy{m3ssage_w1th_typ0}`.

### Referencias
- [Franklin-Reiter Related Message Attack](https://en.wikipedia.org/wiki/Coppersmith%27s_attack#Franklin%E2%80%93Reiter_related-message_attack)
