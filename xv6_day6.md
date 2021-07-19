# 2021-07-19
1. multiprocess bugs
waitpid()에서 sleep()할 때 chan을 curproc이 아닌 p->parent로 설정해야함을 보이기 위한 test program을 만들었다.  
1) fork child1,  1.5)child1 exits, 2) fork child2 2.5) child2에서 waitpid(child1) 후 exit 3) parent에서 waitpid(child2)후에 exit.  
sleep()을 curproc에 대해서 했다면 2.5)에서 전체프로그램이 stop되어야한다고 생각했는데 어떤 경우에는 stop되고 어떤 경우에는 stop이 안되었다.  
그 이유는 2.5)가 1.5)보다 먼저 실행될 경우에만 stop이 되기 때문이었다.  
그래서 1.5)에 sleep(100)을 추가하여 1.5)가 먼저 실행되는 경우를 없앴다.

2. What happens when a trap occurs? -> 제일 먼저 trapframe을 만든다
+ processor pushes %ss, %esp, %eflags, %cs, %eip
+ processor or trap vector pushes error number
+ alltraps pushes the rest of the trapframe(%ds, %es, %fs, %gs, general purpose registers)  
[xv6 book page 42]

3. swtch
+ saves old context to stack and set registers to new context

4. Scheduling
+ scheduler loops through ptable, finds a runnable task and 'swtch'es to that context.  
+ sched is called to 'swtch' back to scheduler context

5. 느낀점
지난 주에 system calls 공부하면서 trap에 대해 다 이해했다고 생각했는데 놓친 부분이 많은 것 같다.
