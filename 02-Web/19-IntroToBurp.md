### Descripción

This website puts a two-factor prompt between you and the flag. Register an account, then take a close look at the requests your browser is actually sending. Try [here](http://chatelaine.cylabacademy.net:39305/) to find the flag
### Solución
```
┌──(kali㉿kali)-[~]
└─$ python3 hola.py     
[*] Obteniendo el token CSRF de la página principal...
[+] Token extraído correctamente: Ijk3ODBjNmI1MzY4MTcxMzZlZDM4NjE1NmNhMGZiMmU3MDc2YWNjYzQi.armcXQ.aC4uCwzytR2n-T4IYVxGsPws05w
[*] Enviando datos de registro...
[*] Ejecutando el bypass del OTP mediante JSON...

[+] Respuesta del servidor obtenida:
Welcome, hacker123 you sucessfully bypassed the OTP request. 
Your Flag: academy{#0TP_Bypvss_SuCc3$S_3c1fad56}

```

### Notas adicionales


### Referencias