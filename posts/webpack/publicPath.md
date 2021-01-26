환경설정에서 publicPath 라는 값을 흔하게 볼 수 있다.\
볼때마다 매번 헷갈려서 찾아보았었는데 이참에 정리해본다.

## path vs publicPath

### path

실제로 번들링된 파일이 생성되는 경로

### publicPath

원본 파일에서 번들링시에,\
모든 경로에 기반이되는, 즉 사용하는 상대경로 앞부분에 붙게되는 `prefix 경로`

---

```js
...
    output: {
        path: 'chun/dist',
        filename: 'app.js',
        publicPath: '/dist/',
    },
...
```

output option이 위와 같다고 가정하자.

CSS, HTML의 모든 상대경로값들은\
`./test.css` -> `/dist/test.css`식으로 변경되고 번들링되어,\
`chun/dist` 디렉토리 아래 생성된다.

## 언제 사용?

이미지 or CSS와 같은 리소스의 위치가 로컬과 실서버환경에서 각각 다른경로로 저장이 되어있을때 유용하다.

에를들어,

- 로컬에서의 이미지 소스경로 -> ./aseets/img/\*
- 실서버에서의 이미지 소스경로 -> `CDN_HOST`/assets/img/\*

일 경우,\
환경별 publicPath 값을 관리하여, 실서버의 경우 `CDN_HOST`로 설정해둠으로써 최종 번들링된 파일에서는 CDN의 자원을 읽어가도록 한다.

## devServer

devServer에도 publicPath가 존재한다.\
메모리에 올라가는 번들링파일에 대한 publicPath 값을 의미하며,\
실제 번들링에는 영향을 미치지 않는다.

## 참고

- https://webpack.js.org/guides/public-path/
- http://52.78.22.201/tutorials/translate/webpack-the-confusing-parts/#tocAnchor-1-5
