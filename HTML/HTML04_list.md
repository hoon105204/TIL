# list

- `<ol>` : 순서가 있는 목차, `type`을 지정 가능하며 역순 적용시 `reversed="reversed"` 속성 적용
  - `type="a"`: 소문자 기호 목록
  - `type="A"`: 대문자 기호 목록
  - `type="i"`: 소문자 로마 숫자 기호 목록
  - `type="I"`: 대문자 로마 숫자 기호 목록
  - `type="1" start="5"`: 숫자 타입이며 시작은 5부터
- `<ul>` : 순서가 없는 목차
- `<li>` : 목차 요소 생성
- `<dl>`: 정의 리스트 생성
- `<dt>`: 용어가 들어가는 곳
- `<dd>`: 용어에 대한 설명이 들어가는 곳

**예제 코드 및 실행**

```html
<h2>순차적</h2>
<b>학원에 오는 순서</b>
<ol>
    <li>눈을 뜬다.</li>
    <li>일어나서 물을 마신다.</li>
    <li>씻는다.</li>
    <ol>
        <li>양치한다.</li>
        <li>세수한다.</li>
    </ol>s
    <li>옷을 입는다.</li>
    <li>출발한다.</li>
</ol>

<h2>비순차적</h2>
<b>집으로 가는 순서</b>
<ul>
    <li>건물 바깥으로 나간다.</li>
    <li>역으로 간다.</li>
    <ul>
        <li>사당행 플랫폼으로 내려간다.</li>
    </ul>
    <li>지하철을 탄다.</li>
</ul>
```

<img src=".\image\HTML04_01list.png" alt="HTML04_01list" style="zoom:90%;" />

```html
<h2>속성 변경 연습</h2>

<ol type="a">
    <li>java</li>
    <li>db</li>
    <li>html</li>
    <li>css</li>
</ol>

<ol type="A">
    <li>java</li>
    <li>db</li>
    <li>html</li>
    <li>css</li>
</ol>

<ol type="i">
    <li>java</li>
    <li>db</li>
    <li>html</li>
    <li>css</li>
</ol>

<ol type="I">
    <li>java</li>
    <li>db</li>
    <li>html</li>
    <li>css</li>
</ol>

<ol type="1" start="5">
    <li>java</li>
    <li>db</li>
    <li>html</li>
    <li>css</li>
</ol>

<ol reversed="reversed">
    <li>java</li>
    <li>db</li>
    <li>html</li>
    <li>css</li>
</ol>
```

<img src=".\image\HTML04_02속성변경.png" alt="HTML04_02속성변경" style="zoom:75%;" />

```html
<h2>정의리스트</h2>
<dl>
    <dt>이곳에는 용어가 들어가는 곳</dt>
    <dd>이곳에는 용어에 대한 설명이 들어가는 곳</dd>
    <dd>여러 줄을 작성 할 수 있다.</dd>
    
    <dt>또다른 용어</dt>
    <dd>또다른 용어에 대한 설명</dd>
</dl>
```

<img src=".\image\HTML04_03정의리스트.png" alt="HTML04_03정의리스트" style="zoom:75%;" />