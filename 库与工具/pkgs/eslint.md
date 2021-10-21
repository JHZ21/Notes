# eslint 

* [eslint](https://eslint.org/)
* 

## 开始

* 安装

```js
npm install eslint --save-dev
# or
yarn add eslint --dev
```

* init

```js
npx eslint --init
# or
yarn run eslint --init
```

* 

```js
npx eslint yourfile.js
# or
yarn run eslint yourfile.js
```

## 配置

### eslintrc.{js,yml,json}

```js
{
    "rules": {
        "semi": ["error", "always"], //语句强制分号结尾
        "quotes": ["error", "double"], //
    }
}
```

### first value: 禁止程度

- `"off"` or `0` - turn the rule off
- `"warn"` or `1` - turn the rule on as a warning (doesn't affect exit code)
- `"error"` or `2` - turn the rule on as an error (exit code will be 1)

