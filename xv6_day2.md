# 2021-07-13
1. ELF(Executable Linking Format)

- Three main types of object files: relocatable file, executable file, shared object file
- sections: provide a linking view of the object file
- segments: group of sections and provide an executable view of the object file

[reference](https://refspecs.linuxfoundation.org/elf/elf.pdf)


2. entry.S

enables paging and creates the first page directory(changes address mode), then jumps to main

controls 3 control registers

- CR4: set PSE bit to increase page size to 4MiB
- CR3: stores physical address of the first page directory
- CR0: Set PG(to enable paging) and WP(CPU can't write to read only pages when privilege level is 0) bits

[reference](https://en.wikipedia.org/wiki/Control_register)

3. 느낀 점

- 1차자료 또는 official document들을 잘 찾아보자
- 대충 쓱 훑어보고 이해했다는 착각을 하지 말자
