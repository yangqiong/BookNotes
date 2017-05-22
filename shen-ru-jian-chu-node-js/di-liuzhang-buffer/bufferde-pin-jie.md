```
var fs = require('fs');
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

