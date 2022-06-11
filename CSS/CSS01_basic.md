# CSS01_basic

# basic

- 스타일 시트 작성 방식 3가지
    1. 인라인 스타일 시트 : 우선순위가 높다.
        
        ```html
        <b style="color: red;">
        ```
        
    2. 내부 스타일 시트 : html 내부에서 간단하게 작성
        
        ```html
        <style> p{background-color: pink;} </style>
        ```
        
    3. 외부 스타일 시트 : CSS 파일을 만든다.
        
        ```css
        /* css 파일 */
        b{color: aqua;}
        ```
        
        ```html
        <!--HTML에 css파일 불러오기-->
        <link href="resource/css01.css" rel="stylesheet" type="text/css">
        ```