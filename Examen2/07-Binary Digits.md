### Descripción
This file doesn't look like much... just a bunch of 1s and 0s. But maybe it's not just random noise. Can you recover anything meaningful from this? Download the file [here](https://challenge-files.cylabacademy.net/library/6ba8983da0e17a2e2015a530788849e9c9c0bc3393d62fa3f9a06ce8068567c8/digits.bin).

### Solución
```
┌──(kali㉿kali)-[~]
└─$ head -c 64 digits.bin
1111111111011000111111111110000000000000000100000100101001000110

┌──(kali㉿kali)-[~]
└─$ # Agrupando cada 8 bits:
└─$ # 11111111 (0xFF), 11011000 (0xD8), 11111111 (0xFF), 11100000 (0xE0) -> Cabecera JPEG

┌──(kali㉿kali)-[~]
└─$ python3 -c "
with open('digits.bin') as f:
    s = f.read().strip()
data = bytes([int(s[i:i+8], 2) for i in range(0, len(s), 8)])
with open('recovered.jpg', 'wb') as out:
    out.write(data)
"

┌──(kali㉿kali)-[~]
└─$ file recovered.jpg
recovered.jpg: JPEG image data, JFIF standard 1.01, resolution (DPI), density 1x1, segment length 16, baseline, precision 8, 800x500, components 3

┌──(kali㉿kali)-[~]
└─$ # Al abrir recovered.jpg con un visor de imágenes se muestra la bandera:
academy{h1dd3n_1n_th3_b1n4ry_6d751a5b}
```

### Notas adicionales
- El archivo contiene una secuencia continua de caracteres ASCII '0' y '1'.
- Al agrupar los bits en bloques de 8 (1 byte), los primeros 4 bytes corresponden a `11111111 11011000 11111111 11100000`, es decir `FF D8 FF E0`, que identifican el encabezado JFIF/JPEG.
- Con un script de Python se convierten los bits binarios a sus bytes correspondientes y se guardan como `recovered.jpg`, donde se encuentra la bandera visualmente.

### Referencias
- [Python int(s, 2) documentation](https://docs.python.org/3/library/functions.html#int)