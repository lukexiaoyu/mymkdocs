# nodejs

让js可以在服务端运行

## fs

### readfile

```js
const fs=require('fs')//import fs模块，nodejs自带的
fs.readFile('./docs/01.html.md','utf-8',(err,data)=>{
    console.log(err);
    console.log('---');
    console.log(data);
})

```

fs.readFile是一个异步

参数1：必选，文件地址

参数2：==可选参数==，以什么编码格式来读取文件

参数3：必选，读取文件的结果，一个回调函数，err是错误信息，data是读取到的数据

### writefile

```js
fs.writeFile('./docs/01.html.md','nice',(err)=>{
    console.log(err);   

})
```

参数1：必选，地址

参数2：必选，写入内容

参数3：==可选参数==，以什么编码格式写入文件

参数4：回调函数，一个参数err

==这个写入会直接覆盖原来所有的东西····==

