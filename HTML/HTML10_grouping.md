# 시멘틱 구조

> HTML 문서에서 의미있는 부분을 의미에 맞는 태그를 사용하는 것을 시멘틱 구조라고 함

- header : 제목, 로고, 아이콘 ...
- nav : 탐색 링크 ...
- container : section과 article로 이루어진 부분
- section : 컨텐츠를 주제별로 묶고 싶을 경우
- article : 독립적인 컨텐츠
- aside : 광고, 메인과 상관없는 내용 정의
- footer : 저작권, 저자, 연락처 ...

<img src=".\image\HTML10_01sementic.png" alt="HTML10_01sementic" style="zoom:100%;" />

```html
<div id="header">
    <h1>제목</h1>
    <div>
        <span><a href="html03_list.html">메뉴1</a></span>
        <span><a href="html04_img.html">메뉴2</a></span>
        <span><a href="html08_text_list_test.html">메뉴3</a></span>
        <span><a href="html10_form02.html">메뉴4</a></span>
    </div>
</div>

<div id="container">
    <div id="left">
        <p>왼쪽 본문 내용</p>
    </div>
    <div id="right">
        <p>오른쪽 본문 내용</p>
    </div>
</div>

<div id="footer">
    <p>copytight &copy; all rights reserved...</p>
</div>

<style type="text/css">
    div{
        border: 1px dashed red;
        margin: 10px;
    }
    #container{
        height: 400px;
    }
    #left{
        width: 60%;
        height: 85%;
        float: left;
    }
    #right{
        width: 30%;
        height: 85%;
        float: right;
    }
</style>
```

<img src=".\image\HTML10_02test.png" alt="HTML10_02test" style="zoom:75%;" />