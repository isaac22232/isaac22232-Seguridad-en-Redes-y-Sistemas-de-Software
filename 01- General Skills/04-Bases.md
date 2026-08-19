### Descripcion
What does this bDNhcm5fdGgzX3IwcDM1 mean? I think it has something to do with bases.

### Solucion
```
Python 3.11.9 (tags/v3.11.9:de54cf5, Apr  2 2024, 10:12:12) [MSC v.1938 64 bit (AMD64)] on win32
Type "help", "copyright", "credits" or "license" for more information.
>>> import codecs
>>> import base64
>>>
>>> base64.b64decode("bDNhcm5fdGgzX3IwcDM1")
b'l3arn_th3_r0p35'

picoCTF{l3arn_th3_r0p35}

```

### Notas adicionales


### Referencias

https://es.wikipedia.org/wiki/Base64