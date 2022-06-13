# JS08_array

# 배열

> 자바스크립트에는 자료형 지정이 없기 때문에 모든 자료형을 보관하는 변수의 모음을 배열로 처리한다.
> 

### 배열 생성 및 초기화

```jsx
// 배열 생성
var arr1 = new Array();
var arr2 = new Array(3);    // 크기에 크게 구애받지 않음

arr1[0] = '바나나';
arr1[1] = '복숭아';
arr1[2] = '키위';
arr1[3] = '딸기';

arr2[3] = '기차';
console.log(arr2);  // (4) [비어 있음 × 3, '기차']

// 초기화 방식
let arr3 = new Array('이창진', '김창진', '박창진');
let arr4 = ['이창진', '김창진', '박창진'];
```

### 메서드

| 메서드 | 설명 |
| --- | --- |
| indexOf() | 배열에서 요소가 위치한 인덱스 리턴(없으면 -1 리턴) |
| concat() | 배열 합치기 |
| reverse() | 배열의 순서를 뒤집는다. 원본 array 배열이 바뀐다. |
| push() | 배열의 맨 뒤에 요소 추가하고 원소 갯수 리턴 |
| sort() | 배열의 원소를 정렬시킴 |
| pop() | 배열의 맨 뒤에 요소 꺼내서 리턴하며, arr에서는 제거된다 |
| shift() | 배열의 맨 앞에 요소 꺼내서 리턴, arr에서는 제거된다 |
| unshift() | 배열의 맨 앞에 요소 추가, 원소 갯수 리턴 |
| slice() | 배열의 요소 선택 잘라내어 array로 리턴, 원본은 바뀌지 않음 |
| splice() | 배열에 index위치 요소 제거 및 추가, 원본에서 제거가 됨 |
| toString() | 배열의 요소 전부를 separator 쉼표와 함께 문자열 합으로 리턴 |
| join() | join은 toString과 비슷하지만 separator 지정 가능 |

```jsx
// indexOf() : 배열에서 요소가 위치한 인덱스 리턴(없으면 -1 리턴)
let arr = ['사과', '딸기', '바나나', '복숭아', '파인애플', '멜론'];
console.log(arr.indexOf('바나나'));  // 2

// concat(): 배열 합치기
let arr1 = ['1', '2', '3'];
let arr2 = ['4', '5', '6'];
let arr3 = arr1.concat(arr2);  // ['1', '2', '3', '4', '5', '6']

// reverse() : 배열의 순서를 뒤집는다. 원본 array 배열이 바뀐다.
console.log(arr1.reverse());  // ['3', '2', '1']
```

```jsx
// push() : 배열의 맨 뒤에 요소 추가, 원소 갯수 리턴
let arr = ['서초동', '방배동', '역삼동', '삼성동', '대치동'];

console.log('arr: ' + arr);

console.log(arr.push('도곡동'));
console.log('arr에 push: ' + arr);

// sort() : 배열의 원소를 정렬시킴
arr.sort();
console.log('arr에 sort: ' + arr);

arr.push('개포동');
console.log('arr에 push: ' + arr);

// pop() : 배열의 맨 뒤에 요소 꺼내서 리턴하며, arr에서는 제거된다
console.log(arr.pop());
console.log('arr에 pop: ' + arr);

arr.pop();
console.log('arr에 pop: ' + arr);

console.log('=============================================');
// shift(): 배열의 맨 앞에 요소 꺼내서 리턴, arr에서는 제거된다
arr = ['야구', '축구', '배구', '농구', '탁구', '테니스'];

console.log(`arr의 기본값: ${arr}`);

console.log(arr.shift());
console.log(`arr에 shift: ${arr}`);

// unshift(): 배열의 맨 앞에 요소 추가, 원소 갯수 리턴
console.log(arr.unshift('당구'));
console.log(`arr에 unshift: ${arr}`);

console.log('=============================================');
// slice(): 배열의 요소 선택 잘라내어 array로 리턴, 원본은 바뀌지 않음
arr = ['자바', '디비', 'html', 'css', 'javascript'];

console.log(`arr: ${arr}`);

console.log(arr.slice(2,4));
console.log(`slice 후 arr: ${arr}`);

// splice(): 배열에 index위치 요소 제거 및 추가, 원본에서 제거가 됨
console.log(arr.splice(2,2));
console.log(`splice 후 arr: ${arr}`);

console.log(arr.splice(1,1,'spring'));  // (제거 위치, 갯수, 추가할 데이터)
console.log(`splice 후 arr: ${arr}`);
```

### toString(), join()

- 배열을 문자열로 반환, 원본을 건드리지 않음

```jsx
let arr = ['나는','올해','부터','욕을','안할거야'];

console.log(arr.toString());    // 나는,올해,부터,욕을,안할거야

// join은 toString과 비슷하지만 separator 지정 가능
console.log(arr.join());        // 나는,올해,부터,욕을,안할거야
console.log(arr.join(' / '));   // 나는 / 올해 / 부터 / 욕을 / 안할거야
```