# 예외처리(Exception)

## 프로그램 오류

- 프로그램 수행 시 치명적 상황이 발생하여 비정상 종료 상황이 발생한 것
  1. 컴파일 에러 : 프로그램의 실행을 막는 소스 상의 문법 에러, 소스 구문을 수정하여 해결
  2. 런타임 에러 : 입력 값이 틀렸거나, 배열의 인덱스 범위를 벗어났거나, 계산식의 오류 들 주로 if문 사용으로 에러 처리
  3. 시스템 에러 : 컴퓨터 오작동으로 인한 에러, 소스 구문으로 해결 불가
- 오류 해결 방법 : 소스 수정으로 해결 가능한 에러를 예외(Exception)라고 하는데 이러한 예외 상황 구문을 처리하는 방법인 예외처리를 통해 해결

## 예외 처리(Exception)

- **RuntimeException** 클래스 : Unchecked Exception으로 주로 프로그래머의 부주의로 인한 오류인 경우가 많기 때문에 예외 처리보다는 코드를 수정해야 하는 경우가 많음
- RuntimeException 후손 클래스
  1. ArithmeticException
     0으로 나눈느 경우 발생 ~> if 문으로 나누는 수가 0인지 검사
  2. NullPointerException
     Null인 참조 변수로 객체 멤버 참조 시도 시 발생 ~> 객체 사용 전에 참조 변수가 null인지 확인
  3. ArrayIndexOutOfBoundsException
     배열의 index 범위를 넘어서 참조하는 경우 발생 ~> 배열명.length를 사용하여 배열의 범위 확인
  4. ClassCastException
     Cast 연산자 사용 시 타입 오류 ~> instanceof 연산자로 객체타입 확인 후 cast 연산
  5. NegativeArraySizeException
     배열 크기를 음수로 지정한 경우 발생 ~> 배열의 크기를 0보다 크게 지정해야 함
- Exception 확인하기
- 예외처리 방법
  1. Exception 처리를 호출한 메소드에게 위임
  2. Exception이 발생한 곳에서 직접 처리(try ~ catch문)