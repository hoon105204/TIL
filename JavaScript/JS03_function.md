# JS03_function

# 함수

- 선언과 호출
    1. 익명 함수 : 함수 이름을 입력하지 않음, 리터럴 방식과 객체 방식으로 선언 가능
    2. 선언적 함수 : 함수 이름을 입력하여 만듦
- 함수 생성 방법

| 방법 | 표현 |
| --- | --- |
| 익명 함수 | function () {} |
| 선언적 함수 | function 함수명() {} |

```jsx
// 익명 함수 리터럴로 선언
var func01 = function () {
	alert("익명 함수");
}
// 호출
func01();

// 선언적 함수 선언
function func02() {
	alert("선언적/명시적 함수");
}
// 호출
func02();
```

> 함수도 변수이므로 같은 명의 함수를 두번 선언하였을 때 마지막에 입력된 값이 저장된다. 
하지만 선언적 함수와 익명 함수를 같이 이용하면 실행순서가 달라진다.
자바 스크립트는 선언적 함수를 먼저 읽기 때문에 선언적 함수가 익명함수 뒤에 있더라도 나중에 읽은 익명 함수가 실행 된다.
> 

```jsx
var func01 = function () { alert("1"); }
function func01() { alert("2"); }

func01(); // 결과는 1의 값이 나온다.
```

### 콜백 함수

> 콜백함수 : 매개변수로 전달되는 함수
> 

```jsx
// 선언
function callTenTimes(callback) {
	for(let i=0; i<10; i++) {
		callback();
	}
}
// 호출
callTenTimes(function () {
	alert('함수 호출');
});
// '함수 호출' 라는 문구가 10번 호출됨
```

### 화살표 함수(arrow function)

```jsx
// 일반적 함수
function basic() {
	console.log();
}
// arrow function
let arrow = () => {
	console.log();
}

let arrow2 = (no1,no2) => no1+no2;    // 리턴값이 하나라 {} 생략 가능
let arrow3 = no1 => console.log(no1); // 매개변수가 하나면 괄호 생략 가능
```

# 클로저

> 함수의 중첩이 이루어 지는것이 가능하며, 내부 함수는 외부 함수 안에서 정의된 모든 변수와 함수들에 접근 가능하다.
반대로 외부 함수에서 내부 함수 안에 정의된 변수와 함수에는 접근 불가(캡슐화)
즉, 상태를 안전하게 변경/유지하는데 이용
> 

```jsx
let increase = (function () {
	let num = 0;
	// 클로저
	return function () {
		return ++num;
	}
})();

console.log(increase());  // 1
console.log(increase());  // 2
```

- 즉시 실행 함수는 한번만 실행되므로 increase가 호출될 때마다 num 변수가 재차 초기화 되지 않음
- num 변수는 외부에서 접근할 수 없는 은닉된 변수 → 의도치 않은 변경 막을 수 있음

# argments

> 함수의 인수(argments)는 배열과 비슷한 객체로 처리가 됨
전달받은 매개변수 갯수를 모를때 이용하면 유용함
> 

```html
<h2 onclick="valTest('multi','캠퍼스','선릉점','5층');">args() 테스트</h2>
<script>
	function valTest() {
	    let val ="";
	    for(let i=0;i<arguments.length; i++) {
	        val += arguments[i]+" ";
	    }
	    console.log(val);
	}
</script>
```

- `arguments` 객체로 전달받은 매개변수 4개의 값을 차례로 처리

# 출력 함수

1. console.log() : 개발자 도구 콘솔창에 출력
2. alert() : 단순 경고나 코드 디버깅 용으로 사용
3. confirm() : 확인/취소 버튼 제공하며 true/false 반환
4. prompt() : 텍스트박스 제공 입력받은값 반환, 확인/취소 버튼 제공

```jsx
// console.log
console.log("콘솔에 출력하기");

// window.alert
alert("알림 내용 출력");

// confirm 이용하여 배경색 바꾸는 함수 생성
function confirmTest() {
    if(confirm("배경을 분홍으로 바꿀까요?")) {
        document.body.style.backgroundColor = "pink";
    } else {
        console.log("기본색상 유지");
    }
}

// prompt, 기본적으로 입력값을 string으로 받는다
function promptTest() {
    const txt = prompt("좋아하는 과목 번호를 선택해 주세요.\n[1.java 2.db 3.ui]");
    switch(txt){
        case "1":
            console.log("역시 자바!!");
            break;
        case "2":
            console.log("와우 DB!!");
            break;
        case "3":
            console.log("오~UI!!");
            break;
        default:
            console.log("1, 2, 3중에 하나 선택하세요.")
    }
}
```