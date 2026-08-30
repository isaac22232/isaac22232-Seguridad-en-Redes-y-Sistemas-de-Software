### Descripcion
What was I last working on? I remember writing a note to help me remember...

You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/160/challenge.zip)

### Solucion
```
Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c_titan/160/challenge.zip
--2026-08-30 03:09:22--  https://artifacts.picoctf.net/c_titan/160/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.95, 3.160.5.40, 3.160.5.64, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.95|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 17740 (17K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                              100%[======================================================================================================================================>]  17.32K  --.-KB/s    in 0.004s  

2026-08-30 03:09:22 (3.85 MB/s) - 'challenge.zip' saved [17740/17740]

Luck222-academy@webshell:~$ ls
challenge.zip
Luck222-academy@webshell:~$ unzip challenge.zip 
Luck222-academy@webshell:~/drop-in$ git log

commit 89d296ef533525a1378529be66b22d6a2c01e530 (HEAD -> master)
Author: picoCTF <ops@picoctf.com>
Date:   Tue Mar 12 00:07:22 2024 +0000

    picoCTF{t1m3m@ch1n3_186cd7d7}
```
### Notas adicionales
git log te deja ver los commits echos


### Referencias
