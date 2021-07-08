#sysprog - dsh
###2021-07-09
1. overview

*super putty와 유사한 프로그램이다.

*server에 client가 접속하면 server에서 client의 terminal을 remote control할 수 있다.

*ui thread에서 키보드 인풋을 받고 어떤 client로 명령어를 보내고 결과값을 받아 화면에 출력할 것인지 정한다.

*ctrl^c 를 누르면 client를 바꾼다.

2. 소감
* 명령어를 주고 결과값을 주고 받는 것 자체는 어렵지 않았다. dup2를 사용해 stdout을 socket으로 redirect하면 된다. ui를 어떻게 구현할 것인지 지금으로서는 복잡해보인다.
client side에도 thread 2개가 돌아가야 한다는데 고민을 좀 더 하고 조금 더 구조를 정리해보아야할 것 같다.
