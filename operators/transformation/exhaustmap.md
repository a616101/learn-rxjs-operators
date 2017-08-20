# exhaustMap

#### 签名: `exhaustMap(project: function, resultSelector: function): Observable`

## 映射成内部 observable，忽略其他值直到该 observable 完成。

<<<<<<< HEAD
### Examples
=======
---

### 示例
>>>>>>> docs(exhaustMap): translate operator exhaustMap.md<100%>

##### 示例 1: 使用 interval 的 exhaustMap 

( [jsBin](http://jsbin.com/woposeqobo/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/9ovzapp9/) )

```js
const interval = Rx.Observable.interval(1000);
const delayedInterval = interval.delay(10).take(4);

const exhaustSub = Rx.Observable
	.merge(
       // 延迟10毫秒，然后开始 interval 并发出4个值
		delayedInterval,
       // 立即发出
		Rx.Observable.of(true)
  )
  /*
   *  第一个发出的值 (of(true)) 会被映射成每秒发出值、 
   *  5秒后完成的 interval observable 。
   *  因为 delayedInterval 的发送是晚于前者的，虽然 observable 
   *  仍然是活动的，但它们会被忽略。
   *
   *  与类似的操作符进行下对比:
   *  concatMap 会进行排队
   *  switchMap 会在每次发送时切换成新的内部 observable
   *  mergeMap 会为每个发出值维护新的 subscription
   */
  .exhaustMap(_ => interval.take(5))
  // 输出: 0, 1, 2, 3, 4
  .subscribe(val => console.log(val))
```

### 其他资源

<<<<<<< HEAD
##### Example 2: Another exhaustMap with interval

( [jsBin](http://jsbin.com/fizuduzuti/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/5ck8yg5k/3/) )

```js
const firstInterval = Rx.Observable.interval(1000).take(10);
const secondInterval = Rx.Observable.interval(1000).take(2);

const exhaustSub = firstInterval
.do(i => console.log(`Emission of first interval: ${i}`))
.exhaustMap(f => secondInterval)
/*
  When we subscribed to the first interval, it starts to emit a values (startinng 0).
  This value is mapped to the second interval which then begins to emit (starting 0).  
  While the second interval is active, values from the first interval are ignored.
  We can see this when firstInterval emits number 3,6, and so on...
  
    Output:
    Emission of first interval: 0
    0
    1
    Emission of first interval: 3
    0
    1
    Emission of first interval: 6
    0
    1
    Emission of first interval: 9
    0
    1
*/
.subscribe(s => console.log(s));
```


### Additional Resources
* [exhaustMap](http://reactivex.io/rxjs/class/es6/Observable.js~Observable.html#instance-method-exhaustMap) :newspaper: - Official docs
=======
* [exhaustMap](http://cn.rx.js.org/class/es6/Observable.js~Observable.html#instance-method-exhaustMap) :newspaper: - 官方文档
>>>>>>> docs(exhaustMap): translate operator exhaustMap.md<100%>

---
> :file_folder: 源码:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/exhaustMap.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/exhaustMap.ts)
