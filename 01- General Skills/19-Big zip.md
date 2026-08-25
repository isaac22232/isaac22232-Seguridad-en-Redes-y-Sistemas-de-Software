### Descripcion

Unzip this archive and find the flag.

- [Download zip file](https://artifacts.picoctf.net/c/503/big-zip-files.zip)
### Solucion

```
Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/503/big-zip-files.zip
Luck222-academy@webshell:~$ unzip big-zip-files.zip

Luck222-academy@webshell:~$ ls
Addadshashanammu  big-zip-files  big-zip-files.zip
Luck222-academy@webshell:~$ grep -rnI "picoCTF{"
files/folder_pmbymkjcya/folder_cawigcwvgv/folder_ltdayfmktr/folder_fnpfclfyee/whzxrpivpqld.txt:1:information on the record will last a billion years. Genes and brains and books encode picoCTF{gr3p_15_m4g1c_ef8790dc}
```
### Notas adicionales
- `grep`: Es la herramienta de búsqueda de patrones en texto por excelencia en Linux.
    
- `-r` (recursive): Le indica a `grep` que no solo busque en la carpeta actual, sino que se meta en **todas las subcarpetas** de manera recursiva, sin importar qué tan profundo esté el archivo.
    
- `-n` (line number): Es vital para no perder tiempo. Cuando encuentre la bandera, te dirá exactamente en qué **número de línea** dentro del archivo se encuentra.
    
- `-I` (letra i mayúscula, ignore binary): **Este es el secreto para archivos masivos.** Le dice a `grep` que ignore automáticamente cualquier archivo binario (como imágenes, ejecutables, audios o volcados de memoria) y busque **solo en archivos de texto plano**. Esto acelera la búsqueda drásticamente y evita que tu terminal se llene de símbolos extraños.

### Referencias
https://gemini.google.com/app/9acda8e47cbe8685?hl=es