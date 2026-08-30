### Descripcion
How to automate tasks to run at intervals on linux servers?
Use ssh to connect to this server:

`Server: saturn.picoctf.net Port: 52622 Username: picoplayer Password: pYkku7iMsS`
### Solucion
```

Luck222-academy@webshell:~$ ssh picoplayer@saturn.picoctf.net -p 52622
The authenticity of host '[saturn.picoctf.net]:52622 ([13.59.203.175]:52622)' can't be established.
ED25519 key fingerprint is SHA256:dMTscRrUiURy7uMu5eGWwEKdd2FzqLzx6LfWhssWnNQ.
This key is not known by any other names
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '[saturn.picoctf.net]:52622' (ED25519) to the list of known hosts.
picoplayer@saturn.picoctf.net's password: 

picoplayer@challenge:~$ crontab -l
no crontab for picoplayer
picoplayer@challenge:~$ cat /etc/crontab
# picoCTF{Sch3DUL7NG_T45K3_L1NUX_7754e199}
```

### Notas adicionales
crontab: el comando y archivo crontab sirve para **programar la ejecución automática de tareas** en sistemas Linux y Unix.

### Referencias
https://gemini.google.com/app/e967aa4251366793?hl=es