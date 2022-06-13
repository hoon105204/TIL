# JS09_페이지이동

# open

```jsx
function popUp() {
    // "_blank" 조건을 줘서 새창으로 나오도록 함
    // open(url, name, specs);
    window.open("js16_popup02.html","_blank","width=200px, height=200px");
}
```

### opener

현재 창을 열었던 창의 참조를 반환

```jsx
function test() {
    let val = "안녕";
    // opener는 부모창이 된다
    opener.document.getElementById("tt").value = val;
}
```

# location

```jsx
let locTest = () => {
    // href: 대입된 해당 링크로 페이지 이동
    location.href = "https://www.daum.net";

    // assign: 페이지 이동
    location.assign("https://www.naver.com");

    // replace: 페이지 이동(전단계 이력x)
    location.replace("https://www.google.com");

    // reload: 페이지 새로고침
    location.reload();
}
```

# history

```jsx
// 앞페이지로 이동
history.forward();

// 이전 페이지로 이동
window.history.back();
    
// 사용자 지정 페이지 이동
history.go(-1);
```