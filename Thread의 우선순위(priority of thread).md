
#### Thread의 우선순위

- 작업의 중요도에 따라 쓰레드의 우선순위를 다르게 하여 특정 스레드가 더 많은 작업시간을 갖게 할 수 있다.
```java
void setPriority(int newPriority) // 쓰레드의 우선순위를 지정한 값으로 변경한다.
int getPriority() // 쓰레드의 우선순위를 반환한다.

public static final int MAX_PRIORITY = 10 //최대 우선 순위
public static final int MIN_PRIORITY = 1 //최소 우선 순위
public static final int NORM_PRIORITY = 5 // 보통 우선 순위
```

- 우리 주위에 우선순위가 높은 것은 : 마우스 포인터가 있다.

- 아무리 우선 순위를 높게 주더라도 확정적으로 높은 우선순위에 있는 스레드가 먼저 작업을 실행하지는 않는다. -> os 스케쥴러에 참고 일 뿐 우선순위를 완전히 바꾸는 것이 아니기 때문이다. 