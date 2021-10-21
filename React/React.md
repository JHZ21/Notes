# React



## react 常见setState的原理解析

* [react 常见setState的原理解析 | 简书](https://www.jianshu.com/p/1e7e956ec1ee)

### batch update 批量更新



#### setState

- 在官方的描述中，setState操作并不保证是同步的，也可以认为是异步的。
- React在setState之后，会经对state进行diff，判断是否有改变，然后去diff dom决定是否要更新UI。
- 在短时间内频繁setState。React会将state的改变压入栈中，在合适的时机，批量更新state和视图，达到提高性能的效果。

### setState 参数  function

> 在setState的第一个参数中传入function，该function会被压入调用栈中，在state真正改变后，按顺序回调栈里面的function。该function的第一个参数为上一次更新后的state。这样就能确保你下一次的操作拿到的是你预期的值

## hook

* 如果我们想要有条件地执行一个 effect，可以将判断放到 Hook 的*内部*：

```jsx
  useEffect(function persistForm() {
    // 👍 将条件判断放置在 effect 中
    if (name !== '') {
      localStorage.setItem('formData', name);
    }
  });
```

### useReducer

```jsx
function useReducer(reducer, initialState) {
  const [state, setState] = useState(initialState);

  function dispatch(action) {
    const nextState = reducer(state, action);
    setState(nextState);
  }

  return [state, dispatch];
}
```

```jsx
function Todos() {
  const [todos, dispatch] = useReducer(todosReducer, []);

  function handleAddClick(text) {
    dispatch({ type: 'add', text });
  }

  // ...
}
```

```js
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

### useState

* setState

  ```jsx
  setCount(initialCount)
  setCount(prevCount => prevCount - 1)
  ```

* 惰性初始 state

  ```jsx
  const [state, setState] = useState(() => {
    const initialState = someExpensiveComputation(props);
    return initialState;
  });
  ```

### useEffect

### useContext

* useContext(MyContext)

```jsx
<MyContext.Provider>

</MyContext.Provider>
```

### useCallback

````jsx
useCallback(fn, deps)
// 相当于 
useMemo(() => fn, deps)
````

### useRef

```js
const refContainer = useRef(initialValue);
```

### useImperativeHandle

```js
useImperativeHandle(ref, createHandle, [deps])
```

* useImperativeHandle 应当与 forwardRef 一起使用

### useLayoutEffect

### useDebugValue

