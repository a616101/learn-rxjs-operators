# timer

#### 签名: `timer(initialDelay: number | Date, period: number, scheduler: Scheduler): Observable`

## 给定持续时间后，再按照指定间隔时间依次发出数字。

### 示例

##### 示例 1: 当 timer 结束时发出一个值

( [jsBin](http://jsbin.com/pazajanehu/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/vpx0y8fu/) )

```js
// 1秒后发出0，然后结束，因为没有提供第二个参数
const source = Rx.Observable.timer(1000);
// 输出: 0
const subscribe = source.subscribe(val => console.log(val));
```

##### 示例 2: timer 1秒后发出值，然后每2秒发出值

( [jsBin](http://jsbin.com/kejidofuje/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/30ddov8j/) )

```js
/*
  timer 接收第二个参数，它决定了发出序列值的频率，在本例中我们在1秒发出第一个值，
  然后每2秒发出序列值
*/
const source = Rx.Observable.timer(1000, 2000);
// 输出: 0,1,2,3,4,5......
const subscribe = source.subscribe(val => console.log(val));
```


### 其他资源

* [timer](http://cn.rx.js.org/class/es6/Observable.js~Observable.html#static-method-timer) :newspaper: - 官方文档
* [创建操作符: interval 和 timer](https://egghead.io/lessons/rxjs-creation-operators-interval-and-timer?course=rxjs-beyond-the-basics-creating-observables-from-scratch) :video_camera: :dollar: - André Staltz

---
> :file_folder: 源码:  [https://github.com/ReactiveX/rxjs/blob/master/src/observable/TimerObservable.ts](https://github.com/ReactiveX/rxjs/blob/master/src/observable/TimerObservable.ts)
