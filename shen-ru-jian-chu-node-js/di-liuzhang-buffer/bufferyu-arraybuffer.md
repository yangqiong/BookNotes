## [ArrayBuffer](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)

ES2015 中的方法，功能类似于Buffer.from\(size\) 创建了size位字节的buffer对象

```
var buf = new ArrayBuffer(10);
var buf1 = Buffer.from(buf);
var buf2 = new Int8Array(buf);
var buf2 = new Int16Array(buf);
```



