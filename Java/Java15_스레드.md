# 스레드

**프로세스(Process)**

> 프로세스란 간단한 의미로 실행중인 프로그램을 의미한다.
> 프로세스는 프로그램이 실행 될 때마다 개별적으로 생성
> 하나의 프로세스는 프로그램을 수행함에 있어 필요한 데이터와 메모리 등의 할당 받은 자원, 그리고 하나 이상의 스레드로 구성이 된다.

**스레드(Thread)**

> 프로세스 내에서 할당된 자원을 이용해 실제 작업을 수행하는 작업 단위
> 모든 프로세스는 하나 이상의 스레드를 가지며 각각 독립적인 작업 단위를 가짐

- 메인 스레드
  - 모든 자바 프로그램은 메인 스레드가 main() 메서드를 실행하며 시작
  - main() 메서드의 첫 코드부터 순차적으로 실행되며, return을 만나면 종료
  - 필요에 의해 작업 스레드들을 만들어 병렬 코드 실행 가능(멀티 스레드)

- 프로세스 종료
  - 싱글 스레드의 경우 메인 스레드가 종료되면 프로세스도 종료되지만, 멀티 스레드의 경우 실행중인 스레드가 하나라도 있으면 프로세스가 종료되지 않음

> Tip! 멀티 프로세스 vs 멀티 스레드
>
> 멀티 프로세스 : 각각의 프로세스를 독립적으로 실행 시키는 것
> 멀티 스레드 : 하나의 프로세스 내에서 여러 스레드가 동시에 작업을 수행하는 것

**멀티 스레드**

- 싱글 스레드 : 메인 스레드 하나만 가지고 작업을 처리 → 한 작업씩 차례대로 처리해 나감
- 멀티 스레드 : 메인 스레드 외의 추가적인 스레드를 이용하여 병렬적으로 작업을 처리

<img src=".\image\Java15_스레드_01싱글스레드와멀티스레드.png" alt="Java15_스레드_01싱글스레드와멀티스레드" style="zoom:67%;" />

멀티 스레드 장점

1. 자원을 보다 효율적으로 사용 가능
2. 사용자에 대한 응답성 향상
3. 애플리케이션의 응답성 향상
4. 작업이 분리되어 코드가 간결해짐
5. CPU 사용률 향상

<img src=".\image\Java15_스레드_02멀티스레드장점.png" alt="Java15_스레드_02멀티스레드장점" style="zoom:65%;" />

멀티 스레드 단점

1. 동기화(Synchronization)에 주의해야 함
2. 교착상태(dead-lock)가 발생하지 않도록 주의해야 함
3. 프로그래밍 시 고려해야 할 사항이 많음

## 스레드 실습

**스레드 생성 및 호출**

1. Runnable 인터페이스를 구현하는 방법

```java
public class Thread01 {

	public static void main(String[] args) {
		System.out.println("===== main strat =====");
		
		// run() 호출은 main() 메서드 위로 쌓이기 때문에 
		// n1.run(), n2.run() 이 모두 수행된 후에 main 스레드가 종료된다.
		MyThread n1 = new MyThread();
		MyThread n2 = new MyThread();
		n1.run();
		n2.run();
		
		// Thread 객체를 통해 MyThread를 실행시켜보자
		// start() 메서드가 새로운 스레드를 생성하고 그 위에 run() 메서드가 쌓이기 때문에
		// 새로운 스레드에서 생성된 run() 과 관계없이 main 스레드는 먼저 종료됨
		Thread m1 = new Thread(new MyThread());
		Thread m2 = new Thread(new MyThread());
		
		m1.start();
		m2.start();
		
		System.out.println("----- main stop -----");
	}
}

class MyThread implements Runnable{

	@Override
	public void run() {
		for(int i =0; i<100; i++) {
			System.out.println("i="+i);
		}
	}
}
```

2. Thread 클래스를 상속받는 방법

```java
class MyThread02 extends Thread {
	
	public MyThread02(String name) {
		super(name);
	}
	
	@Override
	public void run() {
		for(int i=0; i<100; i++) {
			System.out.println(this.getName() + " = " + i);
		}
		System.out.println(this.getName() + " 끝");
	}
	
}

public class Thread02 {
	
	public static void main(String[] args) {
		// 스레드를 상속받았기 때문에 따로 스레드 객체를 생성하여 넣을 필요가 없다
		MyThread02 m1 = new MyThread02("야옹");
		MyThread02 m2 = new MyThread02("멍멍");
		
		// thread scheduling
		// 우선순위(priority), 순환할당(rount_robin)
		// 순환할당은 JVM에 의해 결정. 개발자 임의로 수정 불가
		m1.setPriority(10);
		m2.setPriority(Thread.MIN_PRIORITY);
		// 숫자가 낮을 수록 우선순위가 높다.
		// 우선순위가 높다라고 해도 꼭 먼저 끝나는 것은 아니다.
		
		m1.start();
		m2.start();
	}
}
```



**스레드 스케쥴링**

> 스레드 개수가 코어의 수보다 많을 경우 스레드를 어떤 순서로 동시성을 실행할 것인가를 결정하는 것. 스케쥴링에 의해 스레드들은 번갈아가며 run()메서드를 조금씩 실행

- 우선 순위 방식(Priority)
  - 우선 순위가 높은 스레드가 작업 시간을 더 많이 가지도록 하는 스케쥴링 방식
  - 스레드에 1~10 까지 우선 순위 번호 부여 가능(번호가 높을수록 우선 순위 높음)
  - 스레드 생성 시 우선 순위 기본값은 5
- 순환 할당 방식(Round-Robin)
  - 시간 할당량을 정하여 하나의 스레드를 정해진 시간만큼 실행시키는 방식
  - JVM에 의해 정해짐(코드로 제어 불가능)

**스레드 컨트롤**

- 실행중인 스레드의 상태를 제어하기 위한 것
- 효율적이고 정교한 스케쥴링을 위한 스레드 상태를 제어하는 기능

```java
public class Thread03 {

	public static void main(String[] args) {
		MyThread02 m1 = new MyThread02("야옹");
		MyThread02 m2 = new MyThread02("멍멍");
		
		long start = System.currentTimeMillis();
		m1.start();
		try {
			// m1 thread가 종료 될떄 까지
			// 다른 thread를 멈춘다.
			m1.join();
		} catch (InterruptedException e) {
			e.printStackTrace();
		}
		
		m2.start();
		long end = System.currentTimeMillis();
		
		System.out.println("실행시간: " + (end-start));
		// m1이 끝나고 main끝나는 시점에서 실행시간이 측정된다.
	}
}
```



**동기화**

- 한번에 한 개의 스레드만 프로세스 공유 자원에 접근할 수 있도록 락을 걸어 다른 스레드가 진행중인 작업에 간섭하지 못하도록 한 것
