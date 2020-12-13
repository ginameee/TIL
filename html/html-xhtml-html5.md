html, xhtml, html5 에 대해서 비교한다.\
자세한 내용은 [이곳](https://hackr.io/blog/difference-between-html-html5-xhtml)에서 확인할 수 있으며, 원론적인 차이만 다룬다.

엄밀히 말하면, html은 비교대상이 아니고,\
html의 타입으로 `html5 이전의 html`, `xhtml`, `html5`가 존재한다고 생각하면 된다.\
편의상 html5 이전의 html을 html이라고 부른다.

## html

> content-type: text/html

html5 등장 이전의 html이다.

## xhtml

> content-type: text/xml or application/xhtml+xml

Xtensible HyperText Markup Language의 약자로써 html의 확장판이다.\
파일의 타입은 아래 MIME type에서 알 수 있듯이 `xml`로, html을 xml로 옮긴형태라고 생각하면 된다.\
문법적인 차이가 있고, html보다 엄격하게 문법을 체크한다.

mime type이 text/html일 경우, 내용이 xhtml이더라도 html로 간주한다.

## html5

> content-type: text/html

html(1~4)을 보안해서 등장한 새로운 버전의 html 5번째 버전이다.\
네이밍에 차별성을 둔 이유는 변화가 가장 많은 버전업이었기 때문이라고 생각된다.

기존 html 과의 차이점 중 markup과 관련된 몇개를 말하면,

- Semantic 태그 지원: 영역만을 나타냈던 단순한 태그명이, 의미를 갖게됨
- video, audio를 통한 멀티미디어 데이터 지원
- svg, canvas를 통한 벡터이미지 지원

정도가 있다. 자세한건 아래 사이트를 참고하자.

## 참고사이트

- [html vs xhtml vs html5](https://hackr.io/blog/difference-between-html-html5-xhtml)
- [xhtml vs html](https://developer.mozilla.org/en-US/docs/Archive/Web/Properly_Using_CSS_and_JavaScript_in_XHTML_Documents_)
