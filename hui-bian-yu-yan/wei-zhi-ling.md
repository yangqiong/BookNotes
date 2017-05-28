segment 和 end 一段汇编程序至少有一个段，段名等标号将被编译、链接程序处理为一个段的段地址。

```
段名 segment
 ...
段名 ends
```

assume 将段寄存器与程序的某个段相关联

```
assume cs:段名
```

end 汇编程序的结束标记

程序返回

```
mov ax,4c00H
int 2H
```











