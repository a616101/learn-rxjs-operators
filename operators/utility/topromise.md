# toPromise

#### 签名: `toPromise() : Promise`

## 将 observable 转换成 promise 。

### 示例

##### 示例 1: 基础的 Promise

( [jsBin](http://jsbin.com/favoqecixi/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/thykc9up/) )

```js
// 返回基础的 observable
const sample = val => Rx.Observable.of(val).delay(5000);
// 将基础的 observable 转换成 promise
const example = sample('First Example')
  .toPromise()
  // 输出: 'First Example'
  .then(result => {
    console.log('From Promise:', result);
  });
```

##### 示例 2: 使用 Promise.all

( [jsBin](http://jsbin.com/hutiyicaco/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/xzu6u7hs/) )

```js
// 返回基础的 observable
const sample = val => Rx.Observable.of(val).delay(5000);
/*
  将每个 observable 转换成 promise 并使用 Promise.all 
  来等待所有 promise 解析完成
*/
const example = () => {
  return Promise.all([
    sample('Promise 1').toPromise(),
    sample('Promise 2').toPromise()
  ]);
}
// 输出: ["Promise 1", "Promise 2"]
example().then(val => {
  console.log('Promise.all Result:', val);
});
```


### 其他资源

* [toPromise](http://cn.rx.js.org/class/es6/Observable.js~Observable.html#instance-method-toPromise) :newspaper: - 官方文档

---
> :file_folder: 源码:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/toPromise.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/toPromise.ts)
