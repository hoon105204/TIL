# form

- form 태그는 html에서 사용자가 입력할 수 있는 양식을 제공하는 태그.
- form 태그 내의 input 태그들을 통해 사용자가 입력한 정보를 서버로 넘기는 역할을 한다.
- *action : 입력받은 데이터를 보낼 곳을 입력.
- *method : get/post 등의 전송 방식을 지정. post는 전송 데이터가 주소창에 보여지지 않도록 함(get은 반대)
- name 변수명을 설정하여 submit을 통해 해당 값을 전송함

## text 관련 input 태그

```html
<form method="post">
    <h2>text와 관련된 input 태그</h2>
    아이디: <input type="text" name="userid" size="20" placeholder="아이디를 입력하세요" maxlength="10" value="multi" autofocus>
    <br>
    <label>비밀번호: </label><input type="password" name="userpw" size="20" placeholder="비밀번호를 입력하세요" maxlength="20">
    <br>
    홈페이지: <input type="url" name="homepage" value="https://">
    <br>
    이메일: <input type="email" name="email">
    <br>
    전화번호: <input type="tel" name="phone" placeholder="전화번호를 입력하세요">
    <br><br>
    <input type="submit" value="전송"> &nbsp; <input type="reset" value="취소">
</form>
```

<img src=".\image\HTML09_01text.png" alt="HTML09_01text" style="zoom:100%;" />

```html
<!--여러줄의 텍스트를 입력-->
<form method="post">
    <textarea cols="50" rows="10" style="resize: none;" name="textarea"></textarea>
    <br>
    <input type="submit" value="전송">
</form>
```

## 숫자와 관련된 input 태그

```html
<form>
    <h2>숫자와 관련된 input태그</h2>
    수량: <input type="number" name="amount" min="10" max="100" value="10" step="5">
    <br>
    점수: <input type="range" name="point" min="0" max="100" value="50" step="10">
    <br><br>
    <input type="submit" value="전송">
</form>
```

<img src=".\image\HTML09_02number.png" alt="HTML09_02number" style="zoom:100%;" />

## 라디오 버튼과 체크박스

- label 태그를 통해 input과 연동 가능, 이때 input의 id를 for에 넣으면 됨
- 하나의 라디오 및 체크박스라면 **name 이 동일**해야 함
- `checked = "checked"` 속성은 실행시 미리 선택되어 있게끔 해줌

```html
<form id="form3">
    <h2>라디오버튼과 체크박스</h2><!--label 태그를 통해 추가적 옵션 이용 가능 for는 id로만 연동됨-->
    성별: <input type="radio" name="gender" value="F" id="female" checked><label for="female">여자</label>&nbsp;&nbsp;
    <input type="radio" name="gender" value="M" id="male">남자
    <br>
    취미: <input type="checkbox" id="baseball" name="hobby" value="baseball" checked><label for="baseball">야구</label>&nbsp;&nbsp;
    <input type="checkbox" id="football" name="hobby" value="football"><label for="football">축구</label>&nbsp;&nbsp;
    <input type="checkbox" id="basketball" name="hobby" value="basketball"><label for="basketball">농구</label>
    <br><br>
    <input type="submit" value="전송">
</form>
```

<img src=".\image\HTML09_03radioCheckbox.png" alt="HTML09_02number" style="zoom:100%;" />

## 날짜와 관련된 input 태그

```html
<form>
    <h2>날짜와 관련된 input 태그</h2>
    date: <input type="date" value="2022-09-11" name="date" min="2020-01-01"><br>
    month: <input type="month"><br>
    week: <input type="week"><br>
    time: <input type="time"><br>
    datetime: <input type="datetime-local"><br>

    <br><br>
    <input type="submit" value="전송">
</form>
```

<img src=".\image\HTML09_04date.png" alt="HTML09_02number" style="zoom:100%;" />

## 그 밖의 input 태그

```html
<form>
    <h2>그 밖에 input 태그</h2>
    색상선택: <input type="color" name="color"><br>
    파일선택: <input type="file"><br>
    안보임: <input type="hidden" name="hiddenVal" value="1"><br>
    버튼: <input type="button" value="버튼" onclick="window.alert('Hello~')">

    <br><br>
    <input type="submit" value="전송">
</form>
```

<img src=".\image\HTML09_05other.png" alt="HTML09_05other" style="zoom:100%;" />

## select 태그 & option 태그

```html
<form>
    <h2>select 태그와 option 태그</h2>
    국적: 
    <select name="nation">
        <option value="ko">한국</option>
        <option value="us">미국</option>
        <option value="uk">영국</option>
        <option value="etc">기타</option>
    </select>
    <br><br>
    <!--다중 선택 및 칸크기 조정-->
    국적:
    <select size="2" multiple name="nation">
        <option value="ko">한국</option>
        <option value="us">미국</option>
        <option value="uk">영국</option>
        <option value="etc">기타</option>
    </select>

    <br><br>
    <input type="submit" value="전송">
</form>
```

<img src=".\image\HTML09_06select.gif" alt="HTML09_06select" style="zoom:100%;" />

## form 태그 실습

- `form` 태그에 `action` 속성을 부여해 `submit`버튼 클릭시 입력된 데이터가 `html10_form02_res.html`페이지로 이동됨

```html
<form action="html10_form02_res.html" method="get">
    <fieldset>
        <legend>회원가입</legend>
        <p>아이디: <input type="text" name="id"></p>
        <p>비밀번호: <input type="password" name="pw"></p>
        <p>이메일 수신 여부
            <input type="radio" name="radio" value="y" checked><label for="y">Y</label>&nbsp;
            <input type="radio" name="radio" value="n"><label for="n">N</label>
        </p>
        <p>관심분야
            <input type="checkbox" name="cb1" value="html"><label for="html">HTML</label>&nbsp;
            <input type="checkbox" name="cb2" value="css"><label for="css">CSS</label>&nbsp;
            <input type="checkbox" name="cb3" value="javascript"><label for="javascript">JS</label>&nbsp;
        </p>
        <p>
            <input type="submit" value="전송">
            <input type="reset" value="취소">
        </p>
    </fieldset>
</form>
```

<img src=".\image\HTML09_07test.png" alt="HTML09_07test" style="zoom:100%;" />
