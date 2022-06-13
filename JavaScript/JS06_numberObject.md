# JS06_numberObject

> 정수와 실수를 다루는 객체
> 

```jsx
let numberObj = ()=>{
    // 1. 작성방법
    let num = new Number(7);
    let num2 = 7;
    console.log(num);               // Number {7}
    console.log(num + ", " + num2); // 7, 7

    // 메서드
    num = "12";
    Number.parseInt(num);

    num2 = 333.34567;
    console.log(num2.toFixed(2));   // 333.35, 소수점 자리수 갯수 지정(반올림) 

    num2 = 123;
    console.log(num2.toString(16)); // 7b, 16 진수로 변환

    const no1 = 1/0;
    const no2 = -1/0;
    const no3 = 'string' / 2;       
    console.log(no1);               // Infinity
    console.log(no2);               // -Infinity
    console.log(no3);               // NaN(Not a Number)
    console.log(isNaN(no3));        // NaN인지 확인
}
```

- 문자와 숫자의 `+` 연산

```jsx
// (문자 + 숫자) 문자의 합으로 이루어짐
7 + 7       -> 14
7 + '7'     -> 77
7 + 7 + '7' -> 147
```

- `Number()` 를 이용해 타입 변환

```jsx
Number('7.7');
Number.parseInt('7.7');   // 정수형으로 반환
Number.parseFloat('7.7'); // 실수형으로 반환
```