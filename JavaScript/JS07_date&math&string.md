# JS07_date&math&string

# Date

```jsx
let date = new Date(); // 오늘날짜
inputDate.innerHTML = date.toDateString() + "<br>";           // 날짜 요일(텍스트)
inputDate.innerHTML += date.toLocaleDateString() + "<br>";    // 날짜(숫자)
inputDate.innerHTML += date.toLocaleString() + "<br>";        // 날짜 시간
inputDate.innerHTML += date.toLocaleTimeString() + "<br>";    // 시간

/*
Sun Jun 12 2022
2022. 6. 12.
2022. 6. 12. 오후 8:12:59
오후 8:12:59
*/
```

# Math

```jsx
var num = -123.456;

console.log("절대값: " + Math.abs(num));            // 절대값: 123.456
console.log("난수생성: " + Math.random());          // 난수생성: 0.05191283617228226
console.log("반올림: " + Math.round(num*100)/100);  // 반올림: -123.46
console.log("내림: " + Math.floor(num));            // 내림: -124
console.log("올림: " + Math.ceil(num));             // 올림: -123
console.log("파이: " + Math.PI);                    // 파이: 3.141592653589793
```

# String

```jsx
let str1 = "Apple iPhone";
str1.toUpperCase();  // APPLE IPHONE
str1.toLowerCase();  // apple iphone

str1.length;         // 12
str1.indexOf('e');   // 4
str1.lastIndexOf('e'); // 11

str1.substring(2,10);  // ple iPho

// 문자열 나누기 -> array로 반환
let str2 = "사과, 바나나, 복숭아, 키위, 망고, 수박";

let fruits = str2.split(", ");
console.log(fruits);  // Array(6)

// 문자열 합치기
let str3 = " String ";
let str4 = " Test ";
console.log(str3.concat(str4," Java "," Script "));  // String  Test  Java  Script
```