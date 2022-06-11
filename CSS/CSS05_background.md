# CSS05_background

### 주로 사용하는 배경 속성

| 속성 | 설명 |
| --- | --- |
| background-image | 배경 이미지 삽입 |
| background-size | 배경 이미지의 크기 지정 |
| background-repeat | 배경 이미지의 반복 형태 지정 |
| background-attachment | 배경 이미지의 부착 형태 지정 |
| background-position | 배경 이미지의 위치 지정 |
| background | 한번에 모든 배경 속성 입력 |

```css
h1{
		/* size는 가로크기 세로크기 순으로 입력 가능 */
    background-size: 200px 350px;
    background-image: url("img01.png");
		/* 배경이미지 반복하지 않음 */
    background-repeat: no-repeat;
		/* 키워드를 통한 위치 지정 */
    background-position: center;
		/* x축 y축 위치 지정 */
		background-position: 300px 300px;
}

pre{
		/* 배경 이미지 여려개 삽입 가능 */
    background-image: url("img03.png"), url("img01.png");
		/* 쉼표를 이용하여 이미지 각각의 크기를 지정 */
		background-size: 300px, 100% 200px;
		/* 스크롤을 내려도 배경 이미지의 위치가 변하지 않음 */
    background-attachment: fixed;
}
```