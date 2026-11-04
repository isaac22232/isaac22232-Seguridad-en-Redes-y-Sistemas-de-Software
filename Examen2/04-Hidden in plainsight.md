### Descripción
You’re given a seemingly ordinary JPG image. Something is tucked away out of sight inside the file. Your task is to discover the hidden payload and extract the flag. Download the jpg image [here](https://challenge-files.cylabacademy.net/library/9ec77a1b83f3b582954d97ec39f7926d4dc45f98cd1ef7a24b3172ca385e02b2/img.jpg).

### Solución
```
┌──(kali㉿kali)-[~]
└─$ strings img.jpg | head -n 5
c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9
 $.' ",#
(7),01444
'9=82<.342
!22222222222222222222222222222222222222222222222222

┌──(kali㉿kali)-[~]
└─$ echo "c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9" | base64 -d
steghide:cEF6endvcmQ=

┌──(kali㉿kali)-[~]
└─$ echo "cEF6endvcmQ=" | base64 -d
pAzzword

┌──(kali㉿kali)-[~]
└─$ steghide extract -sf img.jpg -p pAzzword
wrote extracted data to "extracted.txt".

┌──(kali㉿kali)-[~]
└─$ cat extracted.txt
academy{h1dd3n_1n_1m4g3_71ae1957}
```

### Notas adicionales
- El comando `strings` revela una cadena codificada en base64 al inicio de la imagen: `c3RlZ2hpZGU6Y0VGNmVuZHZjbVE9`.
- Al decodificarla, nos indica la herramienta utilizada (`steghide`) y la contraseña en base64 (`cEF6endvcmQ=`), que al decodificarse resulta ser `pAzzword`.
- Empleando `steghide extract -sf img.jpg -p pAzzword`, se extrae el archivo oculto que contiene la bandera.

### Referencias
- [steghide documentation](http://steghide.sourceforge.net/)