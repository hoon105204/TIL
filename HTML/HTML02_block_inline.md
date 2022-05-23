# block_inline

## 블록 요소

- **가로폭 전체의 넓이를 가지는 직사각형 형태** 
- `width`, `height`, `margin`, `padding` 등을 사용하여 형태를 변형하여 레이아웃을 수정할 수 있음
- 줄바꿈이 이루어지며, 블록 요소안에 텍스트, 인라인 요소, 블록 요소 포함가능

```
[HTML5의 블록 요소 종류]
address, article, aside, audio, blockquote, canvas, dd, div, dl, fieldset, figcaption, figure, footer, form, h1, h2, h3, h4, h5, h6, header, hgroup, hr, noscript, ol, output, p, pre, section, table, ul, video
```

**예제 코드**

```html
<h2>블록 요소</h2>
<p>줄바꿈 O</p>
<div style="background-color: aquamarine;">
    블록요소 안에 텍스트, <strong>인라인 요소</strong> 포함가능
    <p>블록요소 안에 블록요소 포함 가능</p>
</div>
```

**실행 결과**

<img src=".\image\HTML02_01블록요소.png" alt="HTML02_01블록요소" style="zoom:90%;" />

## 인라인 요소

- 컨텐츠가 끝나는 지점까지를 넓이로 가짐
- `width`, `height`등의 형태를 변형을 줄 수 없음
- 줄바꿈이 이루어지지 않음
- 인라인 요소 안에 블록요소 지양해야 함

```
[HTML5의 인라인 요소 종류]
a, abbr, acronym, b, bdo, big, br, button, cite, code, dfn, em, i, img, input, kbd, label, map, object, q, samp, small, script, select, span, strong, sub, sup, textarea, tt, var
```

**예제 코드**

```html
<h2>인라인 요소</h2> <!--인라인 요소안에 블록 요소 지양-->
<a href="html04_img.html">줄바꿈 X</a>
<q style="background-color: red;">인라인 요소 안에 텍스트와 <a>인라인 요소</a> 포함가능</q>
<span>인라인 요소 안에 <p>블록요소</p> 넣어보자.</span>
```

**실행 결과**

<img src=".\image\HTML02_01인라인요소.png" alt="HTML02_01인라인요소" style="zoom:90%;" />