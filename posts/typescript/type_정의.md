타입스크립트에서 가장 중요한부분은 이름에 나와있듯이 `타입`이다.\
정의된 타입을 기반으로 `타입추론`을 해주고, 개발시 타입오류를 잡아내거나 타입 자동완성등을 통해 개발에 용이성을 제공한다.

## blah.d.ts 파일

타입에 대한 정의를 담고있는 파일이다.

```ts
// 전역변수
declare const pi = 3.14;

// 인터페이스
type user = {
  name: string;
  pw: string;
};

// 타입
type url = string;
```

## @types 패키지

javascript의 라이브러리(패키지)는 typescript 환경에서는 제대로 사용할 수 없다.

당연히 type에 대한 정의가 없으니 typescript가 타입추론이 불가능하고, 타입에러를 잡지 못한다.\
이를 위해서 패키지의 타입만을 정의해놓은 패키지가 types 패키지다.

일반적으로 패키지 설치시 이름 앞에 @types가 붙는다. (물론 해당 패키지가 types 보조패키지를 만들어놨을때의 이야기..)

jquery -> @types/jquery

## 참고

- https://joshua1988.github.io/ts/config/types.html#types-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC%EB%9E%80
