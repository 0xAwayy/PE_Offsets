# IMAGE-DOS Header
```cpp
align = 0x4, size = 0x40 (64 bytes)
00000000 e_magic         dw ? (magic number)
00000002 e_cblp          dw ? (chip id)
00000004 e_cp            dw ? (pages)
00000006 e_crlc          dw ? (relocs)
00000008 e_cparhdr       dw ? (header sizes)
0000000A e_minalloc      dw ? (min allocation for par)
0000000C e_maxalloc      dw ? (max allocation for par)
0000000E e_ss            dw ? (initial SS val)
00000010 e_sp            dw ? (initial SP val)
00000012 e_csum          dw ? (checksum)
00000014 e_ip            dw ? (initial IP value)
00000016 e_cs            dw ? (initial CS value)
00000018 e_lfarlc        dw ? (relocation table addr)
0000001A e_ovno          dw ? (Overlay Num)
0000001C e_res           dw 4 dup(?) (Reserved)
00000024 e_oemid         dw ? (OEM Identifier)
00000026 e_oeminfo       dw ? (OEM Info)
00000028 e_res2          dw 10 dup(?) (Reserved)
0000003C e_lfanew        dd ? (lfa = location of file address, n = new, presumably location of new file address)
00000040 _IMAGE_DOS_HEADER ends
00000040
```
