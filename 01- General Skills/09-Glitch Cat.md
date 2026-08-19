### Descripcion
Our flag printing service has started glitching!

Hints

1
ASCII is one of the most common encodings used in programming
2
We know that the glitch output is valid Python, somehow!
3
Press Ctrl and c on your keyboard to close your connection and return to the command prompt.

### Solucion
```
Luck222-academy@webshell:~$ nc saturn.picoctf.net 52717
'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'
^C

Luck222-academy@webshell:~$ python
Python 3.10.12 (main, Mar  3 2026, 11:56:32) [GCC 11.4.0] on linux
Type "help", "copyright", "credits" or "license" for more information.

>>> 'picoCTF{gl17ch_m3_n07_' + chr(0x62) + chr(0x64) + chr(0x61) + chr(0x36) + chr(0x38) + chr(0x66) + chr(0x37) + chr(0x35) + '}'

'picoCTF{gl17ch_m3_n07_bda68f75}'

```


### Notas adicionales
* Python utiliza el + para concatenar cadenas 
* chr() es una funcion de python que convierte un numero a su correspondiente caracter ASCII
* Esto fue simplemente una suma de cadenas y caracteres


### Referencias