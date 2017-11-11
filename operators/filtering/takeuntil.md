# takeUntil

#### 签名: ` takeUntil(notifier: Observable): Observable`

## 发出值，直到提供的 observable 发出值，它便完成。

---

:bulb: 如果你只需要指定数量的值，试试 [take](take.md)！

---

### 示例

##### 示例 1: 取值直到 timer 发出

( [jsBin](http://jsbin.com/yevuhukeja/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/zbe9dzb9/) )

```js
// 每1秒发出值
const source = Rx.Observable.interval(1000);
// 5秒后发出值
const timer = Rx.Observable.timer(5000);
// 当5秒后 timer 发出值时， source 则完成
const example = source.takeUntil(timer);
// 输出: 0,1,2,3
const subscribe = example.subscribe(val => console.log(val));
```

##### 示例 2: 取前5个偶数

( [jsBin](http://jsbin.com/doquqecara/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/0dLeksLe/) )

```js
// 每1秒发出值
const source = Rx.Observable.interval(1000);
// 是偶数吗？
const isEven = val => val % 2 === 0;
// 只允许是偶数的值
const evenSource = source.filter(isEven);
// 保存运行中的偶数数量
const evenNumberCount = evenSource
	.scan((acc, _) => acc + 1, 0);
// 不发出直到发出过5个偶数
const fiveEvenNumbers = evenNumberCount.filter(val => val > 5);
  
const example = evenSource
	// 还给出当前偶数的数量以用于显示
  .withLatestFrom(evenNumberCount)
	.map(([val, count]) => `Even number (${count}) : ${val}`)
	// 当发出了5个偶数时，source 则完成
  .takeUntil(fiveEvenNumbers);
/*
	Even number (1) : 0,
	Even number (2) : 2
	Even number (3) : 4
	Even number (4) : 6
	Even number (5) : 8
*/
const subscribe = example.subscribe(val => console.log(val));
```


### 其他资源

* [takeUntil](http://cn.rx.js.org/class/es6/Observable.js~Observable.html#instance-method-takeUntil) :newspaper: - 官方文档
* [使用 takeUntil 来停止流](https://egghead.io/lessons/rxjs-stopping-a-stream-with-takeuntil?course=step-by-step-async-javascript-with-rxjs) :video_camera: :dollar: - John Linquist

---
> :file_folder: 源码:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/takeUntil.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/takeUntil.ts)
