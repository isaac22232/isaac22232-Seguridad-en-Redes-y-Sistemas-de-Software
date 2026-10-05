### Descripción
Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another. What's the final one? Image: [dolls.jpg](https://challenge-files.cylabacademy.net/library/370b91d430bc7ec8382557bcd2fba17a0e4e8ff86df14476a40c9f4b91276fa8/dolls.jpg)

### Solución
```
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/forensic/webnet1/matrioska]
└─$ cd base_images 
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/forensic/webnet1/matrioska/base_images]
└─$ ls
2_c.jpg
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/forensic/webnet1/matrioska/base_images]
└─$ unzip 2_c.jpg  
Archive:  2_c.jpg
warning [2_c.jpg]:  187707 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/3_c.jpg     
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/forensic/webnet1/matrioska/base_images]
└─$ ls
2_c.jpg  base_images
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/forensic/webnet1/matrioska/base_images]
└─$ cd base_images 
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/webnet1/matrioska/base_images/base_images]
└─$ ls
3_c.jpg
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/webnet1/matrioska/base_images/base_images]
└─$ open 3_c.jpg 
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/webnet1/matrioska/base_images/base_images]
└─$ unzip 3_c.jpg 
Archive:  3_c.jpg
warning [3_c.jpg]:  123606 extra bytes at beginning or within zipfile
  (attempting to process anyway)
  inflating: base_images/4_c.jpg     
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/webnet1/matrioska/base_images/base_images]
└─$ ls
3_c.jpg  base_images
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/webnet1/matrioska/base_images/base_images]
└─$ cd base_images 
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/matrioska/base_images/base_images/base_images]
└─$ unzip 4_c.jpg 
Archive:  4_c.jpg
warning [4_c.jpg]:  79578 extra bytes at beginning or within zipfile
  (attempting to process anyway)
 extracting: flag.txt                
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/matrioska/base_images/base_images/base_images]
└─$ ls
4_c.jpg  flag.txt
                                                                                                                                                                                                                                           
┌──(kali㉿kali)-[~/…/matrioska/base_images/base_images/base_images]
└─$ cat flag.txt    
academy{ZNTyvSDXRNO1d0xCkBRMhAoiafpCTvgW}


```

### Notas adicionales


### Referencias