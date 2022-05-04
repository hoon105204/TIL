# 제어문

## 1. 조건문

- 프로그램 수행 흐름을 바꾸는 역할을 하는 제어문중 하나로 조건에 따라 다른 문장이 수행되도록 함

### if 문

- 조건식의 결과 값이 ture면 문장을 수행하며 다음 조건절은 실행하지 않음

```java
if(조건식1) {
    수행할 문장1
} else if(조건식2) {
    수행할 문장2
} else {
    수행할 문장3
}
```

### switch 문

- 조건식 하나로 많은 경우의 수 처리할 때 이용하며, 조건식의 결과는 정수 또는 문자, 문자열
- 조건식의 결과 값과 일치하는 case 문으로 이동
- default 문은 일치하는 case 문이 없을 때 수행

```java
switch(num % 5) {
case 1:
	team= "1조";
	break;
case 2:
	team= "2조";
	break;
case 3:
	team= "3조";
	break;
case 4:
	team= "4조";
	break;
default:
	team= "다시";
}
```



## 2. 반복문

- 프로그램 수행 흐름을 바꾸는 역할을 하는 제어문 중 하나로 특정 문장들을 반복해서 수행하도록 함

### for 문

- 조건식이 true면 문장 반복 수행

```java
for(초기식; 조건식; 증감식) {
    수행될 문장;
}
// 예시
for(int i= 1; i<= 10; i++) {
	System.out.println(i + " 출력 ");
}
```

### while 문

- 조건식이 true 일때 문장 반복 수행

```java
while(조건식) {
	수행될문장;
	[증감식or 분기문];
}
// 예시
int i= 1;
while(i<= 10) {
	System.out.println(i + " 출력 ");
	i++;
}
```

### do ~ while 문

- do 안의 내용 먼저 실행하고 조건식 확인후 true면 문장 반복 수행

```java
do{
	수행될문장;
	[증감식or 분기문];
} while(조건식);
// 예시
int i= 1;
do{
	System.out.println(i + " 출력 ");
	i++;
} while(i<= 10);
```

## 3. 분기문

- **break** : 자신이 포함된 가장 가까운 반복문을 빠져나가게 함

```java
for(int i= 1;; i++) {
	System.out.println(i + " 출력 ");
if(i>= 10) {
		break;
	}
}
```

- **continue** 
  반복문 내에서만 사용 가능하며, countinue 아래 부분은 실행하지 않고 반복문을 다시 실행
  전체 반복 중에 특정 조건을 만족하는 경우를 제외하고자 할 때 유용

```java
for(int i= 1; i<= 10; i++) {
	if(i% 2 == 0) {
		continue;
	}
	System.out.println(i+ " 출력");
}
```

