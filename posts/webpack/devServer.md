로컬에서 웹팩프로젝트를 테스트할때 사용하는 server다.

[webpack-dev-server](https://www.npmjs.com/package/webpack-dev-server) 패키지를 이용하며,
`webpack serve` 명령어를 통해 구동한다.

구동하면 대략적으로 아래와 같은 과정이 일어난다.

1. webpack을 이용해 번들링
2. 번들링된 파일을 메모리에 저쟝
3. webserver를 구동시키고 2번 파일을 서비스
4. webserver 종료와 함꼐 메모리에있던 번들링파일 사라짐

## webpack build 와의 차이점

번들링하는것 까진 똑같지만,\
build는 결과물이 output.path에 저장되는 반면,\
serve는 사용자가 볼 수 없는 메모리에 저장된다.

## devServer

webpack.config.js의 devSever로 환경설정을 할 수 있다.

### publicPath

output.publicPath의 의미와 동일하다.
그러나 메모리에 올라가는 번들링 파일에 대한 publicPath다.

### contentBase

구동되는 webserver의 정적 리소스 경로를 의미한다.

---

## 참고

- https://webpack.js.org/configuration/dev-server/#devservercontentbase
- https://www.npmjs.com/package/webpack-dev-server
