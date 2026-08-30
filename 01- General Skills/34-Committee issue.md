### Descripcion
I accidentally wrote the flag down. Good thing I deleted it!

You download the challenge files here:

- [challenge.zip](https://artifacts.picoctf.net/c_titan/76/challenge.zip)

### Solucion
```
Luck222-academy@webshell:~/drop-in$ wget https://artifacts.picoctf.net/c_titan/76/challenge.zip
--2026-08-30 03:06:52--  https://artifacts.picoctf.net/c_titan/76/challenge.zip
Resolving artifacts.picoctf.net (artifacts.picoctf.net)... 3.160.5.64, 3.160.5.18, 3.160.5.95, ...
Connecting to artifacts.picoctf.net (artifacts.picoctf.net)|3.160.5.64|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 19201 (19K) [application/octet-stream]
Saving to: 'challenge.zip'

challenge.zip                                              100%[======================================================================================================================================>]  18.75K  --.-KB/s    in 0.008s  

2026-08-30 03:06:52 (2.38 MB/s) - 'challenge.zip' saved [19201/19201]

Luck222-academy@webshell:~/drop-in$ git --version
git version 2.34.1
Luck222-academy@webshell:~/drop-in$ git log

[1]+  Stopped                 git log
Luck222-academy@webshell:~/drop-in$ git checkout <e720dc26a1a55405fbdf4d338d465335c439fb3e>
-bash: syntax error near unexpected token `newline'
Luck222-academy@webshell:~/drop-in$ git checkout e720dc26a1a55405fbdf4d338d465335c439fb3e 
Note: switching to 'e720dc26a1a55405fbdf4d338d465335c439fb3e'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by switching back to a branch.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -c with the switch command. Example:

  git switch -c <new-branch-name>

Or undo this operation with:

  git switch -

Turn off this advice by setting config variable advice.detachedHead to false

HEAD is now at e720dc2 create flag
Luck222-academy@webshell:~/drop-in$ cat message.txt 
picoCTF{s@n1t1z3_7246792d}
```

### Notas adicionales
git checkout te deja volver a una version anterior del programa

### Referencias
