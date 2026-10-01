### Descripción
We found this [file](https://challenge-files.cylabacademy.net/library/8388ecc430588d15064755583476bec46e23d42a6d8de6e8995c19e40f2e4c58/c0rrupt-mystery). Recover the flag.

### Solución

**1. Inspección de la cabecera.** Los primeros bytes son:

```
89 65 4e 34 0d 0a b0 aa 00 00 00 0d 43 22 44 52 ...
```

La estructura recuerda a un PNG: hay un chunk de longitud 13 (`00 00 00 0d`) seguido de algo parecido a `IHDR`, y más adelante aparecen cadenas como `sRGB`, `gAMA`, `pHYs`, `IDAT` e `IEND`. El archivo es un PNG con bytes alterados.

**2. Corrección de la firma y de `IHDR`.**

|   |   |   |   |
|---|---|---|---|
|Offset|Valor corrupto|Valor correcto|Elemento|
|0x00–0x07|`89 65 4e 34 0d 0a b0 aa`|`89 50 4e 47 0d 0a 1a 0a`|Firma PNG|
|0x0C–0x0F|`43 22 44 52` (`C"DR`)|`49 48 44 52` (`IHDR`)|Tipo del primer chunk|

**3. Validación de chunks con CRC32.** Tras esa primera corrección, un script que recorre cada chunk (longitud, tipo, datos, CRC) mostró que `IHDR`, `sRGB` y `gAMA` eran válidos, pero `pHYs` fallaba. Cada chunk PNG tiene la forma `[longitud 4 B][tipo 4 B][datos][CRC 4 B]`, y el CRC cubre tipo y datos, así que sirve para confirmar si una reparación es correcta.

**4. Reparación de `pHYs`.** Los datos del chunk eran `aa 00 16 25 00 00 16 25 01`. Los valores de píxeles por unidad son `00 00 16 25` (5669) en ambos ejes, por lo que el primer byte `aa` debía ser `00` (offset 0x46). Con ese cambio el CRC coincidió.

**5. Reparación del primer `IDAT`.** Los bytes `aa aa ff a5 ab 44 45 54` (offset 0x53) contenían longitud y tipo corruptos. El tipo debía ser `IDAT` (`49 44 41 54`). Para la longitud, el siguiente chunk empezaba en el offset 65536 y los datos comenzaban en el 91, de modo que la longitud era 65536 − 91 = 65445 = `0xffa5`. Los dos últimos bytes de la longitud dañada ya eran `ff a5`, lo que confirma la deducción. Quedó `00 00 ff a5 49 44 41 54`.

**6. Verificación.** Con los cuatro `IDAT` e `IEND` con CRC correcto, la imagen se abrió sin errores (1642×1095 px). La flag aparece escrita sobre unos garabatos rojos.

Script resumido de la reparación:

```python
import struct, zlib
d = bytearray(open('c0rrupt-mystery','rb').read())
d[:8] = bytes.fromhex('89504e470d0a1a0a')   # firma PNG
d[12:16] = b'IHDR'                          # tipo del primer chunk
d[70] = 0x00                                # pHYs: primer byte de datos
d[83:91] = struct.pack('>I', 0xffa5) + b'IDAT'  # longitud y tipo del primer IDAT
open('fixed.png','wb').write(d)
```

**Flag:** `academy{c0rrupt10n_1847995}`
### Notas adicionales


### Referencias
