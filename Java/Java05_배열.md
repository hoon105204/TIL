# 배열

- 같은 자료형의 변수를 하나의 묶음으로 다루는 것
- 배열은 저장된 값마다 인덱스 번호가 0부터 시작하여 설정

```java
// 배열의 선언
자료형[] 변수명;

// 배열의 선언 및 할당
자료형[] 배열명 = new 자료형[배열크기];
```

- 배열 저장구조
  - 배열은 참조 변수로 Heap 영역에 할당되며 배열 공간의 주소를 저장
  - 배열 공간의 주소를 이용해 인덱스를 참조하는 방식으로 값 처리
    <img src=".\image\Java05_배열_01배열저장구조.png" alt="Java05_배열_01배열저장구조" style="zoom:50%;" />

- 배열 초기화

```java
// 인덱스를 이용한 초기화
arr[0] = 1;

// for 문을 이용한 초기화
for(int i=0; i<arr.length; i++) {
    arr[i] = i;
}

// 선언과 동시에 초기화
자료형[] 배열명 = new 자료형[] {값1, 값2, ...};
자료형[] 배열명 = {값1, 값2, ...};
```

- 배열 복사

  1. 얕은 복사 : 객체의 주소 값만 가져와 참조형 변수에 저장하고 하나의 객체를 두 변수가 참조

     ```java
     int[] arr1 = new int[4];
     int[] arr2 = arr1;
     ```

     <img src=".\image\Java05_배열_02깊은복사.png" alt="Java05_배열_02깊은복사" style="zoom:50%;" />

  2. 깊은 복사 : 새로운 배열 객체를 생성하여 기존 배열의 데이터를 복사하는 것

     ```java
     // 다양한 깊은 복사 방법
     for(int i = 0; i<arr1.length; i++) {
         arr2[i] = arr1[i];
     }
     System.arraycopy(arr1, 0, arr2, 0, arr1.length);
     arr2 = Arrays.copyof(arr1, arr1.length);
     arr2 = arr1.clone();
     ```

     <img src=".\image\Java05_배열_02얕은복사.png" alt="Java05_배열_02얕은복사" style="zoom:50%;" />

