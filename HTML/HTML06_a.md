# \<a> 태그

- `<a>` : 하이퍼링크 관련 태그
- 인라인 요소
- 네트워크가 연결된 상황이라면 서비스되고 있는 웹페이지도 링크 가능
- 속성
  - `href` : 연결할 링크 설정
    - `href="#"`: 작동은 하되 이동하지 않도록 하는 태그를 작성 가능
    - 외부 페이지 뿐만 아니라 페이지 내부 이동 가능(selector를 통해 내부 태그 탐색)
  - `target` : `target="_blank"` 새창에서 열기, `target="_self"` 현재 페이지에서 열기

```html
<h1>하이퍼링크 관련 태그</h1>
<h3>a태그를 이용한 하이퍼링크 테스트</h3>
<ul>
    <li><a href="html01_block_inline.html">블록요소_인라인요소</a></li>
    <li><a href="html02_title_text.html">제목_글자</a></li>
    <li><a href="html03_list.html">목록</a></li>
    <li><a href="html04_img.html">이미지</a></li>
</ul>
<br>
<h3>네트워크가 연결된 상황이라면 현재 서비스되고 있는 웹페이지도 링크 가능.</h3>
<ul>
    <li><a href="https://www.naver.com" target="_blank">네이버</a></li>
    <li><a href="https://www.google.com" target="_self">구글</a></li>
</ul>
<br>
<h3>페이지 내에서의 링크 기능</h3>
<a href="#a">1번으로</a>
<a href="#b">2번으로</a>
<a href="#c">3번으로</a>

<p id="a">1번</p>
<br><br><br>
<p id="b">2번</p>
<br><br><br>
<p id="c">3번</p>
<br><br><br>

```

<img src=".\image\HTML06_01a.gif" alt="HTML06_01a" style="zoom:80%;" />