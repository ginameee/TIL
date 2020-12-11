동적인효과는 transform과 transition 이용해서 작업한다.

## transform

https://developer.mozilla.org/en-US/docs/Web/CSS/transform

|     값      |   설명   |                 예시                 |
| :---------: | :------: | :----------------------------------: |
|   `scale`   | 크기조절 |       `transform: scale(1.2)`        |
|  `rotate`   |   회전   |      `transform: rotate(45deg)`      |
| `translate` |   이동   | `transform: translate(100px, 200px)` |

## transition

https://developer.mozilla.org/en-US/docs/Web/CSS/transition \
변화를 부드럽게 만들어준다.

> trasition: ${transition\_먹일\_css속성} ${시간} ${변화형태}

- `${transition\_먹일\_css속성}`은 여러개 나열 가능하다 혹은 `all`값으로 모든 css property를 대상으로 할 수 있다.
- `${초}`는 `2s`와 같은 형태로 입력 (250~300ms 가 사용자가 느끼기에 가장 보기 편안한 값)
- `${변화형태}`는 변화가 진행될 형태를 의미한다.

#### 예시

```css
trasition: background-color 2s ease-in;
```

#### 참고사이트

- [변화형태 종류](https://developer.mozilla.org/en-US/docs/Web/CSS/animation-timing-function)
- [사용자 정의 변화형태](https://cubic-bezier.com/)
