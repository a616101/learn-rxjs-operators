# throttleTime

#### 签名: `throttleTime(duration: number, scheduler: Scheduler): Observable`

## 当指定的持续时间经过后发出最新值。

### 示例

##### 示例 1: 每5秒接收最新值

( [jsBin](http://jsbin.com/koqujayizo/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/4zysLc3y/) )

```js
// 每1秒发出值
const source = Rx.Observable.interval(1000);
/*
  throttle 5秒
  throttle 结束前发出的最后一个值将从源 observable 中发出
*/
const example = source
  .throttleTime(5000);
// 输出: 0...6...12
const subscribe = example.subscribe(val => console.log(val));
```

##### 示例 2: throttle 用来合并 observable
> 译者注：此示例有问题，描述和结果都对不上，待修复

( [jsBin](http://jsbin.com/takipadaza/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/xhd1zy3m/) )

```js
// 合并 observables 
const source = Rx.Observable
	.merge(
        // 每0.75秒发出值
		    Rx.Observable.interval(750),
        // 每1秒发出值
        Rx.Observable.interval(1000)
	);
// 在发出值的中间进行 throttle
const example = source.throttleTime(1200);
// 输出: 0...1...4...4...8...7
const subscribe = example.subscribe(val => console.log(val));
```


### 其他资源

* [throttleTime](http://cn.rx.js.org/class/es6/Observable.js~Observable.html#instance-method-throttleTime) :newspaper: - 官方文档
* [过滤操作符: throttle 和 throttleTime](https://egghead.io/lessons/rxjs-filtering-operators-throttle-and-throttletime?course=rxjs-beyond-the-basics-operators-in-depth) :video_camera: :dollar: - André Staltz

---
> :file_folder: 源码:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/throttleTime.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/throttleTime.ts)
