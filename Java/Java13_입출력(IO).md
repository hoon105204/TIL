# 입출력(I/O)

- input 과 output의 약자, 컴퓨터 내부 또는 외부 장치와 프로그램 간의 데이터를 주고 받는 것
- 장치와 입출력을 위해서는 하드웨어 장치에 직접 접근이 필요한데 다양한 매체에 존재하는 데이터들을 사용하기 위해 입출력 데이터를 처리할 공통적인 방법으로 스트림 이용

## 스트림(Stream)

- 입출력 장치에서 데이터를 읽고 쓰기 위해서 자바에서 제공하는 클래스
- 모든 스트림은 *단방향이며* 각각의 장치마다 연결할 수 있는 스트림 존재
- 하나의 스트림으로 입출력을 동시에 수행할 수 없으므로 동시에 수행하려면 2개의 스트림 필요
- 스트림종류
   	1. InputStream(/Reader) : 바이트(/문자) 기반 입력 스트림의 최상위 클래스로 추상클래스임
       (메서드) `read(), close()`
   	2. OutputStream(/Writer) : 바이트(/문자) 기반 출력 스트림의 최상위 클래스로 추상클래스임
       (메서드) `write(), flush(), close()`

## File 클래스

- 파일 시스템의 파일을 표현하는 클래스

- 파일 크기, 파일 속성, 파일 이름 등의 정보와 파일 생성 및 삭제 기능 제공

  ```java
  // File 객체 생성
  File file = new File("파일 경로");
  ```

- 파일/디렉토리 생성 및 삭제 메서드

| 리턴 타입 | 메소드          | 설명                         |
| --------- | --------------- | ---------------------------- |
| boolean   | createNewFile() | 새로운파일생성               |
| boolean   | mkdir()         | 새로운디렉토리생성           |
| boolean   | mkdirs()        | 경로상에없는모든디렉토리생성 |
| boolean   | delete()        | 파일또는디렉토리삭제         |

## File Stream

### 기반스트림

- FileInputStream : 파일로부터 바이트 단위로 읽을 때 사용
  그림, 오디오, 비디오, 텍스트 파일 등 모든 종류의 파일 읽기 가능
  객체 생성 : `FileInputStream fis = new FileInputStream("외부자원 경로")`

- FileOutputStream : 파일로부터 바이트 단위로 저장할 때 사용
  만약 파일이 존재하지 않으면 **자동으로 생성**하지만, 파일이 존재하는 경우 **내용을 덮어쓰는** 단점
  <객체 생성>

  ```java
  FileOutputStream fos = new FileOutputStream("외부자원 경로");
  //만일 기존 파일에 이어서 계속 작성하고 싶다면 아래 예제처럼 객체 생성 시 가능
  FileOutputStream fos = new FileOutputStream("외부자원 경로", true);
  ```

- FileReader : 텍스트 파일로부터 문자 단위로 읽을 때 사용
  텍스트가 아닌 그림, 오디오, 비디오 등의 파일은 읽기 불가능

- FileWriter : 텍스트 파일로부터 문자 단위로 저장할 때 사용

### 보조 스트림

- 스트림의 기능을 향상시키거나 새로운 기능을 추가하기 위해 사용
- 보조 스트림은 실제 데이터를 주고 받는 스트림이 아니기 때문에 입출력 처리 불가능
- 기반 스트림을 먼저 생성한 후 이를 이용하여 보조 스트림 생성

<img src=".\image\Java16_0420_입출력(IO)_01보조스트림.png" alt="Java16_0420_입출력(IO)_01보조스트림" style="zoom:50%;" />

- 보조 스트림 종류
  1. 문자변환(InputStreamReader/OutputStreamWriter),
  2. 입출력성능(BufferedInputStream/BufferedOutputStream),
  3. 기본데이터타입출력(DataInputStream, DataOutputStream),
  4. 객체입출력(ObjectInputStream/ObjectOutputStream) 등의기능을제공하는보조스트림이있음
- 성능 향상 보조스트림
  - 느린 속도로 인해 입출력 성능에 영향을 미치는 입출력 소스를 이용하는 경우 사용
  - 입출력 소스와 직접 작업하지 않고 버퍼에 데이터를 모아 한꺼번에 작업을 하여 실행 성능 향상(입출력 횟수 줄임)

<img src=".\image\Java16_0420_입출력(IO)_02성능향상보조스트림.png" alt="Java16_0420_입출력(IO)_02성능향상보조스트림" style="zoom:60%;" />



