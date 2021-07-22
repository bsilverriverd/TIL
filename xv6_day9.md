# 2021-07-22
1. What exec() does
+ creates a new page directory //setupkvm()  
+ loads program into memory // allocuvm(), loaduvm()
+ creates user stack and save arguements // copyout()
+ commit to the user image  

2. Physical memory(page) management
+ Uses the kalloc.c for physical memory management  
+ Initializes a freelist of physical memory in main(). // kinit1(), kinit2()  

3. 배운점  
+ xv6의 memory layout이 어떻게 되어있는지
+ Virtual address가 physical address에 어떻게 map 되는지.
+ freelist와 entrypagedir와의 관계, 정확히 어떻게 initialize되고 유지되는지 좀 더 자세히 볼 필요가 있겠다.  
