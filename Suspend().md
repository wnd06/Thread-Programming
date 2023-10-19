
### Suspend()

-  스레드의 실행을 일시정지.

```java
void suspend() 스레드를 일시정지 시킨다.
void resume() suspend()에 의해 일시정지된 스레드를 실행대기 상태로 만든다.
void stop() 스레드 즉시 종료시킨다.
```

- deprecated 사용권장 하지 않는다. -> dead - lock(교착상태)을 일으킬 가능성이 있기 때문이다.
- dead - lock : 두 스레드가 서로 자기한테 필요한 것들을 갖고있어서 작업이 진행이 안되는 것
	- A thread가 B thread B가 A가 원하는 걸 가지고 있고 B 또한 B가 원하는 것을 A가 가지고 있어서 대치 상태가 된다.