
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