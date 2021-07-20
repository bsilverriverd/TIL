# 2021-07-20
0. proc stucture에 priority field 추가하기

range를 0(high) ~ 31()low로 설정해주었다.  
priority를 int로 설정했는데 uchar로 하기 좋은 방법은 없을까??

1. getpriority(int pid) 구현

process 'pid'의 priority를 return한다. pid가 0이면 current process의 priority를 return한다.  
성공하면 pid의 priority를, 실패하면(ex. no pid) -1을 리턴한다.

2. setpriority(int pid, int prio) 구현

process 'pid'의 priority를 prio로 설정해준다. pid가 0이면 current process의 priority를 set해준다.  
priority가 변했기 때문에 yield()를 해주어 scheduler가 현재 가장 우선순위에 있는 process를 run하도록 한다.
성공하면 0을, 실패하면(ex. out of range, no pid) -1을 리턴한다.

[reference](https://linux.die.net/man/2/setpriority)  
[reference](https://www.ibm.com/docs/en/zos/2.2.0?topic=functions-setpriority-set-process-scheduling-priority)

3. fork()

fork할 때 priority를 0(highest)로 설정해준다.  parent의 priority를 물려받는 것도 alternative한 방법일 수 있다.

4. priority scheduling

ptable을 한번 scan해서 가장 highest priority가 무엇인지 찾은 다음에  
ptable을 가장 최근에 schedule되었던 process가 있는 위치(cursor)에서 scan을 시작해서 가장 먼저 찾는 highest priority를 가진 process로 swtch한다.  

ptable을 priority queue로 구현하면 어떨까?? state(unused, embryo, sleeping, runnable, running, zombie)와 priority에 따라서 heap을 유지할 수 있다면 꽤 괜찮을지도??
