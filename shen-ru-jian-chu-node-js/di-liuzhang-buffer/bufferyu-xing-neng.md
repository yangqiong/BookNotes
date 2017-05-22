## 网络传输

对于请求静态内容，可以先将静态内容预先转为Buffer的方式，可以避免每次请求都重复自动转换。

## 文件读取

文件fs.createReadStream基于Stream有个选项highWaterMark，如果highWaterMark设置过小，可能导致系统调用次数过多。



