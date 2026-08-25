### Descripcion

Unzip this archive and find the file named 'uber-secret.txt'

- [Download zip file](https://artifacts.picoctf.net/c/501/files.zip)

### Solucion
```
Luck222-academy@webshell:~$ wget https://artifacts.picoctf.net/c/501/files.zip
Luck222-academy@webshell:~$ ls
files.zip
Luck222-academy@webshell:~$ unzip files.zip   
Luck222-academy@webshell:~$ cd files/a
acceptable_books/ adequate_books/   
Luck222-academy@webshell:~$ cd files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets/
Luck222-academy@webshell:~/files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets$ ls
uber-secret.txt
Luck222-academy@webshell:~/files/adequate_books/more_books/.secret/deeper_secrets/deepest_secrets$ cat uber-secret.txt 
picoCTF{f1nd_15_f457_ab443fd1}
```

### Notas adicionales


### Referencias
