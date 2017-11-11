# filter

#### 签名: `filter(select: Function, thisArg: any): Observable`

## 发出符合给定条件的值。

---

:bulb: 如果你希望当不满足条件时完成 observable 的话，请查阅 [takeWhile](takewhile.md)！

---

### 示例

##### 示例 1: 过滤出偶数

( [jsBin](http://jsbin.com/vafogoluye/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/tkz0fuy2/) )

```js
// 发出 (1,2,3,4,5)
const source = Rx.Observable.from([1,2,3,4,5]);
// 过滤掉奇数
const example = source.filter(num => num % 2 === 0);
// 输出: "Even number: 2", "Even number: 4"
const subscribe = example.subscribe(val => console.log(`Even number: ${val}`));
```

##### 示例 2: 基于属性过滤对象

( [jsBin](http://jsbin.com/qihagaxuso/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/yjdsoug1/) )

```js
// 发出 ({name: 'Joe', age: 31}, {name: 'Bob', age:25})
const source = Rx.Observable.from([{name: 'Joe', age: 31}, {name: 'Bob', age:25}]);
// 过滤掉年龄小于30岁的人
const example = source.filter(person => person.age >= 30);
// 输出: "Over 30: Joe"
const subscribe = example.subscribe(val => console.log(`Over 30: ${val.name}`));
```

##### 示例 3: 过滤出大于给定值的数字

( [jsBin](http://jsbin.com/rakabaheyu/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/g1tgreha/) )

```js
// 每1秒发出值
const source = Rx.Observable.interval(1000);
// 过滤掉所有值知道 interval 发出的值大于5
const example = source.filter(num => num > 5);
/*
  "Number greater than 5: 6"
  "Number greater than 5: 7"
  "Number greater than 5: 8"
  "Number greater than 5: 9"
*/
const subscribe = example.subscribe(val => console.log(`Number greater than 5: ${val}`));
```

### 其他资源

* [filter](http://cn.rx.js.org/class/es6/Observable.js~Observable.html#instance-method-filter) :newspaper: - 官方文档
* [使用 filter 添加条件逻辑](https://egghead.io/lessons/rxjs-adding-conditional-logic-with-filter?course=step-by-step-async-javascript-with-rxjs) :video_camera: :dollar: - John Linquist
* [过滤操作符: filter](https://egghead.io/lessons/rxjs-filtering-operator-filter?course=rxjs-beyond-the-basics-operators-in-depth) :video_camera: :dollar: - André Staltz

---
> :file_folder: 源码:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/filter.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/filter.ts)
