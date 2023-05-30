# IMAGE-DOS Header
```cpp
align = 0x4, size = 0x40 (64 bytes)
00000000 e_magic         dw ?
00000002 e_cblp          dw ?
00000004 e_cp            dw ?
00000006 e_crlc          dw ?
00000008 e_cparhdr       dw ?
0000000A e_minalloc      dw ?
0000000C e_maxalloc      dw ?
0000000E e_ss            dw ?
00000010 e_sp            dw ?
00000012 e_csum          dw ?
00000014 e_ip            dw ?
00000016 e_cs            dw ?
00000018 e_lfarlc        dw ?
0000001A e_ovno          dw ?
0000001C e_res           dw 4 dup(?)
00000024 e_oemid         dw ?
00000026 e_oeminfo       dw ?
00000028 e_res2          dw 10 dup(?)
0000003C e_lfanew        dd ?
00000040 _IMAGE_DOS_HEADER ends
00000040
```
