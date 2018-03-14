# Javascript

## 历史

## 干什么（生机活力、强大）

1. 数据验证

2. 操作页面（dom）元素的内容、样式、属性

3. 动态的创建、删除元素

4. 动画

5. cookie、本地存储

   1. ajax （动态获取数据）

      ## 组成

      ECMAScript（描述语言的基本语法和对象）

      基础语法：变量、数据类型、运算符、执行流程、函数、对象

      BOM（browser  object  model 浏览器对象模型）（作用于网页内容的方法和接口）

      地址、历史记录、DOM、屏幕、

      DOM（document object  model 文档对象模型）（和浏览器交互的方法和接口）

      节点（内容、属性、文档）

      # ECM

      ## 引入方式

      1. 标签对：script

         ```html
         <script>
           //js code
         </script>
         ```

      2. 外部引入JS文件

         ```html
         //index.html
         <script src="index.js"></script>
         //index.js
         js code
         ```

      注意事项

      引入多个js文件，js整体，相互联系相互影响相互作用

      外部js文件中，不允许script标签对

      引入外部js文件，script标签对中不允许出现js代码

      ## 调试工具

      1. alert();警示框  加入单引号或双引号可以弹出汉字、字符、字符串
      2. console.log();在控制台输出
      3. document.write();写在页面、文档当中 可以识别标签对

      ​

      ## 特点

      基于对象和事件驱动的松散型解释性语言

      ##### 松散型体现在

      不需要考虑变量的数据类型

      分号可加可不加

      变量可以在声明前调用

      ##### 事件驱动

      由某种操作动作引起相应的事件响应

      ### 如何能够节省内存，方便的存储

      ## 变量

      存储数据的一个容器

      #### 声明

      ##### var  变量名   存在变量的提升，可以在声明之前调用

      ##### let   变量名     识别块级作用域

      与var的区别

      1. 先声明后调用

         ```html
         console.log(num);//报错
         let num=1;
         console.log(num);//输出1
         ```

      2. 不存在变量提升

         变量提升：它会先扫描整个函数体的语句，把所有申明的变量“提升”到函数顶部，它只提升了变量`y`的声明，但不会提升变量`y`的赋值

         ```html
         function foo() {
             var x = 'Hello, ' + y;//Hello, undefined
             alert(x);
             var y = 'Bob';
         }
         foo();
         ```

         ​

      3. 暂时性的死区(只针对与let)

         ```html
         {
         console.log(num);//报错
         //暂时性死区
         let num=1;
         console.log(num);//输出1
         }
         ```

         ​

      4. 同一个作用域里不允许重复声明同一个变量

         ```html
         let num=1;
         let num=2;//报错
         ```

      ##### const  变量名   声明的变量为常量       识别块级作用域

      不允许修改,声明的同时赋值

      常量一般声明在js最前面

      与let相似，先声明后调用

      ​                   暂时性死区

      ​                   不存在变量提升

      ​                   同一个作用域里不允许重复声明同一个变量

      变量名：由数字、字母、下划线、$组成 

      1.  数字不能开头 
      2.  关键字不能作为变量名(eg:var)
      3.  保留字(eg:class)
      4.  有意义
      5.  规则：首字母大写；驼峰命名法
      6.  变量区分大小写

      #### 赋值(默认undefined)

      先声明后赋值

      var a;a=10;

      声明的同时进行赋值

      var a=10;

      一次性声明多个变量，然后赋值

      声明多个变量用“，”隔开

      var a,b,c;

      a=10;b=20；c=30;

      一次性声明多个变量，同时进行赋值

      var a=10,b=20,c=30;

      #### 变量使用时注意事项

      变量值可以修改

      可以重复声明同一个变量

      ​       如果不给新的变量赋值，变量用的还是原来的值

      ​       如果给新的变量赋值，新的值会覆盖原来的值

      声明一个变量需要var去修饰    

      ​     如果不用var修饰并且也没有赋值，会报错

      不用var修饰并且赋值，会变成全局变量（不推荐）

      变量声明没有赋值 默认值是undefined 

      赋值之前调用 默认值是undefined 

      ### 变量能够存储哪些类型的数据

      #### 数据类型：

      ##### 根据它在内存中存储的位置分为2种

      初始数据类型（存在栈区：数据量少，简单读取速度快）

      undefined、number（数字）、string（字符串）、Boolean（布尔）、null

      复合(引用)数据类型（存在堆区：数据量多，复杂读取速度慢）

      object

      #### 检测数据类型

      ##### 判断数据类型：typeof(variable) 

      ##### 判断某一个对象是否由某个构造函数实例化出来的：instanceof

      ```html
      function Person(){
      			this.name='zhangsan';
      			this.age=20;
      			this.sex='男';
      			this.sing=function(){
      				alert('唱歌');
      			};
      		} 
      let lisi=new Person();
      console.log(lisi instanceof Person);//true
      ```

      ####   

      |   数据类型    |                    值                     |  typeof   |
      | :-------: | :--------------------------------------: | :-------: |
      | undefined |                undefined                 | undefined |
      |  boolean  |                true、false                |  boolean  |
      |   null    |              null（空  什么都没有）              |  object   |
      |  number   |  十进制、十六进制(0x)、二进制(0b)、八进制(0o or 0)、特殊值   |  number   |
      |  string   | 通过''（单引号）or""（双引号）包裹起来的字符（数字、字符、汉字、特殊字符） |  string   |
      |  object   |                属性和方法的无序集合                |  object   |

      特殊值：最大值：number.max_value 最小值number.min_value

      特殊字符：\n

      模板字符串：``  在控制台输出会保留在代码程序中的格式

      ${num}  在字符串中表示变量，不需要拼接

      ## 如何操作数据

      ### 运算符

      ##### 算术运算符

      '+'、'-'、'*'、‘/’、‘%’、‘++’、‘--’

      ‘%’：得到某一个范围之内的数

      数字和字符串相加所得结果将为字符串

      ‘+’:都为数字：求和

      ‘+’:一边为字符串：字符串的连接拼接

      var++   先运算后自增

      ++var   先自增后运算

      undefined++   结果：NaN  不是一个数字（not a number）

      ++、--只针对变量不针对常量

      ##### 赋值运算符

      =、+=、-=、*=、/=、%=

      a+=5     =     a=a+5

      ‘+=’:都为数字：求和

      ‘+=’:一边为字符串：字符串的连接拼接

      ##### 比较运算符（运算结果为Boolean值）

      '>'、‘<’、‘==’、‘>='、‘<=’、‘===’、‘!=’、'!=='

      两个数字进行比较：正数>0>负数  负数相比  绝对值越大的反而小

      两个字符串比较：比较字符串首字母的ASCII码值，

      ​       如果第一个字符不相同 ASCII码值大的所在字符串就大

      ```html
      var num='a',num1='bsa' num1>num
      ```

      ​       如果第一个字符相同，以此类推比较第二个，第三个

      ```html
      var num='a',num1='ab' num1>num
      ```

      两个数字型字符串：比较字符串首字母的ASCII码值，

      ​       如果第一个字符不相同 ASCII码值大的所在字符串就大

      ```html
      var num='10',num1='2' num1>num
      ```

      ​       如果第一个字符相同，以此类推比较第二个，第三个

      ```html
      var num='101',num1='12' num1>num
      ```

      字符串与数字比较：字符串尝试转换成数字，

      ​        如果转换成功按照数字的规则进行比较

      ```html
      var num='10',num1='A' num1>num
      ```

      ​        如果转换不成功返回NaN,整个表达式返回false

      ```html
      var num='10',num1='2PX'  false
      ```

      数字和布尔值   true=>1  false=>0

      特殊：undefined==null

      #### undefined、null、NaN的区别

      |           | 数据类型   | 表示       | 什么情况下返回    |      |
      | --------- | ------ | -------- | ---------- | ---- |
      | undefined | object | 没有定义     | 三种情况       |      |
      | null      | object | 空值或无对象的值 | 寻找一个不存在的元素 |      |

      ```javascript
      1.直接访问没有修改的全局变量undefined eg:var x=undefined  x的值为undefined
      2.使用没有声明的变量，在IE下出错，提示“xxx”未定义。已经声明，没有赋值，eg:var x;alert(x);弹出undefined
      3.使用一个不存在的对象属性
      ```

      ​

      ##### 逻辑运算符

      ‘&&’（and）、'||'（or）、‘！’（not）

      false：0 null  undefined  ''(空字符串)   NaN

      ##### 三元运算符

      ```html
      var flag;
      	flag=num%2==0? true:false;
      ```

      new  创建对象

      delete  删除对象的属性或方法

      () 改变运算优先级

      ​    调用函数

      ，一次性声明多个变量

      ##### prompt  输入框

      ```html
      var score=1*prompt('请输入你的成绩',60);
      ```

      ## 流程

      ### 顺序结构

      #### 分支(选择)结构

      1. ##### 单路分支

         if(条件){

         条件成立执行的代码

         }

         ```html
         var num=-10;
         	 if(num>0){
         	 	alert(1);
         	 }
         ```

      2. ##### 双路分支

         if(条件){

         条件成立执行的代码

         }

         else{

         条件不成立执行的代码

         }

         ```html
         var num=-10;
         if(num>0){
         		alert(true);
         	}
         	else{
         		alert(false);
         	}
         ```

      3. ##### 多路分支

         if(条件1){

         条件1成立执行的代码

         }

         else if(条件2){

         条件2成立执行的代码

         }...

         else{

         上述所有条件都不满足，执行

         }

         ```html
         var score=prompt('请输入你的成绩',60);
         	if(score>=90 && score<=100){
         		alert('优秀');
         	}
         	else if(score>=80 && score<90){
         		alert('良')
         	}
         	else if(score>=70 && score<80){
         		alert('中')
         	}
         	else if(score>=60 && score<70){
         		alert('及格')
         	}
         	else if(score>=0 && score<60){
         		alert('不及格')
         	}
         	else{
         		alert('输入错误')
         	}
         ```

      ##### switch(值){

      case 情况1：代码

      break;

      case 情况2：代码

      break;

      case 情况3：代码

      break;

      case 情况4：代码

      break;...

      default:上述所有条件都不满足，执行

      }

      ```html
      switch(parseInt(score/10)){
      		case 10:
      		alert("满分"); 
      		break;
      		case 9:
      		alert("优秀");
      		break;
      		case 8:
      		alert('良');
      		break;
      		case 7:
      		alert('中');
      		break;
      		case 6:
      		alert('及格');
      		break;
      		default:
      		alert('不及格');
      	}
      ```

      分支结构条件：条件不要有重复

      条件是一个范围(if)，条件是定值，用switch语句

      ### 循环结构

      在满足条件的情况下，不停的执行某一段代码

      循环的次数：初始值  最终值 变化值

      ##### for循环:关注循环的次数

      ​     for(变量=初始值;变量<=结束值;变化值){
      ​       循环体;
      ​      }

      ##### while循环（先判断后执行）:关注循环的条件

      ​    当条件满足的时候，执行循环体，当不满足的时候退出循环
      ​     while(循环的条件){
      ​         循环体;

      ​          变化量;

      ​        }

      ```html
      var a=1;
      while(a<10){
        console.log(a);
       a++;
      }
      ```

      ##### do{}while循环（先执行后判断）

      先最少执行一次，再进行条件的判断，如果条件满足继续执行，如果不满足则退出循环。

      do{
      }while(循环的条件)

      ```html
      var a=1;
      do{
        sum+=a;
       a++;
      }while(a<10)
      ```

      知道循环次数，优先考虑for，知道循环“条件”，优先考虑while、do while

      ##### do{}while 和while的区别

       while(先判断后执行):当条件满足的时候，执行循环体，

      ​           当不满足的时候退出循环,一次循环都不做。
       do{}while(先执行后判断)：先最少执行一次，再进行条件的判断，

      ​           如果条件满足继续执行，如果不满足则退出循环。

      #### 跳转语句

      continue:
       跳出并且终止当前的循环，如果下个值仍满足循环条件，
      则继续循环。

      break:
       跳出并且终止当前所在的循环，如果后面有代码，则继续往下执行。

      ## 数组

      存储一系列相同、相关的数据的容器

      ##### 优点：

      方便管理数据

      逻辑清晰，代码方便管理维护

      #### 创建数组

      ```html
      var arr=[];
      var arr1=new Array();
      ```

      #### 赋值

      声明同时赋值

      ```html
      var  arr=[1,2,3,4,5,7];
      ```

      声明之后赋值

      ```html
      var arr=[];
      arr[0]=1;arr[1]=2;
      ```

      #### 通过下标访问

      ```html
      var  arr=[1,2,3,4,5,7];
      arr[0];arr[1];arr[2];arr[3];
      ```

      下标从“0”开始，最大值：.length-1

      #### 数组遍历

      for

      ```html
      var a=[1,2,3,4,5,7];
      for(var i=1;i<a.length;i++){
        document.write(a);
      }
      ```

      #### 注意事项

      1. 数组元素默认undefined

      2. 数组的长度可变

      3. 数组元素可以是任意的数据类型

         ## 函数

         将完成某一特定功能的代码集合起来，可以重复使用的代码块。

         ### 声明函数

         ##### 基本语法(函数前后都能调用)

         ```html
         function 函数名([形参1]，[形参2...]){
           函数体
         [return]
         }
         调用:函数名()
         ```

         ##### 字面量定义(函数后调用,匿名函数)

         ```html
         var 变量=function([形参1]，[形参2...]){
           函数体
         }
         调用:变量名()
         ```

         ##### 对象的形式

         var 变量=new Function([参数1],[参数2]...,"函数体");

         ### 调用函数的方式

          通过括号来调用
         ​       函数名()
         ​       变量名()
          通过触发事件来调用
         ​        对象.事件=function (){}
         自调用（立即执行函数）
         ​        (function (){})()

         ```html
         (function(){
           alter('1233');
         })()
         ```

         #### 创建\调用函数注意问题

         如果两个函数的命名相同，后面的将会覆盖前面的函数。

         以基本语法声明的函数，会在页面载入的时候提前解析到内存中，以便调用。所以可以在函数的前后都能调用。

         但是以字面量形式命名的函数，会在执行到他的时候，才进行赋值。所以只能在函数的后面调用

      #### 参数的作用:

       可以动态的改变函数体内对应的变量的值，使同一函数体得到不同的结果。

      #### 参数的类型(可以是任何数据类型)

      形参:在定义函数的时候，函数括号中定义的变量叫做形参。用来接受实参的值。
      实参:调用函数的时候，在括号中传入的变量或值叫做实参。用于传递值给形参。

      #### 参数的个数

      实参和形参数量相等，一一对应。
      实参小于形参，不会报错，多出形参的值会自动赋值为undefined
      实参大于形参，不会报错，但如果要获得多出实参的值，需要用arguments对象来获取

      arguments:函数内部自动生成的对象，只能在函数内部调用，保存了函数调用时实参的信息

      #### arguments对象 

      每创建一个函数，该函数就会隐式创建一个arguments对象，它包含有实际传入参数的信息。

      #####  arguments对象的属性

      ​        – length 获得实参的个数
      ​        – callee 获得函数本身的引用
      ​        – 访问传入参数的具体的值。arguments[下标]

      ### 默认参数

      参数：传值，传进来的值

       不传给默认值，带有默认值的参数，放置到最后

      1. 分支结构

         ```html
         function sort(arr,type){
         if(type==undefined){
         	type=='<';
           }
             ...
             }
         ```

         ​

      2. 三元表达式

         ```html
         function sort(arr,type){
         type=type==undefined ?默认值:type;
           ...
           }
         ```

         ​

      3. 逻辑或(||)运算

         ```html
         function sort(arr,type){
         type=type||默认值;
           ...
             }
         ```

   2. 直接给默认值(当实参为undefined时仍然执行默认值)

      ```html
      function sort(arr,type=默认值){
        ...
      }
      ```

      #### rest参数

      用来接受剩余(没有形参对应的实参)参数，是一个数组

      没有剩余参数，空数组

      rest参数必须在最后

      ```html
      function fn(a,...rest){
        //rest
      }
      ```

      ...rest不在参数的位置时表示拆分数组

      ```html
      var arr=[2,4,5,5,3,,35,8];
      		console.log(splice(arr,1,2,'x','y','z'));
      		function splice(arr,pos,num,...rest){
      			//newarr 删除之后的数组
      			var newarr=spliceDelete(arr,pos,num);
      			if(rest.length>0){
      				newarr=spliceAdd(newarr,pos,...rest);
      			}
      			return newarr;
      		}
      ```

      ### return的用法

      返回值：在函数调用的地方返回一个值，默认undefined

      ​              返回值可以是任意的数据类型，函数允许写多个return只会执行一个

      ​              多个return会配合分支结构去写

      终止函数执行，return后面的代码不会运行

      ### 作用域(通过函数划分，或{}划分)

      执行的环境决定了变量和函数的作用域

      全局作用域：任意

      ​           范围：函数最外层

      ​                      不用var声明

      局部作用域：某一个函数 

      ​            范围：函数里

      环境：宿主   执行

      预编译：按照从上到下，每个script

      var   function 变量名和函数名预先放置在内存里，它能够记录它声明的环境

      块级作用域：一个{}代表一个区域  

      ```html
       for(let i=0;i<5;i++){
        console.log(i);//输出0,1,2,3,4
       }
      ```

      块级作用域嵌套

      ```html
           let num='abcd';
             {
                 let num=10;
                {
                    let num=20;
                    console.log(num);//输出20
                }
                 console.log(num);输出10
              }
             console.log(num);输出abcd
      ```

      独立作用域：for

           for(let i=0;i<a.length;i++){   //i 独立作用域
             let i=0; //i  块级作用域
           }   
      ​

      #### 特殊类型的函数

      1. ##### 递归函数：函数自己调用自己本身

         ```html
         function jiecheng(num){
         			if(num==1){
         				return 1;
         			}
         			return num*jiecheng(num-1);
         		}
         		console.log(jiecheng(5));
         ```

      2. ##### 回调函数：通过函数的指针来调用函数。

         ​        把一个函数做为另一个函数的参数，当调用这个参数的时候，这个函数就叫做回调函数。

         ```html
         	var a=[6,2,5,8,12,34,65,1];
         		var result=filter(a,function(value) {
         			return value>5;
         		});
         		console.log(result);
         		function filter(arr,fn(){
         			var newarr=[];
         			for (var i = 0; i < arr.length; i++) {
         				if(fn(arr[i])){
         					newarr[newarr.length]=arr[i];
         				}
         			}
         			return newarr;
         		})
         ```

      3. ##### 闭包(内嵌)函数： 在函数内部再嵌套函数(闭包)

           把内部函数当做返回值去调用

         ```html
         function aa(){
         			var num=10;
         			function bb(){
         				num++;
         				return num;
         			}
         			return bb;
         		}
         		var val=aa();
         		alert(val());
         ```

      4. ##### 箭头函数(没有arguments对象)

         一般写在回调函数里

          不能作为构造函数实例化对象

         ```html
         有一个参数
         var fn= a=> a;
         alert(fn(10));
         没有参数
         var fn= ()=> 1;
         alert(fn(10));
         有多个参数
         var fn= (a,b)=> a+b;
         alert(fn(1,3));
         有多个语句块
         var fn= (a,b)=> {
             alert(a);
             alert(b);
             alert(a+b)
          };
          alert(fn(10,20));
         返回对象
         1.let fn=(num)=>({name:'karry',age=18});
           console.log(fn());

         2.let aa=(num)=>{
             return {age=num};
           }
            console.log(aa(18));
         ```

         #### 深拷贝：拷贝值

         ```html
         var arr=[1,2,3,4,5];
         function copy(arr){
           var arr1=[];
           for(var i=0;i<arr.length;i++){
           arr1[i]=arr[i];
         }
           return arr1;                               
         }
         对象拷贝:Object.assign();
         ```

         #### 浅拷贝：拷贝地址

         ```HTML
         var arr=[1,2,3,4,5];
          var arr1=arr;
         ```

         ​

         ## 内置顶层函数

         内置: ECMAscript 自带的函数，ECMAscript将我们常用的一些功能封装起来，我们不需要知道他是怎么实现的，只需要知道怎么调用即可。
         顶层 :在页面当中的任何地方都可以调用。

         ##### 1.escape() 将非字母、数字字符进行编码

         ##### 2.unescape() 对编码的字符串进行解码

         ##### 3.Number() 转换成数字

         布尔值：false为0，true为1
         数字：转换成为本身。其他进制转换成十进制，将无意义的后导0去掉。
         null转换为0
         undefined 转换为 NaN not a number
         字符串(识别进制)
         ​         1.如果字符串当中只有数字，转换为10进制(忽略前导0
         ​    和后导0)
         ​          2.如果是有效的规范的浮点型，转换为浮点值(忽略前导
         ​    0和后导0)
         ​           3.如果是空字符串，则转换为0
         ​           4.如果是其他的值，返回NaN

         ```html
         返回NaN
         Number('abcd');
         Number('12px');
         Number('12.445.6');
         ```

         ##### 4.String() 转换成字符串类型

         – null和undefined: 也都会转换为字符串，分别是 null和undefined
         – 布尔类型:会返回true 和false
         – 数值类型:本身的字符串

         ##### 5.Boolean() 转换成布尔类型

         – 转换为假: ""、 0、 NaN 、undefined、false,null
         – 其他的全部都转换为真。

         ##### 6.parseInt() 将字符串转换为数字

         可以识别十六进制数

         以数字、+、-、空格开头

         第一个数字字符开始，第一个非数字字符结束

         如果一个字符串只包含数字，则以10进制的方式转换为整型。
         他会自动忽略字符串前面的空格，直到找到第一个非空的数值字符串，
         如果字符串的第一个字符不是空格、数字、-，那么返回NaN

         ##### 7.parseFloat() 将字符串转换为浮点数

         字符串当中的 . 只有第一个有效，其他的都是无效的。
         如果字符串是一个有效的整数，他返回的是整数，不会返回浮点数。

         ##### 8.isNaN() 判断一个数能否转换为数值类型。

         如果能转换成数值返回假，不能转换成数值类型，返回真。

         ## 隐式类型转换

         算数运算符:-、*、/、%

         ```html
         var num='10';//num：sting 字符型
         alert(num-1);//num：number 数字型
         ```

         比较运算符 ‘>=’

         逻辑运算符

         if()

         ```html
         var num=11;
         if(num%2){
           alert(ture);
         }
         ```

         while

         三元运算符

         ```html
         var num=10;
         num? num:'x';
         ```

         ## 对象(属性和方法的无序集合体)

         #### 对象的分类

         1.内置对象：Global 全局、Object、String、Array、Number、Math 数学方法对象、Boolean、Function、RegExp 正则
         2.宿主对象
         DOM
         BOM

         #### 创建对象

         json方法(javascript object notation) 原生格式

         ```html
         var obj={};
         ```
         构造函数

         ```html
         function fun1 () {
         }
         var obj=new fun1();
         ```
         Object方法

         ```html
         var obj=new Object();
         ```

         #### 添加属性、方法

         构造方法

         声明的时候添加

         ```html
         function fun1 () {
         this.name='zhang';
         this.age=18;
         this.sex='nan';
         }
         var obj=new fun1();

         function fun1 (name,age,sex) {    //属性传参  参数：name,age,sex
         this.name=name;
         this.age=age;
         this.sex=sex;
         }
         var obj=new fun1();
         ```

         ​

         声明以后添加

         ```html
         function fun1 () {
         }
         var obj=new fun1();
         obj.name='zhang';
         ```

         ​

         json方法

         声明的时候添加

         ```html
         var obj={属性名:属性值，属性名2:属性值2，属性名3:
         属性值3，......};
         var obj={name:'zhang',sex:'nv';age:16,say:function(){
           alert(1)
         }};
         ```

         声明以后添加

         ```html
         var obj={};
         obj.name='zhang';
         ```
         内置函数(js自带)

         只能在声明之后添加 

         ```html
         var obj=new Object();
         obj.name='zhang';
         ```
         class类语法(实例化对象)

         ```HT
         class 类名{
           constructor(参数){
            属性或方法
           };
            方法名(参数){
            属性或方法
           }
         }
         class Student{
             	constructor(name){     //属性传参   name参数
             		this.name=name;
             		this.age=20;
             		this.say=function(){
             			alert('说话');
             		}
             	};
             	study(value){          //方法传参  value参数
             		alert('学习');     //方法名()
             		alert(value);
             	};
             }
             var zhangsan=new Student();
             zhangsan.say();
             zhangsan.study();
             console.log(zhangsan)
         ```

         ​

         #### 访问对象的属性和方法

         访问属性:引用值.属性
         ​                 引用值[“属性”]
         访问方法:引用值.方法名();
         ​                  引用值[ 方法]()

         通过’.‘

         ```html
          function phone(size,color,money){
            	this.size=size;
            	this.color=color;
            	this.money=money;
            	this.msg=function (){
            		alert('发短信');
            		return '收信息'
            	};
            	this.music=function(){
            		alert('听音乐');
            	}
            }
         var iphone=new phone(5.5,'red');
          iphone.msg();
          console.log(iphone.size);
         ```

         ​

         通过下标(字符串)

         ```html
          function phone(size,color,money){
            	this.size=size;
            	this.color=color;
            	this.money=money;
            	this.msg=function (){
            		alert('发短信');
            		return '收信息'
            	};
            	this.music=function(){
            		alert('听音乐');
            	}
            }
         var iphone=new phone(5.5,'red');
          iphone['msg']();
          console.log(iphone['size']);
         ```

         #### 对象属性的遍历

         ```html
         for (var i in Objct){
         Object[i]
         }
         ```

         ##### 对象自带的属性constructor:访问对象的构造函数

         ```html
         var iphone=new phone(5.5,'red');
            console.log(iphone);
            iphone['msg']();
            iphone.name='iphone8';
            console.log(iphone);
            console.log(iphone['size']);
            alert(iphone.constructor);//访问对象的构造函数
         ```

         ​

         ##### 方法可以调用属性，可以调用方法

         ```html
         var obj=new Person('chu',20,'女');
         	    obj.speech('演讲');
         		function Person(name,age,sex){
         			this.name=name;
         			this.age=age;
         			this.sex=sex;
         			this.say=function(value){
         				alert(value);
         			};
         			this.study=function(){     //调用属性
         				alert(this.name);
         			};
         			this.speech=function(value){   //调用方法
         				this.say(value);
         			}
         		}
         ```

         ​

         ##### 属性可以是下标

         ```html
         function phone(size,color,money){
             this[1]='a';
             this[2]='b';
            	this.size=size;
            	this.color=color;
            	this.money=money;
            	this.msg=function (){
            		alert('发短信');
            		return '收信息'	
            	};
            	this.music=function(){
            		alert('听音乐');
            	}
            }
         var iphone=new phone(5.5,'red');
          console.log(iphone[1]);
         console.log(iphone[2]);
         ```

         ##### 判断两个对象是否相等是根据对象的地址

         ```
         function Person(){
         			this.name='zhangsan';
         			this.age=20;
         			this.sex='男';
         			this.say=function(){
         				alert(this.name);
         			}
         			this.play=function(){
         				alert(`${this.name}在玩`);
         			}
         		} 
         		let zhangsan=new Person();
         		let lisi=new Person();
         		console.log(zhangsan.name==lisi.name);//true  根据属性值判断属性是否相等
         		console.log(zhangsan.say()==lisi.say());//true 根据方法返回值判断方法是否相等
         		console.log(zhangsan.say==lisi.say);//false   根据函数的地址判断函数是否相等
         		console.log([]==[]);//false   根据数组的地址判断数组是否相等
         ```

         #### 原型对象(prototype:构造函数的属性):存放公共的一些方法或属性，也是一个对象

         在同一个作用域里只能出现一个prototype   出现多个会出现覆盖的现象   节省内存

         构造函数和原型对象可以拥有相同的属性或方法，会优先使用构造函数的属性或方法

         ```html
         function Person(){
         			this.name='zhangsan';
         			this.age=20;
         			this.sex='男';
         		} //构造函数的原型对象
         		Person.prototype={
                    //添加方法1
         	    	say:function(){
         	    		alert(this.name);
         	    	},
         	    	play:function(){
         				alert(`${this.name}在玩`);
         			}
         	    }//添加方法2   构造函数的原型对象也是一个对象
         	    Person.prototype.eat=function(){
         	    	alert("吃饭");
         	    }
         		let zhangsan=new Person();
         		let lisi=new Person();
         		lisi.eat();
         		console.log(zhangsan.name==lisi.name);//true
         		console.log(zhangsan.say()==lisi.say());//true
         		console.log(zhangsan.say==lisi.say);//true  
         ```

         ##### delete 删除对象的属性或方法(不能删除原型对象中的属性或方法)

         ```html
         function Person(){
         			this.name='zhangsan';
         			this.age=20;
         			this.sex='男';
         			this.sing=function(){
         				alert('唱歌');
         			};
         		} 
         let lisi=new Person();
          lisi.sing();  //唱歌
         delete lisi.name;
         delete lisi.sing;
         console.log(lisi.sing);//undefined
         console.log(lisi);//Person(){age:20;sex:'男';}
         ```

         ​

         ##### 清空一个对象:对象=null

         ```html
         function Person(){
         			this.name='zhangsan';
         			this.age=20;
         			this.sex='男';
         			this.sing=function(){
         				alert('唱歌');
         			};
         		} 
         let lisi=new Person();
         lisi=null//清空
         ```

         ​

         ##### 判断数据类型：typeof

         ##### 判断某一个对象是否由某个构造函数实例化出来的：instaceof

         ```html
         function Person(){
         			this.name='zhangsan';
         			this.age=20;
         			this.sex='男';
         			this.sing=function(){
         				alert('唱歌');
         			};
         		} 
         let lisi=new Person();
         console.log(lisi instanceof Person);//true
         ```

         #### 继承： 继承的类.原型对象=new 要继承的类

         自己的构造函数和原型对象、父类的构造函数和原型对象可以拥有相同的属性或方法，会优先使用自己构造函数的属性或方法，之后是自己原型对象的属性或方法，接着是父类构造函数的属性或方法，最后是父类原型对象的属性或方法

         ```html
         function Person(){
         			this.name='zhangsan';
         			this.age=20;
         			this.sing=function(){
         				alert('唱歌');
         			};
         		} 
         		Person.prototype={
         	    	say:function(){
         	    		alert(this.name);
         	    	},
         	    	play:function(s){
         				alert(`${s}在玩`);
         			}
         	    }
         	    Person.prototype.eat=function(name){
         	    	alert(`${name}吃饭`);
         	    }
         function Student(){
         	    	this.class='wuif1707-1';
         	    	this.number='1707003';
         	    	this.skill=function(){
         	    		alert('学习');
         	    	}
         	    }
         	    Student.prototype=new Person();//继承
         	    var chu=new Student();
         	    console.log(chu);
         	    chu.say();    //调用父类原型对象的方法
         	    chu.eat('chu');//调用父类原型对象单独添加的方法
         	    chu.sing();//调用父类构造函数的方法
         ```

         #### 类的继承

         ```html
         class Student(){
            construction(){
         	    	this.class='wuif1707-1';
         	    	this.number='1707003';
         	    	this.skill=function(){
         	    		alert('学习');
                     }
         	}
         }
         class Student extends Person{
             construction(){
               super();//调用this,必须在函数的第一条语句
               this.name='karry';
             }
         }

         let c=new Student();
         console.log(c.name);
         ```

         #### 冒充继承

         ```html
         call方法:call(冒充对象，参数1，参数2，...)
         function Person(){
         			this.name='zhangsan';
         			this.age=20;
         			this.sing=function(a,b){
         				return a+b;
         			};
         		} 
         function Student(){
         	    	this.class='wuif1707-1';
         	    	this.number='1707003';
         	    	this.skill=function(){
         	    		alert('学习');
         	    	}
         	    }
          Student.prototype=new Person();//继承
         	 var chu=new Student();
              var wang=new Person();
         chu.sing.call(wang,3,4);
         apply方法  数组
         chu.sing.apply(wang,[3,4]);
         ```

         ​

         指向当前对象的原型

         ```html
         function Person(){
         			this.name='zhangsan';
         			this.age=20;
         			this.sing=function(){
         				alert('唱歌');
         			};
         		} 
         		Person.prototype={
         	    	say:function(){
         	    		alert(this.name);
         	    	},
         	    	play:function(s){
         				alert(`${s}在玩`);
         			}
         	    }
         	    Person.prototype.eat=function(name){
         	    	alert(`${name}吃饭`);
         	    }
         function Student(){
         	    	this.class='wuif1707-1';
         	    	this.number='1707003';
         	    	this.skill=function(){
         	    		alert('学习');
         	    	}
         	    }
         	    Student.prototype=new Person();//继承
         	    var chu=new Student();
         console.log(chu.__proto__);
         ```

         ​

         ### 字符串对象

         #### 属性：

         length :返回字符串的长度，不区分中英文，只能用来获取或查看

          construction:返回构造函数

         ```HTM
         var str='sa张dahdks';
         	    console.log(str.length);//9
         	    console.log(String.constructor);
         ```

         #### 方法：

         ##### 查找方法：

         charAt(num):返回指定位置的字符

         charCodeAt(num):返回指定位置字符对应的Unicode(ASCII)码值

         String构造函数:String.fromCharCode:返回Unicode编码所对应的字符串

         ​               接受一个或多个指定的Unicode值，然后返回一个或多个字符串。

         ```html
         var str='sa张dahdks';
         	    console.log(str.charAt(3));//d
         	    console.log(str.charCodeAt(1));//97
         	    console.log(String.fromCharCode(98));//b
         ```

         ##### 查找位置的方法

         indexOf():返回某个指定的字符串，在字符串中首次出现的位置

         lastIndexOf():返回某个指定的字符串，在字符串中最后出现的位置

         存在返回位置，不存在返回-1

         ```html

         ```

         includes():判断某一个字符串中是否存在另一个字符串，存在返回true，不存在返回false

         ##### 截取方法(对原来的字符串没有任何影响)

         slice()：

         ​     1.slice(start,end):从指定的开始位置，截取到指定的结束位置(不包括结束位置)

         ​     2.slice(start,-1):支持负数。负数：从末尾开始计数

         ​     3.slice(start):省略掉结束位置，从指定位置开始，截取到末尾

         substring():不支持负数,其他与slice一样

         substr():

           1.substr(start,length):从指定的开始位置，截取指定长度的字符串

           2.substr(start):如果没有指定截取的长度，默认截取到末尾

         ##### 替换方法(支持正则，对原来的字符串没有任何影响)

         replace(被替换,替换的字符):将字符串中的某一些字符替换成其他的字符

         ##### 重复方法

         repeat(重复次数):将一个字符串重复若干次

         ##### 匹配方法(支持正则)

         match():在某一个字符串中匹配另一个字符串

         匹配成功：返回数组(0  index  input)

         匹配失败：返回null

         ##### 去空方法(对原来的字符串没有任何影响)

         trim():去除空格

         trimLeft():去除左边的空格

         trimRight():去除右边的空格

         ##### 转换方法

         split(分割的条件,分割后数组的长度):字符串转换成数组

         toUpperCase():转换成大写

         toLowerCase():转换成小写

         ##### 样式类型方法

         fontcolor()：给字符串指定颜色，十六进制表示、red、 rgb(255,0,0)

         fontsize()：指定字符串的大小 (1-7)

          ## 数组对象 Array

         ####  面向对象

         ```html
         var arr=new Array();//当构造函数只有一个参数并且还是数字时,数字代表的是数组的长度而不是数组的元素
         var arr=new Array(5);
         Array of(元素);//当构造函数只有一个参数并且还是数字时,数字代表的是数组的元素而不是数组的长度
         var arr=Array.of(5);
         构造函数的方法
         Array.from('集合')：将类似于数组的集合转换为数组
         ```

         #### 属性

         ```html
         length  获取或者设置数组的长度
         construction 返回数组的构造函数
         ```

         #### 方法

         ```html
         添加
         push() :   在数组的末尾添加一个或者多个元素
                    返回值为添加后新数组的长度
         unshift(): 在数组的开头添加一个或者多个元素
                    返回值为添加后新数组的长度

         删除
         pop():     在数组的末尾删除一个元素，不接受参数
                    返回值是被删掉的数组元素
         shift():   在数组的开头删除一个元素，不接受参数
                    返回值是被删掉的数组元素

         万能的添加和删除
         splice(pos,num,...)：从指定位置删除(num)元素，在pos位置添加(...)
                              返回值为数组(被删掉的数组元素)
                pos:删除的位置
                num:删除的个数
                ...:添加的数组元素
         删除：数组.splice(pos,num)
         添加：数组.splice(pos,0,...)
         删除后添加:数组.splice(pos,num,...)

         合并(对原来数组没有影响)
         concat():  合并数组，数组里面合并元素，返回合并后的新数组

         转换
         join(连接符):    数组转换成字符串，默认用“，”连接

         翻转
         reverse():   元素颠倒顺序，返回逆序数组

         排序
         sort():   默认用ASCII码顺序排序  参数必须是函数

                  大——小：sort(function(a,b){
                             return a-b>0;
                           });
                  小——大：sort(function(a,b){
                             return a-b>0;
                           }); 
         遍历数组

         forEach(function(value,index,object){
           语句块
         }) 
         value：数组元素
         index：数组下标
         object：数组

         过滤
              filter(function(value,index,object){
               return 条件 //返回符合条件的value值
              })
              filter((value,index,object)=>条件) 会改变原数组
         映射
              map(function(value,index,object){
               return 条件 //返回符合条件的value值
              })
              map((value,index,object)=>条件) 会改变原数组
         ```
         合并数组的方法

         ```html
         let arr=[1,2,3,4];
         let arr2=['a','b','c'];

         1.for/forEach
         2.arr.push(...arr2);
         3.concat()
         4.Array.prototype.push.apply(arr,arr2);
         5.Array.reduce(function(){})
         ```

         ​

         ​

         ## 数学对象(Math)

         ```html
         abs():绝对值
         max():最大值
         min():最小值
         round():取整(四舍五入)
         ceil():向上取整
         floor():向下取整
         random():随机数
         pow(x,y):x的y次幂
         sqrt():平方根
         numberObj.toFixed(2)指定小数四舍五入后保留的位数
         ```

         this用法

         ```html
         在构造函数里看的是谁来调用它  没有指定为window
         在箭头函数里看的是由定义的时候指定的
         ```

         ​

         ​

         # BOM

         ## window对象(BOM的核心对象)

         window对象的属性和方法可以省略window

         ### 属性

         ```html
         屏幕
         screen:screenX      screenY
                screenLeft   screenTop
         可视窗口的宽高
             innerWith    innerHeight
             兼容性方式
             document.documentElement.clientWidth
             document.documentElement.clientHeight
         窗口的宽高
         outerWidth   outerHeight

         window.frames  所有子窗口 访问一个用下标
         window.parent  父级窗口
         window.top     顶层窗口
         window.self    当前窗口
         ```

         ### 方法

         ```html
         时间
         setInterval(function,time,c):按照指定的周期不停的执行一个函数
            function:接受回调函数，箭头函数，函数名
            time:默认为4毫秒  设置0也是默认值  1000=1s
            c:回调函数的参数
         clearInterval():停止

         setTimeout(function,time):在指定周期之后执行一个函数并且只执行一次
         clearTimeout():停止  释放内存
         close():关闭当前窗口

         根据刷新的的频率定的时间
         requestAnimationFrame(function)  只执行一次
         cancelAnimationFrame()停止
         ```

         ## history对象

         属性

         ```html
         length:长度
         ```

         方法

         ```html
         forward():前进
         back():后退
         go(参数):1表示前进  -1表示后退 0表示刷新
         ```

         ## location对象

         url(Uniform Resource Locator):统一资源定位符

         属性:http://baidu.com/boke/image?

         ```html
         href:设置或返回完整的 URL地址
         protocol:设置或返回当前 URL 的协议
         host:设置或返回主机名和当前 URL 的端口号
         hostname:设置或返回当前 URL 的主机名
         port: 设置或返回当前 URL 的端口号
         pathname:设置或返回当前 URL 的路径部分
         search:设置或返回从问号 (?) 开始的 URL（查询部分）
         hash:设置或返回从井号 (#) 开始的 URL（锚）
         ```

         方法

         ```html
         assign():加载新的文档
         reload():重新加载当前文档 true false
         replace("1,html") 用新的文档替换当前文档

         assign()加载文档后会在历史记录里面留下记录
         replace()是指替换当前文档，不会留下记录
         ```

         # DOM(文档对象模型)

         对html元素的样式、内容、属性进行动态的改变和操作

         ## document对象(DOM的核心对象)

         属性

         ```html
         title   设置或者获取文档的标题
         URL  返回文档的URL
         ```

         方法

         ```html
         document.getElementByid   获取拥有指定id的第一个“元素”
              let id=document.getElementById('box');
         	 id.style.height='500px';

         document.getElementsByTagName 获取指定标签名的元素“集合”，通过下标的方式操作元素
               let div=document.getElementsByTagName('div');
         	  div[1].style.background='pink';

         document.getElementsByClassName 获取指定类名的元素“集合”，通过下标的方式操作元素
               let cl=document.getElementsByClassName('box');

         document.querySelector('选择器') 获取指定选择器的第一个“元素”

         document.querySelectorAll('选择器')获取指定选择器的元素“集合”可以通过forEach遍历
         转换成数组有两种：数组的构造函数里:  Array.from()
                         冒充:Array.prototype.forEach.call(对象，参数)；

         指定范围下面的元素
         document.all  document.getElementsByTagName('*')
         部分获取
         obj.getElemnetsByTagName  obj.getElemnetsByClassName

         document.anchors  获取链接
         document.images  获取图片
         document.forms  获取表单
         document.write()

         内容

         获取或设置文本内容(对象的属性)  innerText   textContent   innerHTML(识别标签对)
         获取或设置标签的属性：对象.属性   obj.id (id名) obj.className(类名)
         设置样式:批量修改  className   id
              行内样式  对象.style.background='red'
                若有“-”  eg:border-radius 首字母大写 对象.style.borderRadius=''
                        还可以用“[]”访问   对象.style[border-radius]=''
         获取样式：行内样式  对象.style.border(只能获取到行内的样式)
               window对象的方法 getComputedStyle(获取对象,null).width(只能获取不能设置)
         获取元素在页面中实际的尺寸：对象的属性 offsetWidth    offsetHeight
         返回相对于定位属性父元素的位置(返回值数字)： offsetLeft   offsetTop  
             跟定位中的left、top无关    父元素必须具有定位属性  
          有影响的：子元素的margin，定位，父元素的padding
         ```

         ## 文档对象模型

         由节点组成一个文档树模型，由元素节点、属性节点、文本节点组成，节点之间相互联系相互影响，称之为模型

         ### 节点

         ```html
         文档：文档节点

         标签：元素节点

         属性：属性节点

         文本：文本节点

         注释：注释节点
         ```

         ### 元素节点属性(没有对应元素返回null)

         ```html
         obj.childElementCount:获取节点的个数

         子节点

         obj.childNodes：获取所有的子元素“集合”  识别文本，空格

         obj.firstChild:获取第一个子元素

         obj.lastChild:获取最后一个子元素

         元素节点

         obj.childer:只识别元素节点“集合”

         obj.firstElementChild:获取第一个元素节点

         obj.lastElementChild:获取最后一个元素节点

         父子节点

         obj.parsentNode:获取某个子元素的父元素

         兄弟节点

         obj.previousSibling:获取某个子元素相邻的上一个兄弟元素

         obj.nextSibling:获取某个子元素相邻的下一个兄弟元素

         obj.previousElementSibling:获取某个子元素相邻的上一个兄弟元素节点

         obj.nextElementSibling:获取某个子元素相邻的下一个兄弟元素节点
         ```

         ### 节点信息属性

         ##### nodeName:  节点名字                   nodeType:节点类型                         nodeValue:节点值

         |  节点  | nodeName  | nodeType(数字) | nodeValue |
         | :--: | :-------: | :----------: | :-------: |
         | 元素节点 |   标签名大写   |      1       |   null    |
         | 文本节点 |   #text   |      3       |   文本内容    |
         | 注释节点 | #comment  |      8       |   注释内容    |
         | 文档节点 | #document |      9       |   null    |

         ### 节点方法

         ##### 创建节点

         ```html
         创建元素节点

                 document.createElement("元素标签名");

          创建属性节点

                 A.对象.属性="属性值“

                 B.对象.setAttribute(属性名,属性值)

                 C. arrt=document.createAttribute(“属性名”);

                 arrt.nodeValue=“属性值”

                 obj.setAttributeNode(arrt);

         创建文本节点

                 对象.innerHTML="";

                document.createTextNode("文本");

         插入到页面当中

         父对象.appendChild(追加的对象) 插入到最后

         父对象.insertBefore(要插入的对象,之前的对象) 插入到某个对象之前

         删除

         父对象.replaceChild(替换成的节点，被替换的节点)

         父对象.removeChild(删除对象)  只删除页面中的内存中依旧存在

         如果确定要删除节点，最好也清空内存 对象=null;

         复制(克隆)

         自己.cloneNode() 复制自己本身  默认false，可以接受一个参数true，表示复制元素内容
         ```

         对象.getAttribute   获取自定义属性

         对象.setAttribute  添加自定义属性

         .scrollTop  超出上边距离

         .scollLeft   超出左边距离

         ### 事件驱动

         用户的操作，浏览器的行为，反馈一些实时的响应

         ```html
         1.事件
                javascript侦测到的用户的操作或是页面 的一些行为如单机、双击等(怎么发生的)
         2.事件源
                引发事件的元素。(发生在谁的身上)
         3.事件处理函数
                 对事件处理的程序或是函数 (发生时要干什么)

         鼠标事件
         onclick 鼠标单击事件
         ondblclick 鼠标双击事件
         onmousedown 鼠标按下事件
         onmouseup 鼠标抬起事件
         onmousemove 鼠标移动事件
         onmouseover\mouseenter 鼠标移入事件
         onmouseout\mouseleave 鼠标移出事件
         鼠标移入移出事件区别
         onmouseover  onmouseenter  触发冒泡事件
         mouseenter   mouseleave

         键盘事件
         onkeyup 键盘弹起事件
         onkeydown 键盘按下事件
         onkeypress 键盘按下或按住

         表单事件
          onsubmit 当表单提交的时候触发的事件
          onreset 当表单重置的时候触发的事件
          onblur 当失去焦点的时候
          onfocus 当获取焦点的时候
          onchange 当内容改变并失去焦点的时候  

         浏览器事件
         onload  当页面中所有的资源加载后的要做的事
         onresize   获取浏览器的宽高
         ```


#### 事件详解

```html
事件绑定方式

1.一般的绑定方式
js脚本
 obj.onclick 
删除  obj.onclick=null;
2.行内
onclik={}

给同一种事件类型绑定多个事件处理系统
obj.addEventListener('click',function(){},false);
参数：事件类型(不需要on)    事件处理程序    boolean值(可写可不写   默认false) 
IE低版本浏览器支持 attachEvent('onclick',function(){}) 只是冒泡形式
参数：事件类型(需要on)    事件处理程序

移除
obj.removeEventListener('click',function(){this},false);
参数：事件类型(不需要on)    事件处理程序(匿名函数删不掉)    boolean值(可写可不写   默认false)
this  指向事件源

IE低版本浏览器支持 detachEvent('onclick',function(){this}) 只是冒泡形式
参数：事件类型(需要on)    事件处理程序  this 指向window
```

#### 事件对象

记录当事件触发时，一些相关信息或详细信息

事件对象只能在事件处理函数内部调用，事件处理函数结束后自动被销毁

```html
关于鼠标事件

   相对于浏览器位置的

      e.clientX 当鼠标事件发生的时候，鼠标相对于浏览器X轴的位置
      e.clientY 当鼠标事件发生的时候，鼠标相对于浏览器Y轴的位置

   相对于屏幕位置的

      e.screenX 当鼠标事件发生的时候，鼠标相对于屏幕X轴的位置
      e.screenY 当鼠标事件发生的时候，鼠标相对于屏幕Y轴的位置

   相对于事件源的位置

      e.offsetX 当鼠标事件发生的时候，鼠标相对于事件源X轴的位置
      e.offsetY 当鼠标事件发生的时候，鼠标相对于事件源Y轴的位置

 相对于文档的位置

      e.pageX 当鼠标事件发生的时候，鼠标相对于文档X轴的位置
      e.pageY 当鼠标事件发生的时候，鼠标相对于文档Y轴的位置

关于键盘事件

    e.key 键盘(区分大小写)
    e.keyCode 获得键盘码
    shift:16  ctrl:17  空格:32 回车13 左上右下：37 38 39 40
    altKey 判断alt键是否被按下 按下是true 反 之是false 布尔值
    e.ctrlKey  判断ctrl键是否被按下 按下是true 反 之是false 布尔值
    e.shiftKey   判断shift键是否被按下 按下是true 反 之是false 布尔值
    e.type 用来检测事件的类型 主要是用于多个事件通用一个事件处理程序的时候

滚轮事件(谷歌，IE)
   mousewheel   火狐里无效果
   e.wheelDelta   滚动方向(上->120或150 下->-120或-150)
   DOMMouseScroll  火狐里的滚轮事件
  e.detail   滚动方向(上->-3 下->3)
阻止浏览器默认行为
   e.preventDefault()  
return false 有时也可以
```



#### 获取事件对象：对象.事件=function (e){}

#### 事件流

当页面中某一个元素事件触发时，本身以及页面中所有的元素(父辈元素)都会响应该事件，按照某一特定的顺序去传播，传播的顺序(执行的顺序)称之为事件流。

```html
事件流类型

    冒泡事件流(下=>上)(所有浏览器都兼容)

        由明确的事件源到最不明确的事件源(从下到上依次触发)
        on  addEventListener(false)

    捕获型事件流(上=>下 IE低版本浏览器不支持)

        由最不明确的事件源到最明确的事件源(从上到下依次触发)
        addEventListener(true)

阻止事件流
     e.stopPropagation();

获取目标事件源的对象
      e.target  可能是事件源也可能是事件源的子类
      e.currentTagret 事件源对象

事件委派(把子元素的事件委派给它的父辈元素)

  页面中有大量的元素添加相同的事件
  通过js动态创建的元素
```

#### 本地存储

LocalStorage    永久性存储    同一个域名下共享

setItem(key value)  设置

getItem(key)   获取

removeItem(key)  移除

clear()

sessionStorage   临时性存储    存储在当前页面   不共享

JSON.stringify()   把对象格式转换成字符串

JSON.parse()      把对象格式字符串转换成数组，里面是一个个对象

Object.keys()   获取对象的属性   返回值为数组

element.classList.add() 添加

element.classList.remove() 移除

element.classList.toggle()  切换

Cookies:

获取  document.cookie  返回值为字符串

设置 document.cookie='name=lisi';

设置存储时间  

	let time=new Date();
	time.setDate(time.getDate()+7);
	document.cookie='sex=nan;expires='+time.toGMTString();
删除Cookies让它的时间过期(已经过去的时间)

```html
let time=new Date();
time.setDate(time.getDate()-7);
document.cookie='sex=nan;expires='+time.toGMTString();
```



#### 改变this指向

call() apply()  bind()

#### 时间对象

创建日期对象
var dateobj=new Date(参数);

```html
可传入的参数格式
1.“时:分:秒 月/日/年” “月/日/年 时:分:秒" 字符串
2.年,月,日,时,分,秒 不能加""
注意:不传参的话，会得到当前时间的信息

获取日期信息的方法

  getDate() 从 Date 对象返回一个月中的某一天 (1 ~ 31)。
  getDay() 从 Date 对象返回一周中的某一天 (0 ~ 6)。
  getMonth() 从 Date 对象返回月份 (0 ~ 11)。
  getFullYear() 从 Date 对象以四位数字返回年份。
  getYear() 请使用 getFullYear() 方法代替。
  getHours() 返回 Date 对象的小时 (0 ~ 23)。
  getMinutes() 返回 Date 对象的分钟 (0 ~ 59)。
  getSeconds() 返回 Date 对象的秒数 (0 ~ 59)。
  getMilliseconds() 返回 Date 对象的毫秒(0 ~ 999)。
  getTime() 返回 1970 年 1 月 1 日至今的毫秒数。
  getTimezoneOffset() 返回本地时间与格林威治标准时间 (GMT) 的分钟差。

设置日期的方法
 
  setDate() 设置 Date 对象中月的某一天 (1 ~ 31)。
  setMonth() 设置 Date 对象中月份 (0 ~ 11)。
  setFullYear() 设置 Date 对象中的年份（四位数字）。
  setYear() 请使用 setFullYear() 方法代替。
  setHours() 设置 Date 对象中的小时 (0 ~ 23)。
  setMinutes() 设置 Date 对象中的分钟 (0 ~ 59)。
  setSeconds() 设置 Date 对象中的秒钟 (0 ~ 59)。
  setMilliseconds() 设置 Date 对象中的毫秒 (0 ~ 999)。
  setTime() 以毫秒设置 Date 对象。
  setUTCDate() 根据世界时设置 Date 对象中月份的一天 (1 ~ 31)。
  setUTCMonth() 根据世界时设置 Date 对象中的月份 (0 ~ 11)。
  setUTCFullYear() 根据世界时设置 Date 对象中的年份（四位数字）。
  setUTCHours() 根据世界时设置 Date 对象中的小时 (0 ~ 23)。
  setUTCMinutes() 根据世界时设置 Date 对象中的分钟 (0 ~ 59)。
  setUTCSeconds() 根据世界时设置 Date 对象中的秒钟 (0 ~ 59)。
  setUTCMilliseconds() 根据世界时设置 Date 对象中的毫秒 (0 ~ 999)。
```

```
es6新语法
   箭头函数
* 剩余和展开
* 在参数里...表示剩余
*对象解构
*模板字符串
*变量let  常量：const    全局作用域：var
* 定义类class
* 函数
* 三种作用
* 1：函数就是把特定功能的代码封装，重复的利用
* 2：函数当做对象
* 3：函数当做类去使用
* 继承extends   更改父元素的属性或方法 用super()否则会发生this指针混乱
* 数组(接受两个参数)
*       map：一一映射到新的数组
*      sort:冒泡排序的算法 影响原数组
*      filter：过滤到新的数组  不影响原数组
*      some:根据条件得到布尔值，再进一步运算
```



## 画布(位图)

基本用法

```html
<canvas>替换内容</canvas>
```

属性

```html
宽高

默认300*150  本身不能画图
width     height     css样式设置宽高时画布中的内容也会进行缩放

线宽
ctx.lineWidth  

线端点样式
ctx.lineCap  三个值  butt 默认(无端点)  round  端点为圆形   square  端点为方形

角样式
ctx.lineJoin 三个值  miter 默认(尖角)  round 圆角  bevel  平角

内角与外角的最大距离
ctx.miterLimit  值为数字  

```

画图环境

```html
let canvas=document.querySelector('canvas');
let ctx=canvas.getContext('2d')
```

画矩形

```html
ctx.fillRect(x,y,w,h)      填充矩形
ctx.strokeRect(x,y,w,h)    描边矩形
ctx.clearRect(x,y,w,h)     清除矩形
位置：x,y   尺寸：w,h
```

样式(在画图之前设置)

```html
ctx.fillStyle=color;      填充样式
ctx.strokeStyle=color;    描边样式
```

路径(不规则图形)

```html
步骤
开始路径   ctx.beginPath()
移动       ctx.moveTo()
画图       ctx.lineTo()
闭合路径(可有可无) ctx.closePath()
填充(可以不需要闭合路劲)/描边  ctx.fill()/ctx.stroke()
```

画圆

```html
ctx.arc(x,y,r,start,end,[bool])
圆心位置：x,y   半径：r  开始弧度：start   结束弧度：end   方向:boolean值 默认false 顺时针
```

画布方法

```html
获取某个指定位置的像素点位置(图片信息)
ctx.getImageData(0,0,canvas.width,canvas.height)
放回去
ctx7.putImageData(d,0,0);  最少三个参数  对象  位置
```



banner左侧的显示方法

```html
	let zuo=document.getElementsByClassName('zuo')[0];//获取左侧内容
	let lis=zuo.getElementsByTagName('li');
	let blj=document.getElementsByClassName('banner-left-js');//获取隐藏内容
	for(let i=0;i<lis.length;i++){
		lis[i].onmouseover=function(){
			blj[i].style.display='block';
		}
		lis[i].onmouseout=function(){
			blj[i].style.display='none';
		}
	}
```

点击后换图片的方法

```html
第一种方法  两张图片互换 
let datu=document.getElementsByClassName('datu')[0];  //获取图片的位置
	let d_lis=datu.getElementsByTagName('li');
	let btn_list=document.getElementsByClassName('btn-list')[0];//获取点击的位置
	let l_lis=btn_list.getElementsByTagName('li');
	//now  表示当前窗口显示的图片
	let now=0;
	for(let i=0;i<l_lis.length;i++){
		l_lis[i].onmouseover=function(){
			d_lis[now].style.display='none';
			d_lis[i].style.display='block';
			now=i;
		}
	}
     
 第二种方法                     
   let datu=document.getElementsByClassName('datu')[0];
	let d_lis=datu.getElementsByTagName('li');
	let btn_list=document.getElementsByClassName('btn-list')[0];
	let l_lis=btn_list.getElementsByTagName('li');
	for(let i=0;i<l_lis.length;i++){
		l_lis[i].onmouseover=function(){
           for(let j=0;j<l_lis.length;j++){
			d_lis[j].style.display='none';
           }
			d_lis[i].style.display='block';
		}
	}
       
    第三种方法  用var声明时用过之后会释放
    let datu=document.getElementsByClassName('datu')[0];
	let d_lis=datu.getElementsByTagName('li');
	let btn_list=document.getElementsByClassName('btn-list')[0];
	let l_lis=btn_list.getElementsByTagName('li');
    //now  表示当前窗口显示的图片
     let now=0;                                       
	for(var i=0;i<l_lis.length;i++){
        l_lis[i].index=i;
		l_lis[i].onmouseover=function(){
			d_lis[now].style.display='none';
			d_lis[this.index].style.display='block';
			now=this.index;
		}
      }
	}                                        
      
第四种方法  var声明闭包函数保存
    let datu=document.getElementsByClassName('datu')[0];
	let d_lis=datu.getElementsByTagName('li');
	let btn_list=document.getElementsByClassName('btn-list')[0];
	let l_lis=btn_list.getElementsByTagName('li');
    //now  表示当前窗口显示的图片
     let now=0; 
    for(var i=0;i<l_lis.length;i++){
		l_lis[i].onclick=(function(i){
			return function(){
			d_lis[now].style.display='none';
			d_lis[i].style.display='block';
			now=i;
			}
		})(i)
	}
```

兼容性问题

```html
function getClass(classname){
  if(document.getElementsByClassName){
     return document.getElementsByClassName(classname)[0];
  }
  else{
    var newarr=[];
    var all=document.getElementsByClassName('*');
    for(var i=0;i<all.length;i++){
      if(all[i].classname==classname){
        newarr.push(all[i]);
        }
      }
     return newarr;                              
   }
}
                                   
若有标签为“box box1”怎么查找
function getClass(classname){  
	  	if(document.getElementsByClassName){  
	  	  return document.getElementsByClassName(classname); 
	  	}  
	  	else{   
	  	 var newarr=[];   
	  	  var all=document.getElementsByTagName('*');  
	  	    for(var i=0;i<all.length;i++){     
	  	     if(checkClass(all[i].className,classname)){    
	  	         newarr.push(all[i]);      
	  	        }    
	  	    }    
	  	    return newarr;   
	  	}
	  }
	function checkClass(className,classname){ 
	  	  var arr=className.split(' ');  
	  	  for(var i=0;i<arr.length;i++){  
	  	       if(arr[i]==classname){ 
	  	  	          return true;        
	  	       }   
	  	  }      
	  	return false;
	}
	for(var i=0;i<classname.length;i++){
		classname[i].innerHTML='包含box的标签';
	}
                                   
                                   
```

