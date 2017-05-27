```
org 07c00h
mov ax, cs
mov ds, ax
mov es, ax
call DispStr
jmp $
DispStr:
    mov ax, BootMessage
    mov bp, ax
    mov cx, 16
    mov ax, 01301h
    mov bx, 000ch
    mov dl, 0
    int 10h
    ret
BootMessage:    db "Hello, OS world!"
times 510-($-$$) db     0;
dw 0xaa55
```

## 计算机启动

当计算机电源被打开时，它会先进行加电自检（POST），然后寻找启动盘，如果是选择从软盘（floppy）启动，计算机就会检查软盘的0面0磁道1扇区，如果发现它以0xAA55结束，则BIOS认为它是一个引导扇区。（软盘一扇区为512个字节）一个正确的引导扇区除了以0xAA55结束之外，还应该包含一段少于512字节的执行码。

