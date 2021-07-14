# 2021-07-14
1. Variadic functions (C)  

불특정 개수의 arguement를 받는 함수. C에서는 제일 첫 arguement의 data type를 지정해줘야한다.  
몇개의 arguement들이 들어왔는지 확인할 수 있는 general한 방법은 없다. 함수를 디자인하는 사람의 몫이다.  
보통 첫 arguement로 갯수를 받는 방법, bitmask를 사용하는 방법, 마지막 arguement를 null로 주는 방법 등이 있다.  
C에서는 va_list라는 data type로 arguement pointer로 사용한다. va_start()로 va_list를 초기화해주고 va_arg()로 다음 arguement를 접근한다.  
xv6의 printf와 cprintf에서는 따로 arguement의 개수를 확인하는 작업이 없는 듯 하다.  

[reference](https://www.gnu.org/software/libc/manual/html_node/Variadic-Functions.html)

2. Inline assembly

format
asm asm-qualifiers ( AssemblerTemplate  // assembly code 에 해당하는 부분
                      : OutputOperands  // AssemblerTemplate이 사용할 C 변수를 담은 comma seperated list(생략가능)
                      : InputOperands   // AssemblerTemplate으로부터 읽어들일 C expression을 담은 comma seperated list(생략가능)
                      : Clobbers  // Output 이외에 AssemblerTemplate이 변환할 register나 value등을 담은 comma seperated list(생략가능)
                      : GotoLabels)  // goto 형식의 asm를 사용할 때 goto가능한 모든 C label을 담은 list

[reference](https://gcc.gnu.org/onlinedocs/gcc/Extended-Asm.html#Extended-Asm)

3. 느낀 점

Variadic functions를 보면서 C에 대해 아직 잘 모르는 것도 많구나 느꼈다.   
printf나 execl 등등 함수들을 보면서 대충 arguement 개수가 특정되지 않은 함수들이 있겠구나 지레짐작만 하고 있었는데 자세하게 살펴본 것은 처음이었다.  
오늘 printf.c랑 console.c를 보면서 여기저기 코드 따라가고 keep track하느라 정신이 없었던 것 같다.  
main함수를 먼저 쭉 읽어볼 필요가 있을 것 같다.
