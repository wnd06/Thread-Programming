
### Thread 구현 방법

#### 1. Thread 상속
```java
class MyThread extends Thread {
	public void run() { //오버라이딩
	//작업내용
	}
}

Mythread t1 = new MyThread();
t1.start();
```

#### 2. Runnable 인터페이스를 구현 

- 상속보다 인터페이스 구현이 더 낫다.
	- 상속은 하나 밖에 안되기 때문이다.

```java
class Mythread2 implements Runnable {
	public void run() { //추상메서드 run()구현
	//작업내용
	}
}

Thread t2 = new Thread(new Mythread2);
t2.start();
```


### 스레드 실행 - start()

- 스레드를 생성한 후 start()를 호출해야 스레드가 작업을 시작한다.

- 두 개의 스레드를 생성을 했더라도 두 개의 스레드 중 어느 것이 먼저 시작할 지는 모른다.
	- os 스케쥴러가 실행순서 결정.

- start() 메서드를 호출하게 되면 새로운 호출스택을 생성하게 된다. ![[스크린샷 2023-10-17 오후 2.28.27.png]]

- 서로 독립적으로 작업을 수행하게 된다.