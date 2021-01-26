typescript 옵션들에 대한 설명을 제공

## compilerOptions

typescript가 compile 할 때 참고하는 옵션 값

왠만한 옵션의 상세내용은 [여기](https://typescript-kr.github.io/pages/compiler-options.html)에 다 있다.

### esModuleInterop

`default: false`

`true`일 경우 CommonJS 모듈을 ES6 모듈 문법 스펙에 맞춰 가져올 수 있도록 해준다.

### baseUrl

compile의 시작 지점을 의미한다.

### paths

baseUrl 을 기준으로, path alias 설정이 가능하다. (Glob 패턴을 사용한다.)

### target

컴파일러가 컴파일할 javascript의 버전

class의 get keyword을 쓰려면 최소 ES5 버전이 되어야 한다.
