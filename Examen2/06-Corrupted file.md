### Descripción
This file seems broken... or is it? Maybe a couple of bytes could make all the difference. Can you figure out how to bring it back to life? Download the file [here](https://challenge-files.cylabacademy.net/library/cefad24659aa422bb4e57016eda1c098a0e8f3e83fbf006b58c235ca0440cb9e/file).

Hints

	1 Try checking the file’s header.

	2 JPEG

	3 Tools like xxd or hexdump can help you inspect and edit file bytes.

### Solución
```
┌──(kali㉿kali)-[~]
└─$ xxd file | head -n 3
00000000: 5c78 ffe0 0010 4a46 4946 0001 0100 0001  \x....JFIF......
00000010: 0001 0000 ffdb 0043 0008 0606 0706 0508  .......C........
00000020: 0707 0708 0808 0a0c 140d 0c0b 0b0c 1912  ................

┌──(kali㉿kali)-[~]
└─$ # Los primeros dos bytes son 5c 78 (\x) en lugar de ff d8 (cabecera mágica de JPEG)
┌──(kali㉿kali)-[~]
└─$ printf '\xff\xd8' | dd of=file conv=notrunc bs=1 count=2
2+0 records in
2+0 records out
2 bytes copied, 0.00018 s, 11.1 kB/s

┌──(kali㉿kali)-[~]
└─$ file file
file: JPEG image data, JFIF standard 1.01, resolution (DPI), density 1x1, segment length 16, baseline, precision 8, 800x500, components 3

┌──(kali㉿kali)-[~]
└─$ mv file repaired.jpg
┌──(kali㉿kali)-[~]
└─$ # Al abrir repaired.jpg con un visor de imágenes se muestra la bandera:
academy{r3st0r1ng_th3_by73s_d28873c8}
```

### Notas adicionales
- Al inspeccionar el archivo con `xxd`, se observa la estructura de un archivo JFIF (`JFIF`), pero los primeros dos bytes están corrompidos con `5c 78` (`\x`) en lugar de los números mágicos estándar de JPEG `ff d8`.
- Modificando los dos primeros bytes a `\xff\xd8` mediante `dd` o un editor hexadecimal (como `hexedit` o `xxd`), la imagen se repara y se puede visualizar normalmente para leer la bandera.

### Referencias
- [List of file signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)
- [dd man page](https://linux.die.net/man/1/dd)