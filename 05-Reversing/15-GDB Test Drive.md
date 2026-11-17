### Descripción
Can you get the flag? Download this [binary](https://challenge-files.cylabacademy.net/library/37a3037cc617e25371d3529e74304830bd22988c8c2f2b39e4355fc6781ac402/gdbme).

Here's the test drive instructions:

- `$ chmod +x gdbme`
- `$ gdb gdbme`
- `(gdb) layout asm`
- `(gdb) break *(main+99)`
- `(gdb) run`
- `(gdb) jump *(main+104)`

### Solución
```
┌──(kali㉿kali)-[~]
└─$ chmod +x gdbme

┌──(kali㉿kali)-[~]
└─$ gdb -q gdbme
Reading symbols from gdbme...
(No debugging symbols found in gdbme)
(gdb) break *(main+99)
Breakpoint 1 at 0x132a
(gdb) run
Starting program: /home/kali/gdbme 

Breakpoint 1, 0x000055555555532a in main ()
(gdb) jump *(main+104)
Continuing at 0x000055555555532f.
academy{d3bugg3r_dr1v3_d28daa02}
[Inferior 1 (process 1234) exited normally]
```

### Notas adicionales
- El binario `gdbme` contiene una llamada a `sleep(100000)` en la instrucción `main+99`.
- Al seguir las instrucciones del reto, establecemos un punto de interrupción en `*(main+99)` para detener la ejecución justo antes de entrar en `sleep`.
- Mediante el comando `jump *(main+104)` de GDB, forzamos al puntero de instrucciones (`rip`) a saltarse la función `sleep`, cayendo directamente en la rutina `rotate_encrypt` que descifra y muestra la bandera en pantalla.

### Referencias
- [GDB Execution Control](https://sourceware.org/gdb/current/onlinedocs/gdb.html/Continuing-and-Stepping.html)
