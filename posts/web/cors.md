다른 출처의 자원을 가져오는 CORS에 대해서 정리한다.

## 동일출처정책

Web에서는 동일출처정책(Same Origin Policy)이라는 보안정책을 사용하는데,\
어떤 출처에서 불러온 스크립트가 다른출처에서 가져온 리소스와의 상호작용하는 것을 제한하는 정책이다.

이 정책에 의해서 CORS가 불가능한 경우가 생기게된다.

#### 출처란?

URL은 다음과 같은 구조로 되어있다.

> `{PROTOCOL}`://`{HOST}`:`{PORT}`/`{PATH}`?`{QUERY_STRING}`#`{FRAGMENT}`

`PROTOCOL + HOST + [PORT]`를 출처라고한다.\
PORT의 경우 80, 443 (HTTP, HTTPS 기본포트) 는 생략 가능하다.

#### 동일출처란?

말 그대로 출처가 동일한 경우를 의미하며,\
요청근원지(`웹 사이트`)와 요청도착지(`웹 서버`) 간의 출처가 동일할 때, 이 둘은 `동일출처`다 라고 이야기한다.

#### 동일출처 예시

요청근원지가 http://chun.client.com:8080 라고 가정

| 응답근원지                              | 동일출처 |
| --------------------------------------- | -------- |
| http://chun.client.com:8080/abc         | O        |
| http://chun.client.com:8080/abc?qs=blah | O        |
| http://chun.client.com:8081             | X        |
| https://chun.client.com:8080            | X        |
| http://chun.server.com:8080             | X        |

## CORS란?

CORS란 (Cross Origin Resource Sharing)의 약자로, 직역하면 `다른 출처간의 자원공유`를 의미한다.\
대부분의 CORS는 허용이 되지만, 동일출처정책의 위배되는 경우 브라우저에 의해 응답이 Block 된다.

#### 허용되는 경우

- `<script src="...">`를 이용해 가져오는 다른출처의 스크립트 자원
- `<link rel="stylesheet" href="...">`를 이용해 가져오는 다른출처의 CSS 자원
- `<img src="...">`를 이용해 가져오는 다른출처의 이미지자원
- `<video>`, `<audio>`를 이용해 가져오는 다른출처의 미디어자원

#### 허용되지 않는경우

동일출처정책에 의해 허용되지 않는 경우이다.

- 어떤 출처에서 불러온 스크립트가 ajax요청과 같은 방법을 통해 다른 출처의 자원을 가져오려는 경우

## CORS의 허용

## Simple Request

다음 조건을 만족하는 요청을 말한다.

#### 절차

1. 브라우저가 다운받은 javascript가 Ajax Request
2. 브라우저가 서버로 Request
3. 서버가 Response
4. 브라우저가 Reponse Header의 Access-Control-Allow-Origin 값을 체크
5. 브라우저가 Block by CORS Policy 여부 판단

## Preflight Request

Simple Request를 제외한 나머지 요청들을 말한다.

브라우저의 요청이 예비요청과 본요청을 나눠진다.

- **예비요청**: OPTION method를 사용하는 요청으로, 다른출처의 접근가능여부를 확인하기 위한 요청
- **본요청**: 실제 자원에 대한 요청

설명의 편의상 서버의 응답도 예비응답과 본응답으로 나눈다.

- **예비응답**: 예비요청에 대한 응답으로, `Acces-Control-Allow-Origin` 헤더만을 포함한 응답
- **본응답**: 요청받은 자원에 대한 응답

#### 절차

1. 브라우저가 다운받은 javascript가 Ajax Request
2. 브라우저가 본요청 전에 예비요청을 날림
3. 서버가 예비요청에 대한 응답을 보내줌
4. 브라우저가 Reponse Header의 Access-Control-Allow-Origin 값을 체크
5. 브라우저가 Block by CORS Policy 여부 판단
6. 클라이언트 출처의 접근이 허용되는 경우, 본요청
7. 서버가 본응답
