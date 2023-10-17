
### 데몬 스레드

- 일반 스레드(non-daemon thread)의 작업을 돕는 보조적인 역할을 수행.
- 일반 스레드가 모두 종료되면 자동적으로 종료된다. -> 보조 스레드이기 떄문
- 가비지 컬렉터, 자동저장, 화면 자동갱신 등에 사용된다.
- 무한 루프와 조건문을 이용해서 실행 후 대기하다가 특정조건이 만족되면 작업을 수행하고 다시 대기 하도록 작성한다.
```java
public void run() {
	while(true) {
		try {
			Thread.sleep(3 * 1000); //3초 마다
		} catch(InterruptedException e) {}
		//autoSave의 값이 true이면 autoSave()를 호출한다.
		if(autoSave) {
			autoSave();
		}
	}
}

void setDaemon(boolean on) -> 스레드를 데몬 스레드로 또는 사용자 스레드로 변경 매개변수 on을 true 로 지정하면 데몬 스레드가 된다.
```

- setDaemon(boolean on) 은 반드시 start()를 호출하기 전에 실행되어야 한다. 그렇지 않으면 exception 발생.

- 무한 루프여도 일반 스레드가 종료되면 데몬 스레드도 종료되므로 상관이 없다.