## 查看内存信息

```
> process.memoryUsage()
{ rss: 15360000,
  heapTotal: 6733824,
  heapUsed: 5110952,
  external: 8736 }
```

rss: Resident Set Size 常驻内存大小；包括Code Segment，Stack，Heap（V8堆内存），External（堆外内存）

