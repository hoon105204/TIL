# CSS08_float & clear

> float 속성은 CSS에서 정렬하기 위해 사용하는 속성
키워드 : left는 왼쪽으로 정렬 시키고 right는 오른쪽으로 정렬시킨다.

clear는 float으로부터 받는 영향을 제거함
키워드 : left, right, both 가 있으며 지정한 방향의 float 영향을 받지 않게 된다
> 

```html
<h1>미니언즈</h1>
<div>
<span><img src="../1_html/image/img03.png"></span>
<p>2등신 몸매와 노란색 피부를 가진 유쾌한 눈깔괴물들이다. 영화 내 개그의 대부분을 책임지는 이들로, 슈퍼배드는 미니언 보는 재미라는 소리까지 나올 정도. 외모는 크게 두 종류인데 외눈박이와 두눈박이이며 두눈박이가 외눈박이보다 개체수가 약간 많다.
</p></div>
<style>
  span{
      float: right;
      background-color: orange;
  }
</style>
```

<img src=".\image\08Untitled.png" alt="08Untitled" style="zoom:67%;" />

float 을 적용한 태그와 Content가 어우러져 있는 것을 볼 수 있음

- p 태그에 clear 속성을 부여

```html
<h1>미니언즈</h1>
<div>
<span><img src="../1_html/image/img03.png"></span>
<p>2등신 몸매와 노란색 피부를 가진 유쾌한 눈깔괴물들이다. 영화 내 개그의 대부분을 책임지는 이들로, 슈퍼배드는 미니언 보는 재미라는 소리까지 나올 정도. 외모는 크게 두 종류인데 외눈박이와 두눈박이이며 두눈박이가 외눈박이보다 개체수가 약간 많다.
</p></div>
<style>
  span{
      float: right;
      background-color: orange;
  }
	p{ clear: both; }
</style>
```

<img src=".\image\08Untitled 1.png" alt="08Untitled 1" style="zoom:67%;" />

span 태그의 float 영향을 받지 않게 됨