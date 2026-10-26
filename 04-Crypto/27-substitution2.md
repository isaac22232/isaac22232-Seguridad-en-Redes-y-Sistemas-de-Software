### Descripción
It seems that another encrypted message has been intercepted. The encryptor seems to have learned their lesson though and now there isn't any punctuation! Can you still crack the cipher? Download the message [here](https://challenge-files.cylabacademy.net/library/750a77d87fa924d5ec8a173d7354dd57792a1597cab3d89fa7443608ba0a35e7/message.txt).

### Solución
```
se obtiene el alfabeto de sustitución completo necesario para decodificar el interior de las llaves:

- **`A6S4J`** se traduce como `N6R4M` (A=N, S=R, J=M).
    
- **`4A41B515`** se traduce como `4N41Y515` (B=Y).
    
- **`15`** se mantiene igual.
    
- **`73O10V5`** se traduce como `73D10U5` (O=D, V=U).
    
- **`IO56E357`** se traduce como `FD56C357` (I=F, E=C), lo cual forma un sufijo hexadecimal aleatorio clásico de estos retos.
    

Al unir todos los segmentos, la frase en formato leetspeak revela "NGRAM ANALYSIS IS TEDIOUS". La bandera final es:

**`academy{N6R4M_4N41Y515_15_73D10U5_FD56C357}`**
```

### Notas adicionales


### Referencias
