# CSS03_box

# box

> CSS에서 각 요소가 박스라는 사각 영역을 생성하고, 이 영역이나 이것을 둘러싼 테두리에 크기, 색상, 위치 등과 관련한 속성을 지정함으로써 스타일을 변경
> 

<img src=".\image\03Untitled.png" alt="03Untitled" style="zoom:67%;" />

| margin | 테두리와 다른 태그 사이의 테루디 바깥쪽 여백 |
| --- | --- |
| border | 테두리 |
| padding | 테두리와 Content 사이의 테두리 안쪽 여백, 배경은 padding 영역 까지만 적용 |
| width | Content를 감싸는 영역의 가로 크기 |
| height | Content를 감싸는 영역의 세로 크기 |

### 박스 여백 부분 조정

```css
div {
	width: 100px; height: 100px;

	/* 위 오른쪽 아래 왼쪽 순으로 조정 가능 */
	margin: 0 30px 0 30px;
	
	/* <위 아래>, <왼쪽 오른쪽> 조정 가능 */
	padding: 0 30px;

	/* 방향별 속성 부여 가능(top, right, bottom, left) */
	padding-right: 20px;
	margin-bottom: 10px;
}
```

### 박스 테두리

```css
div {
	/* 테두리 두께, 형태, 색상 지정 */
	border: 1px dashed red;

	/* 상하좌우 속성 각각 입력 가능 */
	border-left: blue;

	/* 둥근 테두리 만들기, 왼쪽 위부터 시계방향 입력 가능 */
	border-radius: 20px;
	border-radius: 50px 40px 20px 10px;
}
```