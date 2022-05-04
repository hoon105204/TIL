# 연산자

## 연산자 종류와 우선순위

<img src=".\image\Java03_연산자_01연산자종류와우선순위.png" alt="Java03_연산자_01연산자종류와우선순위" style="zoom:67%;" />

**증감 연산자 : ++, --**

- 피연산자의 값에 1을 더하거나 빼는 연산자로 위치에 따라 결과 값이 다르게 나타남
  전위 연산 : 먼저 연산 후 다른 연산 실행
  후위 연산 : 다른 연산 우선 실행 후 연산

**논리 부정 연산자 : !**

- 논리 값을 부정하여 반대 값으로 변경
- 제어문을 활용할 때 많이 쓰임

**산술 연산자 : *, /, %, +, -**

- 일반 수학과 동일한 연산 방법, %는 나누기의 나머지 값을 구하는 연산

**비교 연산자 : ==, !=, >, <**

- 데이터가 같은지, 다른지, 혹은 크기를 비교할 때 쓰이며 항상 논리값(`true, false`)이 결과 값임
- ==, != 는 모든 자료형(기본형, 참조형) 사용 가능하며, >, <는 기본형 boolean과 참조형을 제외하고 나머지 자료형에 모두 사용 가능

**논리 연산자 : &&, ||**

- 논리값 두개를 비교하는 연산자
- && : 두 피연산자가 모두 true 일때 true 반환(AND)
- || : 두 피연산자 중 하나만 true 여도 true 반환(OR)

**복합 대입 연산자 : +=, -=, *=, /=, %=**

- 다른 연산자와 대입 연산자가 결합한 것으로 자기 자신과 연산후 연산 결과를 자기 자신에게 누적 대입
- 증감 연산자와 비슷해 보이지만 증감연산자는 1씩 증감하며 대입 연산자는 원하는 값을 증가시키고 그 변수에 저장 가능

**삼항 연산자 : 조건식 ? 식1 : 식2; **

- 조건식의 결과 값에 따라 연산을 처리하는 방식으로 결과 값이 참일 경우 식1, 거짓일 경우 식2 수행

- 삼항 연산자 안에 삼항 연산자를 중첩하여 쓰는것도 가능

  ```java
  int result1 = a > b ? a++ : b--;
  int result2 = a < b ? a++ : (b == 0 ? a-- : b++);
  ```




# 메서드

```java
// [public] 어디서나 접근, ( + ) 다른 패키지 어떤 클래스던 상관 없음
public static void publicMethod() {
    System.out.println("public method");
}
// [protected] 상속일 경우 상속된 곳에서 ( # )
// 상속이 아닌 경우 같은 패키지 내에서만 접근 가능
protected static void protectedMethod() {
    System.out.println("protected method");
}
// [default] 같은 패키지 내에서 (~)
static void defaultMethod() {
    System.out.println("default method");
}
// [private] 현재 클래스 내에서만 ( - )
private static void privateMethod() {
    System.out.println("private method");
}
// [Nonstatic]
public void NonStaticMethod() {
    System.out.println("non static method");
}
```



