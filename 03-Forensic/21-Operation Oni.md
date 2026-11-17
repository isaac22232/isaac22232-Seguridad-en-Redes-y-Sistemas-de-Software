### Descripción
Note: you must launch a challenge instance in order to view your disk image download link.

Download this disk image, find the key and log into the remote machine.

Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

### Solución
```
┌──(kali㉿kali)-[~]
└─$ gzip -d disk.img.gz

┌──(kali㉿kali)-[~]
└─$ mmls disk.img
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0000206847   0000204800   Linux (0x83)
003:  000:001   0000206848   0000471039   0000264192   Linux (0x83)

┌──(kali㉿kali)-[~]
└─$ # Buscamos la clave SSH privada en la partición principal (offset 206848):
┌──(kali㉿kali)-[~]
└─$ fls -o 206848 -r disk.img | grep -E "id_ed25519|id_rsa|\.ssh"
d/d 2344:	.ssh
+ r/r 2345:	id_ed25519
+ r/r 2346:	id_ed25519.pub

┌──(kali㉿kali)-[~]
└─$ icat -o 206848 disk.img 2345 > id_ed25519

┌──(kali㉿kali)-[~]
└─$ chmod 600 id_ed25519

┌──(kali㉿kali)-[~]
└─$ ssh -i id_ed25519 -p 26312 ctf-player@xebec.cylabacademy.net
ctf-player@operation-oni:~$ ls
flag.txt
ctf-player@operation-oni:~$ cat flag.txt
academy{k3y_5l3u7h_0e000cd7}
```

### Notas adicionales
- Al descomprimir la imagen `disk.img.gz`, usamos `mmls` para inspeccionar la tabla de particiones MBR/DOS.
- La segunda partición Linux (la principal con el sistema de archivos de root) comienza en el sector `206848`.
- Mediante `fls -o 206848 -r disk.img` encontramos la carpeta `.ssh` (inodo `2344`) y dentro de ella la clave privada `id_ed25519` (inodo `2345`).
- Con `icat -o 206848 disk.img 2345 > id_ed25519` extraemos la clave SSH privada y le asignamos permisos estrictos con `chmod 600 id_ed25519`.
- Nos conectamos por SSH a la máquina remota provista por la instancia activa del reto y leemos `flag.txt`.

### Referencias
- [Sleuthkit mmls](https://wiki.sleuthkit.org/index.php?title=Mmls)
- [Sleuthkit fls](https://wiki.sleuthkit.org/index.php?title=Fls)
- [Sleuthkit icat](https://wiki.sleuthkit.org/index.php?title=Icat)
