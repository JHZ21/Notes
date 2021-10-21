# 零基础学习useReducer ，从入门到精通

* [useReducer | 官方文档](https://zh-hans.reactjs.org/docs/hooks-reference.html#usereducer)

  

## 一、useReducer

### 使用形式：

```js
const [state, dispatch] = useReducer(reducer, initialArg, init);
```

> **[`useState`](https://zh-hans.reactjs.org/docs/hooks-reference.html#usestate) 的替代方案**。它接收一个形如 `(state, action) => newState` 的 reducer，并返回当前的 state 以及与其配套的 `dispatch` 方法

### 使用场景：

*  state 逻辑较复杂且包含多个子值
* 下一个 state 依赖于之前的 state 
* 使用 `useReducer` 还能给那些会触发深更新的组件做性能优化，因为[你可以向子组件传递 `dispatch` 而不是回调函数](https://zh-hans.reactjs.org/docs/hooks-faq.html#how-to-avoid-passing-callbacks-down) 

```jsx
const initialState = {count: 0};

function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    default:
      throw new Error();
  }
}

function Counter() {
  const [state, dispatch] = useReducer(reducer, initialState);
  return (
    <>
      Count: {state.count}
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}
```

* init 惰性初始化
  * init函数
  * 初始 state 将被设置为 `init(initialArg)`
  * 计算 state 的逻辑提取到 reducer 外部

```jsx
function init(initialCount) {  return {count: initialCount};}
function reducer(state, action) {
  switch (action.type) {
    case 'increment':
      return {count: state.count + 1};
    case 'decrement':
      return {count: state.count - 1};
    case 'reset':     
      return init(action.payload);    
    default:
      throw new Error();
  }
}

function Counter({initialCount}) {
  const [state, dispatch] = useReducer(reducer, initialCount, init); 
  return (
    <>
      Count: {state.count}
      <button
        onClick={() => dispatch({type: 'reset', payload: initialCount})}>        Reset
      </button>
      <button onClick={() => dispatch({type: 'decrement'})}>-</button>
      <button onClick={() => dispatch({type: 'increment'})}>+</button>
    </>
  );
}
```

### 实现简单版useReducer

```js
function useReducer(reducer, initialState) {
  const [state, setState] = useState(initialState);

  function dispatch(action) {
    const nextState = reducer(state, action);
    setState(nextState);
  }

  return [state, dispatch];
}
```



## 二、例子：useUndo

* [展示例子](https://codesandbox.io/s/5v9yoz7xn4?file=/src/index.js:303-310)
* [use-undo 仓库](https://github.com/homerchen19/use-undo)

### useReducer使用范例

* [useUndo |仓库链接](https://github.com/homerchen19/use-undo/blob/master/index.ts)





## 三、useReducer + useContext

![img](https://p1-jj.byteimg.com/tos-cn-i-t2oaga2asx/gold-user-assets/2019/5/27/16af9e4ff4471be9~tplv-t2oaga2asx-zoom-crop-mark:1304:1304:1304:734.awebp)

* [用 useContext + useReducer 替代 redux|掘金](https://juejin.cn/post/6844903854807482382)
* [这一次彻底搞定 useReducer - useContext使用 | 掘金](https://juejin.cn/post/6844903869609148430)

### 使用Context相比回调函数的优势：

* 对比回调函数的自定义命名，Context的Api更加明确，我们可以更清晰的知道哪些组件使用了dispatch、应用中的数据流动和变化。这也是React一直以来单向数据流的优势。
* 更好的性能：如果使用回调函数作为参数传递的话，因为每次render函数都会变化，也会导致子组件rerender。当然我们可以使用[useCallback解决这个问题](https://link.juejin.cn?target=https%3A%2F%2Freactjs.org%2Fdocs%2Fhooks-faq.html%23how-to-read-an-often-changing-value-from-usecallback)，但相比`useCallback`React官方更推荐使用useReducer，因为React会保证dispatch始终是不变的，不会引起consumer组件的rerender。

## 四、使用总结

* 如果你的页面`state`很简单，可以直接使用`useState`

* 如果你的页面`state`比较复杂（state是一个对象或者state非常多散落在各处）请使用userReducer

* 如果你的页面组件层级比较深，并且需要子组件触发`state`的变化，可以考虑useReducer + useContext





