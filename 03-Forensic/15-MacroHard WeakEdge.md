### Descripción
I've hidden a flag in this file. Can you find it? [Forensics_is_fun.pptm](https://challenge-files.cylabacademy.net/library/ef35dfe613527d28fe872d94179b53bc1a0497ddecf57e51d160c910be3a8e8a/Forensics_is_fun.pptm)

### Solución
```
┌──(kali㉿kali)-[~/macro]
└─$ cd ppt/slideMasters/ 
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/macro/ppt/slideMasters]
└─$ ls
hidden  _rels  slideMaster1.xml
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/macro/ppt/slideMasters]
└─$ open hidden
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/macro/ppt/slideMasters]
└─$ cat hidden                              
Z m x h Z z o g Y W N h Z G V t e X t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/macro/ppt/slideMasters]
└─$ cat hidden | tr -d ' '
ZmxhZzogYWNhZGVteXtEMWRfdV9rbjB3X3BwdHNfcl96MXA1fQ                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/macro/ppt/slideMasters]
└─$ cat hidden | tr -d ' ' | base64 -d
flag: academy{D1d_u_kn0w_ppts_r_z1p5}                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/macro/ppt/slideMasters]


```

### Notas adicionales
Los archivos ppt pueden ser zip


### Referencias