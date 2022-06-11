# CSS09_transform

> CSS transform 속성으로 요소에 회전, 크기 조절, 기울이기, 이동 효과를 부여할 수 있습니다.
> 

| 키워드 | 설명 |
| --- | --- |
| translate(x, y) | 위치를 가로축으로 x, 세로축으로 y 만큼 이동시킴 |
| rotate(Ndeg) | N도 만큼 회전시킴 |
| scale(x,y) | 가로를 x배, 세로를 y배로 늘림 |

```css

.cls{
    width: 100px;
    height: 100px;
    background-color: red;
    color: white;
    word-wrap: break-word;
    font-size: 20pt;
}
.tlate{
    transform: translate(350px, 50px);
}
.trotate{
    transform: translate(500px, 0px) rotate(45deg);
}
.tscale{
    transform: translate(350px, 0px) scale(1.5,0.5);

```

### 속성 전환과 태그선택자(:hover) 활용한 메뉴바 생성

```css
li{
    width: 500px;
    background: pink;
    margin-bottom: 5px;
    font-size: 20pt;
    font-weight: bold;
    list-style-type: none;
    transition: width 1s, color 0.5s, background 1.5s, letter-spacing 1s;
    cursor: pointer;
}
li:hover{
    width: 800px;
    color: white;
    background-color: rgb(38, 6, 72);
    letter-spacing: 3px;
}
```

<img src=".\image\transform.gif" alt="transform" style="zoom:80%;" />