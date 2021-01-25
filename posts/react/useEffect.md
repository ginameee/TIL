class component의 lifecycle을 대체할 수 있는 hook이다.
https://github.com/ginameee/react-playground/blob/master/react-hooks/src/useEffect/readme.md

## 최초호출을 막고 싶을 때

```js
...

const mounted = useRef(false);
// useRef 설명 - https://github.com/ginameee/react-playground/blob/master/react-hooks/src/useRef/readme.md

useEffect(() => {
  if (mounted.current) {
    doSomething(v1, v2);
  } else {
    mounted.current = true;
  }
  // eslint-disable-next-line react-hooks/exhaustive-deps
}, [v1, v2]);

...
```
