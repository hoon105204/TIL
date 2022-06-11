# CSS10_animation

> animation 속성은 애니메이션 효과를 제공해줌
`@keyframes` 과 같이 이용하면 애니메이션, 중간중간의 특정 지점들을 거칠 수 있는 키프레임들을 설정함으로써 CSS 애니메이션 과정의 중간 절차를 세밀하게 제어할 수 있게 함
> 

```css
div{
    width: 100px;
    height: 100px;
    font-size: 30pt;
    color: white;
    background-color: red;
    word-wrap: break-word;
    animation: mybox 2s infinite;
}

@keyframes mybox{
    0%{width: 150px; height: 150px; background-color: yellow; 
        transform: translate(10px, 10px);}

    25%{width: 200px; height: 150px; background-color: green;
        transform: translate(50px, 50px);}

    50%{width: 250px; height: 250px; background-color: blue; 
        font-weight: bold; transform: translate(70px, 50px);}

    75%{width: 300px; height: 300px; background-color: blueviolet; 
        font-weight: bold; transform: translate(100px, 70px);}

    100%{width: 200px; height: 200px; background-color: red; 
        font-weight: bold; transform: translate(60px, 50px);}
}
```

<img src=".\image\animation.gif" alt="animation" style="zoom:67%;" />