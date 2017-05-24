Nodejs Events模块只是发布-订阅模式（观察者模式）的一种官方实现。

其中实现的特性有

* 执行顺序：如果对同一个事件监听了多次，当触发此事件时，按监听的顺序执行回调函数。
* 回调函数的执行过程是同步的，一个接着一个执行。

## 监听多次

如果通过on对事件监听多次，则回调顺序执行；如果通过prependListener对事件监听多次，则后监听先执行

```
var myEmitter = new MyEmitter();
myEmitter.on('event', (a, b) => {
  console.log("on1")
});

myEmitter.prependListener('event', function(){
    console.log("prepend1")
})

myEmitter.prependListener('event', function(){
    console.log("prepend2")
})

myEmitter.on('event', (a, b) => {
  console.log("on2")
});

myEmitter.emit('event', 'a', 'b');

// 结果
// prepend2
// prepend1
// on1
// on2
```

## 监听传参和this

回调函数中的参数个数随意

```
var myEmitter = new MyEmitter();
myEmitter.on('event', function(a, b) {
  console.log(a, b, this);
  // Prints:
  //   a b MyEmitter {
  //     domain: null,
  //     _events: { event: [Function] },
  //     _eventsCount: 1,
  //     _maxListeners: undefined }
});
myEmitter.emit('event', 'a', 'b');
```

ES6中的箭头回调函数

```
var myEmitter = new MyEmitter();
myEmitter.on('event', (a, b) => {
  console.log(a, b, this);
  // Prints: a b {}
});
myEmitter.emit('event', 'a', 'b');
```

### error事件

默认没有erroer事件，如果触发此事件而没有监听，讲跑出异常，程序退出。解决办法

```
var myEmitter = new MyEmitter();
myEmitter.on('error', (err) => {
  console.error('whoops! there was an error');
});
myEmitter.emit('error', new Error('whoops!'));
```

其次解决办法

```
var myEmitter = new MyEmitter();

process.on('uncaughtException', (err) => {
  console.error('whoops! there was an error');
});

myEmitter.emit('error', new Error('whoops!'));
```

## 异步执行

回调函数还是顺序同步执行，只是其中的具体任务变成异步

```
var myEmitter = new MyEmitter();
myEmitter.on('event', (a, b) => {
    setImmediate(() => {
        console.log('this happens asynchronously');
    });
});
myEmitter.emit('event', 'a', 'b');
```

## 其他方法

* emitter.eventNames\(\) 获取所有监听的事件名称
* emitter.listenerCount\(eventName\) 获取某个监听事件的个数
* emitter.listeners\(eventName\) 返回监听此事件的回调函数构成的数组

```
var myEmitter = new MyEmitter();
myEmitter.on('event', (a, b) => {
  console.log(a, b);
});
myEmitter.emit('event', 'a', 'b');


console.log(util.inspect(myEmitter.listeners('event'))); // Prints: [ [Function] ]
for (let fun of myEmitter.listeners('event')){
    fun(1, 2); // Prints: 1, 2
}
```



