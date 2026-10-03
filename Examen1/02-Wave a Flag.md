### Descripcion
Can you invoke help flags for a tool or binary? This program has extraordinarily helpful information...

### Solucion
```
Luck222-academy@webshell:~$ wget https://challenge-files.picoctf.net/c_wily_courier/5a478d0b24d6a4f4185e3adb7a78c41cdad626fb02fe80e083dc33bf8b197d3d/warm
--2026-08-24 16:43:32--  https://challenge-files.picoctf.net/c_wily_courier/5a478d0b24d6a4f4185e3adb7a78c41cdad626fb02fe80e083dc33bf8b197d3d/warm
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 3.160.5.95, 3.160.5.40, 3.160.5.64, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|3.160.5.95|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19312 (19K) [application/octet-stream]
Saving to: 'warm'

warm                                                       100%[======================================================================================================================================>]  18.86K  --.-KB/s    in 0.002s  

2026-08-24 16:43:32 (11.2 MB/s) - 'warm' saved [19312/19312]

Luck222-academy@webshell:~$ ls
README.txt  file  flag  hola  strings  warm
Luck222-academy@webshell:~$ file warm
warm: ELF 64-bit LSB pie executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=9e46ec8729d2f2aa8ffc4b1cdc058081bddcfe67, for GNU/Linux 3.2.0, with debug_info, not stripped
Luck222-academy@webshell:~$ chmod +x warm
Luck222-academy@webshell:~$ ./waem
-bash: ./waem: No such file or directory
Luck222-academy@webshell:~$ ./warm
Hello user! Pass me a -h to learn what I can do!
Luck222-academy@webshell:~$ ./warm -h 
Oh, help? I actually don't do much, but I do have this flag here: academy{b1scu1ts_4nd_gr4vy_ac5832c}

```
### Notas adicionales


### Referencias