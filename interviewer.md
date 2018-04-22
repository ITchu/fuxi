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

10、px、em、rem、vh、vw的区别

https://blog.csdn.net/jyy_12/article/details/42557241

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





## 选择题

1. #### Javascript中制作图片代替按钮的提交效果需要手动提交方法submit()，以下调用正确的是:

   document.myform.submit()

2. #### 以下语句中，没有创建出字符串对象的是（A ）

   A)String str; B) String str = "hello"; 

   C) String str = new String( );  D) new String("hello"); 

3. #### 有关会话跟踪技术描述正确的是(多选) (ABC)

   A. Cookie是Web服务器发送给客户端的一小段信息，客户端请求时，可以读取该信

息发送到服务器端

 	B. 关闭浏览器意味着会话ID丢失，但所有与原会话关联的会话数据仍保留在服务器

上，直至会话过期

​	C. 在禁用Cookie时可以使用URL重写技术跟踪会话

​	D.  隐藏表单域将字段添加到HTML表单并在客户端浏览器中显示

##### 解析   会话跟踪常用的4种方法:

```html
1.URL重写:就是在URL结尾添加一个附加数据以标识该会话,把会话ID通过URL的信息传递过去,以便在服务器端进行识别不同的用户。
2.隐藏表单域:将会话ID添加到HTML表单元素中提交到服务器,此表单不在客户端显示。
3.cookie:cookie是web服务器发送给客户端的一小段信息,客户端请求时可以读取该信息发送到服务器端,进而进行用户的识别。对于客户端的每次请求,服务器都会将cookie发送到客户端,在客户端可以进行保存,以便下次使用。
4.session:在服务器端会创建一个session对象,产生下一个sessionID来标识这个session对象,然后将这个sessionID放在cookie中发送到客户端,下一次访问时,sessionID会发送到服务器,在服务器端进行识别不同的用户,session是依赖cookie的,如果cookie被禁用,那么session也将失效
```

#### 4.下列选项中不属于CSS文本属性的是(A)

A. font-size      B. text-transform  C. text-align     D. line-height

##### 解析  文本属性:

​	

| 属性              | 描述             |
| --------------- | -------------- |
| color           | 设置文本颜色         |
| direction       | 设置文本方向         |
| line-height     | 设置行高           |
| letter-spacing  | 设置字符间距         |
| text-align      | 对齐元素的文本        |
| text-decoration | 向文本添加修饰        |
| text-indent     | 缩进文本元素中的文版本的首行 |
| text-shadow     | 设置文本阴影         |
| text-transform  | 控制元素中的字母       |
| unicode-bidi    | 设置文本方向         |
| white-space     | 设置元素中的空白处理方式   |
| word-spacing    | 设置字间距          |

####  5.点击页面的按钮,使之打开一个新的窗口,加载一个网页,以下JavaScript代码中可执行的是(A)

```html
A. <input type="button" value="new" onclick="open('new.html','_blank')"/>
B.  <input type="button" value="new" onclick="window.location='new.html';"/>
C.  <input type="button" value="new" onclick="location.assign('new.html')"/>
D.  <form target="_blank" action="new.html"><input type="submit" value="new"/></form>
```

##### 解析    

​	A: window.open('弹出窗口的文件名','_blank弹出新的独立窗口') 弹出新窗口的命令   

​	B:在本窗口打开

​	C:没有任何在新窗口打开的语句

​	D:不是用JavaScript而是通过表单提交的方式,一般用于动态网页

#### 6.不能用来修饰interface的有(ACD)

A.  private    B.  public    C.  protected    D.static

##### 解析 interface只能用public修饰

#### 7.HTML5测试

```html
1.HTML5 之前的 HTML 版本是？
A.HTML 4.01
B.HTML 4
C.HTML 4.1
D.HTML 4.9
正确答案：A.HTML 4.01

2.HTML5 的正确 doctype 是？
A.<!DOCTYPE html>
B.<!DOCTYPE HTML5>
C.<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 5.0//EN" "http://www.w3.org/TR/html5/strict.dtd">

正确答案：A.<!DOCTYPE html>

3.在 HTML5 中，哪个元素用于组合标题元素？
A.<group>
B.<header>
C.<headings>
D.<hgroup>
正确答案：D.<hgroup>

4.HTML5 中不再支持下面哪个元素？
A.<q>			标签定义短的引用
B.<ins>			标签定义已经被插入文档中的文本
C.<menu>		标签定义命令的列表或菜单
D.<font>
正确答案：D.<font>

5.HTML5 中不再支持下面哪个元素？
A.<cite>		
B.<acronym>		定义首字母大写
C.<abbr>
D.<base>
正确答案：B.<acronym>

6.在 HTML5 中，onblur 和 onfocus 是：
A.HTML 元素
B.样式属性
C.事件属性
正确答案：C.事件属性

7.用于播放 HTML5 视频文件的正确 HTML5 元素是：
A.<movie>
B.<media>
C.<video>
正确答案：C.<video>

8.用于播放 HTML5 音频文件的正确 HTML5 元素是：
A.<mp3>
B.<audio>
C.<sound>
正确答案：B.<audio>

9.在 HTML5 中不再支持 <script> 元素的哪个属性？
A.rel
B.href
C.type
D.src

正确答案：C.type

10.在 HTML5 中，哪个方法用于获得用户的当前位置？
A.getPosition()
B.getCurrentPosition()
C.getUserPosition()
正确答案：B.getCurrentPosition()

11.新的 HTML5 全局属性，"contenteditable" 用于：
A.规定元素的上下文菜单。该菜单会在用户点击右键点击元素时出现。
B.规定元素内容是否是可编辑的。
C.从服务器升级内容。
D.返回内容在字符串中首次出现的位置。
正确答案：B.规定元素内容是否是可编辑的。

12.在 HTML5 中，contextmenu 和 spellcheck 是：
A.HTML 属性
B.HTML 元素
C.事件属性
D.样式属性
正确答案：A.HTML 属性

13.在 HTML5 中，您能够直接将 SVG 元素嵌入 HTML 页面中。
正确答案：正确

14.由 SVG 定义的图形是什么格式的？
正确答案：XML

15.HTML5 中的 <canvas> 元素用于：
正确答案：绘制图形

16.哪个 HTML5 内建对象用于在画布上绘制？
A.getContent
B.getContext
C.getGraphics
D.getCanvas
正确答案：B.getContext

17.在 HTML5 中，哪个属性用于规定输入字段是必填的？
A.required
B.formvalidate
C.validate
D.placeholder
正确答案：A.required

18.哪种输入类型定义滑块控件？
A.search
B.controls
C.slider
D.range
正确答案：D.range

19.哪种输入类型用于定义周和年控件（无时区）？
A.date
B.week
C.year
正确答案：B.week

20.哪个 HTML5 元素用于显示已知范围内的标量测量？
A.<gauge>
B.<range>
C.<measure>
D.<meter>
正确答案：D.<meter>
```

  #### 8.HTML测试

```html
1.HTML 指的是？
正确答案：超文本标记语言（Hyper Text Markup Language）

2.Web 标准的制定者是？
正确答案：万维网联盟（W3C）

3.在下列的 HTML 中，哪个是最大的标题？
正确答案：<h1>

4.在下列的 HTML 中，哪个可以插入折行？
正确答案：<br>

5.在下列的 HTML 中，哪个可以添加背景颜色？
正确答案：<body bgcolor="yellow">

6.请选择产生粗体字的 HTML 标签：
正确答案：<b>

7.请选择产生斜体字的 HTML 标签：
正确答案：<i>

8.在下列的 HTML 中，哪个可以产生超链接？
正确答案：<a href="http://www.w3school.com.cn">W3School</a>

9.如何制作电子邮件链接？
正确答案：<a href="mailto:xxx@yyy">

10.如何在新窗口打开链接？
正确答案：<a href="url" target="_blank">

11.以下选项中，哪个全部都是表格标签？
正确答案：<table><tr><td>

12.请选择可以使单元格中的内容进行左对齐的正确 HTML 标签：
正确答案：<td align="left">

13.如何产生带有数字列表符号的列表？
您的回答：<list>

正确答案：<ol>

14.如何产生带有圆点列表符号的列表？
正确答案：<ul>

15.在下列的 HTML 中，哪个可以产生复选框？
正确答案：<input type="checkbox">

16.在下列的 HTML 中，哪个可以产生文本框？
正确答案：<input type="text">

17.在下列的 HTML 中，哪个可以产生下拉列表？
正确答案：<select>

18.在下列的 HTML 中，哪个可以产生文本区（textarea）？
正确答案：<textarea>

19.在下列的 HTML 中，哪个可以插入图像？
正确答案：<img src="image.gif">

20.在下列的 HTML 中，哪个可以插入背景图像？
正确答案：<body background="background.gif">
```

#### 9.CSS测试

```html
1.CSS 指的是？
正确答案：Cascading Style Sheets

2.在以下的 HTML 中，哪个是正确引用外部样式表的方法？
正确答案：<link rel="stylesheet" type="text/css" href="mystyle.css">

3.在 HTML 文档中，引用外部样式表的正确位置是？
正确答案：<head> 部分

4.哪个 HTML 标签用于定义内部样式表？
正确答案：<style>

5.哪个 HTML 属性可用来定义内联样式？
正确答案：style

6.下列哪个选项的 CSS 语法是正确的？
正确答案：body {color: black}

7.如何在 CSS 文件中插入注释？
正确答案：/* this is a comment */

8.哪个属性可用于改变背景颜色？
正确答案：background-color:

9.如何为所有的 <h1> 元素添加背景颜色？
正确答案：h1 {background-color:#FFFFFF}

10.如何改变某个元素的文本颜色？
正确答案：color:

11.哪个 CSS 属性可控制文本的尺寸？
正确答案：font-size

12.在以下的 CSS 中，可使所有 <p> 元素变为粗体的正确语法是？
正确答案：p {font-weight:bold}

13.如何显示没有下划线的超链接？
正确答案：a {text-decoration:none}

14.如何使文本以大写字母开头？
正确答案：text-transform:capitalize

15.如何改变元素的字体？
正确答案：font-family:

16.如何使文本变为粗体？
正确答案：font-weight:bold

17.如何显示这样一个边框：上边框 10 像素、下边框 5 像素、左边框 20 像素、右边框 1 像素？
正确答案：border-width:10px 1px 5px 20px

18.如何改变元素的左边距？
正确答案：margin-left:

19.请判断以下说法是否正确：如需定义元素内容与边框间的空间，可使用 padding 属性，并可使用负值？
正确答案：错误

20.如何产生带有正方形项目的列表？
正确答案：list-style-type: square
```

#### 10.JavaScript测试

```html
1.我们可以在下列哪个 HTML 元素中放置 Javascript 代码？
正确答案：<script>

2.写 "Hello World" 的正确 Javascript 语法是？
正确答案：document.write("Hello World")

3.插入 Javacript 的正确位置是？
正确答案：<body> 部分和 <head> 部分均可

4.引用名为 "xxx.js" 的外部脚本的正确语法是？
正确答案：<script src="xxx.js">

5.外部脚本必须包含 <script> 标签吗？
正确答案：否

6.如何在警告框中写入 "Hello World"？
正确答案：alert("Hello World")

7.如何创建函数？
正确答案：function myFunction()

8.如何调用名为 "myFunction" 的函数？
正确答案：myFunction()

9.如何编写当 i 等于 5 时执行一些语句的条件语句？
正确答案：if (i==5)

10.如何编写当 i 不等于 5 时执行一些语句的条件语句？
正确答案：if (i != 5)

11.在 JavaScript 中，有多少种不同类型的循环？
正确答案：两种。for 循环和 while 循环。

12.for 循环如何开始？
正确答案：for (i = 0; i <= 5; i++)

13.如何在 JavaScript 中添加注释？
正确答案：//This is a comment

14.可插入多行注释的 JavaScript 语法是？
正确答案：/*This comment has more than one line*/

15.定义 JavaScript 数组的正确方法是？
正确答案：var txt = new Array("George","John","Thomas")

16.如何把 7.25 四舍五入为最接近的整数？
正确答案：Math.round(7.25)

17.如何求得 2 和 4 中最大的数？
正确答案：Math.max(2,4)

18.打开名为 "window2" 的新窗口的 JavaScript 语法是？
正确答案：window.open("http://www.w3school.com.cn","window2")

19.如何在浏览器的状态栏放入一条消息？
正确答案：window.status = "put your message here"

20.如何获得客户端浏览器的名称？
正确答案：navigator.appName
```

#### 11.jQuery测试

```html
1.下面哪种说法是正确的？
正确答案：jQuery 是 JavaScript 库

2.jQuery 使用 CSS 选择器来选取元素？
正确答案：正确

3.jQuery 的简写是？
正确答案：$ 符号

4.通过 jQuery，选择器 $("div") 选取什么元素？
正确答案：所有 div 元素

5.jQuery 是客户端脚本库，还是服务器端脚本库？
正确答案：客户端脚本

6.可以将 jQuery 与 AJAX 一起使用吗？
正确答案：Yes

7.jQuery html() 方法适用于 HTML 和 XML 文档。
正确答案：错误

8.把所有 p 元素的背景色设置为红色的正确 jQuery 代码是？
正确答案：$("p").css("background-color","red");

9.通过 jQuery，$("div.intro") 能够选取的元素是？
正确答案：class="intro" 的所有 div 元素

10.下面哪个 jQuery 方法用于隐藏被选元素？
正确答案：hide()

11.下面哪种 jQuery 方法用于设置被选元素的一个或多个样式属性？
正确答案：css()

12.下面哪个 jQuery 方法用于执行异步 HTTP 请求？
正确答案：jQuery.ajax()

13.将所有 div 元素的高度设置为 100 像素的正确 jQuery 代码是？
正确答案：$("div").height(100)

14.下面哪句话是正确的？
正确答案：如需使用 jQuery，您能够引用 Google 的 jQuery 库

15.jQuery 是通过哪种脚本语言编写的？
正确答案：JavaScript

16.下面哪个 jQuery 函数用于在文档结束加载之前阻止代码运行？
正确答案：$(document).ready()

17.哪个 jQuery 方法用于处理命名冲突？
正确答案：noConflict()

18.哪个 jQuery 方法用于添加或删除被选元素的一个或多个类？
正确答案：toggleClass()

19.$("div#intro .head") 选择器选取哪些元素？
正确答案：id="intro" 的首个 div 元素中的 class="head" 的所有元素

20.jQuery 是 W3C 标准吗？
正确答案：No
```

#### 12.SQL测试

```html
1.SQL 指的是？
正确答案：Structured Query Language

2.哪个 SQL 语句用于从数据库中提取数据？
正确答案：SELECT

3.哪条 SQL 语句用于更新数据库中的数据？
正确答案：UPDATE

4.哪条 SQL 语句用于删除数据库中的数据？
正确答案：DELETE

5.哪条 SQL 语句用于在数据库中插入新的数据？
正确答案：INSERT INTO

6.通过 SQL，您如何从 "Persons" 表中选取 "FirstName" 列？
正确答案：SELECT FirstName FROM Persons

7.通过 SQL，您如何从 "Persons" 表中选取所有的列？
正确答案：SELECT * FROM Persons

8.通过 SQL，您如何从 "Persons" 表中选取 "FirstName" 列的值等于"Peter" 的所有记录？
正确答案：SELECT * FROM Persons WHERE FirstName='Peter'

9.通过 SQL，您如何从 "Persons" 表中选取 "FirstName" 列的值以 "a" 开头的所有记录？
正确答案：SELECT * FROM Persons WHERE FirstName LIKE 'a%'

10.请判断下列说法是否正确：当所列出的某个条件为 true 时，OR 运算符会显示记录。当列出的所有条件为 true 时，AND 运算符会显示记录。
正确答案：正确

11.通过 SQL，您如何在表 Persons 中选择 FirstName 等于 Thomas 而 LastName 等于 Carter 的所有记录？
正确答案：SELECT * FROM Persons WHERE FirstName='Thomas' AND LastName='Carter'

12.通过 SQL，您如何按字母顺序选取 Persons 表中 LastName 介于 Adams 和 Carter 的所有记录？
正确答案：SELECT * FROM Persons WHERE LastName BETWEEN 'Adams' AND 'Carter'

13.哪条 SQL 语句可返回唯一不同的值？
正确答案：SELECT DISTINCT

14.哪个 SQL 关键词用于对结果集进行排序？
正确答案：ORDER BY

15.通过 SQL，您如何根据 "FirstName" 列降序地从 "Persons" 表返回所有记录？
正确答案：SELECT * FROM Persons ORDER BY FirstName DESC

16.通过 SQL，您如何向 "Persons" 表插入新的记录？
正确答案：INSERT INTO Persons VALUES ('Jimmy', 'Jackson')

17.通过 SQL，您如何向 "Persons" 表中的 "LastName" 列插入 "Wilson" ？
正确答案：INSERT INTO Persons (LastName) VALUES ('Wilson')

18.您如何把 "Persons" 表中 "LastName" 列的 "Gates" 改为 "Wilson" ？
正确答案：UPDATE Persons SET LastName='Wilson' WHERE LastName='Gates'

19.通过 SQL，您如何在 "Persons" 表中删除 "FirstName" 等于 "Fred" 的纪录？
正确答案：DELETE FROM Persons WHERE FirstName = 'Fred'

20.通过 SQL，您如何返回 "Persons" 表中记录的数目？
正确答案：SELECT COUNT(*) FROM Persons
```

#### 13.PHP测试

```html
1.PHP 指的是？
正确答案：PHP: Hypertext Preprocessor

2.PHP 服务器脚本由哪个分隔符包围？
正确答案：<?php…?>

3.如何使用 PHP 输出 "hello world"？
正确答案：echo "Hello World";

4.在 PHP 中，所有的变量以哪个符号开头？
正确答案：$

5.结束 PHP 语句的正确方法是？
正确答案：;

6.PHP 语法与下列哪种最相似？
正确答案：Perl 和 C

7.如何从使用 "get" 方法提交的表单中获取数据？
正确答案：$_GET[];

8.请判断以下说法是否正确：当使用 POST 方法时，变量显示在 URL 中。
正确答案：错误

9.请判断以下说法是否正确：在 PHP 中，既可以使用单引号 ( ' ' ) 也可以使用双引号 ( " " ) 来包围字符串。
正确答案：正确

10.请判断以下说法是否正确：包含文件必须使用文件后缀 ".inc"。
正确答案：错误

11.引用文件 "time.inc" 的正确方法是？
正确答案：<?php require("time.inc"); ?>

12.在 PHP 中创建函数的正确方法是？
正确答案：function myFunction()

13.以只读模式打开文件 "time.txt" 的正确方法是？
正确答案：fopen("time.txt","r");

14.请判断以下说法是否正确：PHP 允许我们直接通过脚本来发送电子邮件。
正确答案：正确

15.连接 MySQL 数据库的正确方法是？
正确答案：mysql_connect("localhost");

16.给 $count 变量加 1 的正确方法是？
正确答案：$count++;

17.在 PHP 中，添加注释的正确方法是？
正确答案：/*…*/

18.请判断以下说法是否正确：PHP 可以在 Microsoft Windows IIS (Internet Information Server) 上运行。
正确答案：正确

19.请判断以下说法是否正确：在 PHP 5 中，在默认情况下 MySQL 支持是启用的。
正确答案：错误

20.以下的变量名，哪个是不合法的？
正确答案：$my-Var
```

#### 14.问答题

```html
1.鼠标手指状显示,在浏览器中的标准写法？
	cursor：point
2.CSS-DIV开发web页面的优势有哪些？
	I.div+css,这个网页设计模式中,div承担了网页的内容,css承担了网页的样式。这样就使网页的内容和样式分离开。(或者说表现与结构分离)
	II.有助于提高搜索引擎亲和力
	III.有助于页面的维护升级和重构
3.如何创建一个JavaScript object？
	I.var person=new Object()
	II.var person={name:'Karry',age:19}
	III.var anotherPerson=Object.create(person,{name:'Karry'})
4.如果我不放<！DOCTYPE html>，HTML5还会工作么?
  	<！DOCTYPE html>只是一个声明,不写同样html5代码是可以正常工作的
5.用一条SQL语句查出每门课都大于80分的学生的姓名
      select distinct name from grade where name not in(select distinct name from grade where score >=80)
6.简述列举文档对象模型DOM里document的常用的查找访问节点的方法?
      Document.getElementById根据元素id查找元素
	  Document.getElementByName根据元素name查找元素
	  Document.getElementTagName根据指定的元素名查找元素
7.在ie中,html对象的id可以作为document的下属对象的变量名直接使用,在ff中不能,此兼容性问题如何解决？
      用getElementById('idName')代替idName作为对象变量使用
8.如何使用canvas和html5中的svg去画一个矩形？
      HTML5使用SVG绘制矩形的代码  
      <svg xmlns="http://www.w3.org/2000/svg" version="1.1">  
        <rect style="fill: rgb(0, 0, 255); stroke-width: 1px; stroke: rgb(0, 0, 0);" height="[object SVGAnimatedLength]" width="[object SVGAnimatedLength]"> </rect>  HTML5使用Canvas绘制矩形的代码  
        var c=document.getElementById("mycanvas");
        var ctx=c.getContext("2d");
        ctx.rect(20,20,150,100); ctx.stroke();
```



#### 跨域:在不同域名下进行数据交互

	不需要跨域情况(协议相同、域名相同、端口号相同)
		www.a.com/a.js  www.a.co/b.js
		在不同文件夹下:www.a.com/a.js  www.a.co/c/b.js
	需要跨域
		www.a.com   b.a.com   子域和主域
		www.a.com   www.b.com
	ajax:XMLHttpRequest() 不能跨域
	跨域的方式：
			1.子域和主域都要设置  document.domain
			2.服务器代理:XMLHttpRequest代理文件  
					缺点:增大服务器的压力
			3.script标签:jsonp
ajax解决跨域问题:

​	在服务器端添加head('Accwss-Control-Allow-Origin:域名')

jsonp解决跨域:json+padding(内填充);把json当做内填充的东西填充到盒子里

	js中写法
	$.ajax({
	  type:'get',
	  url:'',
	  dataType:'jsonp',
	  jsonp:'callback',
	  jsonpCallback:'callback123'  指定回调函数名字
	})
	服务器端
		$userInfo=array('id'=>1,'username'=>'karry','email'=>'15035482512@163.com');
	$callback=$_GET['callback'];
	$result=json_encode($userInfo);
	echo $callback."($result)"

#### vue面试题

1.列举vue2的computed、methods、watch分别的作用和区别

```html
作用：
	computed:在html DOM加载完成后马上执行的,如赋值
	methods:必须要有一定的触发条件才能执行,如点击事件
	watch:观察vue实例上的数据变动
区别:默认加载的时候先computed再watch，不执行methods；触发时间后先methods再watch
```

2.简述下bower,webpack,gulp的作用的指令及用法

```html
bower:包管理器,用来管理项目的外部依赖
webpack:文件打包工具,可以把项目的各种js、css文件等打包合并成一个或多个文件
gulp:工具链,可以配合各种插件做js压缩，css压缩,less编译等工作
```

3.vue-router有哪些常用的守卫钩子函数

https://router.vuejs.org/zh-cn/advanced/navigation-guards.html

4.axios的特点有哪些

```html
基于promise用于浏览器和nodejs的http客户端
特点：
	从浏览器中创建XMLHttpRequest
	从nodejs发出http请求
	支持promise API
	拦截请求和响应
	转换请求和响应数据
	取消请求
	自动转换成json数据
	客户端防止CSRF/XSPF
```

5.单页面的优缺点？

```html
优点
	1.分离前后端关注点,前端负责页面显示,后端负责数据存储和计算,各司其职,不会把前后端的逻辑混杂在一起
	2.减轻服务器的压力,服务器只要出数据就行,不用管展示逻辑和页面合成,吞吐能力会提高几倍
	3.同一套后端程序代码,不用修改就可以运用web界面、手机、平板等各种客户端

缺点
	1.SEO问题  没有html  抓不到什么
	2.刚开始的时候加载可能会慢很多
	3.用户操作需要写逻辑、前进、后退等
	4.页面复杂度提高很多,复杂逻辑难度成倍
```

