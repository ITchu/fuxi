#### 面试题  

1、浏览器兼容问题  不同浏览器，只了解加内核前缀

https://zhuanlan.zhihu.com/p/25123086?refer=dreawer

https://github.com/NoahZhang/Browser-Compatibility-Summary 

2、HTTP请求过程  请求原理

```html
	1、建立TCP连接
	2、web浏览器向web服务器发送请求命令
	3、web浏览器发送请求头信息
	4、web服务器响应
	5、web服务器发送请求头信息
	6、web服务器向浏览器发送数据
	7、web服务器关闭TCP连接
```

不同终端适配  响应式  不同终端尺寸、机型、分辨率

http://blog.csdn.net/azureternite/article/details/52528380

如何知道某个属性或js中的某个方式对某个版本的浏览起是否支持  

https://caniuse.com/

		1、兼容问题  不同浏览器，只了解加内核前缀 
		2、不同终端适配  响应式  不同终端尺寸、机型、分辨率
		3、上传图片怎么压缩
	    4、移动端网页放到移动端App
	    5、h5 企业会用到安卓、IOS
	    6、HTTP请求过程  请求原理
		7、画板怎么加及时通讯功能  你画我猜
		8、解决跨域问题的方法，怎么解决？
			答案：
				jsonp:对方服务器配合的情况下，符合js语法规范 符合自己做的项目：自己做的a项目和b项					 目不在一个域名下
				代理：爬虫的原理 自己做一个浏览器 无论PHP还是nodejs都可以做代理，用require获取到				   HTTP，用require来发起请求  作为客户端要知道有什么请求头 nodejs手册 HTTP 				  request option
				代理的面试：
					当你只用ajax的时候会遇到跨域的问题，你会有几种解决方式：
					1、jsonp方式
						使用起来比较简单，用script标签对，本身可以获取到外部地址的能力
						劣势：应用范围小，对方服务器返货的信息  用jsonp需要对方服务器的配合
					2、代理---本身可以获取到
						不管是fetch还是XML浏览器提供了数据的能力，没有提供跨域的能力，所需要借助其他额外的技术去实现代理，curl_setopt设置选项，通过nodejs和PHP后台进行获取						其他网站数据的能力，获取到了然后提供给前台
						优势：涉及范围比较广：通过代理能够获取你想要的内容
					
		vuex
		9、websocket即时通讯，多页面信息传递localstorage
	    10、闭包的优缺点？
		11、html+css+js  放在哪个组件  webview
		12、利用原生js 实现路由的

#### 笔试:

	1、判断下列表达式的正确性?(a)
		a、[] instanceof Array     
		b、Array instanceof(Function)
		c、[] instanceof Function
	2、下列表达式的返回值是多少?
		var A=function(b){this.b=b;};
		A.prototype.b=1;
		A.prototype.c=2;
		A.prototype.get=function(){return this.b;};
		var a=new A(3);
		(1). a.get();              3
		(2). a.b;                  3
		(3). a.c;                  2
		(4). delete a.b; a,b;      1
	3、下列表达式的返回值分别是什么？
		var o={e:1,f:function(){return this.e}};
		(1). o.f();                     1
		(2). var g=o.f;g();            undefined
		(3). o.f.call({e:2});            2
		(4). o.f.bind({e:3});           [Function: bound f]
		(5). o.f.bind({e:4}).call({e:5}); 4
	4、下面程序的结果
		function fun(n,o){
			console.log(o);
			return{
				fun:function(m){
					return fun(m,n);
				}
			}
		}
		var a=fun(0);a.fun(1);a.fun(2);a.fun(3);    undefined 0 0 0 
		var b=fun(0).fun(1).fun(2).fun(3);          undefined 0 1 2
		var c=fun(0).fun(1);c.fun(2);c.fun(3);        undefined 0 1 1
	5、下面程序的输出结果    Goodbyejack
		var name="World!";
			(function(){
				if(typeof name==='undefined'){
					var name='jack';
					console.log("Goodbye"+name);
				}
				else{
					console.log('Hello'+name);
				}
	
			})();


#### 简答题

1、说下行内元素和块级元素的区别?

	答案：行内元素：
			1.不能设置宽高；
			2.宽高由内容撑开；
			3.不独占一行；
			4.只能容纳文本或者其他行内元素
			5.函内元素中的高、行高及顶和底边距不可改变(顶和底边距就是：margin、padding上下边距设置无效)
		 块级元素：
		 	1.能设置宽高，
		 	2.宽度与浏览器宽度一样，与内容无关，
		 	3.独占一行，
		 	4.可以容纳内联元素和其他块元素
		 	5.块元素中高度、行高以及顶和底边距都可以控制(顶和底边距就是：margin、padding上下边距设置无效)
2、this对象的理解
	答案：全局环境：指向全局对象，在web浏览器中，也就是window对象
					eg:alert(this===window)  //true
	      函数调用：当做为普通函数被调用时，函数内部的this也会指向全局对象
	      			eg：var name = "window";
						function sayName(){
	    					var name = "fun";
	    					alert(this.name);
	                    }
	                    sayName();    // "window"
	      作为对象的方法调用：这里的this指向这个方法所在的对象
	      			eg：var  name="window";
	      				var obj={
	  						name:"obj",
	  						sayName:function(){
	  							alert(this.name)
							}
						}
						obj.sayName();    //"obj"
		 作为构造函数调用：this指向新创建的对象上
		 			eg：function Person(name){
		 					this.name=name,
		 					this.sayName=function(){
		 						alert(this.name)
		 						}
		 				}
		 				var person1=new Person("daoko");
		 				person1.sayName();   //"daoko"
		 				
		 	this总是指向函数的直接调用者(而非间接调用者)
		 	如果有new关键在字，this指向new出来的那个对象；
		 	在事件中，this指向触发这个事件的对象，特殊的是，IE中的attacchEvent中的this总是指向全局对象window
3、null和undefined的区别?

```html
null         表示"没有对象",即一个对象是"没有值"的值,也就是指为"空"，没有任何的属性和方法;
			 典型用法是:
					1.作文函数的参数，表示该函数的参数不是对象。
					2.作为对象原型链的终点。
undefined    表示"缺少值",即一个变量声明了没有初始化(赋值);
			 典型用法是：
				1.变量被声明了，但没有赋值时，就等于undefined
				2.调用函数时，应该提供的参数没有提供，改参数等于undefined
				3.对象没有赋值的属性，该属性的值为undefined
				4.函数没有返回值时，默认返回undefined、
undefined不是一个有效的JSON，而null是
undefined的类型(typeof)是undefined
null的类型(typeof)是object
注意：在验证null时一定要使用===，因为无法分辨null和undefined
	  null==undefined  //true
	  null===undefined //false
```

5、谈谈rem它的作用，以及如何使用

```h
作用：根据终端的屏幕分辨率动态计算元素的大小
应用 ： 多端布局，响应式布局
```

6、如何编写高性能的JavaScript?
7、请说出三种减低页面加载时间的方法

```html
	1.尽量减少页面中重复的HTTP请求数量
	2.服务器开启gzip压缩
	3.css样式的定义放置在文件头部
	4.JavaScript脚本放在文件末尾
	5.压缩合并JavaScript、css代码
	6.使用多域名负载网页内的多个文件、图片
	7.标明高度和宽度
	8.优化图片文件，减小其尺寸，特别是缩略图
	9.图片格式的选择(GIF:提供的颜色较少，可用在一些对的颜色要求不高的地方)
```

8、你能解释一下JavaScript中的继承是如何工作的吗?
9、介绍js有哪些内置对象?

```html
Object是JavaScript中所有对象的父对象
数据封装类对象：Object、Array、Boolean、Number和string
其他对象：Function、Arguments、Math、Date、RegExp、Error
```


10、eval是做什么的?

```html
它的功能是把对应的字符串解析成js代码并运行
应该避免使用eval，不安全，非常耗性能(2次，一次解析成js语句，一次执行)
由JSON字符串转换成JSON对象的时候可以用eval
	eg:var obj=eval('('+str+')')
```


11、什么是window对象?什么是document对象?

```html
window对象是指浏览器打开的窗口
document对象是Documentd对象(HTML 文档对象)的一个只读引用，windowd对象的一个属性
	可以访问页面中所有的元素
```



12、什么是闭包，为什么要用它?

```html
闭包是指由权访问另一个函数作用域中变量的函数
	创建闭包的最常见的方式就是在一个函数内创建另一个函数，通过另一个函数访问这个函数的局部变量，利用闭包可以突破作用域链，将函数内部的变量和方法传递到外部。
闭包的特性：
	1、函数内再嵌套函数
	2、函数内部可以引用外层的参数和变量
	3、参数和变量不会被垃圾回收机制回收
```



13、如何解决跨域问题?

```html
		1、jsonp:对方服务器配合的情况下，符合js语法规范 符合自己做的项目：自己做的a项目和b项					 目不在一个域名下
		2、代理：爬虫的原理 自己做一个浏览器 无论PHP还是nodejs都可以做代理，用require获取到				   HTTP，用require来发起请求  作为客户端要知道有什么请求头 nodejs手册 HTTP 				  request option
			代理的面试：
				当你只用ajax的时候会遇到跨域的问题，你会有几种解决方式：
				1、jsonp方式
					使用起来比较简单，用script标签对，本身可以获取到外部地址的能力
					劣势：应用范围小，对方服务器返货的信息  用jsonp需要对方服务器的配合
				2、代理---本身可以获取到
					不管是fetch还是XML浏览器提供了数据的能力，没有提供跨域的能力，所需要借助其					 他额外的技术去实现代理，curl_setopt设置选项，通过nodejs和PHP后台进行获取						其他网站数据的能力，获取到了然后提供给前台
					优势：涉及范围比较广：通过代理能够获取你想要的内容
```

14、介绍下你最常用的的一款框架?
15、es6的新特性考察，优化了哪些es5中的API?(https://www.cnblogs.com/QxkWeb/p/6912052.html)

```html
新添加的API：
	Array增加了of(..)和from(..)之类的静态函数，以及copyWithin(..)和fill(..)之类的原型函数。
	Object增加了is(..)和assign(..)之类的静态函数。
	Math增加了acosh(..)和clz32(..)之类的静态函数。
   	Number增加了Number.EPSILON之类的静态属性，以及Number.isFinite(..)之类的静态函数。
	String增加了String.fromCodePoint(..)和String.raw(..)之类的静态函数，以及repeat(..)和includes(..)之类的原型函数。

```


16、react的diff算法基本原理与源码解释

```html
web页面是由DOM元素组成，一个web页面的DOM元素组成的结构可以看成一棵  “树”  ##二叉树##  所以web页面就是一棵DOM树结构。

diff  差异比较（different）

react应用的是virtual DOM ， 即虚拟DOM，当页面发生刷新时，就要比较DOM树中哪个节点发生了变化，常规的比较两棵树就是从树的根部开始每个节点，逐级往下进行比较

react diff    对同级同父节点的节点进行比较，更新时，直接删除要更新的节点，包括它的子节点，其他地方用到更新节点时，则是重新创建节点，而不是复用先前的节点，（先前的节点已被销毁）

```



17、什么是函数式编程?JavaScript中如何使用函数式编程?

```
函数式编程：简单的说就是将特定功能的代码打包成函数，使得代码变得简洁，提高代码的可复用性。
```

18、virtual-dom的基本原理及实现(https://www.cnblogs.com/wubaiqing/p/6726429.html)

```html
基本原理：
	用 JavaScript 对象结构表示 DOM 树的结构；然后用这个树构建一个真正的 DOM 树，插到文
档当中当状态变更时，重新构造一棵新的对象树。然后用新的树和旧的树进行比较两个数的差异。
然后把差异更新到久的树上，整个视图就更新了。Virtual DOM 本质就是在 JS 和 DOM 之间做
了一个缓存。既然已经知道 DOM 慢，就在 JS 和 DOM 之间加个缓存。JS 先操作 Virtual DOM
对比排序/变更，最后再把整个变更写入真实 DOM。

```


19、为什么利用多个域名来提供网站资源会更有效

```html
1、CDN缓存更方便
2、突破浏览器并发限制
3、节约cookie带宽
4、节约主域名的链接数，优化界面响应速度
5、防止不必要的安全问题
```


20、promise、generator、async/await的原理解释
21、你有哪些性能优化的方法?

```html
	1、减少HTTP请求次数：css sprites js css源代码压缩、图片大小控制合适；网页gzip，CDN托管，data缓存，图片服务器
	2、前端模块 js+数据，减少由于HTML标签导致的宽带浪费，前端用变量保存ajax请求结果，每次操作本地变量，不用请求，减少请求次数
	3、用innerHTML代替DOM操作，减少DOM操作次数，优化JavaScript性能
	4、当需要设置的样式很多时设置className而不是直接操作style
	5、少用全局变量、缓存DOM节点查找的结果。减少IO读取操作。
	6、避免使用CSS Expression(CSS表达式)又称Dynamic properties(动态属性)
	7、图片预加载，将样式表放在顶部，将脚本放在底部 加上时间戳
	8、避免在页面的主体布局中使用table，table要等其中的内容完全下载之后才会显示出来，显示比div+css布局慢
		对普通网站有一个统一的思路，就是尽量向前端优化、减少数据库的操作、较少磁盘IO。向前端优化指的是，在不影响功能和体验的情况下，能在浏览器执行的不要在服务端执行，能在缓存服务器上直接发挥的不要到应用服务器，程序能直接获取的结果不要到外部去获得，本机内能取得的数据不要到远程取，内存能取到的不要到磁盘取，缓存中有的不要到数据库查询，减少数据库操作，减少更新次数、缓存结果，减少查询次数、将数据库执行的操作尽可能的让你的程序完成(例如join查询)，减少磁盘IO指尽享不要使用文件缓存、减少读写文件次数等。程序优化永远要优化慢的部分，换语言是无法“优化”的


一）内容层面
1、DNS解析优化（DNS缓存、减少DNS查找、keep-alive、适当的主机域名）
  2、避免重定向（/还是需要的）
  3、切分到多个域名
  4、杜绝404

二）网络传输阶段
1、减少传输过程中实体的大小
    1）缓存
    2）cookie优化
    3）文件压缩（Accept-Encoding：g-zip）

2、减少请求的次数
    1）文件适当的合并
    2）雪碧图

3、异步加载（并发,requirejs）
4、预加载、延后加载、按需加载

三）渲染阶段
1、js放底部，css放顶部
2、减少重绘和回流
       3、合理使用Viewport 等meta头部
       4、减少dom节点
      5、BigPipe

四）脚本执行阶段
1、缓存节点，尽量减少节点的查找
2、减少节点的操作（innerHTML）
3、避免无谓的循环，break、continue、return的适当使用
4、事件委托
```



22、列举你所知道的网站前端性能优化的技术手段？

23、列举js实现继承的方式？

http://blog.csdn.net/devincob/article/details/70670224

24、在前端代码开发之前首先要考虑和处理的事情？

25、请用jQuery写出checkbox的全选,反选功能

```html
jQuery
	<script src="jquery-3.2.1.js"></script>
     <script type="text/javascript">
         $(function(){
             var $choose = $("#choose input");
             //全选
             $("#all").click(function(){
                 $choose.each(function(){
                     $(this).prop("checked",true);
                 });
             });
             //全不选
             $("#not").click(function(){
                 $choose.prop("checked",false);
             });
             //反选
             $("#reverse").click(function(){
                 $choose.each(function(){
                     $(this).prop("checked",!$(this).prop("checked"));
                 });
             });
         });
     </script>
HTML
	<div id="box-function">
         <input id="all" type="button" value="全选" />
         <input id="not" type="button" value="全不选" />
         <input id="reverse" type="button" value="反选" />
     </div>
 
     <div id="choose">
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
         <input type="checkbox" />
     </div>

```



#### 浏览器方向

1、对GPU渲染动画的理解
2、浏览器缓存种类,区别与使用细节(http://blog.csdn.net/u011001084/article/details/53005615)
3、浏览器有哪些常驻线程?它们的运行机制是怎么的？哪些线程之间是互
4、线程与进程的区别



#### HTML+css

1、svg动画与canvas动画的适场景(优劣势)

https://www.zhihu.com/question/19690014
2、如何实现一个搜索高亮的文件树，从DOM树中找出子孙节点?
3、css清除float浮动的方式？

http://blog.csdn.net/promisecao/article/details/52771856
4、css选择器有哪些？css哪些属性可以继承？

```html
选择器：id选择器、类选择器、标签选择器、相邻选择器、子选择器、后代选择器、通用选择器、属性选择器、伪类选择器、伪元素选择器
可继承属性：font-size、font-family、color
```


5、谈谈表单的get和post提交方式的区别？

​		post传递数据量较大，较安全，用request.form("")取值

​		get传递数据量较小，没有post安全性强，用request.querystring("")取值
6、什么是响应式布局？如何实现web和手机的响应式？

```html
响应式布局：针对不同的屏幕显示不同的网页布局

```



7、display有哪些值?说明他们的作用

```html
	block           此元素将显示为块级元素。默认宽度为父元素宽度,可设置宽高，换行显示
	none            此元素不会被显示
	inline          此元素将显示为行内元素。默认宽度为内容宽度,不可设置宽高，同行显示
	inline-block    此元素将显示为行内块级元素。默认宽度为内容宽度,可设置宽高，同行显示
	list-item       此元素会作为列表显示
	table           此元素会作为块级表格来显示，表格前后带有换行
	inherit         规定应该从父元素继承display属性的值
```

8、解释css3的flex布局以及适用场景?

```html
该布局模型的目的是提供一种更加高效的方式来对容器中的条目进行布局，对齐和分配空间。在传统的布局方式中，block布局是把块在垂直方向从上到下依次排列；而inline布局则是在水平方向来排列。弹性布局并没有这样的限制，可以由开发人员自由操作。
适用场景：适合移动端开发，在Android和iOS上也完美支持
```

9、CSS的position分别有哪几种,有什么作用?

```html
absolute:生成绝对定位元素,相对于static定位以外的第一个父元素进行定位
relative：生成相对定位的元素,相对于其正常位置进行定位
fixed：生成绝对定位的元素,相对于浏览器窗口进行定位
static:默认值,没有定位,元素出现在正常的流中
inherit:规定应该从父元素继承position属性的值
```

10、px和em的区别

https://www.cnblogs.com/langee/p/6890362.html

11、请解释下面代码的作用

```html
<meta name=viewport content="width=device-width,initial-scale=1,minimum-scale=1.0,maximum-scale=1.0">
```

| 属性名           | 取值                  | 描述                               |
| ------------- | ------------------- | -------------------------------- |
| width         | 正整数或  device-width  | 定义视口的宽度,单位为像素                    |
| height        | 正整数或  device-height | 定义视口的高度,单位为像素,一般不用               |
| initial-scale | [0.0-10.0]          | 定义初始缩放值                          |
| minimun-scale | [0.0-10.0]          | 定义缩小最小比例,它必须小于或等于maximum-scale设置 |
| maximun-scale | [0.0-10.0]          | 定义放大最大比例,它必须大于或等于minimum-scale设置 |
| user-scalable | yes/no              | 定义是否允许用户手动缩放页面,默认值是yes           |

### 函数式编程和面向对象式编程

##### 函数式编程：

```html
什么是函数式编程？

		它是一种‘编程范式’(根据编程语言的特点对编程语言进行分类),也就是如何编写程序的方法论

		它属于‘结构化编程’的一种,主要思想是把运算过程尽量写成一系列嵌套的函数调用

特点(5个鲜明特点)		

	1. 第一等公民：和其他数据类型一样(赋值,参数,作为返回值)
	2. 只用表达式,不用语句：表达式就是单纯的运算，总有返回值，语句就是执行某一操作,没有返回值
	3. 没有副作用：函数的内部和外部没有互动(修改全局变量)
	4. 不修改状态：变量往往用来保存状态，不修改变量意味着状态不能保存在变量中,函数式编程使用参数 保存状态
	5. 引用透明：函数运行不依赖外部的变量，只依赖输入的参数

意义：

   1. 代码简洁，开发快速
   2. 接近自然语言，便于理解
   3. 更方便管理
   4. 易于并发编程

```

##### 对象式编程

```html
什么是对象式编程？

	面向对象程序设计是种具有对象概念的程序编程范型,同时也是一种程序开发的方法，它可能包含数据、属性、代码与方法

对象是什么？
	对象则指的是类的实例，在对象中包括了属性和方法,在对象式编程中将对象作为程序的最基本单元,将程序和数据封装在其中,每个对象都能够接受数据,对数据进行处理并将数据传递给其他对象

创建对象new原理(构造函数、类)步骤
	创建一个空对象，最为将要返回的对象的实例
	将这个空对象的原型,指向构造函数的prototype属性
	将这个空对象赋值给函数内部的this关键字
	开始执行构造函数内的代码

```







