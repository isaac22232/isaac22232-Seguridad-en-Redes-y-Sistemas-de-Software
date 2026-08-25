### Descripcion
Can you find the flag in [file](https://challenge-files.picoctf.net/c_fickle_tempest/6577d3f1500aebcd300787bd5d96216b30aed379c811f5e83e888f897da4a3d5/strings) without running it?
PISTAS:
string
### Solucion
```
Luck222-academy@webshell:~$ wget https://challenge-files.picoctf.net/c_fickle_tempest/6577d3f1500aebcd300787bd5d96216b30aed379c811f5e83e888f897da4a3d5/strings
--2026-08-24 16:34:22--  https://challenge-files.picoctf.net/c_fickle_tempest/6577d3f1500aebcd300787bd5d96216b30aed379c811f5e83e888f897da4a3d5/strings
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 3.160.5.64, 3.160.5.95, 3.160.5.18, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|3.160.5.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 784424 (766K) [application/octet-stream]
Saving to: 'strings'

strings                                                    100%[======================================================================================================================================>] 766.04K  1.86MB/s    in 0.4s    

2026-08-24 16:34:22 (1.86 MB/s) - 'strings' saved [784424/784424]

Luck222-academy@webshell:~$ ls            
README.txt  file  flag  hola  strings
Luck222-academy@webshell:~$ chmod +x strings

Luck222-academy@webshell:~$ strings strings | grep pico
picoCTF{5tRIng5_1T_d6306c19}

```


### Notas adicionales

Strings - muestra las cadenas (caracteres imprimibles) en un archivo binario
### Referencias
https://webshell.cylabacademy.org/