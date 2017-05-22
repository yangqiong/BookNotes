slab动态内存管理机制，有如下三种状态

* full: 完全分配状态
* partial: 部分分配状态
* empty: 没有被分配状态

Node以Buffer.poolSize（默认为8K）为界限区分Buffer是大对象还是小对象。



