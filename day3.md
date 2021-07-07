# sysprog -dropbox
### 2021-07-07

1. conditional statements 내의 boolean operator를 괄호로 잘 묶어주자
오늘 recv()로 int를 주고받는 함수에서 괄호를 하나 잘못 쳐서 오후 내내 애를 먹었다.
```c
//before
while (len < sizeof(int) && (r = recv(sock, _data, sizeof(int)-len, 0) > 0))
```
```c
//after
while (len < sizeof(int) && (r = recv(sock, _data, sizeof(int)-len, 0)) > 0)
```
boolean operator를 사용할 때에는 그냥 아예 괄호로 구역을 확실하게 나누어줘도 될듯 하다
```c
//확실하게
while ((len < sizeof(int)) && 
       ((r = recv(sock, _data, sizeof(int)-len, 0)) > 0))
```
코드 한 줄이 길어질 수는 있겠지만 better safe than sorry

2. how to ensure atomicity and maximize concurrency
오늘 이부분을 좀 고민했어야 했는데 위의 문제로 진도를 못나갔다.
좀 더 깊이있게 생각해보면 고려해야할 시나리오들이 너무 많다.
lock이 필요한 곳이 어디고(list 접근, file read/write 등등?)
file을 전송하는 중에 disconnect되거나 server나 client가 죽으면 어떻게 하고(제대로 하려면 임시파일에다 저장하는 형식으로)
같은 파일에 대한 get와 put이 동시에 일어난다면?(maybe lock? or inotify를 통해 파일이 열려있는 상태를 미리 파악해 대비, 사용자에게 어떻게 할건지 물어보게 하는게 베스트)


3. 
