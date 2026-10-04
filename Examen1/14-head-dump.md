### Descripción
Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag.

The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden.

### Solución
```
┌──(kali㉿kali)-[~/Downloads]
└─$ ls
heapdump-1791084760268.heapsnapshot
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/Downloads]
└─$ file heapdump
heapdump: cannot open `heapdump' (No such file or directory)
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/Downloads]
└─$ file heapdump-1791084760268.heapsnapshot 
heapdump-1791084760268.heapsnapshot: ASCII text, with very long lines (64671)
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/Downloads]
└─$ strings heapdump | grep academy
strings: 'heapdump': No such file
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/Downloads]
└─$ strings heapdump-1791084760268.heapsnapshot | grep academy 
academy{Pat!3nt_15_Th3_K3y_1dc68c38}

```

### Notas adicionales


### Referencias