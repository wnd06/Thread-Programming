### wait()

- 동기화 효율을 높이기 위해 wait(), notify()를 사용
- 객체의 lock을 풀고 스레드를 해당 객체의 waiting pool에 넣는다.
- Object클래스에 정의 되어 있으며, 동기화 블록 내에서만 사용할 수 있다.