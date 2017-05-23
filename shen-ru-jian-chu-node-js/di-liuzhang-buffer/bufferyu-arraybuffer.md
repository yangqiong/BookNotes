## [ArrayBuffer](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/ArrayBuffer)

ES2015 中的方法，功能类似于Buffer.from\(size\) 创建了size位字节的buffer对象

```
var buf = new ArrayBuffer(10);  // 创建了10字节的二进制数据缓冲区
var buf1 = Buffer.from(buf);
var buf2 = new Int8Array(buf);  // Int8Array [ 0, 0, 0, 0, 0, 0, 0, 0, 0, 0 ]
var buf3 = new Int16Array(buf); // Int16Array [ 0, 0, 0, 0, 0 ]
```

**buf1 , buf2, buf3 共享此缓冲区**

```
> buf1[1] = 14;
14
> buf1
<Buffer 00 0e 00 00 00 00 00 00 00 00>
> buf2
Int8Array [ 0, 14, 0, 0, 0, 0, 0, 0, 0, 0 ]
> buf3
Int16Array [ 3584, 0, 0, 0, 0 ]
```

计算机属于小端地址，低地址存储地位，高地址存储高位，所以buf3\[0\] 的数值为 0x0e00，对于10进制为3584。

## [TypedArray](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/TypedArray) {#TypedArray_对象}

* Int8Array
* Uint8Array
* Uint8ClampedArray
* Int16Array
* Uint16Array
* Int32Array
* Uint32Array
* Float32Array
* Float64Array


