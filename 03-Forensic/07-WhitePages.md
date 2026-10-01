### Descripción
I stopped using YellowPages and moved onto WhitePages... but [the page they gave me](https://challenge-files.cylabacademy.net/library/164023ae7e53a7b325e50a82f7cd942427fd0f38084d555c162501500fc475c3/whitepages.txt) is all blank!

### Solución
```

┌──(kali㉿kali)-[~]
└─$ nano solucion.py       
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~]
└─$ python solucion.py      

academy

SEE PUBLIC RECORDS & BACKGROUND REPORT
5000 Forbes Ave, Pittsburgh, PA 15213
academy{not_all_spaces_are_created_equal_d4c2f3dcae81af992c8e86ddecdf2dd5}


```

### Notas adicionales
- **Concepto de Esteganografía de espacios en blanco:** Este reto es un ejemplo clásico de esteganografía, la técnica de ocultar información dentro de otro formato que no levante sospechas. En este caso específico, se aprovechan los caracteres invisibles o no imprimibles para introducir datos.

- **Importancia de la lectura binaria:** Es un error muy común intentar copiar y pegar el texto del archivo o leerlo en Python usando el modo de texto normal (`'r'`). Muchos sistemas operativos e IDEs normalizan automáticamente los espacios Unicode inusuales convirtiéndolos en espacios estándar, lo que destruiría permanentemente el código binario y haría imposible resolver el reto. Siempre se debe manejar la información forense "en crudo" (raw bytes).

### Referencias
