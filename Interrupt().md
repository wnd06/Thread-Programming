
### Interrupt()

-  대기상태(WAITING)인 스레드를 실행대기 상태(RUNNABLE)로 만든다. ([[Thread의 상태]])
```java
void interrupt() // thread의 interrupted상태를 false에서 true로 변경.
boolean isInterrupted() // thread의 interrupted상태를 반환.
static boolean interrupted() // 현재 threaddml interrupted상태를 알려주고, false로 초기화
```
- 게임 continue를 할 때도 활용할 수 있다.

#### isInterrupted() 와 interrupted()의 차이점

1. interrupted()는 static 메소드이다. 그래서 [[Sleep()]]과 같이 호출한 자기자신 스레드의 interrupted 상태를 알려준다. (그래서 사용할 때 또한 Thread.interrupted()로 사용해야한다.)
```java
public class InterruptExam {  
    public static void main(String[] args) {  
        ThreadEx th1 = new ThreadEx();  
        th1.start();  
		...
        th1.interrupt();  
        System.out.println("isInterrupted():" + th1.isInterrupted());//true  
//        // 메인 스레드가 인터럽트 되었는지 확인  
        System.out.println("Interrupted():" + th1.interrupted()); //false
    }  
}
```
- 그래서 아무리 위에서 th1.interrupted()를 사용한다해도 **th1의 interrupt의 상태가 아니라 main 스레드의 interrupt 상태를 출력**해주기 때문에  사용할 때도 Thread.interrupted() 이런식으로 사용해주는 것이 맞다.

2. isInterrupted는 스레드의 interrupt 상태만 반환 해주지만 interrupted()는 상태변수를 반환과 동시에 false로 초기화한다.