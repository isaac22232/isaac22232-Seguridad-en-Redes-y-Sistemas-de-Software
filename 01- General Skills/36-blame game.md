### Descripcion
Someone's commits seems to be preventing the program from working. Who is it?

You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/157/challenge.zip)

### Solucion
```
Luck222-academy@webshell:~/drop-in$ wget https://artifacts.picoctf.net/c_titan/157/challenge.zip
--2026-08-30 03:15:56--  https://artifacts.picoctf.net/c_titan/157/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.40, 3.160.5.18, 3.160.5.95, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.40|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 293587 (287K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                              100%[======================================================================================================================================>] 286.71K  1.84MB/s    in 0.2s    

2026-08-30 03:15:56 (1.84 MB/s) - 'challenge.zip' saved [293587/293587]

Luck222-academy@webshell:~/drop-in$ git init
Reinitialized existing Git repository in /home/Luck222-academy/drop-in/.git/
Luck222-academy@webshell:~/drop-in$ git log --message.py
fatal: unrecognized argument: --message.py
Luck222-academy@webshell:~/drop-in$ git log -- message.py

commit 2466febd40004b9ca644ce924181d07e23dcfaeb
Author: picoCTF{@sk_th3_1nt3rn_cfca95b2} <ops@picoctf.com>
Date:   Tue Mar 12 00:07:06 2024 +0000

    optimize file size of prod code
```

### Notas adicionales


### Referencias
https://hackmd.io/@mochimamrifai/B11BTbNUR