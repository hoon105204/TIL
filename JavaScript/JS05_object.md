# JS05_object

# 객체

> 객체란 관련된 데이터와 함수의 집합을 의미
구성: 함수, 속성, this, 프로토타입
키값을 사용하여 속성을 식별한다.
> 

```jsx
// 객체 생성 예시
var product = {
	제품명: '7D 망고',
	가격: 3000,
	성분: ['망고', '설탕', '색소'],
	원산지: '필리핀'
}
```

| 키 | 속성 |
| --- | --- |
| 제품명 | ‘7D 망고’ |
| 가격 | 3000 |
| 성분 | [’망고’, ‘설탕’, ‘색소’] |
| 원산지 | ‘필리핀’ |

```jsx
// 객체명['속성명'] 으로 속성에 접근하기
product['제품명'] -> '7D 망고'
product['가격'] -> 3000
product['성분'] -> ['망고', '설탕', '색소']
product['원산지'] -> '필리핀'

// 객체명.속성명 으로 속성에 접근
product.제품명 -> '7D 망고'
product.가격 -> 3000
product.성분[0] -> '망고'
product.원산지 -> '필리핀'
```

- for 문을 이용하면 객체 요소를 하나씩 살펴 볼 수 있음

```jsx
for (var 키 in 객체) {
	문장
}

// 예시
for (var i in product) {
	alert(i + " : " + product[i]);
}
```

```jsx
let dog = {
    name : '콩이',
		// 함수 자료형의 속성을 메서드라고 부른다.
    eat : function(food){
				// 자신의 속성을 호출할 때 this를 써야함
        alert(this.name + '가 ' + food + '를 먹고있네요~');
    }

}
// 메서드 호출
dog.eat('바나나');
```

- 속성 추가와 제거

```jsx
// 속성 추가
product.score = 10;

// 속성 제거
delete(product.score);
```