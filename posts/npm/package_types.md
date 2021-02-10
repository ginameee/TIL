## Public vs Private

npm의 repositroy(? 정확한 명칭은 모르겠다.)는 git과 마찬가지로 public 이랑 private이 존재한다.

private의 경우 접근가능한 access_token을 갖고있어야만 접근이 가능하며,\
접근이 불가능할 경우 permission에러가 아닌 404를 뱉는다.

#### 참고

- https://docs.npmjs.com/about-access-tokens

## Global vs Local

패키지 설치는 전역과 지역 두가지 방법이 존재한다.

|          | Local                                    | Global             |
| -------- | ---------------------------------------- | ------------------ |
| 유효범위 | npm intsall을 실행한 프로젝트 디렉토리   | 모든 장소          |
| 저장장소 | 프로젝트 안에 있는 node_modules 디렉토리 | 사용자의 OS System |

유효범위에서 알 수 있듯이,\
global은 터미널을 열고 명령어를 통해서 어느곳에서든 사용할 수 있다.

반면에 local은 npm install을 진행한 프로젝트안에서만 사용할 수 있는데,\
library 형태의 package는, 프로젝트내의 js파일에서 import 하여 사용하고,\
실행파일 형태의 package는 일반 터미널에서는 사용이 불가능하고, package.json의 script 또는 npx 명령어를 이용하여 실행할 수 있다.

#### npx

npx란 npm 에서 제공하는 도구로써, 패키지의 설치(없을경우)와 실행을 동시에 해주는 도구이다.
설치와 동시에 실행만을 수행하고, 수행이 완료되면 해당패키지는 삭제해버리므로 기존 시스템에 아무런 영향을 주지 않는다.

npx 가 무작정 패키지를 설치하여 실행하는건 아니고,\
일단 아래장소들을 차례로 패키지가 있는지를 탐색하고 없으면 설치한다.

- $PATH
- local project (node_modules)

#### 참고

- https://nodejs.dev/learn/npm-global-or-local-packages
- https://webruden.tistory.com/275
- https://www.npmjs.com/package/npx
