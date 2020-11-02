컴포넌트 성능을 최적화 하는 방법을 정리해본다.

---

## React.memo

함수형 컴포넌트에서 shouldComponentUpdate or Purecomponent 대신 사용할 수 있는 방법, <br>
사용하는 props의 변화가 없을 경우, update를 하지 않는다.

```js
const TodoItem = ({ done, children, onToggle, onRemove }) => {
  return (
    <div className={cx("todo-item")} onClick={onToggle}>
      ---
    </div>
  );
};

export default React.memo(TodoItem); //done, children, onToggle, onRemove 변화가 없을경우 update하지 않는다.
```

---

## useState 함수형 업데이트

일반적으로 useState의 set함수는 새로운 값을 파라미터로 받는다. <br>
useCallback안에서 useState를 사용할 경우, useCallback의 두번째 파라미터 배열에 의존하는 state를 추가해주어야 한다. <br>
즉, state가 바뀌면 useCallback의 set함수 또한 갱신이 되는데, <br>
useState의 set함수에 값 대신 <u>함수형 업데이트값을 넣어줌</u>으로써 불필요한 갱신을 막을 수 있다.

함수형 업데이트 값일 경우, <br>
파라미터로 이전 상태의 state 값을 얻는다.

```js
// 변경 전(setTodos(값))
const handleInsert = useCallback(
  (e) => {
    const newTodo = {
      text: input,
      done: false,
      id,
    };
    id++;

    setTodos([newTodo, ...todos]);
    setInput("");
  },
  [todos, input]
);

// 변경 후 (setTodos(함수형 업데이트 값))
const handleInsert = useCallback(
  (e) => {
    const newTodo = {
      text: input,
      done: false,
      id,
    };
    id++;

    setTodos((todos) => todos.concat(newTodo));
    setInput("");
  },
  [input]
);
```

---

## react-virtualized

보이는 component만 렌더링 작업을 하여 리소스를 아낀다. <br>

### 설치

```
npm i react-virtualized
```

### 사용

보이는 영역을 세팅해주고, 보이는 영역일때 수행 될 render 함수를 정의해준다.

```js
import React, { useCallback } from "react";
import { List } from "react-virtualized";
import TodoItem from "../TodoItem";

const TodoList = ({ todos, onToggle, onRemove }) => {
  const rowRenderer = useCallback(
    ({ index, key, style }) => {
      const todo = todos[index];

      return (
        <TodoItem
          key={key}
          done={todo.done}
          onToggle={() => {
            onToggle(todo.id);
          }}
          onRemove={() => {
            onRemove(todo.id);
          }}
          style={style}
        >
          {todo.text}
        </TodoItem>
      );
    },
    [todos, onToggle, onRemove]
  );

  return (
    <List
      className="TodoList"
      width={500} // 리스트 전체높이
      height={513} // 리스트 전체크기
      rowCount={todos.length} // 항목 갯수
      rowHeight={57} // 항목 높이
      rowRenderer={rowRenderer} // 항목 렌더링 함수
      list={todos} // 항목
      style={{ outline: "none" }} // 목록 전체에 적용되는 기본 스타일
    ></List>
  );
};
```

### 스타일 깨짐 현상 해결

```js
// 1. style prop 추가
// 2. TodoListItem-virtualized 클래스 div wrapper element 추가 & styled prop 적용
const TodoItem = ({ done, children, onToggle, onRemove, style }) => {
  return (
    <div className="TodoListItem-virtualized" style={style}>
      <div className={cx("todo-item")} onClick={onToggle}>
        <input className={cx("tick")} type="checkbox" checked={done} readOnly />
        <div className={cx("text", { done })}>{children}</div>
        <div
          className={cx("delete")}
          onClick={(e) => {
            onRemove();
            e.stopPropagation();
          }}
        >
          [지우기]
        </div>
      </div>
    </div>
  );
};
```

---

## 코드스플리팅

웹펙이(혹은 다른 번들러) 번들링을 진행할 때,
하나의 파일이 아닌, 특정 기준으로 여러개의 파일로 나눠서 번들링을 진행하는 기법으로,\
로딩이나 캐싱에 있어서 최대의 효율을 낼 수 있도록 하는방법이다.

여러 기준으로 코드를 나눌 수 있지만,\
자주 사용하는 방식은 로딩되는 파일을 기준으로 파일을 나누는 방식이다.\
즉, 동적로딩을 통한 코드스플리팅이다.

webpack 제공하는 import 함수를 이용해서, 동적으로 파일을 import 한다. <br>
동적으로 import되는 파일은 호출하는 시점에 request 하게 된다.

```javascript
import("./notify").then((result) => {
  // export default는 result.default를 참조한다.
  result.default();
});
```

### React에서 컴포넌트 동적 로딩 하는 법

동적으로 import한 컴포넌트를 state에 저장한다. <br>
단점) 매번 컴포넌트를 저장할 state를 선언해주어야 한다.

```js
class App extends React.Component {
  state = {
    SplitMe: null,
  };
```
