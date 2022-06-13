# JS11_event

> 이벤트는 키보드를 누르거나 마우스를 클릭하는 것처럼 어떤 현상이 프로그램에 영향을 미치는 것을 의미
> 

### 인라인 이벤트 모델

- 요소 내부에 이벤트 속성으로서 실행할 내용을 작성하는 방식

```jsx
<button onclick="test1();">클릭!</button>
<script>
    function test1() {
        alert("인라인 이벤트 버튼 작동!");
        console.log(window.event);          
				// 일반함수라 매개변수 설정으로 이벤트 객체 확인 불가능
    }
</script>
```

### 고전 이벤트 모델

- 요소가 가지는 이벤트 속성에 핸들러를 연결하는 방법

```jsx
<button id="btn1">클릭</button>
<button id="btn2">클릭!</button>
<script>
    // 만약 상단 작성시 onload 안에 있어야 함
    // btn1을 인식 못하기 때문
    // window.onload = function(){}
    
		let btn1 = document.getElementById("btn1");
    
    btn1.onclick = function(){
        alert("btn1이 클릭 되었습니다.");
    }

    document.getElementById("btn2").onclick = (e)=> {
        alert("btn2가 클릭 되었습니다.");
        console.log(e);
				// 매개변수(window.event = e)로 이벤트와 관련된 모든 정보를 가져옴
        console.log(window.event.target);  // 이벤트 객체의 타겟 정보를 가져옴
        console.log(e.target);             // 이벤트 객체의 타겟 정보를 가져옴

        btn2.onclick = null;               // onclick 이벤트 제거할 수 있음
    }
</script>
```

### 표준 이벤트 모델

```jsx
let btn3 = document.getElementById("btn3");
btn3.addEventListener("click", function(){
    alert("표준이벤트 모델 버튼 작동!");
});
// 콜백함수는 다른함수의 인자값으로 이용되는 함수
btn3.addEventListener("mouseenter", function(e){ 
    alert("표준이벤트 모델 마우스 엔터 작동!");
    console.log(e);  // 매개변수를 통해 이벤트 객체 확인 가능
});
```