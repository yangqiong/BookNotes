```
# Configuration file for Bochs

# how much memory the emulated machine will have
megs: 32

# filename of ROM images
romimage: file=/usr/local/Cellar/bochs/2.6.8_1/share/bochs/BIOS-bochs-latest
vgaromimage: file=/usr/local/Cellar/bochs/2.6.8_1/share/bochs/VGABIOS-lgpl-latest

# what disk images will be used
floppya: 1_44=a.img, status=inserted    

# choose the boot disk
boot: floppy

# where do we send log messages?
log: bochsout.txt

# disable the mouse
mouse: enabled=0

# enable key mapping, using US layout as default
mouse: enabled=0 
keyboard: keymap=/usr/local/Cellar/bochs/2.6.8_1/share/bochs/keymaps/sdl-pc-us.map
```

## 计算机启动

计算机电源被打开时，它会先进行自检（POST），然后寻找启动盘，如果是选择从软盘启动（floppy），计算机就先检查软盘的0面0磁道1扇区，如果发现它以0xAA55结束，则BIOS认为它是一个引导扇区。



