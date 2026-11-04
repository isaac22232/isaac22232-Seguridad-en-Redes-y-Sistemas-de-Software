### Descripción
Can you find the flag in this disk image? Wrap what you find in the academy{} flag format. Download the disk image [here](https://challenge-files.cylabacademy.net/library/0b369ed5974a5e777ca3bc323bd39d75a6f27762a449d16cd2a0ffc08b2a6aa8/timeline-1-partition4.img.gz).

	Hints
	1 Create a Sleuthkit MAC timeline!
	2 Look at recent timestamps
	3 Pay close attention to timestamps near an anti-forensic action
	4 Filter only new files by grepping for `macb`

### Solución
```
┌──(kali㉿kali)-[~]
└─$ gzip -d timeline-1-partition4.img.gz

┌──(kali㉿kali)-[~]
└─$ fls -m / -r timeline-1-partition4.img > body.txt

┌──(kali㉿kali)-[~]
└─$ mactime -b body.txt -d | grep "macb" | tail -n 10
Mon Dec 01 2025 15:50:07,49,macb,r/rrw-r--r--,0,0,32716,"/etc/chat"
Mon Dec 01 2025 15:50:23,1024,macb,d/drwxr-xr-x,0,0,33017,"/lib/rc/cache"
Mon Dec 01 2025 15:50:23,8,macb,r/rrw-r--r--,0,0,33020,"/lib/rc/cache/softlevel"
Mon Dec 01 2025 15:50:23,9,macb,r/rrw-------,0,0,4943,"/root/.ash_history"
Mon Dec 01 2025 15:50:23,32,macb,r/rr--------,0,0,65278,"/var/lib/seedrng/seed.credit"

┌──(kali㉿kali)-[~]
└─$ # Justo después del archivo /etc/chat (inodo 32716) a las 15:50:07, se ejecutó shred (/usr/bin/shred) a las 15:50:20

┌──(kali㉿kali)-[~]
└─$ icat timeline-1-partition4.img 32716
NTczNDE3aDEzcl83aDRuXzdoM18xNDU3XzU4NTI3YmIyMjIK

┌──(kali㉿kali)-[~]
└─$ echo "NTczNDE3aDEzcl83aDRuXzdoM18xNDU3XzU4NTI3YmIyMjIK" | base64 -d
573417h13r_7h4n_7h3_1457_58527bb222

academy{573417h13r_7h4n_7h3_1457_58527bb222}
```

### Notas adicionales
- Se genera la línea de tiempo forense con `fls` y `mactime`.
- Siguiendo las pistas, se filtran los eventos con atributos `macb` más recientes.
- A las `15:50:07` se creó/modificó el archivo `/etc/chat` (inodo 32716), e inmediatamente después a las `15:50:20` se accedió a `/usr/bin/shred` (acción antiforense).
- Al extraer el contenido del inodo 32716 mediante `icat`, se obtiene una cadena en base64 que al decodificarse y colocarse en formato `academy{}` revela la bandera.

### Referencias
- [Sleuthkit fls tool](https://wiki.sleuthkit.org/index.php?title=Fls)
- [Sleuthkit mactime tool](https://wiki.sleuthkit.org/index.php?title=Mactime)
- [Sleuthkit icat tool](https://wiki.sleuthkit.org/index.php?title=Icat)