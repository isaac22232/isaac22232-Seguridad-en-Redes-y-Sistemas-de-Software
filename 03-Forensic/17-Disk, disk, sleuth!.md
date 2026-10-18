### Descripción
Use `srch_strings` from the sleuthkit and some terminal-fu to find a flag in this disk image. [dds1-alpine.flag.img.gz](https://challenge-files.cylabacademy.net/library/34106bdd624e0aec8af0ba0e9c52e7fd45d5d1415761ffc98b2130cace440057/dds1-alpine.flag.img.gz)

### Solución
```
┌──(kali㉿kali)-[~/image_s]
└─$ srch_strings dds1-alpine.flag.img | grep academy
  SAY academy{f0r3ns1c4t0r_n30phyt3_6502313d}


```
### Notas adicionales


### Referencias
