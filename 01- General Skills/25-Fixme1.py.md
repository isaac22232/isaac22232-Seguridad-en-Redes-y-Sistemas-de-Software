### Descripcion
Fix the syntax error in this Python script to print the flag.

[Download Python script](https://artifacts.picoctf.net/c/26/fixme1.py)

### Solucion
```
Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/26/fixme1.py
--2026-08-26 16:37:43--  https://artifacts.picoctf.net/c/26/fixme1.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.40, 3.160.5.64, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.40|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 837 [application/octet-stream]
Saving to: 'fixme1.py'

fixme1.py                    100%[============================================>]     837  --.-KB/s    in 0s      

2026-08-26 16:37:43 (41.4 MB/s) - 'fixme1.py' saved [837/837]
2026-08-26 16:37:43 (41.4 MB/s) - 'fixme1.py' saved [837/837]

Luck222-academy@webshell:~$ python3 fixme1.py
  File "/home/Luck222-academy/fixme1.py", line 20
    print('That is correct! Here\'s your flag: ' + flag)
IndentationError: unexpected indent

Luck222-academy@webshell:~$ nano -l fixme1.py
Luck222-academy@webshell:~$ python3 fixme1.py
That is correct! Here's your flag: picoCTF{1nd3nt1ty_cr1515_09ee727a}
Luck222-academy@webshell:~$ 
```

### Notas adicionales
nano -l: muestra las lineas numeradas en el editor

### Referencias