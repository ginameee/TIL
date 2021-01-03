Block, Element, Modifer 의 약자로, 클래스를 명명하는 방법/규칙

> Block\_\_Element--modifer

### Block

독립적으로 의미를 갖는 객체로, 쉽게 Component 라고 생각하자

### Element

독립적으로 의미를 갖지못하는, Block 을 구성하는 요소

### Modifier

Block이나 Element의 flag로 동작이나 모습에 대한 속성 값을 나타낸다.

---

## TIP

BEM은 CSS 네이밍 방법론에 불과하기때문에 정답은 없다.\
내가 마크업하면서 느꼈던 점들을 공유한다.

### Nested Element 방지

Block\_\_Element가 여러 자식을 가질 경우, 계속 nested 되어 가독성이 떨어진다.\
그럴경우 Element를 Block으로 만들어버리자.

BEM은,\
`Block__Element--Modifer`지 `Block__Element__Element--Modifier` 가 아니다.

### data-attribute

개인적인 생각으로는 Modifier는 HTML5의 data-attribute로 대체가 가능해보인다.

```html
<!-- 나라별로 색상을 다르게 먹이고 싶을 때 -->
<!-- B__E--M -->
<div class="countries">
  <div class="countries__item--korea">
    <h1>korea</h1>
  </div>
  <div class="countries__item--japan">
    <h1>Japan</h1>
  </div>
  <div class="countries__item--china">
    <h1>China</h1>
  </div>
</div>

<!-- B__E data-attribute -->
<div class="countries">
  <div class="countries__item" data-name="korea">
    <h1>korea</h1>
  </div>
  <div class="countries__item" data-name="japan">
    <h1>Japan</h1>
  </div>
  <div class="countries__item" data-name="china">
    <h1>China</h1>
  </div>
</div>
```

---

## 참고할만한 사이트

- [BEM 정의](http://getbem.com/introduction/)
- [BRM 정의 및 사용예시](https://css-tricks.com/bem-101/)
- [BEM의 잘못된 예시 및 해결방법](https://www.smashingmagazine.com/2016/06/battling-bem-extended-edition-common-problems-and-how-to-avoid-them/)
