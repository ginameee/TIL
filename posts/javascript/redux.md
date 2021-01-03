애플리케이션의 상태관리를 위한 라이브러리로, 내용을 정리해본다.

그림의 출처는 [생활코딩](https://opentutorials.org/course/1) 이다.

<img src="posts/javascript/imgs/redux_process.png"/>

## 개요

어플리케이션의 상태를 State라고 하는 전역공간에서 저장 관리하는 기법\
단순히 전역변수를 선언하고 애플리케이션의 다양한 컴포넌트들이 조회한다고 생각하면 된다.

---

## 장점

일반적인 전역변수 선언과의 차이점이라고 하면,

- State의 접근/조작을 안전하게 통제함으로써 정합성, 무결성등을 보장한다.
- 컴포넌트간의 상태동기화가 간편하다. (데이터 변화에 따른 동기화 작업이 편리하다)
- Store라는 별도의 공간에서 State를 조작하므로 관련 로직이 분리되고 이는 유지보수에 유용하다.

---

## 구성요소

- `state`: 데이터를 저장하는 장소
- `reducer`: state에 값을 기록하는 기록자, store를 생성할 때 정의한다.
- `subscribe`: state가 변경됬을 때 호출될 함수들을 등록 하는 행위로, state가 변경되었을 때 등록된 함수들을 호출해준다.
- `action`: 사용자의 조작에 의해 발생한 이벤트로, 타입과 데이터를 갖고있는 객체다.
- `dispatch`: action을 store에 전달하기 위한 행위라고 생각하면 된다. 크게 3가지 일을 수행한다.
  1. action을 받는다
  2. reducer를 호출, action을 전달한다.
  3. subscriber에게 변경된 사실을 알린다.
- `getState`: state의 값을 얻어올 때 사용한다.

이 구성요소들이 *동작하는 흐름*은 다음과 같다.

1. 사용자의 조작으로 `action`이 발생
2. action을 `dispatch`에게 전달
   - 전달받은 action을 `reducer`에게 전달 (state가 변경됨을 의미)
   - subscriber를 호출
3. reducer가 `state`를 변경
4. `subscriber`가 구독중인 함수들(render로 지칭)을 호출
5. `render`가 `getState`를 통해 변경된 상태값을 애플리케이션에 반영

#### 적용 측면

*리듀서를 실제로 적용하는 관점*에서 에서 구성요소들을 설명해본다.\
크게 *사용자가 직접 정의*해야하는 부분과 _리덕스의 내장된 기능_ 으로 나눌 수 있다.

- 외부(사용자)에서 정의

  - `reducer`: action에 따른 state 변경로직을 담고있는 함수
  - `initial state`: state의 초기 상태값 (객체, primitive 값등 다양한 형태로 가능)
  - `action types`: state를 변경할 수 있는 action들의 이름
  - `functions for action objs`: action객체 (reducer에 전달가능한 형태) 생성을 위한 함수
  - `render`: state를 화면에 반영하기 위한 함수

- 리덕스 내장

  - `createStore`: store 생성
  - `dispatch`: (store가 제공) 액션객체를 reducer에 전달해주는 함수
  - `getState`: (store가 제공) store의 state를 가져옴
  - `subscriber`: (store가 제공) state 변경시 동작할 함수를 등록해주는 함수

---

## 구현방법

1. 액션타입 정의 (`action types`)

```javascript
const INCREMENT = "increment";
const DECREMENT = "decrement";
```

2. 액션객체생성함수 정의 (`functions for action objs`)

```javascript
const increment = (amount) => {
  return {
    type: increment,
    amount,
  };
};

const decrement = (amount) => {
  return {
    type: increment,
    amount,
  };
};
```

3. state 초깃값 설정 (`initial state`)

```javascript
const initialState = {
  number: 0,
};
```

4. 리듀서 정의 (`reducer`)

```javascript
function reducer(state = initialState, action) {
  switch (action.type) {
    case INCREMENT:
      return {
        ...state,
        number: state.number + action.amount,
      };
    case DECREMENT:
      return {
        ...state,
        number: state.number - action.amount,
      };
    default:
      return state;
  }
}
```

5. 스토어 생성

```javascript
import { createStore } from "redux";

const store = createStore(reducer);
```

6. 렌더 또는 구독시 동작할 함수들 정의 (`render`)

```javascript
const render = () => {
  const state = store.getState();
  // ... Render something
  console.log("::: render", state.number);
};

const render2 = () => {
  const state = store.getState();
  // ... Render something
  console.log("::: render2", state.number);
};
```

7. 구독

```javascript
const unsubscribe = store.subscribe(render);
const unsubscribe2 = store.subscribe(render2);
```

---

## 규칙

#### 단일 스토어

하나의 애플리케이션은 하나의 스토어만 갖는다.\
즉, 하나의 상태저장공간만 갖는다.

모듈화를 하고싶을 경우,\
스토어가 아닌 `리듀서를 모듈화`하여, 단일 스토어에서 해당 모듈에서 사용하고자 하는 state 프로퍼티만 접근/변경하도록 한다.

#### 모든 변화(reducer)는 순수함수로 구성한다

- 모든 함수는 파라미터에만 의존한다, 같은 파라미터 = 같은 결과
- 외부 네트워크나, 데이터베이스에 직접 접근하지않는다. (다른 결과가 return 되거나, 요청자체가 실패할 수 있다.)
- new Date() or Math.random() 함수를 사용해선 안된다. (다른결과가 return)

#### 읽기 전용

store의 state는 읽기전용이며 불변성을 지켜야한다.\
따라서 state를 변경한다는 의미는 기존값에 대한 조작(상태변경)이 아니라, `새로운 값의 할당`이다.

---

## 편리한 사용

#### redux-actions

```shell
npm i redux-actions
```

redux를 조금 편리하게 사용할 수 있도록 도와주는 라이브러리로, 크게 다음 2가지 기능을 제공한다.

- 액션객체생성함수의 손쉬운 정의
- reducer에서 switch/case문을 쉽게 대체

```js
import { createAction, handleAction } from "redux-actions";

const INCREASE = "increase";
const DECREASE = "decrease";

const initialState = {
  number: 0,
};

/* 
    ### 액션객체생성함수의 손쉬운 정의 ###
*/

/* 
< 사용 전 >
export const increase = () => ({ type: INCREASE });
export const decrease = () => ({ type: DECREASE });
*/

export const increase = creaseAction(INCREASE);
export const decrease = creaseAction(DECREASE);

/*
    ### reducer의  switch/case 문을 쉽게 대체 ###
*/

/*
< 사용 전 >
export default reducer = (state = initialState, action) => {
  switch (action.type) {
    case INCREASE:
      return {
        ...state,
        state: state.number + 1,
      };
    case DECREASE:
      return {
        ...state,
        state: state.number - 1,
      };
    default:
      return state;
  }
};
*/

export default reducer = handleActions(
  {
    [INCREASE]: (state, action) => ({ ...state, number: state.number + 1 }),
    [DECREASE]: (state, action) => ({ ...state, number: state.number + 1 }),
  },
  initialState
);
```

#### bindActionCreators

redux가 제공하는 함수로,\
action객체를 dispatch하는 과정을 편리하게 해주는 함수

create action obj -> dispatch 과정을 하나로 묶어준다.

```js
...
import { dispatch, bindActionCreators } from 'redux';

const ACTION_1 = 'action1';
const ACTION_2 = 'action2';

const action1 = () => ({ type: ACTION_1 });
const action2 = () => ({ type: ACTION_2 });

// 사용 전
dispatch(action1());
dispatch(action2());


// 사용 후
const ac = bindActionCreator({
  action1,
  action2
}, dispatch);

ac.action1(); // = dispatch(action1());
ac.action2(); // = dispatch(action2());
```
