ret指令用栈中的数据，修改IP的内容，从而实现近转移。 // 相当于pop IP

retf指令用栈中的数据，修改CS和IP的内容，从而实现远转移。// 相当于 pop IP，pop CS

call指令将当前的IP或CS压入栈中，然后转移。

## 子程序

```
call 标号
...
标号:
    ...
    ret
```



