slab动态内存管理机制，有如下三种状态

* full: 完全分配状态
* partial: 部分分配状态
* empty: 没有被分配状态

Node以`Buffer.poolSize`（默认为8K）为界限区分Buffer是大对象还是小对象

初始状态

```
var pool;
funtcion allocPool(){
    pool = new SlowBuffer(Buffer.poolSize);
    pool.used = 0;
}
```

第一次分配小Buffer对象：var buf1 = new Buffer\(1024\);

由于pool为undefined，调用allocPool

```
buf1.parent = pool;
buf1.offset = pool.used;
pool.used += buf1.length;
```

第二次分配小Buffer对象：

 var buf2 = new Buffer\(4000\), 由于 buf1.byteLength + buf2.byteLength &lt; Buffer.poolSize 

```
buf2.parent = pool;
buf2.offset = pool.used;
pool.used += buf2.length;
```

var buf3 = new Buffer\(8000\), 如果 buf1.byteLength + buf3.byteLength &gt; Buffer.poolSize

```
allocPool();
buf2.parent = pool;
buf2.offset = pool.used;
```



