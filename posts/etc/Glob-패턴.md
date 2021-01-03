https://velog.io/@k7120792/Glob-%ED%8C%A8%ED%84%B4%EA%B3%BC-%EC%A0%95%EA%B7%9C%ED%91%9C%ED%98%84%EC%8B%9D

정규표현식처럼 특수문자를 조합한 패턴을 이용해 파일들을 선택할 수 있는 방법으로, \
`tsconfig.json`, `webpack.config.json` 등 여러 환경설정 파일에서 사용된다.

---

## 자주 사용하는 패턴

- /\*\*.js: 현재 디렉토리와 그 하위 디렉토리 내에 존재하는 모든 .js 파일들을 선택

- /\*.{js,ts}: 현재 디렉토리 내에 존재하는 모든 .js, .ts파일들을 선택

- /example[1-3].js: 현재 디렉토리 내에 있는 example1.js, example2.js, example3.js파일들을 선택

#### \* vs \*\*

- \*\*: 디렉토리, 파일 모두를 포함한다.
- \*: 파일만 포함한다.
