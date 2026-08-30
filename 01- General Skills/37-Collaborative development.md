### Descripcion
My team has been working very hard on new features for our flag printing program! I wonder how they'll work together?

You can download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/178/challenge.zip)

### Solucion
```
Luck222-academy@webshell:~$ ls
challenge.zip  drop-in
Luck222-academy@webshell:~$ cd drop-in/
Luck222-academy@webshell:~/drop-in$ ls
flag.py
Luck222-academy@webshell:~/drop-in$ head flag.py
print("Printing the flag...")
Luck222-academy@webshell:~/drop-in$ git branch -a

[5]+  Stopped                 git branch -a
Luck222-academy@webshell:~/drop-in$ git checkout part-1 
error: pathspec 'part-1' did not match any file(s) known to git
Luck222-academy@webshell:~/drop-in$ git checkout feature/part-1
Switched to branch 'feature/part-1'
Luck222-academy@webshell:~/drop-in$ ls
flag.py
Luck222-academy@webshell:~/drop-in$ head flag.py 
print("Printing the flag...")
print("picoCTF{t3@mw0rk_", end='')Luck222-academy@webshell:~/drop-in$ 

Luck222-academy@webshell:~/drop-in$ git checkout feature/part-2
Switched to branch 'feature/part-2'
Luck222-academy@webshell:~/drop-in$ head flag.py 
print("Printing the flag...")
print("m@k3s_th3_dr3@m_", end='')Luck222-academy@webshell:~/drop-in$ git checkout feature/part-3
Switched to branch 'feature/part-3'
Luck222-academy@webshell:~/drop-in$ head flag.py 
print("Printing the flag...")

print("w0rk_6c06cec1}")
Luck222-academy@webshell:~/drop-in$ 

picoCTF{t3@mw0rk_m@k3s_th3_dr3@m_w0rk_6c06cec1}

```

### Notas adicionales


### Referencias
