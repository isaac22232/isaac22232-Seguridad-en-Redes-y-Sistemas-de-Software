### Descripcion
Can you break into this super secure portal?

### Solucion
```
picoCTF{not_this_again_4daf93}


```

### Notas adicionales
- **Análisis del Arreglo Ofuscado:** El script inicializa un arreglo (`_0x5a46`) que contiene los fragmentos de la bandera y funciones de JavaScript desordenadas. A continuación, una función anónima (IIFE) ejecuta un bucle `while` que rota los elementos del arreglo 435 veces (el valor hexadecimal `0x1b3`) mediante métodos `shift()` y `push()`, devolviendo el arreglo a su orden lógico.
    
- **Mapeo de Funciones y Variables:** El código utiliza una función traductora (`_0x4b5b`) para llamar a los elementos del arreglo ya ordenado. Por ejemplo, la llamada `_0x4b5b('0x2')` se traduce como la función `'substring'`, y `_0x4b5b('0x0')` como `'getElementById'`.
    
- **Resolución de la Lógica Matemática:** Al traducir el código ofuscado, se revela una serie de condiciones `if` anidadas que validan la contraseña usando `substring()`. El tamaño base de los bloques está definido por la variable `split = 4`. Al resolver las operaciones matemáticas en hexadecimal de las posiciones, se determinó el rango de cada fragmento.
    
- **Filtrado de Ruido y Ensamblaje:** El código ofuscado incluye validaciones redundantes (ej. comprobar la posición 7 a 9) para generar "ruido" y confundir el análisis. Ignorando estas comprobaciones falsas y ordenando los 4 bloques principales de 8 caracteres cada uno, la estructura real es la siguiente:
    
    - Posición 0 a 8 (`split*0x2`): **`picoCTF{`**
        
    - Posición 8 a 16 (`split*0x2*0x2`): **`not_this`**
        
    - Posición 16 a 24 (`split*0x3*0x2`): **`_again_4`**
        
    - Posición 24 a 32 (`split*0x4*0x2`): **`daf93}`**

### Referencias
