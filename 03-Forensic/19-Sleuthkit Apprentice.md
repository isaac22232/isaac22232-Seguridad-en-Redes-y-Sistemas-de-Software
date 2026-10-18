### Descripción
Download this disk image and find the flag.

Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.

- [Download compressed disk image](https://challenge-files.cylabacademy.net/library/162bc8bf6dd1abbc5269c16570e170277369a39cf46bdd8d99443e136fabcc5f/disk.flag.img.gz)

### Solución
```
┌──(kali㉿kali)-[~/diskimage]
└─$ fls -o 360448 -r  disk.flag.img 1995
r/r 2363: .ash_history
d/d 3981: my_folder
+ r/r * 2082(realloc): flag.txt
+ r/r 2371: flag.uni.txt
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/diskimage]
└─$ icat -o 360448  disk.flag.img 2371 
academy{by73_5urf3r_85e9b307}


```
### Notas adicionales


### Referencias
