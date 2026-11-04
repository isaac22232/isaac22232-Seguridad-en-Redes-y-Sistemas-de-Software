### Descripción
The SOC team discovered a suspiciously large log file after a recent breach. When they opened it, they found an enormous block of encoded text instead of typical logs. Could there be something hidden within? Your mission is to inspect the resulting file and reveal the real purpose of it. The team is relying on your skills to uncover any concealed information within this unusual log. Download the encoded data here: [Logs Data](https://challenge-files.cylabacademy.net/library/8389f7eb8ae95fd4453f1e2d27498905b415efec5fc738bfd0983d56c09959bf/logs.txt). Be prepared—the file is large, and examining it thoroughly is crucial .

### Solución
```
┌──(kali㉿kali)-[~]
└─$ head -c 30 logs.txt
iVBORw0KGgoAAAANSUhEUgAAA4AAAA

┌──(kali㉿kali)-[~]
└─$ base64 -d logs.txt > decoded.png

┌──(kali㉿kali)-[~]
└─$ file decoded.png
decoded.png: PNG image data, 896 x 1152, 8-bit/color RGB, non-interlaced

┌──(kali㉿kali)-[~]
└─$ # Al abrir la imagen generada, en la parte inferior aparece una cadena en hexadecimal:
└─$ # 61636164656D797B666F72656E736963735F616E616C797369735F69735F616D617A696E675F64666332623462397D

┌──(kali㉿kali)-[~]
└─$ echo "61636164656D797B666F72656E736963735F616E616C797369735F69735F616D617A696E675F64666332623462397D" | xxd -r -p
academy{forensics_analysis_is_amazing_dfc2b4b9}
```

### Notas adicionales
- El archivo `logs.txt` contiene un bloque base64 que comienza con la cabecera mágica de una imagen PNG (`iVBORw0KGgo...` -> `\x89PNG`).
- Al decodificar el contenido a formato PNG (`base64 -d logs.txt > decoded.png`), se obtiene una ilustración de un hacker frente a su laptop.
- En la esquina inferior izquierda de la imagen se encuentra un texto en hexadecimal que, convertido a texto con `xxd -r -p`, revela la bandera.

### Referencias
- [PNG Magic Bytes](https://en.wikipedia.org/wiki/PNG)
- [xxd man page](https://linux.die.net/man/1/xxd)