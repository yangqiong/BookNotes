在正常的JavaScript执行中，无法立即回收的内存有全局变量引用和闭包两种情况。由于V8的内存机制，要十分消息此类变量是否**无限制**的增加，因为它会导致老生代中的对象增多。

* 全局变量（不通过var声明或者定义在global变量上），由于全局变量作用域需要直到进程退出才能释放，此时将导致引用的对象常驻内存（常驻在老生代中）

* 闭包 实现外部作用域访问内部作用域的方法

内存泄露的场景：

* 缓存
* 队列消费不及时
* 作用域未释放

## 内存泄露检测

heapdump: `let heapdump = require('heapdump')`; 内存泄露的时候会生成`heap-dump-<sec>.<usec>.heapsnapshot`文件，然后通过Chrome的开发者工具的Memory进行分析

memwatch-next: 全队垃圾回收会触发stats事件，经过5次垃圾回收内容仍然没有释放会触发lead事件，可以对堆内存进行比较

**缺少实践和应用**

## 大内存应用场景

操作大文件，Node提供了Stream模块。

对于读取或者写入大文件由于V8内存限制无法使用fs.readFile，fs.writeFile；可以通过fs.createReadStream和fs.createWreiteStream或者pipe来操作。

对于不是字符串层面的操作可以使用Buffer，Buffer使用堆外内存。

