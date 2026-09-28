### Descripción
This file contains more than it seems. Get the flag from [garden.jpg](https://challenge-files.cylabacademy.net/library/3c60c5a7f7a8067606c51d4b4b3c7913fae709b11e2f2c7adbc0a0b4cda452ff/garden.jpg).

### Solución
```
┌──(kali㉿kali)-[~]
└─$ strings -n 20 garden.jpg
Copyright (c) 1998 Hewlett-Packard Company
IEC http://www.iec.ch
IEC http://www.iec.ch
.IEC 61966-2.1 Default RGB colour space - sRGB
.IEC 61966-2.1 Default RGB colour space - sRGB
,Reference Viewing Condition in IEC61966-2.1
,Reference Viewing Condition in IEC61966-2.1
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
&'()*56789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
Here is a flag: academy{more_than_m33ts_the_3y3ff3b9e86}

```

### Notas adicionales
xxd: que crea **volcados hexadecimales** de archivos o entrada estándar y también puede revertir un volcado hexadecimal a su forma **binaria** original.
| more: va dando por partes el resultado

### Referencias