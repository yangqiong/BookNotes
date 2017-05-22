## 字符串转Buffer

Buffer.from\(string \[, encoding\]\)

一个Buffer对象可以存储不同编码类型的字符串转码的值，可以通过write方法实现

buf.write\(string, \[offset, \[, length\]\]\[, encoding\]\)

## Buffer转字符串

buf.toString\(\[encoding \[,start \[, end\]\]\]\)

## Buffer编码类型

Buffer.isEncoding\(encoding\)判断编码是否支持转换

对于不支持的编码类型，可以借助iconv（C++实现）和iconv-lite（JavaSciript实现）实现。

