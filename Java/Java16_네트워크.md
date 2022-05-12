# 네트워크

## 네트워크

- 여러 대의 컴퓨터를 통신 회선으로 연결한 것(홈 네트워크, 지역 네트워크, 인터넷 등)

🔸서버와 클라이언트

- 네트워크로 연결된 컴퓨터간의 관계를 역할(role)로 구분한 개념
- 서버는 서비를 제공하는 프로그램으로 클라이언트의 연결을 수락하고 요청 내용을 처리 후 응답을 보내는 역할
- 클라이언트는 서비스를 받는 프로그램으로 네트워크 데이터를 필요로 하는 모든 어플리케이션이 해당 됨

🔸IP주소 : 네트워크 상에서 컴퓨터를 식별하는 번호로 네트워크 어댑터(랜카드)마다 할당되어 있음

🔸포트(Port) : 같은 컴퓨터 내에서 프로그램을 식별하는 번호로 클라이언트는 서버 연결 요청 시 IP주소와 포트 번호를 알아야 함

InetAddress : IP 주소를 다루기 위해 자바에서 제공하는 클래스

~~~java
import java.net.InetAddress;
import java.net.UnknownHostException;

public class InetTest {

	public static void main(String[] args) throws UnknownHostException {
		InetAddress addr = InetAddress.getLocalHost();

		System.out.println(addr);
		System.out.println("localhost: " + addr.getHostAddress());
		System.out.println("host name: " + addr.getHostName());
		System.out.println();
		
		// 모든 InetAddress를 가져옴
		InetAddress[] iArr = InetAddress.getAllByName("www.youtube.com");
		
		for(int i=0; i<iArr.length; i++) {
			System.out.println(iArr[i].getHostName() + " : " + iArr[i].getHostAddress());
		}
		
	}

}
~~~

## 소켓 프로그래밍

소켓을 이용한 통신 프로그래밍

🔸 소켓 : 프로세스 간의 통신에 사용되는 양쪽 끝단

🔸 TCP : 데이터 전송 속도가 느리지만 정확하고 안정적으로 전달할 수 있는 연결 지향적 프로토콜

🔸UPD : 데이터 전송 속도가 빠르지만 신뢰성 없는 데이터를 전송하는 비연결 지향적 프로토콜

## TCP 소켓 프로그래밍

- 클라이언트와 서버간의 1:1 소켓 통신
- 서버가 먼저 실행 되어 클라이언트의 요청을 기다려야 하고 서버용 프로그램과 클라이언트용 프로그램을 따로 구현해야 함
- 자바에서는 TCP 소켓 프로그래밍을 위해 java.net 패키지에서 ServerSocket 과 Socket 클래스 제공

<img src=".\image\Java16_네트워크_01TCP.png" alt="Java16_네트워크_01TCP" style="zoom:80%;" />

- 서버용 TCP 소켓 프로그래밍 순서
  1. 서버의 포트번호 정함
  2. 서버용 소켓 객체 생성
  3. 클라이언트 쪽에서 접속 요청이 오길 기다림
  4. 접속 요청이 오면 요청 수락 후 해당 클라이언트에 대한 소켓 객체 생성
  5. 연결된 클라이언트와 입출력 스트림 생성
  6. 보조 스트림을 통해 성능 개선
  7. 스트림을 통해 읽고 쓰기
  8. 통신 종료

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.ServerSocket;
import java.net.Socket;

public class Server {

	public static void main(String[] args) {
		// 서버 생성
		// 요청을 기다림
		ServerSocket serverSocket = null;
		// 요청이 생기면 소캣을 만듦
		Socket serviceSocket = null;
		
		// 출력 객체
		PrintWriter out = null;
		BufferedReader in = null;
		
		try {
			serverSocket = new ServerSocket(8888);
		} catch (IOException e) {
			e.printStackTrace();
		}
		
		while(true) {
			System.out.println("client를 기다립니다.");
			
			try {
				// accept부분을 통해 client 응답 기다리는 부분
				serviceSocket = serverSocket.accept();
				System.out.println("클라이언트가 접속했습니다.");
				
				// client에게 받은 내용을 라인단위로 읽어오기
				// getInputStream이 바이트 단위라 InputStreamReader 이용
				in = new BufferedReader(new InputStreamReader( serviceSocket.getInputStream() ));
				
				// 잘 받았다라고 다시 내보내기, true는 auto flush하겠다는것
				out = new PrintWriter(serviceSocket.getOutputStream(), true);
				
				// 읽어오기
				String inputLine = null;
				while( (inputLine = in.readLine()) != null ) {
					System.out.println("클라이언트가 보낸 메세지: " + inputLine);
					
					out.println(inputLine + "잘 받았어");
				}
				out.close();
				in.close();
				serviceSocket.close();
				serverSocket.close();
				
			} catch (IOException e) {
				e.printStackTrace();
			}
		}
	}
}
```

- 클라이언트용 TCP 소켓 프로그래밍 순서
  1. 서버의 IP 주소와 서버가 정한 포트번호를 매개변수로 하여 클라이언트용 소켓 객체 생성
  2. 서버와의 입출력 스트림 오픈
  3. 보조 스트림을 통해 성능 개선
  4. 스트림을 통해 읽고 쓰기
  5. 통신 종료

```java
import java.io.BufferedReader;
import java.io.IOException;
import java.io.InputStreamReader;
import java.io.PrintWriter;
import java.net.Socket;
import java.net.UnknownHostException;

public class Client {

	public static void main(String[] args) {
		
		Socket clientSocket = null;
		PrintWriter out = null;
		BufferedReader in = null;
		BufferedReader stdIn = null;
		
		System.out.println("sever에 접속합니다.");
		
		try {
			clientSocket = new Socket("localhost", 8888);
			// 서버로 보내는 스트림
			out = new PrintWriter(clientSocket.getOutputStream(), true);
			// 서버로 부터 받는 스트림
			in = new BufferedReader(new InputStreamReader(clientSocket.getInputStream()));
			// 키보드로 부터 입력받는 스트림
			stdIn = new BufferedReader(new InputStreamReader(System.in));
			
			String inputLine = null;
			while( (inputLine=stdIn.readLine()) != null) {
				out.println(inputLine);
				System.out.println("서버로부터 받은 메세지: " + in.readLine());
			}
			
			stdIn.close();
			in.close();
			out.close();
			clientSocket.close();
			
		} catch (UnknownHostException e) {
			e.printStackTrace();
		} catch (IOException e) {
			e.printStackTrace();
		}
	}
}
```



## UDP 소켓 프로그래밍

- UDP는 연결 지향적이지 않기 때문에 연결 요청을 받아줄 서버 소켓이 필요 없음
- java.net 패키지에서 제공하는 두 개의 DatagramSocket 간에 DatagramPacket으로 변환된 데이터 주고 받음

<img src=".\image\Java16_네트워크_02UDP.png" alt="Java16_네트워크_02UDP" style="zoom: 80%;" />

- 서버용 UDP 소켓 프로그래밍 순서
  1. 서버의 포트번호 정함
  2. DatagramSoket 객체 생성
  3. 연결한 클라이언트 IP주소를 가진 InetAddress 객체 생성
  4. 전송할 메세지를 byte[]로 바꿈
  5. 전송할 메세지를 DatagramPacket 객체에 담음
  6. 소켓 레퍼런스를 사용하여 메세지 전송
  7. 소켓 닫음

```java
import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.InetAddress;
import java.net.SocketException;

public class Server {
	public static void main(String[] args) throws IOException {
		// 소켓 UDP 방식
		DatagramSocket ds = new DatagramSocket();
		System.out.println("클라이언트");
		
		// 보낼 data
		byte[] buff = "연습입니다.".getBytes();
		
		// 패킷 생성
		DatagramPacket sendP = 
				new DatagramPacket(buff, buff.length, InetAddress.getByName("localhost"), 9999);
		
		// 패킷 보내기
		ds.send(sendP);
		
		ds.close();
		ds.disconnect();
	}
}
```

- 클라이언트용 UDP 소켓 프로그래밍 순서
  1. 서버가 보낸 메세지를 받을 byte[] 준비
  2. DatagramSocket 객체 생성
  3. 메세지 받을 DatagramPacket 객체 준비
  4. byte[]로 받은 메세지를 String으로 바꾸어 출력
  5. 소켓 닫음

```java
import java.io.IOException;
import java.net.DatagramPacket;
import java.net.DatagramSocket;
import java.net.SocketException;

public class Client {
	public static void main(String[] args) throws IOException {
		// 서버 생성(소켓을 만든다) UDP방식
		DatagramSocket ds = new DatagramSocket(9999);
		System.out.println("서버");
		
		// 받을 배열 생성
		byte[] buff = new byte[1024];
		
		// 패킷을 받음
		DatagramPacket receiveP = new DatagramPacket(buff, buff.length);
		
		ds.receive(receiveP);
		
		System.out.println(new String( receiveP.getData() ));
		
		// 종료
		ds.close();
		ds.disconnect();
	}
}
```

