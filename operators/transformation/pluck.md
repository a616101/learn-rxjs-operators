# pluck

#### 签名: `pluck(properties: ...args): Observable`

## 选择属性来发出。

### 示例

##### 示例 1: 提取对象属性

( [jsBin](http://jsbin.com/zokaxiwahe/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/58v9xq0f/) )

```js
const source = Rx.Observable.from([
  {name: 'Joe', age: 30},
  {name: 'Sarah', age:35}
]);
// 提取 name 属性
const example = source.pluck('name');
// 输出: "Joe", "Sarah"
const subscribe = example.subscribe(val => console.log(val));
```

##### 示例 2: 提取嵌套的属性

( [jsBin](http://jsbin.com/joqesidugu/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/n592m597/) )

```js
const source = Rx.Observable.from([
  {name: 'Joe', age: 30, job: {title: 'Developer', language: 'JavaScript'}},
  // 当找不到 job 属性的时候会返回 undefined
  {name: 'Sarah', age:35}
]);
// 提取 job 中的 title 属性
const example = source.pluck('job', 'title');
// 输出: "Developer" , undefined
const subscribe = example.subscribe(val => console.log(val));
```


### 其他资源

* [pluck](http://cn.rx.js.org/class/es6/Observable.js~Observable.html#instance-method-pluck) :newspaper: - 官方文档

---
> :file_folder: 源码:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/pluck.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/pluck.ts)
