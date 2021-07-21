# 2021-07-21
0. Software testing 순서
프로그램을 먼저 짜고 test를 하는게 아니라 test case(scenario)를 먼저 만들어 놓고 프로그램을 만든다.  
scenario를 먼저 생각해 놓아야 나중에 debugging하기 수월하다.  
scheduler 같이 reactive한 프로그램에서 더욱 신경써야하는 부분.  
Test case를 만들 때 필요한 function들의 api를 미리 정해서 여러명이서 test case를 만들거나 프로그램을 만들 때 호환될 수 있도록 하기

1. priority 구현
range: [-10, 10], default 0  
int getpriority(int pid,  int * prio) : process 'pid'의 priority를 prio에 반환. pid가 0인 경우 current process의 priority를 prio에 반환.  
성공하면 0을 return, ptable에 pid가 없거나 기타 에러가 발생하면 -1을 return.  
// POSIX에서는 prio를 바로 반환해주고 -1인 경우 errno를 통해 -1이 의미하는 것이 failure/priority인지 확인하도록 되어있는데,  
xv6에서는 errno가 따로 없는 듯 하여 포인터로 반환하도록 함.  
int setpriority(int pid, int prio): process 'pid'의 priority를 prio로 설정. pid가 0인 경우 current process의 priority를 설정.  
성공하면 0을 return. ptable에 pid가 없거나, prio가 out of range이거나 기타 에러가 발생하면 -1을 return 한다.
  
2. Strict(fixed) priority scheduling vs soft priority scheduling
Strict priority scheduling과 달리 soft priority scheduling에서는 low priority process들이 starve하는 경우를 해소시키고자 이들의 priority를 높이는 일을 한다.  
하지만 이 경우 priority 자체를 설정하는게 무의미해질 수 있기 때문에 보통 priority를 일시적으로 boost 해주고 다시 원래 priority로 복구하는 방식을 씉다고 함.  

3. Timer interrupt
xv6에서는 0.01 초마다 timer interrupt가 발생함. Timer interrupt가 발생하면 global 변수인 ticks라는 counter를 increment하고 yield()한다(scheduler로 return).  

