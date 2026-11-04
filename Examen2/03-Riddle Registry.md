### Descripción
Hi, intrepid investigator! 📄🔍 You've stumbled upon a peculiar PDF filled with what seems like nothing more than garbled nonsense. But beware! Not everything is as it appears. Amidst the chaos lies a hidden treasure—an elusive flag waiting to be uncovered. Find the PDF file here [Hidden Confidential Document](https://challenge-files.cylabacademy.net/library/b32f1f1945481591df61d328d02995fe3521d16b70928fbe44e3bd90c4ccb113/confidential.pdf) and uncover the flag within the metadata.

### Solución
```
┌──(kali㉿kali)-[~]
└─$ pdfinfo confidential.pdf
Title:          
Subject:        
Keywords:       
Author:         YWNhZGVteXtwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV85ZDNjYzY2OX0=
Creator:        
Producer:       PyPDF2
CreationDate:   
ModDate:        
Custom Metadata: no
Metadata Stream: no
Tagged:          no
UserProperties:  no
Suspects:        no
Form:            none
JavaScript:      no
Pages:           1
Encrypted:       no
Page size:       612 x 792 pts (letter)
Page rot:        0
File size:       182532 bytes
Optimized:       no
PDF version:     1.3

┌──(kali㉿kali)-[~]
└─$ echo "YWNhZGVteXtwdXp6bDNkX20zdGFkYXRhX2YwdW5kIV85ZDNjYzY2OX0=" | base64 -d
academy{puzzl3d_m3tadata_f0und!_9d3cc669}
```

### Notas adicionales
- Al inspeccionar los metadatos del documento PDF mediante `pdfinfo` o `exiftool`, se observa que el campo `Author` contiene una cadena en base64.
- Al decodificar dicha cadena con `base64 -d`, se obtiene directamente la bandera.

### Referencias
- [pdfinfo man page](https://linux.die.net/man/1/pdfinfo)