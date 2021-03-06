## 개요

https://developer.mozilla.org/en-US/docs/Learn/HTML/Howto/Use_data_attributes

HTML5에서 추가된 스펙으로, 사용자 정의 어트리뷰트다.\
엘리먼트에 기본 어트리뷰트를제외하고 임의의 데이터를 넣고싶을때 유용하게 사용 가능하며 data-\* 형식으로 데이터를 넣는다.

```html
<div data-display-name="jang" data-score="10"></div>
<div data-display-name="chun" data-score="15"></div>
<span data-display-name="chun" data-score="25"></span>
```

```css
[data-display-name="jang"] {
  background-color: blue;
}

[data-display-name="chun"] {
  background-color: yellow;
}

span[data-display-name="chun"] {
  background-color: yellow;
}

*::after {
  content: attr(data-score);
}
```

```js
const spanEl = document.querySelector('span[data-display-name="chun"]');
console.log(spanEl.dataset.displayName); // 'chun'
```

## 주의할점

dom요소에 저장하는 데이터들은 외부에서 쉽게 조회가 가능하다.\
따라서 로직을 처리하기위한, 사용자에게 보여져도 무방한 데이터들만 저장하자.\
개인정보와같은 민감한 정보는 js에 암호화해서 저장하자.

## vs aria-\* attribute

비슷한 문법으로 사용되는 aria와 종종 비교되는데,\
사용방법은 동일하나, 목적자체가 다르다.

aria는 시각장애인이 컨텐츠를 더 명확하게 확인할 수 있도록 하기위한 용도로 등장했기에,\
사용자 데이터 추가를 위한 목적이라면 data attribute를 사용하는게 맞다.
