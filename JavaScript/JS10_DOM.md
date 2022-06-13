# JS10_DOM

> DOM(Document Object Model)
HTML 태그를 자바스크립트에서 문서 객체로 변환하는 것을 ‘문서 객체를 선택한다’고 표현
문서 객체를 조작하려면 먼저 문서 객체를 선택해야 함
> 

### 문서 객체를 선택하는 메서드

| 구분 | 메서드 | 설명 |
| --- | --- | --- |
| 1개 선택 | document.getElementById(아이디) | 아이디로 1개 선택 |
| 1개 선택 | document.querySelector(선택자) | 선택자로 1개 선택 |
| 여러개 선택 | document.getElementsByName(이름) | name 속성으로 여러개 선택 |
| 여러개 선택 | document.getElementsByClassName(클래스) | class 속성으로 여러개 선택 |
| 여러개 선택 | document.querySelectorAll(선택자) | 선택자로 여러개 선택 |

### 문서객체 조작

- 글자 조작

| 속성 | 설명 |
| --- | --- |
| textContent | 문서 객체 내부 글자를 순수 텍스트 형식으로 가져오도록 변경 |
| innerHTML | 문서 객체 내부 글자의 HTML 태그를 반영해 가져오도록 변경 |

```jsx
function searchId() {
    let doc = document.getElementById("test");
    console.log(doc);
    doc.innerHTML = "<b>id로 탐색합니다.</b>"; // innerHTML은 태그안을 탐색
    doc.style.color = "red";
}

function searchName() {
    let doc = document.getElementsByName("test02"); // 배열 형태로 가져옴
    console.log(doc);
    doc[1].value ="name 속성으로 엘리먼트 탐색";
}

function searchTagName() {
    let doc = document.getElementsByTagName("p");
    doc[3].innerHTML = "tagName으로 탐색";
    doc[3].style.color = "blue";
}

function searchQS() {
    let doc = document.querySelector("p"); // 첫번째 하나만 선택해 온다
    let doc2 = document.querySelectorAll("p"); // 전체를 배열로 가져옴
    console.log(doc);
    console.log(doc2);

    doc2[4].innerHTML = "querySelectorAll(css선택자)";
}
```

- 속성 조작

| 메서드 | 설명 |
| --- | --- |
| setAttribute() | 속성 지정 |
| getAttribute() | 속성 추출 |
| createAttribute() | 속성 생성 |

```jsx
function eleCreate() {
	let div = document.createElement("div");
	// <div></div>
	
	let txt = document.createTextNode("엘리먼트 생성 메서드");
	
	div.appendChild(txt);
	// <div>엘리먼트 생성 메서드</div>
	
	// 속성 변경
	// 1. 
	let attr = document.createAttribute("style");
	// style = ""
	attr.nodeValue = "border:2px solid blue";
	// style = "border:2px solid blue"
	
	div.setAttributeNode(attr);
	// <div style = "border:2px solid blue">엘리먼트 생성 메서드</div>
	
	// 2. [많이 사용!]
	div.setAttribute("class","test");
	// <div style="border:2px solid blue" class="test">엘리먼트 생성 메서드</div>
	
	document.body.appendChild(div);

}
```

### 부모탐색, 자식탐색

| 속성 | 설명 |
| --- | --- |
| parentNode | 부모태그 노드 |
| childNodes | 자식 노드들, 태그 사이사이 text 노드도 모두 인식됨 |
| children | 자식 엘리먼트(태그)만 가져온다 |

### 태그 이동

| 메서드 | 설명 |
| --- | --- |
| appendChild(노드) | 노드를 자식태그들 중 가장 마지막에 붙여 넣는다 |
| insertBefore(노드, 자식) | 노드를 자식 엘리먼트의 앞에 붙여넣는다 |