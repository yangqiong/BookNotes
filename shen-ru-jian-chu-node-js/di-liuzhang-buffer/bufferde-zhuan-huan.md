## 字符串转Buffer

Buffer.from\(string \[, encoding\]\)

一个Buffer对象可以存储不同编码类型的字符串转码的值，可以通过write方法实现

buf.write\(string, \[offset, \[, length\]\]\[, encoding\]\)

## Buffer转字符串

buf.toString\(\[encoding \[,start \[, end\]\]\]\)

## Buffer编码类型

Buffer.isEncoding\(encoding\)判断编码是否支持转换

对于不支持的编码类型，可以借助iconv（C++实现）和iconv-lite（JavaSciript实现）实现。

```
var iconv = require("iconv-lite");
var str = iconv.decode(buf, "gb2312");
var buf = iconv.encode(str, "gb2312");
```

iconv-lite对于无法转换的内容如果是多字节，会输出"黑背景？"，单字节输出？

iconv则有三级降级策略，会尝试翻译无法转换的内容，或者忽略这些内容。如果不设置忽略，iconv对于无法转换的内容将会得到EILSEQ一场

```
new Iconv("UTF-8", "ASCII");
new Iconv("UTF-8", "ASCII//IGNORE");
new Iconv("UTF-8", "ASCII//TRANSLIT");
new Iconv("UTF-8", "ASCII//TRANSLIT//IGNORE")
```



