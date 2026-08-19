### Descripción
Using netcat (nc) is going to be pretty important. Can you connect to fickle-tempest.picoctf.net at port 62817 to get the flag?
### Solución

```
Luck222-academy@webshell:~$ man nc
Luck222-academy@webshell:~$ nc --help
nc: invalid option -- '-'
usage: nc [-46CDdFhklNnrStUuvZz] [-I length] [-i interval] [-M ttl]
          [-m minttl] [-O length] [-P proxy_username] [-p source_port]
          [-q seconds] [-s sourceaddr] [-T keyword] [-V rtable] [-W recvlimit]
          [-w timeout] [-X proxy_protocol] [-x proxy_address[:port]]
          [destination] [port]
Luck222-academy@webshell:~$ nc fickle-tempest.picoctf.net 62817
You're on your way to becoming the net cat master
picoCTF{nEtCat_Mast3ry_0d33dA2C}
^C
Luck222-academy@webshell:~$ 
```
### Notas adicionales
* nc es una herramienta de red que permite conectarse a un puerto especifico
* También puedo abrir un puerto TCP o UDP en maquina y luego desde otro conectarme a ese puerto
### Referencias
