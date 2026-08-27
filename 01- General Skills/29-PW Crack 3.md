### Descripcion
Can you crack the password to get the flag?

Download the password checker [here](https://artifacts.picoctf.net/c/16/level3.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/16/level3.flag.txt.enc) and the [hash](https://artifacts.picoctf.net/c/16/level3.hash.bin) in the same directory too.

There are 7 potential passwords with 1 being correct. You can find these by examining the password checker script.

### Solucion
```
Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/16/level3.py
--2026-08-26 17:01:33--  https://artifacts.picoctf.net/c/16/level3.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.40, 3.160.5.95, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1337 (1.3K) [application/octet-stream]
Saving to: 'level3.py'

level3.py                    100%[============================================>]   1.31K  --.-KB/s    in 0s      

2026-08-26 17:01:33 (52.6 MB/s) - 'level3.py' saved [1337/1337]

Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/16/level3.flag.txt.enc
--2026-08-26 17:01:44--  https://artifacts.picoctf.net/c/16/level3.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.40, 3.160.5.64, 3.160.5.95, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.40|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level3.flag.txt.enc'

level3.flag.txt.enc          100%[============================================>]      31  --.-KB/s    in 0s      

2026-08-26 17:01:44 (18.1 MB/s) - 'level3.flag.txt.enc' saved [31/31]

Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/16/level3.hash.bin
--2026-08-26 17:01:57--  https://artifacts.picoctf.net/c/16/level3.hash.bin
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.40, 3.160.5.64, 3.160.5.95, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.40|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16 [application/octet-stream]
Saving to: 'level3.hash.bin'

level3.hash.bin              100%[============================================>]      16  --.-KB/s    in 0s      

2026-08-26 17:01:57 (6.26 MB/s) - 'level3.hash.bin' saved [16/16]

Luck222-academy@webshell:~$ ls
level3.flag.txt.enc  level3.hash.bin  level3.py
Luck222-academy@webshell:~$ nano -l level3.py
Luck222-academy@webshell:~$ tail level3.py



level_3_pw_check()


# The strings below are 7 possibilities for the correct password. 
#   (Only 1 is correct)
pos_pw_list = ["6997", "3ac8", "f0ac", "4b17", "ec27", "4e66", "865e"]

Luck222-academy@webshell:~$ python3 level3.py
Please enter correct password for flag: 865e
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_2b072a90}

SOLUCION2:
Luck222-academy@webshell:~$ nano level3.py
Luck222-academy@webshell:~$ python3 level3.py 
Probando contraseña: 6997...
Probando contraseña: 3ac8...
Probando contraseña: f0ac...
Probando contraseña: 4b17...
Probando contraseña: ec27...
Probando contraseña: 4e66...
Probando contraseña: 865e...

¡Contraseña correcta encontrada!: 865e
Welcome back... your flag, user:
picoCTF{m45h_fl1ng1ng_2b072a90}

```

### Notas adicionales


### Referencias