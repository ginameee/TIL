## pseudo classes

https://developer.mozilla.org/ko/docs/Web/CSS/Pseudo-classes

엘리먼트를 세부적으로 선택하고자 할떄 사용하는 selector로 `selector:` or ` selector::` 뒤에 특정 값을 넣는다.\
특정 엘리먼트를 위한 클래스를 새로 만드는 것 보다 훨씬 효율적인 방법이다.

ex)

- 처음이나 마지막에 있는 클래스
- 특정 엘리먼트 다음에 있는 클래스
- 특정 상태에 있는 클래스

### 특정 순서의 엘리먼트 선택

```css
/* 마지막 div */
div:last-child {
  background-color: red;
}

/* 짝수 */
div:nth-child(even),
div:nth-child(2n) {
  background-color: red;
}

/* 홀수 */
div:nth-child(odd),
div:nth-child(2n + 1) {
  background-color: red;
}

/* 네개의 간격으로 */
div:nth-child(4n + 1) {
  background-color: red;
}
```

### input의 attirbute를 이용한 선택

```css
/*
required 한 input만 선택
<input type="password" required>
*/
input:required {
  border: 1px solid tomato;
}
```

---

## attribute selector

https://developer.mozilla.org/ko/docs/Web/CSS/Attribute_selectors

attribute 값을 이용한 선택

```css
/*
placeholder에 name이라는 텍스트를 포함한 input
<input type="type" placeholder="first name">
<input type="type" placeholder="last name">
*/
input[placeholoder~="username"] {
  background-color: yellow;
}
```

---

## not

css 중 예외처리를 하고싶을 때

```css
/* 
클래스명이 fancy 가 아닌 span 엘리먼트들
<span class="fancy">blahblah</span> => 미적용
<span class="haha">blahblah</span> => 적용
<span>blahblah</span> => 적용
 */
span:not(.fancy) {
  color: green;
}
```
