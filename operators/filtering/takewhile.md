# takeWhile

#### 签名: `takeWhile(predicate: function(value, index): boolean): Observable`

## 发出值，直到提供的表达式结果为 false 。

### 示例

##### 示例 1: 使用限定条件取值

( [jsBin](http://jsbin.com/zanefaqexu/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/btroncone/yakd4jgc/) )

```js
// 发出 1,2,3,4,5
const source = Rx.Observable.of(1,2,3,4,5);
// allow values until value from source is greater than 4, then complete
// 允许值发出直到 source 中的值大于4，然后便完成
const example = source.takeWhile(val => val <= 4);
// 输出: 1,2,3,4
const subscribe = example.subscribe(val => console.log(val));
```

##### 示例 2: takeWhile() 和 filter() 的区别

( [jsBin](http://jsbin.com/yatoqurewi/1/edit?js,console) | [jsFiddle](https://jsfiddle.net/r497jgw3/1/) )

```js
// 发出 3, 3, 3, 9, 1, 4, 5, 8, 96, 3, 66, 3, 3, 3
const source = Rx.Observable.of(3, 3, 3, 9, 1, 4, 5, 8, 96, 3, 66, 3, 3, 3);

// 允许值通过直到源发出的值不等于3，然后完成
// 输出: [3, 3, 3]
source
 .takeWhile(it => it === 3 )
 .subscribe(val => console.log('takeWhile', val));

// 输出: [3, 3, 3, 3, 3, 3, 3]
source
 .filter(it => it === 3)
 .subscribe(val => console.log('filter', 3));
```

### 相关食谱

* [智能计数器](../../recipes/smartcounter.md)

### 其他资源

* [takeWhile](http://cn.rx.js.org/class/es6/Observable.js~Observable.html#instance-method-takeWhile) :newspaper: - 官方文档
* [使用 takeWhile 完成流](https://egghead.io/lessons/rxjs-completing-a-stream-with-takewhile?course=step-by-step-async-javascript-with-rxjs) :video_camera: :dollar: - John Linquist

---
> :file_folder: 源码:  [https://github.com/ReactiveX/rxjs/blob/master/src/operator/takeWhile.ts](https://github.com/ReactiveX/rxjs/blob/master/src/operator/takeWhile.ts)
