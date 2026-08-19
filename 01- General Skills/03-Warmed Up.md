### Descripcion
What is 0x3D (base 16) in decimal (base 10)?

### Solucion

```
Luck222-academy@webshell:~$ python
Python 3.10.12 (main, Mar  3 2026, 11:56:32) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> int(0x3d,16)
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: int() can't convert non-string with explicit base
>>> int("0x3D",16)
61

picoCTF{61}
```


### Notas adicionales
La función int, convierte cualquier numero a base 10, el segundo parámetro indica la base en la que esta el numero

### Referencias

* https://webshell.cylabacademy.org/