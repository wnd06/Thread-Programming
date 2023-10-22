
#### Dead Lock

- 동기화를 통해 락을 획득하여 동일한 자원을 여러 곳에서 함부로 사용하지 못하도록 하였습니다. 하지만 두 개의 쓰레드에서 서로가 가지고 있는 락이 해제되기를 기다리는 상태가 생길 수 있으며 이러한 상태를 **교착상태(deadlock)** 이라고 합니다.
- 교착상태가 되면 어떤 작업도 실행되지 못하고 서로 상대방의 작업이 끝나기만 바라는 무한정 대기 상태입니다.

#### Dead Lock 발생조건

- **상호 배제 (Mutual Exclusion)** : 한 자원에 대해 여러 쓰레드 동시 접근 불가
    
- **점유와 대기 (Hold and Wait)** : 자원을 가지고 있는 상태에서 다른 쓰레드가 사용하고 있는 자원 반납을 기다리는 것
    
- **비선점 (Non Preemptive)** : 다른 쓰레드의 자원을 실행 중간에 강제로 가져올 수 없음
    
- **환형대기 (Circle Wait)** : 각 쓰레드가 순환적으로 다음 쓰레드가 요구하는 자원을 가지고 있는 것


위의 4가지 조건을 모두 충족할 경우 데드락이 발생하게 됩니다. 반대로 말하면, 위 4가지 중 하나라도 충족하지 않을 경우 데드락을 해결할 수 있다는 뜻이기도 합니다.

#### 데드락 실습
```java
public class TestCircularWaitDeadlock {  
    public static void main(String[] args) {  
        Object resource1 = new Object();  
        Object resource2 = new Object();  
  
        Thread task1 = new Thread(() -> {  
            synchronized (resource1) {  
                System.out.println("First Thread has resource1's lock");  
  
                try {  
                    Thread.sleep(1000);  
                } catch (InterruptedException e) {}  
  
                System.out.println("First Thread want to have resource2's lock so wait.");  
  
                synchronized (resource2) {  
                    System.out.println("First Thread has resource2's lock too");  
                }  
            }  
  
        });  
        Thread task2 = new Thread(()-> {  
            synchronized (resource2) {  
                System.out.println("Second Thread has resource2's lock");  
  
                try {  
                    Thread.sleep(1000);  
                } catch (InterruptedException e) {}  
                System.out.println("Second Thread want to have resource1's lock so wait.");  
  
                synchronized (resource1) {  
                    System.out.println("Second Thread has resource1's lock too");  
                }  
            }  
  
  
        });  
        task1.start();  
        task2.start();  
    }  
}
```

1. 스레드가 동시에 실행이 됩니다. 첫 번째로 synchronized를 이용해 객체 하나에 스레드 하나만 올 수 있게 해놓았다. (상호 배제)

2. 다음 객체로 가기 위해 기다립니다. 다음 객체의 락을 얻기 위해 기다린다.(점유와 대기) (스레드는 코드가 끝나야 다음 작업을 실행 합니다.) 

3. 우선 순위는 기본 값을 해놓았다. (비선점)

4. synchronized 안의 또 하나의 synchronized가 실행 되어야 하는데 이미 들어가려는 객체에는 다른 스레드가 lock이 걸려 있어서(환형 대기) 현재 synchronized가 실행이 되지 않고 계속 wait 상태를 기다리고 있다.
