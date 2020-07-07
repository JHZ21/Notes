# 手撕代码



## New 

* 箭头函数会捕获其`所在上下文`的 `this` 值，作为自己的 `this` 值

* new： 函数作为构造函数调用的时，上下文环境的this指向实例对象

* 手写 new

  `new`被调用后做了三件事情:

  1. 让实例可以访问到私有属性
  2. 让实例可以访问构造函数原型(constructor.prototype)所在原型链上的属性
  3. 如果构造函数return返回的结果不是引用数据类型，则返回实例对象

  ```js
  function newFactory(ctor, ...args) {
      if(typeof ctor !== 'function'){
        throw 'newOperator function the first param must be a function';
      }
      let obj = new Object();
      // obj.__proto__.__proto__ = ctor.prototype
      // 中间隔一个原型， 相当于ctor子类，使得obj原型扩展内容时，不会污染到ctor.prototype
      obj.__proto__ = Object.create(ctor.prototype);
      let res = ctor.apply(obj, ...args);
      
      let isObject = typeof res === 'object' && typeof res !== null;
      let isFunction = typoof res === 'function';
      return isObect || isFunction ? res : obj;
  };
  ```

  

## bind

* 手写bind

1. `bind` 与 `call/apply` 的区别就是返回的是一个待执行的函数，而不是函数的执行结果;
2. `bind` 返回的函数作为构造函数与 `new` 一起使用，绑定的 `this` 需要被忽略;

> 调用绑定函数时作为this参数传递给目标函数的值。如果使用new运算符构造绑定函数，则忽略该值。—— MDN

```js
Function.prototype.bind = function(context, ...initArgs) {
    // bind 调用的方法一定要是一个函数
    if (typeof this !== 'function') {
      throw new TypeError('not a function');
    }
    let self = this;
    let F = function() {};
    F.prototype = this.prototype;
    let bound = function(...finnalyArgs) {
      // 将前后参数合并传入
      return self.call(this instanceof F ? this : context || this, ...initArgs, ...finnalyArgs);
    }
    bound.prototype = new F();
    return bound;
}
```



## call

```js
Function.prototype.call = function(context, ...args) {
	const fn = Symbol('fn')
	context[fn] = this
	const result = eval('context.fn(...args)')
	delete context[fn]
	return result
}
```

## apply

```js
Function.prototype.apply = function(context, args) {
	const fn = Symbol('fn')
	context[fn] = this
	const result = eval('context.fn(...args)')
	delete context[fn]
	return result
}

```

## promise

```js
// Promsie

function Promise(exec) {
	this.onResolvedCbs = []
	exec(value => {
		setTimeout(() => {
			this.data = value
			this.onResolvedCbs.forEach(item => item(value))
		})
	})
}
  
Promise.prototype.then = function(onResolved) {
	return new Promise(resolve => {
		this.onResolvedCbs.push(() => {
			const result = onResolved(this.data)
			result instanceof Promise ? result.then(resolve) : resolve(result)
		})
	})
}

```

## shallowClone

```js
// shallowClone 浅拷贝

function shallowClone(target) {
	if(typeof target === 'object' && target !== 	null) {
		const cloneTarget = Array.isArray(target)? [] : {}
		for(let prop in target) {
			if(target.hasOwnProperty(prop)) {
				cloneTarget[prop] = target[prop]
			}
		}
		return cloneTarget
	} else {
		return target
	}
}

```

## deepClone

```js
// deepClone 深拷贝

function shallowClone(target) {
	if(typeof target === 'object' && target !== null) {
		const cloneTarget = Array.isArray(target)? [] : {}
		for(let prop in target) {
			if(target.hasOwnProperty(prop)) {
				cloneTarget[prop] = target[prop]
			}
		}
		return cloneTarget
	} else {
		return target
	}
}

// deepClone 2

const isObject = (target) => (typeof target === 'object' || typeof target === 'function') && target !== null

const deepClone = (target, map = new WeakMap()) => {
	if(map.get(target)) 
		return target

	if (isObject(target)) {
		map.set(target, true)
		const cloneTarget = Array.isArray(target) ? []: {}
		for (let prop in target) {
			if (target.hasOwnProperty(prop)) {
				cloneTarget[prop] = deepClone(target[prop], map)
			}
		}
		return cloneTarget
	} else {
		return target
	}
}
const a = {val:2}
a.target = a
let newA = deepClone(a, new WeakMap())
console.log(newA)

// deepClone 3

const getType = (data) => { // 获取数据类型
	const baseType = Object.prototype.toString.call(data).replace(/^\[object\s(.+)\]$/g, '$1').toLowerCase();
    const type = data instanceof Element ? 'element' : baseType;
    return type;
};
const isPrimitive = (data) => { // 判断是否是基本数据类型
    const primitiveType = 'undefined,null,boolean,string,symbol,number,bigint,map,set,weakmap,weakset'.split(','); // 其实还有很多类型
    return primitiveType.includes(getType(data));
};
const isObject = data => (getType(data) === 'object');
const isArray = data => (getType(data) === 'array');
const deepClone = data => {
    let cache = {}; // 缓存值，防止循环引用
    const baseClone = _data => {
        let res;
        if (isPrimitive(_data)) {
            return data;
        } else if (isObject(_data)) {
            res = { ..._data }
        } else if (isArray(_data)) {
            res = [..._data]
        };
        // 判断是否有复杂类型的数据，有就递归
        Reflect.ownKeys(res).forEach(key => {
            if (res[key] && getType(res[key]) === 'object') {
                // 用cache来记录已经被复制过的引用地址。用来解决循环引用的问题
                if (cache[res[key]]) {
                    res[key] = cache[res[key]];
                } else {
                    cache[res[key]] = res[key];
                    res[key] = baseClone(res[key]);
                };
            };
        });
        return res;
    };
	return baseClone(data);
};

```

## debounce

```js
// debounce 防抖

function debounce(func, wait) {
  let tiemout = null
  return function(...args) {
    const context = this
    tiemout && clearTimeout(tiemout)
    tiemout = setTimeout(()=> func.apply(context, args), wait)
  }
}
```

```js
function debounce2(fn={}, wait=50, immediate) {
  let timer = null
  return function() {
    if(immediate) {
      fn.apply(this, arguments)
    }
    if(timer) {
      clearTimeout(timer)
      timer = null
    }
    timer = setTimeout(() => {
      fn.apply(this, arguments)
    }, wait);
  }
}
```





## throttle

```js
// throttle 节流

function throttle(func, wait) {
  let timeout = null
  return function (...args) {
    const context = this
    if (!timeout) {
      timeout = setTimeout(() => {
        timeout = null
        func.apply(context, args)
      }, wait)
    }
  }
}



```

```js
// 首次可以立即执行

function throttle2(func, wait) {
  let pre = 0
  return function (...args) {
    const now = Date().now()
    if (now - pre >= wait) {
      pre = now
      func.apply(this, args)
    }
  }
}
```

```js
// 首次立即执行，末次间隔内调用两次，会有效执行两次

// me 创作 
function throttle3(func, delay) {
  let context = this;
  let args = arguments;
  let nowTime = +new Date();

  if (!lastTime || nowTime > lastTime + delay) {
    //判断为第一次触发，立即函数立即生效
    lastTime = nowTime;
    func.apply(context, args);
  } else if (lastTime &&
    lastTime < nowTime &&
    nowTime < lastTime + delay) {
    //间隔取触发，使用相应时间的定时器，让函数在下个间隔时刻触发生效。并只触发一次定时器，
    // 无需清除定时器
    let time = lastTime + delay - nowTime; // 让定时器在下个间隔时刻生效
    lastTime = nowTime + time;  // 预判下次时间
    setTimeout(() => {
      func.apply(context, args);
    }, time);
  }
}
```

## instanceOf

```js
function instanceOf(left, right) {
  let proto = left.__proto__
  let prototype = right.prototype
  while(true) {
    if(proto == null) {
      return false
    } else if (proto === prototype) {
      return true
    }
    proto = proto.__proto__
  }
}
```

