### Descripción
This service provides you an encrypted flag. Can you decrypt it with just N & e?

### Solución
```
# Valores del reto
N = 14289403731993452018291608760489751062578351671004376261061061350509950099157542931399507605801157129161450350964320222784809933953795837752192033097733134
e = 65537
cyphertext = 9642025770200338812406661737639261583974429539035846204797580345803233010444275718638598670386908520641552908860062574710162140907028445507129736537254657

# 1. Vulnerabilidad del RSA par
p = 2
q = N // 2

# 2. Calculamos la llave privada (d) usando la función pow nativa de Python
phi = (p - 1) * (q - 1)
d = pow(e, -1, phi)

# 3. Desciframos el mensaje matemático
m = pow(cyphertext, d, N)

# 4. Convertimos el entero gigante a texto ASCII (reemplazando long_to_bytes)
flag = m.to_bytes((m.bit_length() + 7) // 8, byteorder='big').decode('utf-8')

print(f"[+] Valor de p: {p}")
print(f"[+] Valor de q: {q}")
print(f"\n[+] Bandera capturada: {flag}")

[+] Valor de p: 2
[+] Valor de q: 7144701865996726009145804380244875531289175835502188130530530675254975049578771465699753802900578564580725175482160111392404966976897918876096016548866567

[+] Bandera capturada: academy{tw0_1$_pr!m3207f407f}

```

### Notas adicionales


### Referencias
