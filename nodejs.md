# nodejs

##### Markdown：https://hinesboy.github.io/mavonEditor/dist/

百度编辑器：http://ueditor.baidu.com/website/onlinedemo.html

解析Markdown语法的包：npm    markdown-it



JavaScript(文件) ---->  运行在客户端(dom---->html css)

php  wamp apache运行

nodejs  安装到自己的系统     编译的环境

HTTP协议  静态Apache服务器   响应头的类型  content-type (HTML、css、js. png jpeg gif mp3 mp4 下载)  状态:200 请求成功  404 找不到  304  503 302重定向

cookie  HTTP无状态协议  只负责传输请求  

cookie 服务器给客户端有cookie  带过去

cache-content  缓存策略 

last-modified  缓存的时间

if-modified-since  比较要访问的文件当前的修改时间和上次修改文件的时间作比较

content-Encoding  编码格式  gzip  可以加快网络传输的效率

字符集的格式:charset=utf-8

处理静态的服务器

浏览器：两个模块：解析HTML+CSS（ -webkit- | -moz- | -o- ）、 解析js（V8引擎）



## 模块 

​	模块： 完整的功能集合

​			高内聚  低耦合

​			编程思想

##### import xxx from "xxx"

​	没有任何环境能够识别 import
​	采用babel去识别

（后台）nodejs  运行在服务器   访问本机文件  访问速度取决于服务器硬件

后台操作内容的时候，操作本机内容

cmd:common module defined（正常的模块加载方式）

（前台）

前台所有的文件都来自于远程，读取速度，时间都不确定

amd	async   module  defined（异步模块加载方式）

##### html中发送http请求的地方

​	script img form ajax link
​	 script标签对中加入属性async="true"实行异步

require.js

```html
引入 :<script data-main="3.js" src="node_modules/requirejs/require.js"></script>
js间依赖： define(["1.js", "2.js", "3.js"], function(a,b,c){
				console.log(a, b, c);
			});
```



差别：访问的差别

前台使用异步机制：需要耗时或者不确定执行时间的， 正常线程中的操作执行完后才会执行异步的操作

单线程异步机制：同一时间只能执行一条指令



### cmd

全局变量global

顶层对象 module    module.exports



核心模块   自定义模块    第三方模块    （模块：包）

​		require引入 不需要加路径

核心模块：nodejs自带的模块

第三方模块：第三方写好的模块，使用前需要先安装npm包

​			 爬虫 request包 命令：npm install request

​			引入require("request")不需要加路径

自定义模块：自定义的模块，引用时需要按路径的方式写

require()访问规则：1. 不带路径

​					a. 先访问核心模块，

​					b. 其次当前目录下的node_modules，

​					c. 访问上一级目录下的node_modules,若还是没有找到继续向上一级访问node_modules,直到根目录(磁盘根目录)

​					d. not found module

    2.  带路径

        a. 按照指定路径去找相应文件，（相对路径）

        b. 按照指定的路径去找相应文件，（绝对路径）

				3. 后缀名

       				1. 带后缀名   按照指定的后缀名查找
       				2. 不带后缀名   首相会查找后缀名是js的文件，其次后缀名是.json（内容必须符合json要求） ， 再是.node(c++代码)



path: 

​	当前目录： __dirname

​	当前文件（目录）：__filename

### require 与 npm install

require : 就近原则

npm install : 就远原则  上层目录中没有node_module文件会引入到当前文件夹

## npm

npm adduser

npm login

npm init   初始化说明文件（package.json）

上传自定义模块   24小时后不可删除

npm publish  推送包到npm

npm unpublish   包名@版本   [--force]  强制执行  删除    

install    （简写 i）下载安装     xxxx@version   --save    (加上--save会在项目package.json中添加上依赖dependencies)

（生产依赖 / 开发依赖 --save-dev  (--D) ）

生产依赖dependencies， 开发依赖devDependencies

npm uninstall 包名   卸载包

npm install    包名     安装包

命令台命令：npm install 包名 --save  生产依赖  简写：npm i 包名 -S

​			npm install 包名  --save-dev  开发依赖    npm i 包名 

```html
npm install xxx@version
npm uninstall 
npm config set/get registry http:
npm adduser
npm login
npm publish
npm unpublish 包名@version
```

## require()

模块：    module需要返回，module.exports

require()返回（模块）对象





知道一个东西比懂得一个东西更难得      需要机会

知道了一个东西要懂得它是艰难的

### http（tcp/ip）

HTTP协议网址：tool.oschina.net/commons/

接收    相应   web服务器

PHP   wamp  window    Apache   MySQL   PHP

华硕  主板

网址接收步骤

接收：CPU接收键盘指令调度内存   -----存储---->CPU(高速缓存) -------> 显卡-------->屏幕 

​	CPU--------->地址------>网卡-------->交换机--------->路由-------->dns--------->地址---->dns------>机器

硬盘(固态硬盘) (通过键盘协议 )

响应： 网卡---------->CPU-------->node.js-------->找相应的资源---------->(请求端的地址)网卡

构造服务器  Apache  HTTP  nodejs  客户端



HTTP  无状态的协议  不会保存状态 session  cookie 只能由客户端发起

content-type:返回数据的类型和编码

如何建立连接，如何断开连接

三次握手   

​	1、客户端------->服务器

​	2、客户端发送请求完成

​	3、服务器接收请求完成

 四次挥手   确定双方断开



request    =   new IncommingMessage()    // request 是IncommingMessage 的实例;

request.url   是浏览器请求的的信息，即地址栏中的内容，URL规则可自定义



路径：    windows本地资源路径   c:\a\b\c,    linux    c:/a/b/c

​		url   http的路径		/a/b/c

req.setHeader(name, value);

req.writeHeader(resCode, []);



头信息content-type：

​	属性：cache-cortol  值：private  只有第一次访问的时候访问服务器，之后缓存

​						no-cache  每一次都会请求服务器

​						max-age  秒计时(多少秒之内使用缓存)

​	X-UA-Compatible：IE=edge,chrome=1 HTML设置头信息

```html
强制用IE的高版本解析，可以解决兼容性问题
<meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1">
```

/* private | no-catch | max-age=num ; last-modified为true时无效*/

#### 模板引擎

一种将数据和逻辑代码与视图模板分离，动态将数据与模板组合输出的思想。



PHP smarty模板引擎

vue  {{}}模板引擎

html  ejs模板引擎、jade模板引擎

### 缓存控制

Catch-Control：

​	private    只有第一次访问的时候访问服务器，之后直接访问访问缓存

​	no-catch    每一次都会请求服务

​	max-age=10    秒计时

last-modified   (与catch-control不能共存，同时存在时，last-modified有效)

#### 创建系统级别的命令

​	1、在当前目录下创建package.json

​	2、在package.json文件里面添加配置项“bin”:{命令：“执行文件”}

​	3、要执行的文件头部，指定解析的模块

​		#!/usr/bin/env node

​	4、把当前的这个功能打包上传

​		npm login

​		npm publish

​	5、将对应的包全局安装 

​		npm install 包名 -g

​	6、可以全局使用，能全局使用的命令就是你在bin里设置的命令

​	7、可以忽略4、5步，不用打包上传，直接全局使用

​		npm link 创建快捷方式

### Express

| 动态服务器

***vue 控制器 通过js对象实现（Vue对象）



数据与视图分离----让工作更有条理，前后端分离

控制器，将相应的数据与相应的视图绑定

========MVC

中间件  接受请求和响应请求中间的过程

#### form

```
form.action="/destinct/<%=data.id%>"    //提交
router.get('/destinct/:id', function(req, res){    //接收
  var id = req.params.id;
})
```

#### process

- cwd()    返回进程的根目录

#### Buffer

- buffer 存储在内存之外（操作系统限制各类软件占用大量内存）

# Light

```
var reg = /^\/list\/([^\/])+\/?$/;
```

```
**字符串查找  拆分  分析
原子： \w  任意一个字母、数字、下划线
	  \W  除了字母数字下划线
	  \d  匹配任意一个数字
	  \D  除了数字
	  \s  匹配任意一个空白
	  \S  除了空白
	  
	  [^]  ^非
	  ^  开头
	  $  结尾
	  \b  边界判断 多在英文单词中使用
	  
原子组：[]
元字符：具有特殊意义的字符 []  () ^ $ . (点匹配除了回车外的任意字符) {}
转译符：\
模式修饰符：i    不区分大小写字母的匹配
		   m    将字符串视为多行，修饰^或$
		   g    全局匹配，找到所以匹配项
量词（贪婪）：{数字} {至少，之多}  
	  *  0  多
	  +  1  多
	  ?  0  1   使贪婪特性变为吝啬
	  
()  能够保存匹配到的内容

str.replace(reg,'')；
str.replace(reg,function(a,b));   a:匹配所有    b:匹配括号里的
str.match(reg)   返回匹配到的结果（数组）
str.split(reg)
	  
eval('')  将原生字符串转换为JavaScript代码
取消反向引用： ?:
```

svn

#### touch 文件名  添加文件

echo 内容 > 文件名  添加文件及内容

mkdir  根目录  添加

rm  目录名  删除目录名

rm -prf  目录名   强制删除目录


###webpack
   全局安装  npm install --global webpack
   文档  https://doc.webpack-china.org/concepts/
   ```html
        import  接受的变量  from  地址
        引入文件 import aa,{aa,bb} from "文件地址"
        
        访问文件   默认返回(只有一个默认) export default bb;
                  其他返回值  export { 
                                aa,bb....
                               }
        接收到之后   aa 默认返回值  可与返回的变量名不同
                   {aa,bb}  其他返回值 必须与返回的变量名相同 
                   
   