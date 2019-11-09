# 大纲-day01
## 初识Nodejs
- JavaScript是什么？ 
- JavaScript可以运行在哪里？ 

![](img/1.png)

| 浏览器     | 内核      |
| ------- | ------- |
| IE      | Trident |
| FireFox | Gecko   |
| Chrome  | WebKit  |
| Safari  | WebKit  |
| Opera   | Presto  |
| Edge    | Chakra  |

## Node.js的诞生
![image](img/2.png)

- 作者Ryan Dahl 瑞恩·达尔
    + 2004 纽约 读数学博士 
    + 2006 退学到智利 转向开发 
    + 2009.5对外宣布node项目，年底js大会发表演讲 
    + 2010 加入Joyent云计算公司 
    + 2012 退居幕后

> Node.js 是一种建立在Google Chrome’s v8 engine上的 non-blocking (非阻塞）, event-driven （基于事件的） I/O平台. 
> Node.js平台使用的开发语言是JavaScript，平台提供了操作系统低层的API，方便做服务器端编程，具体包括文件操作、进程操作、通信操作等系统模块

## Node.js可以用来做什么？

- 具有复杂逻辑的动态网站 
- WebSocket服务器 
- 命令行工具 
- 带有图形界面的本地应用程序 
- ......

## 终端基本使用
### 打开应用
- notepad 打开记事本
- mspaint 打开画图
- calc 打开计算机
- write 写字板
- sysdm.cpl 打开环境变量设置窗口
### 常用命令
- md 创建目录
- rmdir(rd) 删除目录，目录内没有文档。
- rd  /s/q abc（目录名） 删除子目录
- echo on a.txt 创建空文件
- del 删除文件
- rm 文件名 删除文件
- cat 文件名 查看文件内容
- cat > 文件名 向文件中写上内容。

## Node.js开发环境准备

1. 普通安装方式[官方网站](https://nodejs.org/zh-cn/)

2. 多版本安装方式
    - 卸载已有的Node.js
    - 下载[nvm](https://github.com/coreybutler/nvm-windows)
    - 在C盘创建目录dev
    - 在dev目中中创建两个子目录nvm和nodejs
    - 并且把nvm包解压进去nvm目录中
    - 在install.cmd文件上面右键选择【以管理员身份运行】
    - 打开的cmd窗口直接回车会生成一个settings.txt文件，修改文件中配置信息
    - 配置nvm和Node.js环境变量
        + NVM_HOME:C:\dev\nvm
        + NVM_SYMLINK:C:\dev\nodejs
    - 把配置好的两个环境变量加到Path中
## nvm常用的命令
- nvm list 查看当前安装的Node.js所有版本
- nvm install 版本号 安装指定版本的Node.js
- nvm uninstall 版本号 卸载指定版本的Node.js
- nvm use 版本号 选择指定版本的Node.js

## Node.js之HelloWorld
- 命令行方式REPL
- 运行文件方式
- 全局对象概览

## 服务器端模块化
- 服务器端模块化规范CommonJS与实现Node.js
- 模块导出与引入
- 模块导出机制分析
- 模块加载规则
    + 模块查找 不加扩展名的时候会按照如下后缀顺序进行查找 .js .json .node
- 模块分类
    + 自定义模块
    + 系统核心模块
        * fs 文件操作
        * http 网络操作
        * path 路径操作
        * querystring 查询参数解析
        * url url解析
        * ......

## ES6常用语法
- 变量声明let与const
- 变量的解构赋值
    + 数组解构赋值
    + 对象解构赋值
    + 字符串解构赋值
- 字符串扩展
    + includes()
    + startsWith()
    + endsWith()
    + 模板字符串
- 函数扩展
    + 参数默认值
    + 参数结构赋值
    + rest参数
    + 扩展运算符
    + 箭头函数
- 类与继承

## Buffer的基本操作

/*

    
    Buffer本质上就是字节数组
    1、构造方法（类）
    2、静态方法
    3、实例方法
*/

// 实例化buf对象
// let buf = new Buffer(5);
// let buf = Buffer.alloc(5);
// console.log(buf);

// let buf = Buffer.from('hello','utf8');
// console.log(buf);

// let buf = Buffer.from([0x62, 0x75, 0x66, 0x66, 0x65, 0x72]);
// console.log(buf.toString());

// -------------------------------------------
// 静态方法
// console.log(Buffer.isEncoding('utf8'));
// console.log(Buffer.isEncoding('gbk'));

// let buf = Buffer.from('hello');
// console.log(Buffer.isBuffer(buf));
// console.log(Buffer.isBuffer({}));

// let buf = Buffer.from('中国','ascii');
// console.log(Buffer.byteLength(buf));
// console.log(buf.toString());

// let buf1 = Buffer.alloc(3);
// let buf2 = Buffer.alloc(5);
// let buf3 = Buffer.concat([buf1,buf2]);
// console.log(Buffer.byteLength(buf3));

// let buf1 = Buffer.from('tom');
// let buf2 = Buffer.from('jerry');
// let buf3 = Buffer.concat([buf1,buf2]);
// console.log(Buffer.byteLength(buf3));
// console.log(buf3.toString());

// ---------------------------------------
// 实例方法
// let buf = Buffer.alloc(5);
// buf.write('hello',2,2);
// console.log(buf);

// let buf = Buffer.from('hello');
// let buf1 = buf.slice(2,3);
// console.log(buf === buf1);//false
// console.log(buf1.toString());

// toJSON方法不需要显式调用，当JSON.stringify方法调用的时候会自动调用toJSON方法
// const buf = Buffer.from([0x1, 0x2, 0x3, 0x4, 0x5]);
// const buf = Buffer.from('hello');
// const json = JSON.stringify(buf);
// console.log(json);

## 路径操作

const path = require('path');

// 获取路径的最后一部分
// console.log(path.basename('/foo/bar/baz/asdf/quux.html'));
// console.log(path.basename('/foo/bar/baz/asdf/quux.html', '.html'));

// 获取路径
// console.log(__dirname);
// console.log(path.dirname('/abc/qqq/www/abc'));

// 获取扩展名称
// console.log(path.extname('index.html'));

// 路径的格式化处理
// path.format() obj->string
// path.parse()  string->obj

// let obj = path.parse(__filename);
// console.log(obj.base);
/*
{ root: 'E:\\', 文件的跟路径
  dir: 'E:\\node\\day02\\02-code',文件的全路径
  base: '02.js',文件的名称
  ext: '.js',扩展名
  name: '02' 文件名称
}
*/
// let objpath = {
//     root : 'd:\\',
//     dir : 'd:\\qqq\\www',
//     base : 'abc.txt',
//     ext : '.txt',
//     name : 'abc'
// };
// let strpath = path.format(objpath);
// console.log(strpath);

// 判断是否为绝对路径
// console.log(path.isAbsolute('/foo/bar'));
// console.log(path.isAbsolute('C:/foo/..'));

// 拼接路径（..表示上层路径；.表示当前路径）,在连接路径的时候会格式化路径
// console.log(path.join('/foo', 'bar', 'baz/asdf', 'quux', '../../'));

// 规范化路径
// console.log(path.normalize('/foo/bar//baz/asdf/quux/..'));
// console.log(path.normalize('C:\\temp\\\\foo\\bar\\..\\'));

// 计算相对路径
// console.log(path.relative('/data/orandea/test/aaa', '/data/orandea/impl/bbb'));
// console.log(path.relative('C:\\orandea\\test\\aaa', 'C:\\orandea\\impl\\bbb'));

// 解析路径
// console.log(path.resolve('wwwroot', 'static_files/png/', '../gif/image.gif'));

// 两个特殊属性
console.log(path.delimiter);//表示路径分隔符（windows是\ Linux是/）
console.log(path.sep);//环境变量分隔符(windows中使用; linux中使用:)

## 异步I/O input/output

/*

    异步I/O input/output
    1、文件操作
    2、网络操作
    
    在浏览器中也存在异步操作：
    1、定时任务
    2、事件处理
    3、Ajax回调处理
    
    js的运行时单线程的
    引入事件队列机制
    
    Node.js中的事件模型与浏览器中的事件模型类似
    单线程+事件队列
    
    Node.js中异步执行的任务：
    1、文件I/O
    2、网络I/O
    
    基于回调函数的编码风格
## 文件操作-查看文件状态

const fs = require('fs');
console.log(1);
fs.stat('./abc',(err,stat) => {

    // 一般回调函数的第一个参数是错误对象，如果err为null,表示没有错误，否则表示报错了
    if(err) return;
    // if(stat.isFile()){
    //     console.log('文件');
    // }else if(stat.isDirectory()){
    //     console.log('目录');
    // }
    // console.log(stat);
    /*
    atime 文件访问时间
    ctime 文件的状态信息发生变化的时间（比如文件的权限）
    mtime 文件数据发生变化的时间
    birthtime 文件创建的时间
    */
    console.log(2);
});
console.log(3);

// 同步操作
// console.log(1);
// let ret = fs.statSync('./data.txt');
// console.log(ret);
// console.log(2);

## 读文件操作

const fs = require('fs');
const path = require('path');

let strpath = path.join(__dirname,'data.txt');
// fs.readFile(strpath,(err,data)=>{
//     if(err) return;
//     console.log(data.toString());
// });

// 如果有第二个参数并且是编码，那么回调函数获取到的数据就是字符串
// 如果没有第二个参数，那么得到的就是Buffer实例对象
// fs.readFile(strpath,'utf8',(err,data)=>{
//     if(err) return;
//     // console.log(data.toString());
//     console.log(data);
// });

// 同步操作
let ret = fs.readFileSync(strpath,'utf8');
console.log(ret);

## 写文件操作

const fs = require('fs');
const path = require('path');

let strpath = path.join(__dirname,'data.txt');
// fs.writeFile(strpath,'hello nihao','utf8',(err)=>{
//     if(!err){
//         console.log('文件写入成功');
//     }
// });

// let buf = Buffer.from('hi');
// fs.writeFile(strpath,buf,'utf8',(err)=>{
//     if(!err){
//         console.log('文件写入成功');
//     }
// });

// 同步操作
fs.writeFileSync(strpath,'tom and jerry');

## 大文件操作（流式操作）

/*

    大文件操作（流式操作）
    fs.createReadStream(path[, options])
    fs.createWriteStream(path[, options])
*/

const path = require('path');
const fs = require('fs');

let spath = path.join(__dirname,'../03-source','file.zip');
let dpath = path.join('C:\\Users\\www\\Desktop','file.zip');

// let readStream = fs.createReadStream(spath);
// let writeStream = fs.createWriteStream(dpath);

// 基于事件的处理方式
// $('input[type=button]').on('click',function(){
//     console.log('hello');
// });
// let num = 1;
// readStream.on('data',(chunk)=>{
//     num++;
//     writeStream.write(chunk);
// });

// readStream.on('end',()=>{
//     console.log('文件处理完成'+num);
// });
// -----------------------------------

// pipe的作用直接把输入流和输出流
// readStream.pipe(writeStream);

// ----------------------------------
fs.createReadStream(spath).pipe(fs.createWriteStream(dpath));

## 目录操作

/*

    目录操作
    1、创建目录
    fs.mkdir(path[, mode], callback)
    fs.mkdirSync(path[, mode])
    2、读取目录
    fs.readdir(path[, options], callback)
    fs.readdirSync(path[, options])
    3、删除目录
    fs.rmdir(path, callback)
    fs.rmdirSync(path)
*/

const path = require('path');
const fs = require('fs');
// 创建目录
// fs.mkdir(path.join(__dirname,'abc'),(err)=>{
//     console.log(err);
// });

// fs.mkdirSync(path.join(__dirname,'hello'));
// --------------------------------
// 读取目录
// fs.readdir(__dirname,(err,files)=>{
//     files.forEach((item,index)=>{
//         fs.stat(path.join(__dirname,item),(err,stat)=>{
//             if(stat.isFile()){
//                 console.log(item,'文件');
//             }else if(stat.isDirectory()){
//                 console.log(item,'目录');
//             }
//         });
//     });
// });

// let files = fs.readdirSync(__dirname);
// files.forEach((item,index)=>{
//     fs.stat(path.join(__dirname,item),(err,stat)=>{
//         if(stat.isFile()){
//             console.log(item,'文件');
//         }else if(stat.isDirectory()){
//             console.log(item,'目录');
//         }
//     });
// });
// ------------------------------
// 删除目录
// fs.rmdir(path.join(__dirname,'abc'),(err)=>{
//     console.log(err);
// });

fs.rmdirSync(path.join(__dirname,'qqq'));

## 文件操作案例（初始化目录结构）

/*

    文件操作案例（初始化目录结构）
*/
const path = require('path');
const fs = require('fs');

let root = 'C:\\Users\\ASUS\\Desktop';
let fileContent = `
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    <div>welcome to this</div>
</body>
</html>
`;

// 初始化数据
let initData = {
    projectName : 'mydemo',
    data : [{
        name : 'img',
        type : 'dir'
    },{
        name : 'css',
        type : 'dir'
    },{
        name : 'js',
        type : 'dir'
    },{
        name : 'index.html',
        type : 'file'
    }]
}

// 创建项目跟路径
fs.mkdir(path.join(root,initData.projectName),(err)=>{
    if(err) return;
    // 创建子目录和文件
    initData.data.forEach((item)=>{
        if(item.type == 'dir'){
            // 创建子目录
            fs.mkdirSync(path.join(root,initData.projectName,item.name));
        }else if(item.type == 'file'){
            // 创建文件并写入内容
            fs.writeFileSync(path.join(root,initData.projectName,item.name),fileContent);
        }
    });
});

## 全局安装

/*

    全局安装 -g：
    全局安装的包位于Node.js环境的node_modules目录下，全局安装的包一般用于命令行工具
    
    本地安装：
    本地安装的包在当前目录下的node_modules里面，本地安装的包一般用于实际的开发工作
    ------------------------------------------------------------
    npm常用的命令：
    1、安装包（如果没有指定版本号，那么安装最新版本）
    npm install -g 包名称 (全局安装)
    npm install 包名称 (本地安装)
    
    2、安装包的时候可以指定版本
    npm install -g 包名称@版本号
 i5ting_toc -f outline.md -o //markdown转换成浏览器的模式。
    3、卸载包
    npm uninstall -g 包名
    
    4、更新包（更新到最新版本）
    npm update -g 包名
    
    开发环境（平时开发使用的环境）
    生产环境（项目部署上线之后的服务器环境）
    --save 向生产环境添加依赖 dependencies
    --save-dev 向开发环境添加依赖 DevDependencies 

*/

## yarn工具基本使用


    安装yarn工具：npm install -g yarn

    1、初始化包
    npm init
    yarn init
    2、安装包
    npm install xxx --save
    yarn add xxx
    3、移除包
    npm uninstall xxx
    yarn remove xxx
    4、更新包
    npm update xxx
    yarn upgrade xxx
    5、安装开发依赖的包
    npm install xxx --save-dev
    yarn add xxx --dev
    6、全局安装
    npm install -g xxx
    yarn global add xxx
    7、设置下载镜像的地址
    npm config set registry url
    yarn config set registry url
    8、安装所有依赖
    npm install
    yarn install
    9、执行包
    npm run
    yarn run
*/