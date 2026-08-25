### Descripcion
Can you make sense of this file?

Download the file [here](https://artifacts.picoctf.net/c/472/enc_flag).
Pistas:
1. Multiple decoding is always good.
### Solucion

```
Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/472/enc_flag
--2026-08-24 22:55:43--  https://artifacts.picoctf.net/c/472/enc_flag
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.40, 3.160.5.64, 3.160.5.18, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.40|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 349 [application/octet-stream]
Saving to: 'enc_flag'

enc_flag                                                   100%[======================================================================================================================================>]     349  --.-KB/s    in 0s      

2026-08-24 22:55:43 (153 MB/s) - 'enc_flag' saved [349/349]

Luck222-academy@webshell:~$ ls
Addadshashanammu  Addadshashanammu.zip  README.txt  enc_flag

Luck222-academy@webshell:~$ file enc_flag
enc_flag: ASCII text
Luck222-academy@webshell:~$ cat enc_flag
VmpGU1EyRXlUWGxTYmxKVVYwZFNWbGxyV21GV1JteDBUbFpPYWxKdFVsaFpWVlUxWVZaS1ZWWnVh
RmRXZWtab1dWWmtSMk5yTlZWWApiVVpUVm10d1VWZFdVa2RpYlZaWFZtNVdVZ3BpU0VKeldWUkNk
MlZXVlhoWGJYQk9VbFJXU0ZkcVRuTldaM0JZVWpGS2VWWkdaSGRXCk1sWnpWV3hhVm1KRk5XOVVW
VkpEVGxaYVdFMVhSbFZrTTBKeldWaHdRMDB4V2tWU2JFNVdDbUpXV2tkVU1WcFhWVzFHZEdWRlZs
aGkKYlRrelZERldUMkpzUWxWTlJYTkxDZz09Cg==

Luck222-academy@webshell:~$ cat enc_flag | base64 -d
VjFSQ2EyTXlSblJUV0dSVllrWmFWRmx0TlZOalJtUlhZVVU1YVZKVVZuaFdWekZoWVZkR2NrNVVX
bUZTVmtwUVdWUkdibVZXVm5WUgpiSEJzWVRCd2VWVXhXbXBOUlRWSFdqTnNWZ3BYUjFKeVZGZHdW
MlZzVWxaVmJFNW9UVVJDTlZaWE1XRlVkM0JzWVhwQ00xWkVSbE5WCmJWWkdUMVpXVW1GdGVFVlhi
bTkzVDFWT2JsQlVNRXNLCg==
Luck222-academy@webshell:~$ cat enc_flag | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d | base64 -d
picoCTF{base64_n3st3d_dic0d!n8_d0wnl04d3d_73494190}

```
### Notas adicionales
Se puede decodificar varias veces de la mismo formato o de otro 

### Referencias
https://medium.com/@omstaendlig/picoctf-writeup-repetitions-e37aa158416d