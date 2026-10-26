### Descripción
Can you decrypt this message? Decrypt this [message](https://challenge-files.cylabacademy.net/library/848831bc0df5e68fe8f320c91c47f635bce35a7c8236c696f9478bfaf39cfd10/cipher.txt) using this key "CYLAB".

### Solución
```
Aplicando los desplazamientos de la clave **C-Y-L-A-B** (2, 24, 11, 0, 1) iterativamente solo sobre las letras del texto:

- **Prefijo (`caldfow`):**
    
    - c - 2 (C) = a
        
    - a - 24 (Y) = c
        
    - l - 11 (L) = a
        
    - d - 0 (A) = d
        
    - f - 1 (B) = e
        
    - o - 2 (C) = m
        
    - w - 24 (Y) = y
        
    - Resultado: `academy`
        
- **Cuerpo de la bandera (`O0NU_WQ3_G1G3O3T3_A1AH3S`):**
    
    - O - 11 (L) = D | N - 0 (A) = N | U - 1 (B) = T _(Los números y guiones mantienen su lugar)_ -> `D0NT`
        
    - W - 2 (C) = U | Q - 24 (Y) = S -> `US3`
        
    - G - 11 (L) = V | G - 0 (A) = G | O - 1 (B) = N | T - 2 (C) = R -> `V1G3N3R3`
        
    - A - 24 (Y) = C | A - 11 (L) = P | H - 0 (A) = H | S - 1 (B) = R -> `C1PH3R`
        
- **Sufijo final (`42eaff9d`):**
    
    - e - 2 (C) = c
        
    - a - 24 (Y) = c
        
    - f - 11 (L) = u
        
    - f - 0 (A) = f
        
    - d - 1 (B) = c
        
    - Resultado: `42ccuf9c`
        

Al unir todas las partes decodificadas respetando los números, guiones y corchetes originales, obtienes tu bandera:

**`academy{D0NT_US3_V1G3N3R3_C1PH3R_42ccuf9c}`**
```

### Notas adicionales


### Referencias
