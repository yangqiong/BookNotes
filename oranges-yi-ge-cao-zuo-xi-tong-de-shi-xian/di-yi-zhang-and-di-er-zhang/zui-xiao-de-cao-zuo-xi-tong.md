## 计算机启动

当计算机电源被打开时，它会先进行加电自检（POST），然后寻找启动盘，如果是选择从软盘（floppy）启动，计算机就会检查软盘的0面0磁道1扇区，如果发现它以0xAA55结束，则BIOS认为它是一个引导扇区。（软盘一扇区为512个字节）一个正确的引导扇区除了以0xAA55结束之外，还应该包含一段少于512字节的执行码。

一旦BIOS发现了引导扇区，就会将这512字节的内容装载到内存地址0000:7c00处，然后跳转到0000:7c00处将控制权彻底交给这段引导代码。到此为止，计算机不在由BIOS中固有的程序来控制，而变成由操作系统的一部分来控制。

编译 `nasm boot.asm -o boot.bin`

制作镜像 `dd if=boot.bin of=a.img bs=512 count=1 conv=notrunc`

安装bochs虚拟机 `brew install bochs`

启动虚拟机 `bochs`  bootsrc在此目录下（Mac下有提示映射错误，先忽略），默认进入debug模式，需按c并回车

![](/assets/os.png)

---

* [计算机是如何启动的](http://www.ruanyifeng.com/blog/2013/02/booting.html)



