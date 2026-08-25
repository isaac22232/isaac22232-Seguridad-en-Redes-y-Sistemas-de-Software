### Descripcion
Can you look at the data in this binary? The bash script might help!

### Solucion
```
Luck222-academy@webshell:~$ wget https://challenge-files.picoctf.net/c_wily_courier/b6c2dd492eb053dfbb3fcfa9eb142c8d11f6a00c0691031fc92b045d65b6e56a/static
--2026-08-24 16:49:16--  https://challenge-files.picoctf.net/c_wily_courier/b6c2dd492eb053dfbb3fcfa9eb142c8d11f6a00c0691031fc92b045d65b6e56a/static
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 3.160.5.18, 3.160.5.95, 3.160.5.64, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16776 (16K) [application/octet-stream]
Saving to: 'static'

static                                                     100%[======================================================================================================================================>]  16.38K  --.-KB/s    in 0s      

2026-08-24 16:49:16 (140 MB/s) - 'static' saved [16776/16776]

Luck222-academy@webshell:~$ wget https://challenge-files.picoctf.net/c_wily_courier/b6c2dd492eb053dfbb3fcfa9eb142c8d11f6a00c0691031fc92b045d65b6e56a/ltdis.sh
--2026-08-24 16:49:39--  https://challenge-files.picoctf.net/c_wily_courier/b6c2dd492eb053dfbb3fcfa9eb142c8d11f6a00c0691031fc92b045d65b6e56a/ltdis.sh
Resolving challenge-files.picoctf.net (challenge-files.picoctf.net)... 3.160.5.40, 3.160.5.18, 3.160.5.64, ...
Connecting to challenge-files.picoctf.net (challenge-files.picoctf.net)|3.160.5.40|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 785 [application/octet-stream]
Saving to: 'ltdis.sh'

ltdis.sh                                                   100%[======================================================================================================================================>]     785  --.-KB/s    in 0s      

2026-08-24 16:49:39 (31.9 MB/s) - 'ltdis.sh' saved [785/785]

Luck222-academy@webshell:~$ ls
README.txt  ltdis.sh  static

Luck222-academy@webshell:~$ chmod +x ltdis.sh
Luck222-academy@webshell:~$ ./ltdis.sh
Attempting disassembly of  ...
objdump: 'a.out': No such file
objdump: section '.text' mentioned in a -j option, but not found in any input file
Disassembly failed!
Usage: ltdis.sh <program-file>
Bye!
Luck222-academy@webshell:~$ ./ltdis.sh static
Attempting disassembly of static ...
Disassembly successful! Available at: static.ltdis.x86_64.txt
Ripping strings from binary with file offsets...
Any strings found in static have been written to static.ltdis.strings.txt with file offset
Luck222-academy@webshell:~$ ls                      
README.txt  ltdis.sh  static  static.ltdis.strings.txt  static.ltdis.x86_64.txt

Luck222-academy@webshell:~$ cat static.ltdis.strings.txt | grep pico             
   3020 picoCTF{d15a5m_t34s3r_20335e41}

```

### Notas adicionales
.sh Son archivos que contienen comandos de linux, agrupados se les llama script bash

### Referencias