### Descripcion
Fix the syntax error in the Python script to print the flag.

[Download Python script](https://artifacts.picoctf.net/c/5/fixme2.py)

### Solucion
```
Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/5/fixme2.py
--2026-08-26 16:42:12--  https://artifacts.picoctf.net/c/5/fixme2.py
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.40, 3.160.5.95, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.40|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1029 (1.0K) [application/octet-stream]
Saving to: 'fixme2.py'

fixme2.py                    100%[============================================>]   1.00K  --.-KB/s    in 0s      

2026-08-26 16:42:12 (57.0 MB/s) - 'fixme2.py' saved [1029/1029]

Luck222-academy@webshell:~$ python3 fixme2.py
  File "/home/Luck222-academy/fixme2.py", line 22
    if flag = "":
       ^^^^^^^^^
SyntaxError: invalid syntax. Maybe you meant '==' or ':=' instead of '='?
Luck222-academy@webshell:~$ nano fixme2.py
Luck222-academy@webshell:~$ python3 fixme2.py
That is correct! Here's your flag: picoCTF{3qu4l1ty_n0t_4551gnm3nt_4863e11b}
Luck222-academy@webshell:~$ 
```

### Notas adicionales


### Referencias