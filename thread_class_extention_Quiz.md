
## thread_class_extention_Quiz

### Quiz-01
```java
public class Counter {  
    int count;  
    String name;  
    int maxCount;  
    public Counter(String name, int maxCount) {  
        this.maxCount = maxCount;  
        this.name = name;  
        this.count = 0;  
    }  
  
    public void run() {  
        try {  
            while(count != maxCount) {  
                Thread.sleep(1000);  
                System.out.println(name + " : " + ++count);  
            }  
        } catch (InterruptedException e) {  
            e.printStackTrace();  
        }  
  
    }  
  
  
    public static void main(String[] args) {  
        Counter counter = new Counter("Counter1", 10);  
        Counter counter2 = new Counter("Counter2", 10);  
        System.out.println(Thread.currentThread() + "start");  
        counter.run();  
        counter2.run();  
        System.out.println(Thread.currentThread() + "end");  
    }  
}
```


### Quiz-02
```java
  
public class ThreadCounter extends Thread{  
    int count;  
    String name;  
    int maxCount;  
  
    public ThreadCounter(String name, int maxCount) {  
        this.name = name;  
        this.maxCount = maxCount;  
        this.count = 0;  
    }  
  
    @Override  
    public void run() {  
        try {  
            while (count != maxCount) {  
                Thread.sleep(1000);  
                System.out.println(name + " : " + ++count);  
            }  
        }catch (InterruptedException e) {  
            e.printStackTrace();  
        }  
    }  
  
    public static void main(String[] args) {  
        ThreadCounter threadCounter = new ThreadCounter("ThreadCounter", 10);  
        ThreadCounter threadCounter2 = new ThreadCounter("ThreadCounter2", 10);  
        System.out.println(Thread.currentThread() + "start");  
        threadCounter.start();  
        threadCounter2.start();  
        System.out.println(Thread.currentThread() + "end");  
    }  
}
```

### Quiz-03

- #### 실행 결과가 예상 결과와 비슷하게 출력되는가?
    
	- answer : 예상 결과랑은 다르게 출력된다.
```
Counter1 : 1
Counter1 : 2
Counter1 : 3
Counter1 : 4
Counter1 : 5
Counter1 : 6
Counter1 : 7
Counter1 : 8
Counter1 : 9
Counter1 : 10
Counter2 : 1
Counter2 : 2
Counter2 : 3
Counter2 : 4
Counter2 : 5
Counter2 : 6
Counter2 : 7
Counter2 : 8
Counter2 : 9
Counter2 : 10
```

- 예상 결과와 다르다면 이유에 대해 설명해 보자.
	- answer : Counter 코드에서는 싱글 스레드로 작동중이기 때문이다. 그래서 한 번 작업을 할 때 스레드가 하나이기 때문에 Counter1 객체의 작업을 끝내고 Counter2 객체의 작업을 시작하기 때문에 이러한 결과가 출력된다.

### Quiz-04

- 실행 결과가 예상 결과와 비슷하게 출력되는가?
	- 예상 결과와 똑같다.
```
ThreadCounter2 : 1
ThreadCounter : 1
ThreadCounter : 2
ThreadCounter2 : 2
ThreadCounter2 : 3
ThreadCounter : 3
ThreadCounter2 : 4
ThreadCounter : 4
ThreadCounter2 : 5
ThreadCounter : 5
ThreadCounter2 : 6
ThreadCounter : 6
ThreadCounter2 : 7
ThreadCounter : 7
ThreadCounter2 : 8
ThreadCounter : 8
ThreadCounter2 : 9
ThreadCounter : 9
ThreadCounter2 : 10
ThreadCounter : 10
```

- 예상 결과와 다르다면 이유에 무엇일까?
	- 예상 결과와 다르지 않다. 현재의 프로세스에는 멀티스레드가 있기 때문이다. 스레드가 2개가 만들어져 있어 동시에 작업이 가능하기 때문에 이런 결과가 출력된다.