# IMAGE-DOS Header
```cpp
typedef struct _IMAGE_DOS_HEADER {
    WORD   e_magic;       // 0x00: Magic number
    WORD   e_cblp;        // 0x02: Bytes on last page of file
    WORD   e_cp;          // 0x04: Pages in file
    WORD   e_crlc;        // 0x06: Relocations
    WORD   e_cparhdr;     // 0x08: Size of header in paragraphs
    WORD   e_minalloc;    // 0x0A: Minimum extra paragraphs needed
    WORD   e_maxalloc;    // 0x0C: Maximum extra paragraphs needed
    WORD   e_ss;          // 0x0E: Initial (relative) SS value
    WORD   e_sp;          // 0x10: Initial SP value
    WORD   e_csum;        // 0x12: Checksum
    WORD   e_ip;          // 0x14: Initial IP value
    WORD   e_cs;          // 0x16: Initial (relative) CS value
    WORD   e_lfarlc;      // 0x18: File address of relocation table
    WORD   e_ovno;        // 0x1A: Overlay number
    WORD   e_res[4];      // 0x1C: Reserved words
    WORD   e_oemid;       // 0x24: OEM identifier (for e_oeminfo)
    WORD   e_oeminfo;     // 0x26: OEM information; e_oemid specific
    WORD   e_res2[10];    // 0x28: Reserved words
    LONG   e_lfanew;      // 0x3C: File address of new exe header
} IMAGE_DOS_HEADER, *PIMAGE_DOS_HEADER;    // Size = 0x40 or 64 bytes

```

# IMAGE-DOS File Header
```cpp
typedef struct _IMAGE_FILE_HEADER {
    WORD    Machine;              // 0x00: The architecture type of the computer
    WORD    NumberOfSections;     // 0x02: The number of sections
    DWORD   TimeDateStamp;        // 0x04: The time that the image was created
    DWORD   PointerToSymbolTable; // 0x08: The offset of the symbol table
    DWORD   NumberOfSymbols;      // 0x0C: The number of symbols
    WORD    SizeOfOptionalHeader; // 0x10: The size of the optional header
    WORD    Characteristics;      // 0x12: The characteristics of the image
} IMAGE_FILE_HEADER, *PIMAGE_FILE_HEADER;  // Size = 0x14 or 20 bytes
```

# IMAGE-OPTIONAL_HEADER
```cpp
typedef struct _IMAGE_OPTIONAL_HEADER {
    WORD    Magic;                         // 0x00: The state of the image file
    BYTE    MajorLinkerVersion;            // 0x02: The major version number of the linker
    BYTE    MinorLinkerVersion;            // 0x03: The minor version number of the linker
    DWORD   SizeOfCode;                    // 0x04: The size of the code section
    DWORD   SizeOfInitializedData;         // 0x08: The size of the initialized data section
    DWORD   SizeOfUninitializedData;       // 0x0C: The size of the uninitialized data section
    DWORD   AddressOfEntryPoint;           // 0x10: A pointer to the entry point function
    DWORD   BaseOfCode;                    // 0x14: A pointer to the beginning of the code section
    ULONGLONG   ImageBase;                 // 0x18: The preferred address of the first byte of the image when loaded into memory
    DWORD   SectionAlignment;              // 0x20: The alignment of sections loaded into memory
    DWORD   FileAlignment;                 // 0x24: The alignment factor used to align the raw data of sections in the image file
    WORD    MajorOperatingSystemVersion;   // 0x28: The major version number of the required operating system
    WORD    MinorOperatingSystemVersion;   // 0x2A: The minor version number of the required operating system
    WORD    MajorImageVersion;             // 0x2C: The major version number of the image
    WORD    MinorImageVersion;             // 0x2E: The minor version number of the image
    WORD    MajorSubsystemVersion;         // 0x30: The major version number of the subsystem
    WORD    MinorSubsystemVersion;         // 0x32: The minor version number of the subsystem
    DWORD   Win32VersionValue;             // 0x34: Reserved, must be zero
    DWORD   SizeOfImage;                   // 0x38: The size of the image, including all headers, as the image is loaded in memory
    DWORD   SizeOfHeaders;                 // 0x3C: The combined size of an MS‐DOS stub, PE header, and section headers rounded up to a multiple of FileAlignment
    DWORD   CheckSum;                      // 0x40: The image file checksum
    WORD    Subsystem;                     // 0x44: The subsystem that the image is required to run on
    WORD    DllCharacteristics;            // 0x46: The DLL characteristics of the image
    ULONGLONG   SizeOfStackReserve;         // 0x48: The size of the stack to reserve
    ULONGLONG   SizeOfStackCommit;          // 0x50: The size of the stack to commit
    ULONGLONG   SizeOfHeapReserve;          // 0x58: The size of the local heap space to reserve
    ULONGLONG   SizeOfHeapCommit;           // 0x60: The size of the local heap space to commit
    DWORD   LoaderFlags;                   // 0x68: Reserved, must be zero
    DWORD   NumberOfRvaAndSizes;           // 0x6C: The number of data-directory entries in the remainder of the Optional Header
    IMAGE_DATA_DIRECTORY DataDirectory[IMAGE_NUMBEROF_DIRECTORY_ENTRIES]; // 0x70: Array of IMAGESure, here is the continuation:
} IMAGE_OPTIONAL_HEADER64, *PIMAGE_OPTIONAL_HEADER64;  // Size = 0xF0 or 240 bytes
```

# IMAGE_DATA_DIRECTORY
```cpp
typedef struct _IMAGE_DATA_DIRECTORY {
    DWORD   VirtualAddress;    // The relative virtual address of the table
    DWORD   Size;              // The size of the table, in bytes
} IMAGE_DATA_DIRECTORY, *PIMAGE_DATA_DIRECTORY;
```

# IMAGE_SECTION_HEADER
```cpp
typedef struct _IMAGE_SECTION_HEADER {
    BYTE    Name[IMAGE_SIZEOF_SHORT_NAME]; // 0x00: An 8-byte, null-padded UTF-8 encoded string
    union {
        DWORD   PhysicalAddress;           // 0x08: The physical address of the section
        DWORD   VirtualSize;               // 0x08: The virtual size of the section
    } Misc;
    DWORD   VirtualAddress;                // 0x0C: The virtual address of the section
    DWORD   SizeOfRawData;                 // 0x10: The size of the section data
    DWORD   PointerToRawData;              // 0x14: A pointer to the first page of the section
    DWORD   PointerToRelocations;          // 0x18: A pointer to the beginning of the relocation entries for the section
    DWORD   PointerToLinenumbers;          // 0x1C: A pointer to the beginning of the line-number entries for the section
    WORD    NumberOfRelocations;           // 0x20: The number of relocation entries for the section
    WORD    NumberOfLinenumbers;           // 0x22: The number of line-number entries for the section
    DWORD   Characteristics;               // 0x24: The characteristics of the image
} IMAGE_SECTION_HEADER, *PIMAGE_SECTION_HEADER;  // Size = 0x28 or 40 bytes
```

# IMAGE_IMPORT_DESCRIPTOR
```cpp
typedef struct _IMAGE_IMPORT_DESCRIPTOR {
   union {
       DWORD   Characteristics;             // 0x00: 0 for terminating null import descriptor
       DWORD   OriginalFirstThunk;          // 0x00: RVA to original unbound IAT (PIMAGE_THUNK_DATA)
   };
   DWORD   TimeDateStamp;                   // 0x04: 0 if not bound,
                                           // -1 if bound, and real date\time stamp
                                           //     in IMAGE_DIRECTORY_ENTRY_BOUND_IMPORT (new BIND)
                                           // O.W. date/time stamp of DLL bound to (Old BIND)

   DWORD   ForwarderChain;                  // 0x08: -1 if no forwarders
   DWORD   Name;                            // 0x0C: RVA to DLL name
   DWORD   FirstThunk;                      // 0x10: RVA to IAT (if bound this IAT has actual addresses)
} IMAGE_IMPORT_DESCRIPTOR;
```

# IMAGE_THUNK_DATA
```cpp
typedef struct _IMAGE_THUNK_DATA {
   union {
       DWORD ForwarderString;   // If the function is forwarded to another DLL, this is the address of the string that gives the DLL name and function name
       DWORD Function;          // If the executable is bound, this is the address of the imported function
       DWORD Ordinal;           // If the function is imported by ordinal, this is the ordinal value
       DWORD AddressOfData;     // If the function is imported by name, this is the address of an IMAGE_IMPORT_BY_NAME structure
   } u1;
} IMAGE_THUNK_DATA;
```

# IMAGE_IMPORT_BY_NAME
```cpp
typedef struct _IMAGE_IMPORT_BY_NAME {
    WORD    Hint;         // An index into the export name pointer table of the DLL
    BYTE    Name[1];      // The name of the imported function, as a null-terminated ASCII string
} IMAGE_IMPORT_BY_NAME;
```
