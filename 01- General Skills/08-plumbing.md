### Descripcion
Sometimes you need to handle process data outside of a file. Can you find a way to keep the output from this program and search for the flag?

Connect to fickle-tempest.picoctf.net 63063.
### Solucion
```
I don't think this is a flag either
Not a flag either
This is defintely not a flag
I don't think this is a flag either
Not a flag either
^C
Luck222-academy@webshell:~$ nc fickle-tempest.picoctf.net 63063 > hola

Luck222-academy@webshell:~$ cat hola | grep pico
picoCTF{digital_plumb3r_d3246b6B}

Luck222-academy@webshell:~$ nc fickle-tempest.picoctf.net 63063 | grep pico
picoCTF{digital_plumb3r_d3246b6B}


```

### Notas adicionales
* > se utiliza para redirigir la salida de cualquier comando a un archivo de texto
* | la barra vertical o tambien llamado pipe redirige la salida

### Referencias
