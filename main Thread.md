
### main 스레드

- main 메서드의 코드를 수행하는 쓰레드
- 스레드는 사용자 스레드와 데몬 스레드 두종류가 있다.
	- 사용자 스레드 : main Thread이다.
	- 데몬 스레드 : 사용자 스레드가 하는 것을 보조해주는 보조 Thread이다.
- 실행 중인 사용자 스레드가 하나도 없을 때 프로그램은 종료된다.

- join() 메서드 : main 스레드가 다른 스레드의 작업이 끝날 때 까지 종료되지 않고 기다리는 메서드이다.
