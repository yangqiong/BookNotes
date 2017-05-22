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

如上代码，在**data += trunk** 的过程中隐藏着trunk.toString\(\)，对于宽字节编码，则可能出现截断，导致打印data中出现乱码

