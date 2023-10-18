### Sleep()

- 현재 스레드를 지정된 시간동안 멈추게한다.
	- 자기 자신을 멈추게 하기 때문에 static메소드이다.

- 예외처리흘 해야한다.(InterruptedExceptiondl 발생하면 깨어남)
	- 시간종료
	- Interrupted - 깨우는 것. 

- 특정 쓰레드를 지정해서 멈추게 하는 것은 불가능하다.

```java
try {
	th1.sleep(2000);
} catch(InterruptedExceptionv e) {}
```
- 위의 코드가 메인 스레드에서 호출을 하였지만 sleep()메서드를 적용한 것은 th1 스레드이다. 하지만 이 코드가 실행되게 된다면 th1이 sleep 되는 것이 아닌 메인 스레드가 sleep이 된다.

- 결국 sleep을 호출한 자기 자신이 sleep이 되는 것이다.