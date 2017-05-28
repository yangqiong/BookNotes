在程序中，段名就是相当于一个标号，它代表了段地址。

```
asssume cs:code,ds:data,ss:stack
data segment
    dw 0123H, 0456H
data ends
stack segment
    dw 0,0
stack ends;
code segment
start:
    mov ax, stack
    mov ss, ax
    mov sp, 16
    
    mov ax, data
    mov ds, ax
    ...
code ends
end start
```

end start 指明程序的程序入口，被转化为一个入口地址，存储在可执行文件的描述信息中。当程序被加载到内存时，从可执行文件的描述信息中读取入口地址，设置CS:IP。

“代码段”，“数据段”，“栈段”完全是我们的安排，具体的使用还是会根据寄存器CS，DS，SP的指向。

在8086CPU中，每个段空间最大为64KB，所以如果数据超过，就不能放在一个段中，需要定义多个段。

`dw` （define word）定义字型数据，在8086CPU中一个字占2个字节。

