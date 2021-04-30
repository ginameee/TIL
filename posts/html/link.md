현재문서와 외부 리소스의 관계를 명시한다.

## rel

#### preconnect

```html
<link rel="preconnect" href="https://example.com" />
```

https://example.com 이라는 origin에서 자원을 가져올 수 있다는 힌트다.\
브라우저는 해당 origin으로 미리 전체연결을 설정한다.

새 연결을 여는것은 리소스를 많이 사용하므로, 과도한 사용은 지양하자.

#### dns-prefetch

```html
<link rel="dns-prefetch" href="https://example.com" />
```

preconnect와 비슷하지만, origin으로 미리 전체연결설정까지는 하지 않고, dns에 쿼리요청까지만 진행한다.\
서버의 IP주소를 미리 확인하는 것은 50ms~300ms의 시간을 줄일 수 있다.

#### prefetch

```html
<link rel="prefetch" href="/style.css" as="style" />
```

백그라운드에서 미리 리소스를 로드/캐시한다.
다음페이지를 위한 리소스(ex. js번들)를 미리 받아놓기위한 용도로 유용하다.

#### preload

```html
<link rel="preload" href="/style.css" as="style" />
```

#### prerender

```html
<link rel="prerender" href="https://example.com/about.html" />
```

백그라운드에서 페이지를 미리 렌더링하여 캐싱해놓는다.\
이렇게하면 페이지이동시 로드없이 전환된다.

#### modulepreload

```html
<link rel="modulepreload" href="/script.js" />
```

최대한 빨리 script를 다운로드받고 캐시/컴파일한다.\
모듈의 다운로드되어야만 앱이 동작하는 환경일 때 유용하게 사용할 수 있다.

## href

## onload

## onerror

## 참고

[정의](https://couplewith.tistory.com/m/entry/%EA%BF%80%ED%8C%81-%EC%9B%B9%EC%84%9C%EB%B9%84%EC%8A%A4-%EC%84%B1%EB%8A%A5-%EC%B5%9C%EC%A0%81%ED%99%94-%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80-prefetchpreconnect?category=212809)

[prelaod vs prefetch](https://medium.com/reloading/preload-prefetch-and-priorities-in-chrome-776165961bbf)
