img 태그와 관련된 내용들 정리한다.

### img 태그 404 처리

API가 개발중이라 response가 죄다 mock 데이터라서 유효하지않는 경우가 많다.\
image url 또한 마찬가진데, img 태그의 src가 유효하지 않을 경우, 404 error 가 발생한다.\
이를 이용해서 img 태그에 onError 이벤트를 추가하여 src값을 대체이미지로 변경할 수 있다.

React나 Vue를 사용중이라면,\
굳이 이 방법을 사용하지 않고 src에 해당하는 state or prop에 기본값을 설정해주면된다.

```html
<img
  id="태그_아이디"
  scr="이미지_주소"
  onError="this.src='대체_이미지_주소';"
/>
```
