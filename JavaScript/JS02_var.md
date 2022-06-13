# JS02_var

# 변수

> 값을 저장할 떄 사용하는 식별자
변수를 만드는 것을 ‘선언한다’고 표현하며, 
변수에 값을 저장하는 것은 ‘값을 할당한다’라고 표현
변수를 선언한 후 처음 값을 할당하는 것을 ‘변수 초기화’ 라고 함
> 

### 종류

- var: 선언 안되있어도 undefined만 나오고 실행에는 문제가 안됨
- let: 선언 안되있으면 에러가 나옴
- const: 상수 초기화 안되있으면 에러나옴 and 값을 변경할 수 없음(보안에 좋음), const는 가르키는 주소가 바뀔수 없음

### 선언 규칙

1. 대소문자 구분
2. 영문, $, _로 시작해야 함
3. 영문, $, _, 숫자를 포함할 수 있음
4. 키워드나 예약어를 사용할 수 없음

```jsx
// 변수 선언 및 초기화
var test1=1;
let test2=2;
const test3=3;

{   // 블럭에서 변수선언
            var no=10;
            let no2=20;
            const no3=30; }
console.log(no); // var는 블럭 밖에서도 이용 가능(최근에는 let, const를 이용함)
```

```jsx
// 전역변수
let variable=10;
function test01(){
    variable = variable + 5;
    document.getElementById("v01").innerHTML = "<b style='color:red; background:yellow;'>"+variable+"</b>";
}

// 지역변수
function test02(){
    const variable2 = variable+100;
    document.getElementById("v02").innerHTML = "<b>"+variable2+"</b>"
}
// console.log(variable2); // 지역변수라 함수 밖에서 인지 X
```

### 호이스팅

> JavaScript에서 **호이스팅**(hoisting)이란, 인터프리터가 변수와 함수의 메모리 공간을 선언 전에 미리 할당하는 것을 의미합니다. `var`로 선언한 변수의 경우 호이스팅 시 `undefined`로 변수를 초기화합니다. 반면 `let`과 `const`로 선언한 변수의 경우 호이스팅 시 변수를 초기화하지 않습니다.
> 

```jsx
// var 변수는 호이스팅이 이루어짐
console.log(test1);   // undefined 출력
var test1=1;

// let과 const는 호이스팅이 이루어지지 않음
console.log(test2);   // error
let test2=2;
```

# 자료형

- 같은 변수라도 저장되는 값에 따라 자료형이 달라짐

```jsx
// 문자
var variable3 = "문자";
console.log(variable3 + " : " + typeof variable3); // 문자 : string

// 숫자
variable3 = 4.4;
console.log(variable3 + " : " + typeof variable3); // 4.4 : number

// 논리
variable3 = true;
console.log(variable3 + " : " + typeof variable3); // true : boolean

// null
variable3 = null;
console.log(variable3 + " : " + typeof variable3); // null : object

// 객체(array)
variable3 = [1,3,5,7,9];
console.log(variable3 + " : " + typeof variable3); // 1,3,5,7,9 : object

// 함수
variable3 = function(){
   alert("함수저장");
}
console.log(variable3 + " : " + typeof variable3); 
/* function(){
   alert("함수저장");
} : function */
variable3(); // 함수 실행
```