# JS01_start

- 자바스크립트 작성 방식 3가지
    1. inline 방식
    2. 내부 작성 방식(embedded)
    3. 외부 작성 방식

```html
<h1>자바스크립트 작성방식 3가지</h1>
<ol>
    <li onclick="alert('inline')">1. inline 방식</li>
</ol>

<!-- 2. 내부 작성 방식 -->
<script>
    function embeddedTest(){
        var doc = document.getElementsByTagName("li")[0];
        doc.style.color="red";
        doc.innerHTML = "<b>글자가 바뀝니다.</b>";
    }
</script>

<!-- 3. 외부 작성 방식, 스크립트 파일 불러오기 -->
<script src="./js/test.js"></script>
```