# nodejs



## 接受图片

[nodejs接受图片](https://blog.csdn.net/MyNameIsXiaoLai/article/details/85602200)





## jwt

* 原理

```js
import CryptoJs from 'crypto-js';


const base64UrlEncode: (val: string | Object) => string = (val) => {
  const wordArray = (val as any).clamp ? val : CryptoJs.enc.Utf8.parse(typeof val === 'string' ? val : JSON.stringify(val));
  let  base64Url =  CryptoJs.enc.Base64.stringify(wordArray);
  base64Url = base64Url.replace(/=+$/, '');
  base64Url = base64Url.replace(/\+/g, '-');
  base64Url = base64Url.replace(/\//g, '_');
  return base64Url;
};


async getCGUserToken() {
    const tel = 'telxxxxx';
    if (!tel) return;
    const secret = 'xxxxxx';
    // 参数顺序不可变!
    const header = {
      typ: 'JWT',
      alg: 'HS256'
    };
    const payload = {
      tel,
      exp: Math.floor(Date.now() / 1000)  //过期时间戳，秒级时间戳
    };
    const encodedString = `${base64UrlEncode(header)}.${base64UrlEncode(payload)}`;
    const signature = base64UrlEncode(CryptoJs.HmacSHA256(encodedString, secret));
    const jwt = `${encodedString}.${signature}`;
    return jwt;
  }
```

* 使用 jsonwebtoken 依赖包

  * [jsonwebtoken](https://github.com/auth0/node-jsonwebtoken)

  