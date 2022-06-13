# JS04_operator

> == / != : 값이 같은지만 확인
=== / !== : 값과 자료형 둘다 일치하는지 확인할 때 사용
> 

```jsx
const opTest = ()=>{
    let check1 = 1;
    let check2 = "1";

    console.log(check1 == 1);       // true
    console.log(check1 == "1");     // true
    console.log(check2 == 1);       // true
    console.log(check2 == "1");     // true
    console.log("==========")
    console.log(check1 === 1);      // true
    console.log(check1 === "1");    // false 두개의 타입이 다르다
    console.log(check2 === 1);      // false 두개의 타입이 다르다
    console.log(check2 === "1");    // true
}
```