### Descripcion
Can you break into this super secure portal?

### Solucion
```
picoCTF{no_clients_plz_2eb02b45}
```

### Notas adicionales

- **Inspección del Código Fuente:** Se auditó el código fuente de la página web (HTML y JavaScript) directamente desde el navegador. Al estar expuesto públicamente del lado del cliente, se localizó rápidamente la función de validación `verify()`, la cual es la encargada de verificar la contraseña que ingresa el usuario.
    
- **Análisis de la Lógica de Fragmentación:** Al revisar el interior de la función `verify()`, se detectó que la contraseña (la bandera) estaba codificada en texto plano (hardcoded). Sin embargo, para intentar ocultarla, el desarrollador la dividió en múltiples fragmentos desordenados utilizando la función `substring()` y una variable base definida como `split = 4`.
    
- **Ordenamiento de los Bloques Lógicos:** Para reconstruir la contraseña correcta, se extrajeron todas las sentencias `if` anidadas y se ordenaron secuencialmente calculando los multiplicadores matemáticos de la variable `split`. El desglose secuencial exacto es el siguiente:
    
    - Posición 0 a 4 (`0, split`): **`pico`**
        
    - Posición 4 a 8 (`split, split*2`): **`CTF{`**
        
    - Posición 8 a 12 (`split*2, split*3`): **`no_c`**
        
    - Posición 12 a 16 (`split*3, split*4`): **`lien`**
        
    - Posición 16 a 20 (`split*4, split*5`): **`ts_p`**
        
    - Posición 20 a 24 (`split*5, split*6`): **`lz_2`**
        
    - Posición 24 a 28 (`split*6, split*7`): **`eb02`**
        
    - Posición 28 a 32 (`split*7, split*8`): **`b45}`**
        
- **Ensamblaje Final:** Al concatenar sistemáticamente todos los fragmentos extraídos de la lógica expuesta, desde la posición 0 hasta la 32, se reconstruyó la credencial completa sin necesidad de ejecutar el script.
### Referencias
