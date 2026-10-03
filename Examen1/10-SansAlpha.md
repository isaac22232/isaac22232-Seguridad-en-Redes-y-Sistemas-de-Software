### Descripción


### Solución
```

SansAlpha$ ls
SansAlpha: Unknown character detected
SansAlpha$ ./*
\x1b[?2004h\x1b[?2004l
bash: ./blargh: Is a directory
\x1b[?2004h
SansAlpha$ ./*/*
\x1b[?2004l
bash: ./blargh/flag.txt: Permission denied
\x1b[?2004h
SansAlpha$ /???????/????????? /???????????????/???????????????
\x1b[?2004l
bash: /???????/?????????: No such file or directory
\x1b[?2004h
SansAlpha$ /???/???[!_]64 /????/??????????/??????/????????
\x1b[?2004l
cmV0dXJuIDAgYWNhZGVteXs3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iZDQ5ZWUzZn0=
\x1b[?2004h
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/clab/fixme3/src]
└─$ sudo su                                       
[sudo] password for kali: 
┌──(root㉿kali)-[/home/kali/clab/fixme3/src]
└─# cd ..
                                                                                                                                                                                                                                           
┌──(root㉿kali)-[/home/kali/clab/fixme3]
└─# cd ..
                                                                                                                                                                                                                                           
┌──(root㉿kali)-[/home/kali/clab]
└─# cd ..
                                                                                                                                                                                                                                           
┌──(root㉿kali)-[/home/kali]
└─# echo "cmV0dXJuIDAgYWNhZGVteXs3aDE1X211MTcxdjNyNTNfMTVfbTRkbjM1NV9iZDQ5ZWUzZn0" | base64 -d   
return 0 
academy{7h15_mu171v3r53_15_m4dn355_bd49ee3f}   
```

### Notas adicionales


### Referencias