[CSS도 변수](https://developer.mozilla.org/en-US/docs/Web/CSS/--*)사용이 가능하다.
부모노드에 선언 후, 자식노드에서 사용이 가능하다

```css
:root {
  --font-size: 32px;
}
.class1 {
  font-size: var(--font-size);
}
.class2 {
  font-size: var(--font-size);
}
.class3 {
  font-size: calc(var(font-size) * 2);
}
```

[:root 의사클래스](https://developer.mozilla.org/ko/docs/Web/CSS/:root)는, 문서트리의 루트요소의 선택자이다. 일반적으로 html을 의미한다.

이런 변수는 특히 미디어쿼리에서 아주 유용하게 사용이 가능하다.

```css
:root {
  --background-color: thistle;
  --text-color: whitesmoke;
  --base: 8px;
}
.first-list {
  background-color: var(--background-color);
  color: var(--text-color, red);
  margin-left: var(--base);
}

.second-list {
  background-color: var(--background-color);
  color: var(--text-color, red);
  margin-left: calc(var(--base) * 2);
}

@media screen and (max-width: 768px) {
  :root {
    --background-color: salmon;
    --text-color: whitesmoke;
    --base: 4px;
  }
}
```
