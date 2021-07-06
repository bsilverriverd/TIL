# sysprog - dropbox
### 2021-07-06
1. inotify
파일시스템 내의 변화를 감지하려면 주기적으로 file의 modified time등을 모니터링해야한다.
이 라이브러리는 파일시스템 내에 생긴 변화를 "watch"하여 알려주기 때문에 편리하다.
```
struct inotify_event {
               int      wd;       /* Watch descriptor */
               uint32_t mask;     /* Mask describing event */
               uint32_t cookie;   /* Unique cookie associating related
                                     events (for rename(2)) */
               uint32_t len;      /* Size of name field */
               char     name[];   /* Optional null-terminated name */
           };
```
이 구조체를 사용해서 modified된 event를 알려준다.

[reference](https://www.thegeekstuff.com/2010/04/inotify-c-program-example/)
[reference2](https://man7.org/linux/man-pages/man7/inotify.7.html)

2. IO models
![alt-text](https://developer.ibm.com/developer/default/articles/l-async/images/figure1.gif "IOmodels")
[reference](https://developer.ibm.com/articles/l-async/)
