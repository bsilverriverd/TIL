# 2021-07-12
1. BIOS

Kernel을 Load하기 위한 일종의 간이 OS

2. Boot Loader

BIOS에서 Kernel을 Load하는 실질적 프로그램이다. 오로지 Kernel을 Load하고 소멸하는 것이 목적이다. 마치 Sicilian Defense에서 c5 pawn처럼.

3. GDB commands

+ b *(addr): Add breakpoint
+ c : execute until it meets a breakpoint
+ x/i (addr) : show N lines of instructions starting at (addr)
+ x/x (addr) : show memory status at (addr)
+ si : extecute next instruction

4. QEMU

QEMU (short for Quick EMUlator) is a free and open-source emulator and virtualizer that can perform hardware virtualization.

4. 내일 먼저 해볼 것

*call *0x10018에 breakpoint 설정하고 0x10018이 담고 있는 주소가 가리키는 instruction이 무엇인지 찾아보기

5. 공부하면서 느낀 점

+ Assembly code와 C code는 line by line을 딱딱 들어맞지 않는다. jump instruction들을 유심히 봐야한다. OS 수업 때 들은 내용이 벌써 가물가물해지는 것 같다 ...
