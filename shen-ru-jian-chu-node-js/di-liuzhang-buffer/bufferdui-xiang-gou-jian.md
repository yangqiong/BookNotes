* Buffer.from\(array\) 返回一个新的Buffer对象
* Buffer.from\(arrayBuffer \[, byteOffset \[, length \]\]\) 返回一个Buffer对象，与ArrayBuffer共享内存
* Buffer.from\(buffer\) 以copy形式返回一个新的Buffer对象
* Buffer.from\(string \[, encoding\]\) 返回一个新的Buffer对象
* Buffer.alloc\(size \[, fill \[, encoding \]\]\) 返回一个新的Buffer对象，被初始化为“fill”，且不经过内置pool创建
* Buffer.allocUnsafe\(size\) 返回一个新的Buffer对象，未被初始化，可能经过pool创建
* Buffer.allocUnsafeSlow\(size\) 返回一个新的Buffer对象，不经过内置pool创建

是否经过pool创建，可以观察buf.parent.byteLength是否跟传入的参数创建的一致还是跟Buffer.poolSize一样



