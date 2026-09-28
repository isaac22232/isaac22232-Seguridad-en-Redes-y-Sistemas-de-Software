### Descripción
I don't like scrolling down to read the code of my website, so I've squished it. As a bonus, my pages load faster! Browse [here](http://xebec.cylabacademy.net:43287/), and find the flag!

### Solución
```
┌──(kali㉿kali)-[~]
└─$ curl -s http://xebec.cylabacademy.net:43287/ | grep -o 'class="academy{[^}]*}"'
class="academy{}"
class="academy{}"
class="academy{}"
class="academy{}"
class="academy{}"
class="academy{}"
class="academy{}"
class="academy{}"
class="academy{}"
class="academy{}"
class="academy{}"
class="academy{pr3tty_c0d3_f2dc9e9e}"
class="academy{}"
class="academy{}"


```

### Notas adicionales


### Referencias