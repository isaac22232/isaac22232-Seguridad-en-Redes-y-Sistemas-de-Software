### Descripcion
Can you crack the password to get the flag?

Download the password checker [here](https://artifacts.picoctf.net/c/11/level1.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/11/level1.flag.txt.enc) in the same directory too.

### Solucion
```
Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/11/level1.py
--2026-08-26 16:49:49--  https://artifacts.picoctf.net/c/11/level1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.64, 3.160.5.18, 3.160.5.95, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 876 [application/octet-stream]
Saving to: 'level1.py'

level1.py                    100%[============================================>]     876  --.-KB/s    in 0s      

2026-08-26 16:49:49 (354 MB/s) - 'level1.py' saved [876/876]

Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/11/level1.flag.txt.enc
--2026-08-26 16:50:05--  https://artifacts.picoctf.net/c/11/level1.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.95, 3.160.5.40, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.95|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 30 [application/octet-stream]
Saving to: 'level1.flag.txt.enc'

level1.flag.txt.enc          100%[============================================>]      30  --.-KB/s    in 0s      

2026-08-26 16:50:05 (2.45 MB/s) - 'level1.flag.txt.enc' saved [30/30]

Luck222-academy@webshell:~$ ls
level1.flag.txt.enc  level1.py
Luck222-academy@webshell:~$ nano level1.py
Luck222-academy@webshell:~$ python3 level1.py
Please enter correct password for flag: 1e1a
Welcome back... your flag, user:
picoCTF{545h_r1ng1ng_fa343060}
```

### Notas adicionales


### Referencias