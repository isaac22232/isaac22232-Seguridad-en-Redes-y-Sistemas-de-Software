### Descripción
A second message has come in the mail, and it seems almost identical to the first one. Maybe the same thing will work again. Download the message [here](https://challenge-files.cylabacademy.net/library/7bfa985513e099d32240b37e499262d5fb6147c074a8ee5ecd932c14deb05ac7/message.txt).

### Solución
```
Al aplicar este mapeo monoalfabético a lo largo de todo el texto (por ejemplo, T=C, H=F, L=R), obtenemos las letras necesarias para descifrar la cadena contenida dentro de las llaves al final del documento (`HL3MC3RTB_4774TN5_4L3_T001_7S0043K0`):

TXT

- **HL3MC3RTB** se traduce como `FR3QU3NCY` (H=F, L=R, M=Q, C=U, R=N, T=C, B=Y).
    
- **4774TN5** se traduce como `4774CK5` (T=C, N=K).
    
- **4L3** se traduce como `4R3` (L=R).
    
- **T001** se traduce como `C001` (T=C).
    
- **7S0043K0** se traduce como `7B0043A0` (S=B, K=A).
    

Uniendo todas las partes decodificadas, la bandera final es:

**`academy{FR3QU3NCY_4774CK5_4R3_C001_7B0043A0}`**
```

### Notas adicionales


### Referencias
