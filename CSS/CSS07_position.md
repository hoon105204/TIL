# CSS07_position

> 요소의 위치를 지정할 때는 X 좌표와 Y 좌표를 지정하는 절대 위치 좌표 방법과 요소를 입력한 순서에 따라 지정하는 상대 위치 좌표 방법을 사용
position 속성을 이용하면 원하는 위치에 배치 가능하며, z-index를 통해 전/후 위치 지정
> 

### position 속성 키워드

| 키워드 | 설명 |
| --- | --- |
| absolute | 절대 위치 좌표 설정 |
| fixed | 화면을 기준으로 절대 위치 좌표 설정 |
| relative | 초기 위치에서 상하좌우 위치 이동 |
| static | 위쪽에서 아래쪽 순서대로 배치 |

```css
.myblue{
    position: absolute;
    top: 30px;
    left: 100px;
}
```

### z-index 속성

- 숫자가 클 수록 앞에 위치

```css
.myred{
    background-color: red;
    position: relative;
    top: 50px;
    z-index: 2;
}
```

### overflow

- overflow 속성은 내용이 요소 크기를 벗어나 모두 보여주기 힘들 때에 어떻게 보여줄지 지정
    - hidden : 영역을 벗어나는 부분 감춤
    - scroll : 영역을 벗어나는 부분 스크롤로 만듦
    - auto : 영역을 벗어나면 자동으로 처리함

```css
#body{
    width: 300px;
    height: 200px;
    border: 1px solid red;
    overflow: auto;
}
```

### 실습

```html
<style>
    #box{
        width: 550px;
        border: 1px red dashed;
        position: relative;
    }
    p{
        width: 130px;
        height: 100px;
    }
    .myred{
        background-color: red;
        position: relative;
        top: 50px;
        z-index: 2;
    }
    .myblue{
        background-color: blue;
        position: absolute;
        top: 30px;
        left: 100px;
        z-index: 1;
    }
    .mygreen{
        background-color: green;
        position: relative;
        left: 30px;
        top: -30px;
    }
    .myred:hover, .myblue:hover, .mygreen:hover{
        z-index: 100;
    }
    #fixed{
        width: 100px;
        height: 200px;
        background-color: black;
        color: white;
        position: fixed;
        right: 50px;
        top: 100px;
    }
</style>
<div id="box">
    <p class="myred"></p>
    <p class="myblue"></p>
    <p class="mygreen"></p>
</div>
<div id="fixed">
    fixed!!
</div>
<br><br><br><br><br><br><br><br><br><br><br><br>
```

<img src=".\image\position.gif" alt="position" style="zoom:67%;" />