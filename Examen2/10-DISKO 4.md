### Descripción
Can you find the flag in this disk image? This time I deleted the file! Let see you get it now! Download the disk image [here](https://challenge-files.cylabacademy.net/library/3b73866c41eaa168316a81b545f02dc25de5f23f1db0bcfb268afc0539d359af/disko-4.dd.gz).

	Hints
	1 How would you look for deleted files?

### Solución
```
┌──(kali㉿kali)-[~]
└─$ gzip -d disko-4.dd.gz

┌──(kali㉿kali)-[~]
└─$ fls -d -r disko-4.dd
r/r * 522629:	log/messages
r/r * 532021:	log/dont-delete.gz

┌──(kali㉿kali)-[~]
└─$ icat disko-4.dd 532021 > dont-delete.gz

┌──(kali㉿kali)-[~]
└─$ zcat dont-delete.gz
Here is your flag
academy{d3l_d0n7_h1d3_w3ll_0a4d31fa}
```

### Notas adicionales
- Se descomprime la imagen forense con `gzip -d`.
- Con `fls -d -r disko-4.dd` se listan recursivamente únicamente los archivos marcados como borrados (`-d`).
- Se localiza el archivo borrado `log/dont-delete.gz` con inodo `532021`.
- Con `icat disko-4.dd 532021 > dont-delete.gz` se extrae el contenido del archivo comprimido y con `zcat dont-delete.gz` se descomprime al vuelo mostrando la bandera.

### Referencias
- [Sleuthkit fls tool](https://wiki.sleuthkit.org/index.php?title=Fls)
- [Sleuthkit icat tool](https://wiki.sleuthkit.org/index.php?title=Icat)