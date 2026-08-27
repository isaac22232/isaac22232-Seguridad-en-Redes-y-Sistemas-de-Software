### Descripcion
Can you crack the password to get the flag?

Download the password checker [here](https://artifacts.picoctf.net/c/13/level2.py) and you'll need the encrypted [flag](https://artifacts.picoctf.net/c/13/level2.flag.txt.enc) in the same directory too.

### Solucion
```
Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.py
--2026-08-26 16:54:25--  https://artifacts.picoctf.net/c/13/level2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.40, 3.160.5.64, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.40|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 914 [application/octet-stream]
Saving to: 'level2.py'

level2.py                    100%[============================================>]     914  --.-KB/s    in 0.001s  

2026-08-26 16:54:25 (889 KB/s) - 'level2.py' saved [914/914]

Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
--2026-08-26 16:54:49--  https://artifacts.picoctf.net/c/13/level2.flag.txt.enc
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.18, 3.160.5.64, 3.160.5.95, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.18|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 31 [application/octet-stream]
Saving to: 'level2.flag.txt.enc'

level2.flag.txt.enc          100%[============================================>]      31  --.-KB/s    in 0s      

2026-08-26 16:54:49 (360 KB/s) - 'level2.flag.txt.enc' saved [31/31]

Python 3.11.9 (tags/v3.11.9:de54cf5, Apr  2 2024, 10:12:12) [MSC v.1938 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36)
'de76'

Python 3.11.9 (tags/v3.11.9:de54cf5, Apr  2 2024, 10:12:12) [MSC v.1938 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>>
>>> chr(0x64) + chr(0x65) + chr(0x37) + chr(0x36)
'de76'
```

### Notas adicionales


### Referencias