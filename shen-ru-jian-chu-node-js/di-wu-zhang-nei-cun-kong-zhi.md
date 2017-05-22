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

V8堆内存分为新生代内存空间和老生代内存空间。

新生代内存的最大值在64为系统和32为系统上默认分别为32M和16M。

老生代内存的最大值在64为系统和32为系统上默认分别为1.4G和0.7G。

可以在启动时通过`node --max-old--space-size=3000 // 单位为MB` `node --max-new--space-size=1024 // 单位为KB` 修改



