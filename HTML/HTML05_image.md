# image

- `<img>` : 이미지를 읽어 오는 태그
- 속성
  - `<src>` : 이미지 경로를 설정하여 이미지 파일을 불러옴
  - `<alt>` : 이미지를 읽을 수 없을 때 대체되는 텍스트
  - `<width>, <height>` : 이미지의 너비와 높이를 지정

```html
<h1>img 태그</h1>
<p>src: 속성에 이미지 경로를 설정하여 이미지 파일을 불러온다.</p>
<p>width, height 이미지의 너비와 높이를 지정한다.</p>
<p>alt : 이미지를 읽을 수 없을 때 대체되는 텍스트</p>
<img src="image/img01.png" width="200px" height="250px" alt="미니언즈">
<!-- pt : 1pt = 0.72inch
%em, rem은 상대적인 크기
-->

<h4>가변크기</h4>
<img src="image/img01.png" width="15%px" height="250px" alt="미니언즈">
<img src="image/img02.png" width="15%px" height="250px" alt="미니언즈">
<img src="image/img03.png" width="15%px" height="250px" alt="미니언즈">

<h3>이미지에 링크 걸기</h3>
<a href="html01_block_inline.html">
    <img src="image/img01.png" width="200px" height="250px" alt="미니언즈">
</a>
```

<img src=".\image\HTML05_01img.png" alt="HTML05_01img" style="zoom:75%;" />

<img src=".\image\HTML05_02imgLink.png" alt="HTML05_02imgLink" style="zoom:75%;" />