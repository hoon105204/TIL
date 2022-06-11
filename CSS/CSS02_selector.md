# CSS02_selector

# selector

## **1) 기본 선택자**

> 기본적으로 css는 위에서 아래로 적용된다. 같은 태그에 여러 css속성이 설정된 경우 우선순위에 따라 스타일이 적용된다.
> 
> 
> 태그 선택자 < 클래스 선택자 < 아이디 선택자 < 인라인 스타일 < !important 순서로 우선순위를 가진다.
> 
1. 태그 선택자(`태그 이름`) : 태그 이름을 지정하여 선언
    
    ```html
    <div><span>안녕</span></div>
    <style> div{height: 300px; background-color: red;} </style>
    ```
    
2. id 선택자(`#id`) : 요소 id를 지정하고 지정된 id 값으로 속성 적용 및 레이아웃 구성
(주의) id 속성은 중복하여 작성하지 않도록 해야함
    
    ```html
    <div id="box">
        <h1>#box</h1>
    </div>
    <style> #box{width: 800px; margin: 0 auto;} </style>
    ```
    
3. 클래스 선택자(`.클래스`) : 특정한 클래스를 가진 태그를 선택할 때 이용, 클래스 속성은 중복이 가능함
    
    ```html
    <div class="menu">div1</div>
    <div class="menu">div2</div>
    <style> .menu{display: none;} </style>
    ```
    
4. 전체 선택자(``) : 모든 태그를 선택

## **2) 속성 선택자**

> 특정 속성(title, name, id 등...)값을 가지는 태그를 선택할 때 사용, 속성과 같은 대괄호를 사용해 입력
> 
1. `선택자[속성]` : 특정한 속성이 있는 태그를 선택
    
    ```css
    p[title]{background-color: skyblue;}
    ```
    
2. `선택자[속성=값]` : 특정한 속성 내부 값이 특정 값과 같은 태그 선택
    
    ```css
    p[title="b"]{background-color: yellow;}
    ```
    

## **3) 후손/자손 선택자**

1. 후손 선택자(`선택자A 선택자B`) : 하위 선택자라고 부르기도 하며, 특정 요소 하위의 요소를 지정할 때 이용
    
    ```css
    div span{background-color: coral;}
    ```
    
2. 자손 선택자(`선택자A > 선택자B`) : 자식 선택자라고 부르기도 하며, 바로 아래 있는 특정 요소를 지칭할 때 이용
    
    ```css
    #did > div > p{background-color: silver;}
    ```
    

## **4) 동위 선택자**

1. (`선택자A ~ 선택자B`) : 같은 레벨에 있는 모든 태그들
    
    ```css
    h3 ~ div {color:green;}
    ```
    
2. (`선택자A + 선택자B`) : 같은 레벨에 있는 태그중 바로 밑에 있는 태그
    
    ```css
    span + b{background-color: lightsalmon;}
    ```
    

## **5) 가상 클래스 선택자**

> 선택자 뒤에 :가상이벤트를 붙여 특정 이벤트마다 적용 할 스타일을 설정 가능 (ex.a:hover)
> 
1. 반응 선택자 : 사용자 반응으로 생성되는 특정한 상태를 선택
    - `:active` - 마우스를 클릭했을 때
    - `:hover` - 마우스를 롤오버 했을 때
2. 상태 선택자 : 입력 양식의 상태를 선택할 때 사용
    - `:checked` - 체크 상태의 input 태그 선택
    - `:focus` - 포커스 된 input 태그
    - `:link` - 방문한 적이 없는 링크
    - `:visited` - 방문한 적이 있는 링크
    - `:enabled` - 사용 가능한 input 태그 선택
    - `:disabled` - 사용 불가능한 input 태그 선택
3. 구조 선택자 : 특정한 위치에 있는 태그를 선택할 때 사용
    - `:first-child` - 첫번째 자식
    - `:last-child` - 마지막 자식
    - `:nth-child(수열)` - 수열 번째에 해당하는 자식
    - `:first` - 첫번째 요소
    - `:last` - 마지막 요소

## **6) 그룹 선택자**

> 여러 요소에 각각 같은 속성을 적용할 때 이용선택자A,선택자B...
> 

```css
/* 그룹 선택자 */
p,pre,strong{color: rgb(31, 1, 116);}
```