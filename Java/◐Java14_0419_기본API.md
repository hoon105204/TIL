# String 관련 클래스

- String 클래스
  - 문자열 값 수정 불가능, **immuatble(불변)**
  - 수정 시 수정된 문자열이 새로 할당 되어 새 주소를 넘김
- StringBuffer 클래스
  - 문자열 값 수정 가능, **mutable(가변)**
  - 수정, 삭제 등이 기존 문자열에 수정되어 적용
  - 기본 16문자 크기로 지정된 버퍼를 이용하며 크기 증가 가능
  - 쓰레드 safe기능 제공(성능 저하 요인)
- StringTokenizer 클래스
  - String클래스에서 제공하는 spit()메소드와 같은 기능을 하는 클래스로 생성 시 전달받은 문자열을 구분자로 나누어 각 토큰에 저장(**split()**을 많이 씀)

```java
import java.util.*;

public class TestStringTokenizer {
    public static void main(String[] args) {
        String str = "AA|BB|CC";
        
        StringTokenizer st = new StringTokenizer(str,"|");
        
        while(st.hasMoreTokens()) {
            System.out.println(st.nextToken());
        }
    }
}
```



# Wrapper 클래스

- Primitive Data Type을 객체화 해주는 클래스 -> 내부에 선언된 다양한 기능 사용 가능

| PrimitiveData Type | WrapperClass |
| :----------------: | :----------: |
|      boolean       |   Boolean    |
|        byte        |     Byte     |
|        char        |  Character   |
|       short        |    Short     |
|        int         |   Integer    |
|        long        |     Long     |
|       float        |    Float     |
|       double       |    Double    |

# 날짜 관련 클래스

- Date 클래스 : 시스템으로 부터 현재 날짜, 시간 정보를 가져와 다룰 수 있게 만들어진 클래스

```java
Date today = new Date(); // 시스템으로 부터 현재 날짜, 시간 정보를 가져옴
Date when new Date(123456789L); // long형 정수값을 가지고 1970년 기준으로 초를 추가 가능
```

- Calendar 클래스 : getInstance() 메소드를 통해서 객체 생성
- GregoriaCalendar 클래스 :  Calendar의 후손클래스로, 시간 정보를 필드를 이용하여 다룰 수 있음

# Format 관련 클래스

- SimpleDateFormat 클래스 : Date의 날짜 시간 정보를 원하는 format으로 출력
- Formatter 클래스 : 값 출력 시 format 적용하여 출력(printf와 비슷)

