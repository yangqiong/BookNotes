* Buffer.from\(array\)  返回一份新的Buffer
* Buffer.from\(arrayBuffer \[, bufferOffset, length\]\) 返回一个的Buffer对象但与arrayBuffer共享内存
* Buffer.from\(buffer\) 返回一份新的Buffer对象
* Buffer.from\(string \[, encoding\]\) 返回一个新的Buffer对象
* Buffer.alloc\(size \[, fill, \[, encoding\]\]\) 返回一份新的Buffer对象，填充为“fill”，默认为0
* Buffer.allocUnsafe\(size\) 返回一份新的Buffer对象，内存未初始化
* Buffer.allocUnsafeSlow\(size\) 同上，但不使用内部pool



