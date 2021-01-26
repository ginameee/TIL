typescript 옵션들에 대한 설명을 제공

## compilerOptions

typescript가 compile 할 때 참고하는 옵션 값

왠만한 옵션의 상세내용은 [여기](https://typescript-kr.github.io/pages/compiler-options.html)에 다 있다.

### esModuleInterop

`default: false`

`true`일 경우 CommonJS 모듈을 ES6 모듈 문법 스펙에 맞춰 가져올 수 있도록 해주는 옵션이다.

즉, CommonJS 모듈방식과, ES6 모듈방식을 섞어서 쓸 수 있도록 해준다.\
CommonJS 방식으로 export 된걸 ES6 방식으로 import 한다거나 그 반대의 경우도 가능하다.

https://simsimjae.medium.com/es%EB%AA%A8%EB%93%88%EB%B0%A9%EC%8B%9D%EA%B3%BC-commonjs-%EB%AA%A8%EB%93%88-%EB%B0%A9%EC%8B%9D%EC%9D%84-%EC%84%9E%EC%96%B4-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0-esmoduleinterop-65529471948e

### baseUrl

compile의 시작 지점을 의미한다.

### paths

baseUrl 을 기준으로, path alias 설정이 가능하다. (Glob 패턴을 사용한다.)

### target

컴파일러가 컴파일할 javascript의 버전

class의 get keyword을 쓰려면 최소 ES5 버전이 되어야 한다.
