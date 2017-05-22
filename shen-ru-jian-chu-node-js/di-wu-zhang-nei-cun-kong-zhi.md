## 查看内存信息

```
> process.memoryUsage()
{ rss: 15360000,
  heapTotal: 6733824,
  heapUsed: 5110952,
  external: 8736 }
```

rss: Resident Set Size 常驻内存大小；包括Code Segment，Stack，Heap（V8堆内存），External（堆外内存）。[\[参考链接\]](http://stackoverflow.com/questions/12023359/what-do-the-return-values-of-node-js-process-memoryusage-stand-for)

heapTotal V8为堆内存分配的总大小，heapUsed为已使用的堆内存大小。

默认情况下 64位系统堆内存为1.4G + 64M，32位系统堆内存约为0.7G + 32M。

V8堆内存分为新生代内存空间和老生代内存空间。

