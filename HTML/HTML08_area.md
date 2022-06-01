# 영역관련 태그

`<div>` : 줄바꿈 적용, 이미 존재하는 태그의 다음 줄에 영역이 설정(블록 요소)
`<span>`: 줄바꿈이 적용되지 않음, 옆으로 영역이 이어진다(인라인 요소) -> **크기지정이 안됌**
`<p>`   : 문단 영역 지정하는 태그(블록 요소)
`<pre>` : 입력한대로 문단 영역 지정하는 태그(블록 요소)

```html
<h2>영역 관련 태그</h2>
<h3>div 태그</h3> 
<div style="border: 1px solid black; background-color: lightpink; width: 100px; height: 100px;">첫 번째 영역</div>
<div style="border: 1px solid black; background-color: rgb(255, 255, 187); width: 100px; height: 100px">두 번째 영역</div>
<div style="border: 1px solid black; background-color: lightgreen; width: 100px; height: 100px;">세 번째 영역</div>
<br>
<h3>span태그</h3>
<span style="border: 1px solid black; background-color: lightpink; width: 100px; height: 100px;">첫 번째 영역</span>
<span style="border: 1px solid black; background-color: rgb(255, 255, 188); width: 100px; height: 100px;">두 번째 영역</span>
<span style="border: 1px solid black; background-color: lightgreen; width: 100px; height: 100px;">세 번째 영역</span>

<br>
<h3>영역의 차이</h3>
<b>div</b>
<div style="background-color: yellow;">하이퍼 텍스트 마크업 언어(영어: Hyper Text Markup Language, HTML, 문화어: 초본문표식달기언어, 하이퍼본문표식달기언어)는 웹 페이지를 위한 지배적인 마크업 언어다. 또한, HTML은 제목, 단락, 목록 등과 같은 본문을 위한 구조적 의미를 나타내는 것뿐만 아니라 링크, 인용과 그 밖의 항목으로 구조적 문서를 만들 수 있는 방법을 제공한다. 그리고 이미지와 객체를 내장하고 대화형 양식을 생성하는 데 사용될 수 있다. HTML은 웹 페이지 콘텐츠 안의 꺾쇠 괄호에 둘러싸인 "태그"로 되어있는 HTML 요소 형태로 작성한다. HTML은 웹 브라우저와 같은 HTML 처리 장치의 행동에 영향을 주는 자바스크립트와 본문과 그 밖의 항목의 외관과 배치를 정의하는 CSS 같은 스크립트를 포함하거나 불러올 수 있다. HTML과 CSS 표준의 공동 책임자인 W3C는 명확하고 표상적인 마크업을 위하여 CSS의 사용을 권장한다.</div>

<b>span</b>
<span style="background-color: hotpink;">하이퍼 텍스트 마크업 언어(영어: Hyper Text Markup Language, HTML, 문화어: 초본문표식달기언어, 하이퍼본문표식달기언어)는 웹 페이지를 위한 지배적인 마크업 언어다. 또한, HTML은 제목, 단락, 목록 등과 같은 본문을 위한 구조적 의미를 나타내는 것뿐만 아니라 링크, 인용과 그 밖의 항목으로 구조적 문서를 만들 수 있는 방법을 제공한다. 그리고 이미지와 객체를 내장하고 대화형 양식을 생성하는 데 사용될 수 있다. HTML은 웹 페이지 콘텐츠 안의 꺾쇠 괄호에 둘러싸인 "태그"로 되어있는 HTML 요소 형태로 작성한다. HTML은 웹 브라우저와 같은 HTML 처리 장치의 행동에 영향을 주는 자바스크립트와 본문과 그 밖의 항목의 외관과 배치를 정의하는 CSS 같은 스크립트를 포함하거나 불러올 수 있다. HTML과 CSS 표준의 공동 책임자인 W3C는 명확하고 표상적인 마크업을 위하여 CSS의 사용을 권장한다.</span>

```

<img src=".\image\HTML08_01area.png" alt="HTML08_01area" style="zoom:75%;" />