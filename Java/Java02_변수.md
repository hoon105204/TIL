# 변수

- 데이터 저장 단위
  비트( bit) : 컴퓨터가 나타내는 데이터의 저장 최소 단위로서 2진수 값 하나를 저장할 수 있는 메모리 공간을 의미
  바이트(byte) : 데이터 처리 또는 문자의 최소 단위로서 8개의 비트가 모여 하나의 바이트가 구성됨

- **변수란** 메모리 공간(RAM)에 한개의 값을 기록하기 위한 장소(공간)

**변수의 자료형(Type)**

1. 기본형
   - **실제 데이터(값)**을 저장
   - 논리형, 문자형, 정수형, 실수형으로 나뉘고 8개의 자료형이 있음
   - 각 자료형 별 데이터 저장 크기가 다름
2. 참조형
   - 데이터가 저장되어 있는 주소를 저장(**객체의 주소**)
   - 기본형을 제외한 나머지(String 등), 사용자 정의 자료형
   - 4byte의 공간을 저장공간으로 할당

<img src=".\image\Java01_변수_01자료형.png" alt="Java01_변수_01자료형" style="zoom:55%;" />

**변수의 선언**

- 메모리 공간에 데이터를 저장할 수 있는 공간을 할당하는 것
  ` 자료형 변수명 ; `

**변수의 명명 규칙**

1. 대소문자 구분이 되며 길이 제한이 없다.
2. 예약어를 사용하면 안된다.
3. 숫자로 시작하면 안된다.
4. 특수문자는 '_'와 '$'만을 허용한다.
5. 여러 단어 이름은 단어의 첫 글자를 대문자로 한다.

**변수의 초기화**

- 변수를 사용하기 전에 처음으로 값을 저장하는 것
  -> 지역변수는 반드시 초기화 해야 된다.

상수 : 초기화 이후 다른값 대입이 불가능한 데이터

데이터 오버플로우 : 허용된 비트 범위를 초과한 값이 대입되어 침범되는 현상

**형변환(castring)**

- 컴퓨터 값처리는 같은종류 자료형만 대입, 연산 가능하며 결과도 같은 종류가 나온다
- 다른 자료형 끼리 연산을 위해 형변환이 필요함
- **자동형변환** : 연산시 컴파일러가 자동으로 형변환하는 것을 의미한다.

<img src=".\image\Java01_변수_02형변환.png" alt="Java01_변수_02형변환" style="zoom: 67%;" />

- **강제형변환** : 데이터가 큰 자료형에서 작은 자료형으로 변경시 자료형으로 형변환을 해줄 수  있으며, *데이터 손실*이 있을 수 있어 유의해야 한다.

**변수와 메모리 구조**

| 메모리 구조 | 설명                                                         |
| ----------- | ------------------------------------------------------------ |
| Static      | static 예약어로 선정된 필드, 메소드가 저장되는 공간<br />클래스, 변수 등 |
| HEAP        | new 연산자에 의해 동적으로 할당하고 저장되는 공간<br />객체 배열 등 |
| STACK       | 메소드를 호출하면 자동으로 생기고 메소드가 끝나면 자동소멸<br />지역변수, 매개변수, 메서드 호출 스택 등 |

**출력  메서드**

- `System.out.print()`: () 안의 변수, 문자, 숫자, 논리값을 모니터에 출력해 주는 메서드
- `System.out.println()`: print문과 동일하게 출력은 해주지만 출력 후 자동으로 출력창에 줄바꿈을 해주는 메서드
- `System.out.printf("%형식", 변수 등)`: 정해져 있는 형식에 맞춰서 그 형식에 맞는 값(변수)을 줄바꿈 하지 않고 출력

**Scanner**

- 사용자로부터 입력되는 정수, 실수, 문자열을 처리하는 클래스

- `import java.util.Scanner;`

- `Scanner sc = new Scanner(System.in);`

  

  