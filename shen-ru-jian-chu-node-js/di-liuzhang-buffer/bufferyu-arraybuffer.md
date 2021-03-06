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

实例有个buffer属性返回被引用的ArrayBuffer

实例有个byteLength属性返回被引用的ArrayBuffer的字节数



Buffer对象即为Uint8Array对象

**区别ArrayBuffer对象,TypedArray对象的slice方法返回的是原对象的拷贝，而Buffer对象的slice方法返回的是原对象的引用**

```
var buf1 = Buffer.alloc(8);     // <Buffer 00 00 00 00 00 00 00 00>
var buf2 = new Uint8Array(8);   // <Buffer 00 00 00 00 00 00 00 00>
buf1.buffer                     //  ArrayBuffer { byteLength: 8 }
buf2.buffer                     //  ArrayBuffer { byteLength: 8 }
```

**Buffer.from\(TypedArray对象\) 拷贝 与Buffer.from\(ArrayBuffer\)引用**

    const arr = new Uint16Array(2);

    arr[0] = 5000; // 0x1388
    arr[1] = 4000; // 0x0fa0

    // Copies the contents of `arr`
    const buf1 = Buffer.from(arr);

    // Shares memory with `arr`
    const buf2 = Buffer.from(arr.buffer);

    // Prints: <Buffer 88 a0>
    console.log(buf1);

    // Prints: <Buffer 88 13 a0 0f> // 也体现了计算机是属于小
    console.log(buf2);

    arr[1] = 6000;

    // Prints: <Buffer 88 a0>
    console.log(buf1);

    // Prints: <Buffer 88 13 70 17>
    console.log(buf2);

### buf.readInt16BE，buf.readInt16LE 等

```
var buf = Buffer.from([0, 5]);
buf.readInt16BE(); // 5
buf.readInt16LE(); // 1280
buf.readInt16LE(1); // Throws an exception: RangeError: Index out of range 默认为报错，读取16位，但只有8位
buf.readInt16LE(1, true) // 5 // 设置后不报错
```



