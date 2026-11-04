### Descripción
Can you find the flag in this disk image? Wrap what you find in the academy{} flag format. Download the disk image [here](https://challenge-files.cylabacademy.net/library/bf9a20c350075c5863371e078daee1d570d4062902edc8a4a042e02a7cebf161/partition4.img.gz).

	Hints
	1 Create a Sleuthkit MAC timeline!
	2 Sloppy timestomping can yield strange (very old) timestamps

### Solución
```
┌──(kali㉿kali)-[~]
└─$ gzip -d partition4.img.gz

┌──(kali㉿kali)-[~]
└─$ fls -m / -r partition4.img > body.txt

┌──(kali㉿kali)-[~]
└─$ mactime -b body.txt -d -y 1970-01-01 | head -n 5
Date,Size,Type,Mode,UID,GID,Meta,File Name
1985-01-01T17:00:00Z,41,macb,r/rrw-r--r--,0,0,4945,"/bin/bcab"
2021-10-18T17:54:17Z,451,ma..,r/rrw-r--r--,0,0,64994,"/usr/share/apk/keys/alpine-devel@lists.alpinelinux.org-4a6a0840.rsa.pub"
2021-10-18T17:54:17Z,451,ma..,r/rrw-r--r--,0,0,64995,"/usr/share/apk/keys/alpine-devel@lists.alpinelinux.org-5243ef4b.rsa.pub"

┌──(kali㉿kali)-[~]
└─$ icat partition4.img 4945
NzFtMzExbjNfMHU3MTEzcl9oM3JfNDNhMmU3YWYK

┌──(kali㉿kali)-[~]
└─$ echo "NzFtMzExbjNfMHU3MTEzcl9oM3JfNDNhMmU3YWYK" | base64 -d
71m311n3_0u7113r_h3r_43a2e7af

academy{71m311n3_0u7113r_h3r_43a2e7af}
```

### Notas adicionales
- Se descomprime la imagen de disco con `gzip -d`.
- Siguiendo la pista sobre timestomping con marcas de tiempo anómalas muy antiguas, se crea un archivo de cuerpo con `fls -m / -r partition4.img > body.txt` y se procesa con `mactime`.
- El primer archivo en la línea temporal es `/bin/bcab` (inodo 4945) con fecha `1985-01-01`.
- Extrayendo el contenido del inodo con `icat partition4.img 4945` se obtiene una cadena en base64. Al decodificarla y envolverla en el formato `academy{}`, se completa el reto.

### Referencias
- [Sleuthkit fls tool](https://wiki.sleuthkit.org/index.php?title=Fls)
- [Sleuthkit mactime tool](https://wiki.sleuthkit.org/index.php?title=Mactime)
- [Sleuthkit icat tool](https://wiki.sleuthkit.org/index.php?title=Icat)