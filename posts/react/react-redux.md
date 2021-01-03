React에서 Redux를 편하게 사용할 수 있도록 해주는 라이브러리

react에서 redux는,\
redux store가 제공하던 dispatch, subscribe를 자동으로 처리해준다.

# Container/Presentaional Component Pattern

## 개요

Redux사용 시 자주 사용하는 패턴으로,\

- `Container Component`: dispatch, getState를 통해 State를 조회/조작 한다.
- `Presentaional Component`: Container Component로 부터 state값을 props로 전달받아 화면에 표현해준다.

2가지의 컴포넌트를 사용하는 패턴이다.

## 장점

- 유지보수의 편리: 데이터(state)를 fetch, 조작하는 부분과, 표현하는 부분이 분리되고, 이런 관심사분리는 해당 부분을 개발할때에는 그 부분에만 집중할 수 있으므로 개발시에도 용이하고, 추후 유지보수에도 편의성을 높여준다.
- 재사용이 용이: Presentaional Component는 prop만 전달받으면 되므로, 다른곳에서도 활용이 가능해진다.
