# CSS04_display

> 가시 속성은 태그가 화면에 보이는 방식을 지정하며, 대표적으로 display 속성이 있음.
display 속성을 이용하여 인라인 혹은 블록 속성을 부여 가능하며, 보이거나 안보이도록 할 수 있음
> 

# display

| none | 화면에 보이지 않음 |
| --- | --- |
| block | 블록 박스 형식으로 지정 |
| inline | 인라인 박스 형식으로 지정 |
| inline-block | 블록과 인라인의 중간 형태로 지정 |

inline-block과 block은 margin과 padding을 부여 가능

```css
#div1 {
	/* 태그가 화면에 보이지 않도록 함 */
	display: none;
}
```