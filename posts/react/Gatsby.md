Gatsby

# 개요

리액트기반의 프레임워크로,\
리액트 기반의 웹 애플리케이션을 정적인 형태의 웹사이트로 변환/생성해준다.

정적인 웹 사이트란,\
블로그나 회사소개 페이지처럼 외부와의 통신이 거의 없는 정적인 내용만을 담고있는 웹 사이트들을 말한다.

물론 비동기데이터요청과 같은 작업도 클라이언트 사이드에서 가능하다. (generate된 이후에는 SPA처럼 동작)

# 장점

- 파일시스템기반의 자동 라우팅처리
- 편리한 페이지 생성
- 단순한 로직으로 서비스를 만들기 쉬움
- html파일이 generate 되어있으므로 SPA의 단점인 SEO를 극복

# 단점

- 복잡한 로직을 구현하기에는 한계가 있다.
- 정적 HTML 생성에 필요한 외부데이터를 가져오는 방식이 제한적이다 (GraphQL / createPages API)

# fetch data

2가지 방법이 존재한다.

| 방법            | how to fetch data                                       | how to pass data to component        | how to use data in component          |
| --------------- | ------------------------------------------------------- | ------------------------------------ | ------------------------------------- |
| graphQL         | by defining graphQL in bottom of Component and using it | by graphQL with gatsby automatically | refer to data props gotton by graphQL |
| createPages API | In createPages, using any libraries for fetching data   | by                                   |

1. graphQL
2. createPages API

## graphQL

## createPage

gatsby 가 제공하는 API다

1. createPages에서 fetching data 및 creating page\
   (원하는 라이브러리 사용 ex. axios)

   ```

   ```

2. 페이지 template 컴포넌트에서 pageContext를 이용해 1번에서 fetching 한 데이터에 접근
