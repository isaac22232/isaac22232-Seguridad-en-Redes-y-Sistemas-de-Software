### Descripcion
This website can be rendered only by picobrowser, go and catch the flag!

### Solucion
```
Luck222-academy@webshell:~$ curl -s http://fickle-tempest.picoctf.net:49242/flag -H "User-Agent: picobrowser" | grep pico                                                  
         <!-- <strong>Title</strong> --> picobrowser!
            <p style="text-align:center; font-size:30px;"><b>Flag</b>: <code>picoCTF{p1c0_s3cr3t_ag3nt_fba5c48f}</code></p>
```

### Notas adicionales

- Te conectaste al servidor disfrazado del navegador "picobrowser".
    
- El servidor verificó tu disfraz de "picobrowser" y decidió responder enviándote un documento de texto que contenía la bandera.
    
- El documento completo probablemente tenía etiquetas HTML (`<html>`, `<body>`, etc.), pero gracias al `| grep pico`, descartaste toda la basura visual y tu terminal solo imprimió las dos líneas que te interesaban: la validación (`picobrowser!`) y la bandera ganadora (`Flag: picoCTF{p1c0_s3cr3t_ag3nt_fba5c48f}`).
### Referencias
