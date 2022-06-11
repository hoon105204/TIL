# CSS11_mediaquery

> 다양한 디바이스들이 웹브라우징을 지원하면서 웹에서 화면의 해상도에 따라 유연하게 컨텐츠를 배치해야 함
이때 반응형 웹디자인의 기본이 되는 Media Query를 이용하면 편리함
> 

### 기본 문법

```css
@media (조건) {
  스타일
}
```

- 조건 부분이 만족될 때 스타일이 적용되며, 조건을 만족시키지 못하면 스타일이 적용되지 않음

### 지정할 수 있는 미디어

- `all` : 모든 미디어 유형 대상
- `print` : 프린터 대상
- `screen` : 스크린 화면 대상
- `speech` : 음성장치 대상

### 연습

- 이미지 태그에 media query를 적용하여 창의 가로크기가 변화함에 따라 이미지 변화를 줌

```css
img{
    width: 200px;
    transition: width 0.5s linear, opacity 1s;
}

@media screen and (min-width: 700px){
    img{
        width: 400px;
		}
}

@media screen and (min-width: 1024px){
    img{
        width: 600px;
        opacity: 0.5;
    }
}
```

<img src=".\image\mediaquery.gif" alt="mediaquery" style="zoom: 50%;" />