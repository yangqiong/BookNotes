### buf.toString\(\[encoding\[, start\[, end\]\]\]\)

注意点: **如果不是以某种编码（不是原始正确编码）转为字符串，然后再根据此编码转为buffer，bufer的值可能跟原来不同**

为什么呢？比如e4对于的10进制值为228 而228超过了ascii 128为的范畴，所以被取为100（228-128）对应的值为d。

```
var buf = Buffer.from("中国", "utf8"); // <Buffer e4 b8 ad e5 9b bd>
var str1 = buf.toString("ascii") // 'd8-e\u001b='
Buffer.from(str1, "ascii") // <Buffer 64 38 2d 65 1b 3d>
```



