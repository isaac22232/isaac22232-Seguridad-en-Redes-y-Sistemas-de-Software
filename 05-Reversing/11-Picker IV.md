### Descripción
Can you figure out how this program works to get the flag?

### Solución
```
┌──(kali㉿kali)-[~/reversing]
└─$ nm picker-IV                                               
000000000040038c r __abi_tag
0000000000404068 B __bss_start
0000000000404070 b completed.0
0000000000404058 D __data_start
0000000000404058 W data_start
00000000004011d0 t deregister_tm_clones
00000000004011c0 T _dl_relocate_static_pie
0000000000401240 t __do_global_dtors_aux
0000000000403e00 d __do_global_dtors_aux_fini_array_entry
0000000000404060 D __dso_handle
0000000000403e08 d _DYNAMIC
0000000000404068 D _edata
0000000000404078 B _end
                 U exit@GLIBC_2.2.5
                 U fclose@GLIBC_2.2.5
                 U fgetc@GLIBC_2.2.5
00000000004013e0 T _fini
                 U fopen@GLIBC_2.2.5
0000000000401270 t frame_dummy
0000000000403df8 d __frame_dummy_init_array_entry
00000000004021bc r __FRAME_END__
0000000000403fe8 d _GLOBAL_OFFSET_TABLE_
                 w __gmon_start__
000000000040209c r __GNU_EH_FRAME_HDR
0000000000401000 T _init
0000000000402000 R _IO_stdin_used
                 U __isoc99_scanf@GLIBC_2.7
                 U __libc_start_main@GLIBC_2.34
0000000000401343 T main
                 U printf@GLIBC_2.2.5
0000000000401276 T print_segf_message
                 U putchar@GLIBC_2.2.5
                 U puts@GLIBC_2.2.5
0000000000401200 t register_tm_clones
                 U setvbuf@GLIBC_2.2.5
                 U signal@GLIBC_2.2.5
                 U sleep@GLIBC_2.2.5
0000000000401190 T _start
0000000000404068 B stdout@GLIBC_2.2.5
0000000000404068 D __TMC_END__
00000000004012a1 T win


                                                                                                                    
┌──(kali㉿kali)-[~/reversing]
└─$ chmod +x picker-IV
                                                                                                                    
┌──(kali㉿kali)-[~/reversing]
└─$ ./picker-IV    
Enter the address in hex to jump to, excluding '0x': 4012a1
You input 0x4012a1
You won!

                                                                                                                    
┌──(kali㉿kali)-[~/reversing]
└─$ nc chatelaine.cylabacademy.net 28528
Enter the address in hex to jump to, excluding '0x': 4012a1
You input 0x4012a1
You won!
academy{n3v3r_jump_t0_u53r_5uppl13d_4ddr35535_cd521e4c}

```

### Notas adicionales


### Referencias
