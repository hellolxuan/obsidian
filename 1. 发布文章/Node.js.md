---
title: Node.js
tags:
  - 技术
  - Node.js
author: Lxuan
toc: true
keywords: Node.js
categories: Node.js
date: 2022-1-15
abbrlink: 5063
thumbnail: Node.js/node.js.png
cover: Node.js/node.js.png
top:
---
......

<!--more-->

[TOC]

## 一、 初识 Node.js

### 1. 浏览器中JavaScript的组成部分

   <img src="Node.js/2.jpg" alt="" style="zoom: 67%;" />

   为什么JavaScript可以在浏览器中被执行？

   <img src="Node.js/1.jpg" style="zoom:80%;" />

   不同的浏览器使用不同的 JavaScript 解析引擎：

   Chrome浏览器=> V8

   Firefox浏览器=>OdinMonkey(奥丁猴)

   Safri 浏览器=>JSCore

   IE 浏览器=>Chakra(查克拉)

   etc.. 

   其中，Chrome浏览器的 V8 解析引擎性能最好！

### 2. Node.js简介

#### 2.1 什么是Node.js?

   Node.js® is a JavaScript runtime built on Chrome's V8 JavaScript engine.

   Node.js 是一个基于 ChromeV8 引擎的 JavaScript 运行环境。

   Node.js 的官网地址：https://nodejs.org/zh-cn/

#### 2.2 Node.js 中的 JavaScript 运行环境

   <img src="Node.js/3.png" alt="" style="zoom: 80%;" />

   浏览器 JavaScript 的前端运行环境。
   Node.js 是 JavaScript 的后端运行环境。

   Node.js 中无法调用DOM 和 BOM 等浏览器内置API。

#### 2.3 Node.js可以做什么

   Node.js 作为一个 JavaScript 的运行环境，仅仅提供了基础的功能和 API。然而，基于 Node.js 提供的这些基础能，很多强大的工具和框架如雨后春笋，层出不穷，所以学会了 Node.js，可以让前端程序员胜任更多的工作和岗位：

   ① 基于 Express 框架 (http://www.expressjs.com.cn/），可以快速构建 Web 应用
   ② 基于 Electron 框架 (https://electronjs.org/），可以构建跨平台的桌面应用
   ③ 基于 restify 框架（http://restify.com/），可以快速构建 API 接口项目
   ④ 读写和操作数据库、创建实用的命令行工具辅助前端开发、etc......

#### 2.4 Node.js好学吗？怎么学？

   浏览器中的 JavaScript 学习路径：

   JavaScript 基础语法＋浏览器内置API（DOM＋BOM）＋ 第三方库（jQuery、art-template等）

   Node.js 的学习路径：

   JavaScript基础语法 + Node.js 内置 API 模块（fs、path、http等） + 第三方 API 模块（express、mysqI等）

### 3. Node.js环境的安装

   如果希望通过 Node.js 来运行 Javascript 代码，则必须在计算机上安装 Node.js 环境才行。

   安装包可以从 Node.js 的官网首页直接下载，进入到 Node.js 的官网首页（https://nodejs.org/en/），点击绿色的按钮，下载所需的版本后，双击直接安装即可。

#### 3.1 区分LTS版本和Current版本的不同

   ① LTS 为长期稳定版，对于追求稳定性的企业级项目来说，推荐安装 LTS 版本的 Node.js。

   ② Current 为新特性尝鲜版，对热衷于尝试新特性的用户来说，推荐安装 Current 版本的 Node.js。但是，Current 版本中可能存在隐藏的 Bug 或安全性漏洞，因此不推荐在企业级项目中使用 Current 版本的 Node.js。

#### 3.2 查看已安装的Node.js的版本号

   在终端输入命令 node -v 后，按下回车键，即可查看已安装的 Nodejs 的版本打开终端，.

### 4. 在Node.js 环境中执行 JavaScript 代码

   打开终端，输入node 执行文件的路径

------

## 二、 fs文件系统模块

### 1. 什么是fs文件系统模块

   fs 模块是 Node.js 官方提供的、用来操作文件的模块。它提供了一系列的方法和属性，用来满足用户对文件的操作需求。
   例如:
   fs.readFile() 方法，用来读取指定文件中的内容
   fs.writeFile() 方法，用来向指定的文件中写入内容
   如果要在 JavaScript 代码中，使用 fs 模块来操作文件，则需要使用如下的方式先导入它：  

   ```javascript
   const fs = require('fs')
   ```

### 2. 读取指定文件中的内容

#### 2.1 fs.readFile() 的语法格式

   使用 fs.readFile0 方法，可以读取文件中的内容，语法格式如下：

   ```javascript
   fs.readFile(path[, options], callback)
   ```

   参数解读:
   参数1：必选参数，字符串，表示文件的路径。
   参数2：可选参数，表示以什么编码格式来读取文件。
   参数3：必选参数，文件读取完成后，通过回调函数拿到读取的结果。

#### 2.2 fs.readFile() 的示例代码

   以utf8的编码格式，读取指定文件的内容，并打印 err 和 dataStr 的值：

   ```javascript
   //1.导入fs模块，来操作文件
   const fs = require('fs')
   
   //2.调片fs.readFile()方法读取文件
   //  参数1：读取文件的存放路径
   //  参数2：读取文件时候采用的编码格式，一般默认指定utf8
   //  参数3：回调函数，拿到读取失败和成功的结果 err dataStr
   fs.readFile('./files/11.txt', 'utf8', function(err, dataStr) {
     //2.1 打印失败的结果
     console.log(err)
     console.log('------')
     //2.2 打印成功的结果
     console.log(dataStr)
   })
   ```

### 3. 向指定的文件中写入内容

#### 3.1 fs.writeFile()的语法格式

   ```javascript
   fs.writeFile(file, data[, options], callback)
   ```

   参数解读：
   参数1：必选参数，需要的字符串，表示文件的存放路径。
   参数2：必选参数，表示要写入的内容。
   参数3：可选参数，表示以什么格式写入文件内容，默认值是 utf8。
   参数4：必选参数，文件写入完成后的回调函数。

#### 3.2 fs.writeFile()的示例代码

   ```javascript
   //1.导入fs模块，来操作文件
   const fs = require('fs')
   
   //2.调用fs.writeFile()方法，写入文件的内容
   fs.writeFile('./files/2.txt', 'abcd', function(err){
     //2.1 如果文件写入成功，则 err 的值为 null  
     console.log(err)
   })
   ```

#### 3.3 判断文件是否写入成功

   ```javascript
   //1.导入fs模块，来操作文件
   const fs = require('fs')
   
   //2.调用fs.writeFile()方法，写入文件的内容
   fs.writeFile('./files/2.txt', 'abcd', function(err){
       if (err) {
           return console.log('文件写入失败！' + err.message)
       }
       console.log('文件写入成功！')
   })
   ```

### 4. 练习 - 考试成绩整理

   使用 fs 文件系统模块，将素材目录下成绩.txt文件中的考试数据，整理到成绩-ok.txt文件中。

   整理前，成绩.txt文件中的数据格式如下：

   ```
   小红=99 小白=100 小黄=70 小黑=66 小绿=88
   ```

   整理完成之后，希望得到的成绩-ok文件中的数据格式如下：

   ```
   小红：99
   小白：100
   小黄：70
   小黑：66
   小绿：88
   ```

   核心实现步骤：

   ① 导入需要的 fs 文件系统模块
   ② 使用 fs.readFile0 方法，读取素材目录下的 成绩.txt 文件
   ③ 判断文件是否读取失败
   ④ 文件读取成功后，处理成绩数据
   ⑤ 将处理完成的成绩数据，调用 fs.writeFile0 方法，写入到新文件 成绩-ok.txt 中

   ```javascript
   const fs = require('fs')
   
   fs.readFile('./成绩.txt', 'utf8', function(err, dataStr) {
       if (err) {
           return console.log('读取文件失败！' + err.message)
       }
       console.log('读取文件成功！' + dataStr)
   
       //先把成绩的数据，按照空格进行分割
       const arr1 = dataStr.split(' ')
       console.log(arr1)
           //循环分割后和数组，对每一项数据，进行字符串的替换操作
       const arr2 = []
       arr1.forEach(item => {
           arr2.push(item.replace('=', ':')) //push 查找 = 修改为 ：
       })
       console.log(arr2);
       //把新数组中的每一项，进行合并，得到一个新的字符串
       const newstr = arr2.join('\r\n')
       console.log(newstr);
   
       //调用fs.writeFile()方法，把处理完毕的成绩，写入到新文件中
       fs.writeFile('./成绩-ok.txt', newstr, function(err) {
           if (err) {
               return console.log('写入文件失败！' + err.message);
           }
           console.log('成绩写入成功！');
       })
   })
   ```

### 5. fs 模块 - 路径动态拼接的问题

   在使用 fs 模块操作件时，如果提供的操作路径是以 ./ 或 ../ 开头的相对路径时，很容易出现路径动态拼接错误的问题。
   原因：代码在运行的时候，<u>**会以执行 node 命令时所处的目录**</u>，<u>动态拼接出被操作文件的完整路径</u>。

   ```javascript
   //在执行2-9行程序时，如图2.3.1
   const fs = require('fs')
   
   fs.readFile('./files/1.txt', 'utf8', function(err, dataStr) {
       if (err) {
           return console.log('读取文件失败！' + err.message);
       }
       console.log('读取文件成功！' + dataStr);
   })
   
   //但是若修改 node 命令的执行目录，就会读取失败，如图2.3.2
   ```

   ![图2.3.1](Node.js/image-20220110054445144.png)

   ![图2.3.2](Node.js/image-20220110054855524.png)

   解决办法就是绝对路径，但是绝对路径与相对路径的斜线格式不同，为了能表示真正的“\”，需要修改为“\\”,如：

   ```javascript
   ...
   fs.readFile('C:\\Users\\12748\\Desktop\\vscode\\files\\1.txt', 'utf8', function(err, dataStr) {
   ...
   ```

   但是使用绝对路径不仅移植性非常差，且不利于维护，使用__dirname就可以完美解决，如：

   ```javascript
   const fs = require('fs')
   
   //__dirname 表示当前所处目录
   fs.readFile(__dirname + '\\files\\1.txt', 'utf8', function(err, dataStr) {
       if (err) {
           return console.log('读取文件失败！' + err.message);
       }
       console.log('读取文件成功！' + dataStr);
   })
   ```

------

## 三、 path 路径模块

### 1. 什么是 path 路径模块

   <u>**path 模块**</u>是 Node.js 官方提供的、用来<u>处理路径</u>的模共了一系列的方法和属性，用来满足用户对处理需求。如：

   path.join() 方法，<u>用来将多个路径拼接成一个完整的路径字符串</u>
   path.basename() 方法，用来从路径字符串中，将文件名解析出来

   如果要在 JavaScript 代码中，使 path 模块来处理路径，则需要使用如下方式先导入它：

   ```javascript
   const path = require('path')
   ```

### 2. 路径拼接

#### 2.1 path.join() 语法格式

   ```javascript
   path.join([...paths])
   ```

   参数解读：
   ...paths \<string> 路径片段的序列
   返回值：\<string>

#### 2.2 path.join() 的代码示例

   使用 path.join() 方法，可以把多个路径片段拼接为完整的路径字符串：

   ```javascript
   const pathStr = path.join('/a', '/b/c', '../', './d', 'e)
   consle.log(pathStr) // 输出 \a\b\d\e
   
   const pathStr2 = path.join(__dirname, './files/1.txt')
   console.log(pathStr2）// 输出 当前文件所处目录\files\1.txt
   ```

### 3. 获取路径中的文件名

#### 3.1 pal.basename() 的语法格式

   使用 path.basename(）方法，可以获取路径中的最后一部分，经常通过这个方法获取路径中的文件名，语法格式如下：

   ```javascript
   path.basename(path[, ext])
   ```

   参数解读：
   path \<string> 必选参数，表示一个路径的字符串
   ext \<string> 可选参数，表示文件扩展名
   返回: \<string> 表示路径中的最后一部分

#### 3.2 path.basename() 代码示例

   ```javascript
   const fpath ='/a/b/c/index.htTml' // 文件的存放路径
   
   var fullName = path.basename(fpath)
   console.log(fullName) // 输出 index.html
   
   var namewithoutExt = path.basename(fpath, '.html')
   console.log(namewithoutExt）// 输出 index，删除.html扩展名
   ```

### 4. 获取路径中的文件扩展名

#### 4.1 path.wxtname() 的语法格式

   ```javascript
   const path = require('path')
   
   const fpath = '/a/b/c/index.html' // 路径字符串
   
   const fext = path.extname(fpath)
   console.log(fext) // 输出 .html
   ```

### 5. 综合案例 - 时钟案例

#### 5.1 案例要实现的功能

   将素材目录下的 index.html 文件拆分成三个文件，分别是：index.css、index.js、index.html

#### 5.2 案例实现步骤

   ① 创建两个正则表达式，分别用来匹配 \<style> 和 \<script> 标签

   ② 使用 fs 模块，读取需要被处理的 HTML 文件

   ③ 自定义 resolveCSS 方法，来写入 index.css 样式文件

   ④ 自定义 resolveJS 方法，来写入 index.js 脚本文件

   ⑤ 自定义 resolveHTML方法，来写入 index.html 文件

#### 5.3.1 步骤一：导入需要的模块并创建正则表达式

   ```javascript 
   // 1.1 导入 fs 文件系统模块
   const fs=require('fs')
   // 1.2 导入path 路径处理模块
   const path= require('path')
   
   // 1.3 匹配 <style></style> 标签的正则
   //		 其中 \s 表示空白字符；\S 表示非空白字符；* 表示匹配任意次
   const regStyle = /<style>[\s\S]*<\/style>/
   // 1.4 匹配 <script></script> 标签的正则
   const regScript = /<script>[\s\S]*<\script>/
   ```

#### 5.3.2 步骤二：导入需要的模块并创建正则表达式

```javascript
// 2.1 读取需要被处理的 HTML 文件
fs.readFile(path.join(__dirname, '../素材/index.html'), 'utf8', function(err, dataStr) {
    // 2.2 读取 HTML 文件失败
    if (err)
        return console.log('读取 HTML 文件失败！' + err.message)
    resolveCSS(dataStr)
    resolveJS(dataStr)
    resolveHTML(dataStr)
})
```

#### 5.3.3 步骤三：自定义 resolveCSS 方法

```javascript
// 3.1 处理 css 样式
function resolveCSS(htmlStr) {
    // 3.2 使用正则提取页面中的 <style></style> 标签
    const r1 = regStyle.exec(htmlStr)
        // 3.3 将提取出来的样式字符串，进行字符串的 replace 替换操作
    const newCSS = r1[0].replace('<style>', '').replace('</style>', '')
        // 3.4 将提取出来的 css 样式，写入到 index.css 文件中
    fs.writeFile(path.join(__dirname, './clock/index.css'), newCSS, functon(err) {
        if (err) return console.log('写入 CSS 样式失败！' + err.message)
        console.log('写入 CSS 样式成功！')
    })
}
```

#### 5.3.4 步骤四：定义 resolveJS 方法

```javascript
// 4.1 处理 js 脚本
function resolveJS(htmlStr) {
    // 4.2 使用正则提取页面中的 <script></script> 标签
    const r2 = reScript.exec(htmlStr)
        // 4.3 将提取出来的脚本字符串，做进一步的处理
    const newJS = r2[0].replace('<script>', '').replace('</script>', '')
        // 4.4 将提取出来的 js 脚本，写入到 index.js 文件中
    fs.writeFile(path.join(__dirname, './clock/index.js'), newJS, function(err) {
        if (err) return console.log('写入 JavaScript 脚本失败！' + err.message)
        console.log('写入 JS 脚本成功！')
    })
}
```

#### 5.3.5 步骤五： 自定义 resolveHTML 方法

```javascript
// 5. 处理 html 文件
function resolveHTML(htmlStr) {
    // 5.1 使用字符串的 replace 方法，把内嵌的 <style> 和 </script> 标签，替换成外联的 <link> 和 <script> 标签
    const newHTML = htmlStr
        .replace(regStyle, '<link rel="stylesheet" href="./index.css"/>')
        .replace(regScript, '<script src="./index.js"></script>')
        // 5.2 将替换完成之后的 html 代码，写入到 index.html 文件中
    fs.writeFile(path.join(__dirname, './clock/index.html'), newHTML, function(err) {
        if (err) return console.log('写入 HTML 文件失败！' + err.message)
        console.log('写入 HTML 页面成功！')
    })
}
```

#### 5.4 案例中的两个注意点

① fs.writeFile() 方法只能用来创建文件，不能用来创建路径

② 重复调用 fs.writeFile() 写入同一个文件，新写入的内容会覆盖之前的旧内容

------

## 四、http 模块

### 1. 什么是 http 模块

在网络节点中，负责消费资源的电脑，叫做客户端；对外提供网络资源的电脑，叫做服务器。
http 模块是 Node.js 官方提供的、用来创建 web 服务器的模块。通过 http 模块提供的 http.createServer() 方法，就能方便的把一台普通的电脑，变成一台 Web 服务器，从而对外提供 Web 资源服务。

如果要希望使用 http 模块创建 Web 服务器，则需要先导入它：

```javascript
const http = require('http')
```

### 2. 进一步理解 http 模块的作用

服务器和普通电脑的区别在于，服务器上安装了 web 服务器软件，例如：IIS、Apache 等。通过安装这些服务器软件，就能把一台普通的电脑变成一台 web 服务器。

在 Node.js 中，我们不需要使用 IIS、Apache 等这些第三方 web 服务器软件。因为我们可以基于 Node.js 提供的
http 模块,通过几行简单的代码，就能轻松手写一个服务器软件，从而对外提供web 服务。

### 3. 服务器相关的概念

#### 3.1 IP 地址

IP 地址就是互联网上每台计算机的唯一地址，因此 IP 地址具有唯一性。如果把”个人电脑”比作“一台电话”，那么“IP地址”就相当于“电话号码”，只有在知道对方 IP 地址的前提下，才能与对应的电脑之间进行数据通信。

IP 地址的格式：通常用“点分十进制”表示成（a.b.c.d）的形式，其中，a,b,c,d 都是 0～255 之间的十进制整数。例如：用点分十进表示的 IP地址（192.168.1.1）

<u>127.0.0.1 代表本机 IP 地址</u>

#### 3.2 域名和域名服务器

尽管 IP 地址能够唯一地标记网络上的计算机，但IP地址是一长串数字，不了另一套一字符型的地址方案，即所谓的域名（Domain Name）地址。

IP地址和域名是对应的关系，这份对应关系存放在一种叫做域名服务器（DNS，Domain name server）的电脑中。使用者只需通过好记的域名访问对应的服务器即可，对应的转换工作由域名服务器实现。因此，域名服务器就是提供 IP 地址和域名之间的转换服务的服务器。

<u>127.0.0.1 对应的域名是 localhost</u>

#### 3.3 端口号

计算机中的端口号，就好像是现实生活中的门牌号一样。通过门牌号，外卖小哥可以在整栋大楼众多的房间中，准确把外卖送到你的手中。

同样的道理，在一台电脑中，可以运行成百上千个 web 服务。每个 web 服务都对应一个唯一的端口号。客户端发送过来的网络请求，通过端口号，可以被准确地交给对应的 web 服务进行处理。

① 每个端口号不能同时被多个 web 服务占用。

② 在实际应用中，URL 中的 80 端口可以被省略。

### 4 创建最基本的 web 服务器

#### 4.1 创建 web 服务器的基本步骤

① 导入http模块
② 创建 web 服务器实例
③ 为服务器实例绑定request 事件
④ 启动服务器

#### 4.2.1 步骤1导入 http模块

如果要希望使用 http 模块创建 Web 服务器，则需要先导入它：

```javascript
const http = require('http')
```

#### 4.2.2 步骤2创建web 服务器实例

调用 http.createServer() 方法，即可快速创建一个 web 服务器实例：

```javascript
const server = http.createServer()
```

#### 4.2.3 步骤3为服务器实例绑定 request 事件

为服务器实例绑定request 事件

```javascript
// 使用服务器实例的] .on(）方法，为服务器绑定一个 request 事件
server.on('request', function(req, res) {
  // 只要有客户端来请求我们自己的服务器，就会触发 request 事件，从而调用这个事件处理函数
  console.log('Someone visit our web server.')
})
```

#### 4.2.4 启动服务器

调用服务器实例的 .listen0 方法，即可启动当前的web 服务器实例:

```javascript
// 调用 server.listen(端口号，cb回调）方法,即可启动 web 服务器
server.listen(8050, function() {
    console.log('httpp server running at http://127.0.0.1:8050')
})
```

#### 4.3 req 请求对象

只要服务器接收到了了客户端的请求，就会调用通过 server.on() 为服务器绑定的 request 事件处理函数。如果想在事件处理函数中，访问客户端相关的数据或属性，可以使用如下的方式：

~~~javascript
server.on('request', (req) => {
// req 是请求对象，它包含了与客户端相关的数据和属性，例如：
// req.url 是客户端请求的 URL 地址
// req.method 是客户端的 method 请求类型
const str = `Your request url is ${req.url},and request method is ${req.method}
console.log(str)
})
~~~

