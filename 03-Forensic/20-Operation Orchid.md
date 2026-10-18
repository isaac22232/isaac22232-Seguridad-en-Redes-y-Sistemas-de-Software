### Descripción
Download this disk image and find the flag.

Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://challenge-files.cylabacademy.net/library/7d645367284f9df9139dd5ad212e5c3bd0815b7674ca700648a3983158394892/disk.flag.img.gz)

### Solución
```
┌──(kali㉿kali)-[~]
└─$ icat -o 411648 disk.flag.img 1782 > flag.txt.enc                            

┌──(kali㉿kali)-[~]
└─$ openssl aes256 -salt -in flag.txt.enc -out fla.txt -k unbreakablepassword1234567 -d

academy{h4un71ng_p457_718ebd29}

```
### Notas adicionales


### Referencias
