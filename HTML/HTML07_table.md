# Table

- `<table>` : 기본적인 표를 생성
  - `<border>` : 테이블의 선 두께를 지정
- `<tr>` : 표의 행을 나타내는 태그
- `<th>` : 표의 제목 셀을 나타내는 태그
- `<td>` : 표의 일반 셀을 나타내는 태그
- `<caption>` : 테이블 제목
- `<thead>, <tbody>, <tfoot>` : 테이블 지정 영역
- 속성
  - `<style>` : 테이블 스타일 지정
  - `<rowspan>` : 세로 열 합치기
  - `<colspan>` : 가로 행 합치기

```html
<h1>표의 행과 열 합치기</h1>
<table border="1">
    <caption>[회원 정보]</caption>
    <tr>
        <td style="width: 130px; height: 150px;" colspan="2" rowspan="2">사진</td>
        <td style="width: 80px;">이름</td>
        <td style="width: 200px;"></td>
    </tr>
    <tr>
        <td>연락처</td>s
        <td></td>
    </tr>
    <tr>
        <td style="width: 70px; height: 50px;">주소</td>
        <td colspan="3"></td>
    </tr>
    <tr>
        <td height= "100px">자기소개</td>
        <td colspan="3"></td>
    </tr>
```

<img src=".\image\HTML07_01table.png" alt="HTML07_01table" style="zoom:100%;" />

```html
    <table border="1">
        <caption>테이블 제목</caption>
        <colgroup>
            <col width="100px" />
            <col width="200px" />
            <col width="300px" />
        </colgroup>
        <tfoot>
            <tr>
                <td>f1</td>
                <td>f2</td>
                <td>f3</td>
            </tr>
        </tfoot>
        <thead>
            <tr>
                <th>컬럼01</td>
                <th>컬럼02</td>
                <th>컬럼03</td>
            </tr>
        </thead>
        <tbody>
            <tr>
                <td>1</td>
                <td>2</td>
                <td>3</td>
            </tr>
            <tr>
                <td>4</td>
                <td>5</td>
                <td>6</td>
            </tr>
        </tbody>
```

<img src=".\image\HTML07_02table2.png" alt="HTML07_02table2" style="zoom:100%;" />