```
<Buffer e4 b8 ad e5 9b bd e4 ba ba>var fs = require('fs');
var rs = fs.createReadStream("data.txt");
var data = "";
rs.on("data", function(trunk){
    data += trunk;
})
rs.on("end", function(){
    console.log(data);
})
```

如上代码，在**data += trunk** 的过程中隐藏着trunk.toString\(\)，对于宽字节编码，则可能出现截断，导致打印data中出现乱码。

## 解决方法1

rs.setEncoding\("utf8"\)，原因在于调用setEncoding时，可读流对象内置了decoder对象，此对象来源于string\_decoder模块StringDecoder对象。

```
// Buffer.from("中国人") <Buffer e4 b8 ad e5 9b bd e4 ba ba>
var StringDecoder = require("string_decoder").StringDecoder;
var decoder = new StringDecoder("utf8");
var buf1 = Buffer.from([0xe4, 0xb8, 0xad, 0xe5]) // 中
console.log(decoder.write(buf1)) // 中
var buf2 = Buffer.from([0x9b, 0xbd, 0xe4, 0xba, 0xba])
console.log(decoder.write(buf2)) // 国人
```



