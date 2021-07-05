# sysprog
## chat server/client
### 2021-07-05
1. setsockopt() and TCP_NODELAY

TCP_NODELAY 를 설정해주면 socket을 unbuffered한 상태로 만들어준다

Latency를 줄여주지만 효율은 떨어진다.

Interactive한 프로그램에서 필요한 설정이다.

[reference](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux_for_real_time/7/html/tuning_guide/tcp_nodelay_and_small_buffer_writes)

2. fcntl() and blocking/unblocking

```c
// Test if the socket is in non-blocking mode:
if(fcntl(sockfd, F_GETFL) & O_NONBLOCK) {
    // socket is non-blocking
}

// Put the socket in non-blocking mode:
if(fcntl(sockfd, F_SETFL, fcntl(sockfd, F_GETFL) | O_NONBLOCK) < 0) {
    // handle error
}
```
[reference](https://stackoverflow.com/questions/6326064/c-c-sockets-and-a-non-blocking-recv)
