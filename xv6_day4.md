# 2021-0715
1. system calls

system call은 eac에 system call fuction을 저장하고 interrupt 64를 발생시킨다.  
(xv6에서는 trap와 interrupt를 동일한 것으로 취급한다. 보통은 trap은 current proccess가 발생시키는 것, interrupt는 current proccess와 연관이 없을 수도 있는 device에서 발생시키는 것)
(256가지 interrupt 중 0~31은 software exceptions, 32~63는 hardware exceptions, 64는 system call로 쓰인다)

trap handler에서 system call임을 판단하면 syscall()을 부른다. syscall()에서는 eax의 값을 읽어들여서 해당하는 system call을 수행한다.  
user space 내의 선언된 system call aarguement를 읽어들이기 위해 argint,  argptr, argstr 등의 함수를 사용한다.  

2. How processes are created and ended

exec()을 부르게 되면 processtable(ptable)에서 빈 슬롯(UNUSED)을 찾는다. 찾으면 EMBRYO state로 바꾸고 initialize 후 RUNNABLE state로 바뀐다.  
process가 exit()을 통해 terminate하게 되면 사용하던 file descriptor들을 모두 닫고 자기 parent를 wake한다. (wait을 하면서 SLEEPING state에 있을 수 있기 때문)  
종료되지 않은 child process들의 parent를 initproc으로 설정해준다.  
ZOMBIE state로 들어간다. (다른 process에서 wait해줘야 비로소 UNUSED 상태로 돌아간다)

3. 느낀 점

system call 하나를 수정하기 위해서 많은 노고가 필요하다는 것을 깨달았다. 그것이 쓰인 곳과 관련된 코드들을 다 일일이 다 수정해야하기 때문이다.  
user mode에서 kernel mode로 바뀔 때 kernel stack에 어떤 값이 들어가는지 정확하게 정리하고 넘어가야겠다. 
