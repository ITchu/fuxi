# HTML

##### 1：通过标记符号来标记要显示的网页中的各个部分

##### 2：由浏览器解释执行的语言

##### 3：Html是一种超文本标记语言

# CSS

### 指层叠样式表

##### 用来为HTML标签定义样式，修饰HTML元素。

### 基本语法说明

##### 选择器所有声明必须写在大括号{}之间

##### 每一条声明都必须以英文分号结尾

##### 

### 1.创建html文件，css文件

##### 改后缀名为.html,.css

### 2.HTML主题创建(英文状态)

##### （1）HTML：4s+tab

##### （2）！+tab键

##### （3）html:5+tab

### 3.标签

##### 用尖括号括起来的叫做标签

##### 双标签：成对存在的  

##### 开始标签  结束标签

```html
<head></head>
```

##### 单标签：只存在一个

```html
<img>
```

### 4.标签的构成

##### 标签名  属性=属性值

```html
<img src="">
```

### 5.注释标签(<!—注释掉的内容-->)

##### Ctrl+/

### 6.图像标签 （img）

```html
<img src="" alt="" title="">
```

##### src:引入图片的路径

##### alt:加载失败

##### title:提示文本

### 7.link标签（关联html和css）

```html
<link rel="stylesheet"  href="">
```

##### href:要链接的css的路径

### 8.css语法

##### 选择器{

##### 属性=属性值；

##### }

### 9.选择器

##### 选中页面中的元素

基础选择器：标签  类名  id 后代  群组 交叉  通用

id > 类名 > 标签 > 通用

伪元素选择器

伪类选择器  :hover  :focus  :root

子代选择器

#### 标签选择器：

##### css: 标签名

#### 类名选择器(class)：

##### html: class=”类名”（不能写中文不能以数字开头）

#####                   css: .类名

#### ID选择器: 

html:id=”id名”

css: #id名

#### 选择器优先级：id（100）>类名（10）>标签（1）

#### 后代选择器：

通过父元素选中子元素

css:   父元素（空格）  子元素

html:父子关系

有类名优先选中类名

##### 后代选择器的优先级：id(100)+class(10)  >  class(10)+div(1)

#### 群组选择器：

公用通用的样式

css:选择器，选择器，选择器

#### 交叉选择器:

同时满足两个条件的标签会被选中

#### 伪元素选择器：

::first-line	选中第一行文本

::first-letter	选中第一个字母

::after	插入元素内部的后面

::before	插入元素内部的前面

```css
div::after{
  content:"";
  display:block;
}
```

#### 伪类选择器

##### 结构伪类选择器：选中真实存在的bottom元素

:first-child   选中第一个子元素
:nth-child(2)   选中第二个子元素  写几选中第几个子元素
​                 2n    偶数

​                 2n+1   奇数

​                odd   奇数

​                 even  偶数

:nth-last-child    选中倒数第几个子元素

:last-child        选中最后一个子元素

会忽视其它标签，视其它标签类型而不见，只能选中这种类型的

:first-of-type   这种类型的第一个

:last-of-type     这种类型的最后一个

:nth-of-type(2)     这种类型的第二个

属性选择器：E[attr]:匹配E元素，且有attr属性

​                      div[class]

​                      E[attr="box"]:匹配E元素，且有attr属性,属性值为box

​                      div[class="box"]

​                       E[attr|="box"]:匹配E元素，且有attr属性,属性值中有连字符，以box单词开头（它本身也会被选中）

​                      div[class|="box"]

​                      E[attr~="box"]:匹配E元素，且有attr属性,属性值中有空格，其中一个是box单词（它本身也会被选中）

​                      div[class~="box"]

​                       E[attr*="box"]:匹配E元素，且有attr属性,属性值中包含box字母的元素会被选中

​                      div[class*="box"]

​                       E[attr6^="box"]:匹配E元素，且有attr属性,属性值中以box开头的元素会被选中

​                      div[class^="box"]

​                       E[attr6$="box"]:匹配E元素，且有attr属性,属性值中以box结尾的元素会被选中

​                      div[class$="box"]



#### 子代选择器

div>p:直系父级为div的p元素

同级元素：

div+p:选中div后面紧跟着的p标签    兄弟元素

div~p:紧跟着div后面所有的的p标签   所有的

## 选择器的优先级

一个选择器的优先级由4个等级a,b,c,d确定，当比较两个选择器时，先比较a,a值大的优先级高，如果a相等则比较b，b值大的优先级高，以此类推。因此，无论b的值多大，也不会对a值的比较造成影响。

- a是由style确定，如果一个属性由元素上的style属性定义，则a为1，否则a为0；

- b是id的数量，如果一个元素上没有id，则b为0；

- c是class、伪类、属性选择器的数量;

- d是标签选择器以及伪元素的数量；

- e代表通用选择器；

- !important的优先级最高，高于由style确定的属性

  ​

### 10.颜色表示方式

##### (1)      单词（关键字 eg:blue）

##### (2)      十六进制：#

##### (3)      Rgb(,,)

### 11.超链接标签（a）

```html
<a href=""  targe="" title=""></a>
```

##### href:要跳转页面的路径

##### target:新的页面是否在本窗口打开

#####                                     _self 在本窗口打开（默认值）

#####                                     _blank   在新窗口打开

#####            title:主题文本

#### 绝对路径

##### 从盘符开始一级一级往下找 

#### 相对路径

##### （1）参考文件和目标文件在同级时直接引入目标文件名

##### （2）参考文件和目标文件的文件夹在同级时先进入目标文件的文件夹在进入目标文件

##### （3）返回一级一个../返回两级两个../

### 12.字体

|    大小     |  颜色   |     字体      |       样式  斜体       |         加粗         |
| :-------: | :---: | :---------: | :----------------: | :----------------: |
| font-size | color | font-family | font-style: italic | font-weight  :bold |

#### 文本属性

##### 水平居中：text-align :center

##### 垂直居中：line-height:

### 13.浮动

#### 使div横排

##### float：left

#### 间距

|       右间距       |       左间距       |     上间距     |       下间距        |
| :-------------: | :-------------: | :---------: | :--------------: |
| margin-rigt:  ; | margin-left:  ; | margin-top: | margin-bottom： ； |

1. 何时用：在改变排布方式的时候用

2. 分类:左浮动：float：left

   ​         右浮动：float：right

3. 浮动的元素会脱离文档流

4. 浮动卡顿问题：子元素高于其他元素时会发生卡顿

5. 浮动的BUG：描述：父元素不设置高度，子元素都浮动，浮动的子元素撑不开父元素的高度

   解决：

   1. 能设置高度尽量设置高度
   2. 父元素加overflow:hidden;
   3. 最后一个子元素clear：both；清除浮动

### 14.标签的分类

1. 块标签：能设置宽高，独占一行   eg：div标签
2. 行内标签：不能设置宽高，不独占一行，宽高由内容撑开   eg：a标签、span标签
3. 行内块标签：能设置宽高，不独占一行   eg：img标签

### 15.标签的转换

1. 转换成行内标签：display：inline
2. 转换成块标签：display：block
3. 转换成行内块标签：display：inline-block

display：none   ：用来设置元素的隐藏，并且不占据空间

a/div标签包图片，会有2px-4px的间隙，和字体大小（font-size）有关

```css
img{
  display:block;
  width:100%;
  height:100%;
}
```

### 16.盒子模型

1. 四个部分：

   内容：

   内填充：内容到边框的距离  padding  

   ​               问题：把盒子撑大

   ​               解决方法：缩小盒子的宽高，减去相应的数值

   ​               简写：

   ​               padding：20px;       一个值    四个方向

   ​               padding：20px  10px;      两个值  上下  左右

   ​               padding：20px  10px  5px;      三个值  上  左右  下

   ​               padding：20px  10px  5px  30px;     四个值  上  右  下 左

   ​               padding-top:20px;          上

   ​               padding-bottom:20px;          下

   ​               padding-left:20px;          左

   ​               padding-right:20px;          右

   边框：border

   ​            border:10px   solid #000;(粗细   样式   颜色)

   ​             border-top(上):10px   solid #000;

   ​             border-bottom(下):10px   solid #000;

   ​             border-left(左):10px   solid #000;

   ​             border-right(右):10px   solid #000;

   ​             border-top:none;

   外边距：盒子与盒子之间的距离   margin

   ​              简写

   ​              margin：20px;       一个值    四个方向

   ​              margin：20px  10px;      两个值  上下  左右

   ​              margin：20px  10px  5px;      三个值  上  左右  下

   ​              margin：20px  10px  5px  30px;     四个值  上  右  下 左

   ​              margin-top:10px;       上

   ​              margin-bottom:10px;       下

   ​              margin-left:10px;       左

   ​              margin-right:10px;       右

   ​              margin：0 auto； 使块元素水平居中

   #### 盒子模型中的问题

   1. 浏览器默认样式

      ```css
      *{
        margin：0；
        padding：0；
      }
      ```

      *通用选择器：选中页面中的所有标签

   2. margin可以设置负值，padding不能设置负值

   3. 行内标签没有上下外边距，只有左右外边距

   4. 盒子的真实宽高：

      宽：width  +  padding-left  +  padding-right  +  border-left  +  border-right

      高：height +  padding-top  +  padding-bottom  +  border-top  +  border-bottom

   5. 当重复设置同一区域时会显示较大值

      解决方法：上面盒子设置下边距，左边的盒子设置右边距

      可以继承的属性

      font-    text-    line-     color

      不能继承的属性

      a标签

      去掉a标签下划线

      写在通用选择器里

      ```
      text-decoration:none;

      ```

      文档流：从左到右，从上到下

      a标签设置宽高的两种情况

      1. display：block；
      2. float:left; （可以看成行内块标签，但不属于行内块标签）   需要改变排布方式时添加

      ​


1.    margin-top的BUG（同时具备5个条件）

      1. 子元素是父元素的第一个子元素

      2. 父元素没有内填充

      3. 父元素没有边框

      4. 子元素没有浮动

      5. 父元素没有浮动

         描述：给子元素添加margin-top，好像作用在父元素身上

      解决：

      1. 用父元素的padding-top模拟子元素的margin-top，子元素的margin-top要去掉
      2. 给父元素添加overflow：hidden（超出部分隐藏）；

###     17.背景图片

​                在页面中需要经常更新的用img去引用

​                不经常更新的图片用背景图片去引用

​                引入背景：background-image：URL('图片路径')；

​                禁止重复：background-repeat：no-repeat;

​                背景图片位置：background—position：

​                                           单词：水平：left  center  right

​                                                        垂直：top  center  bottom

​                                            百分比：   

​                                            像素： 图片精灵

​                                             简写：background：pink （颜色） url（‘路径’）（图片） no-repeat  （禁止重复） 20%   20%（百分比）；

​               步骤：

1. 建立盒子并且设置宽高

2. 引入背景图片

3. 设置背景图片的大小                      

                                                 border-radius:50%;

                                                圆角  20px

                                                圆   50%

###  18.列表标签：块标签

ul标签--列表容器

li标签--列表项

样式：list-style:none;去掉默认点样式

### 19.定位

### 相对定位：参考元素本身的位置

父元素：position:relative;

通过top bottom left right进行调整

### 绝对定位：元素发生层叠关系时用

父元素：position:relative;

子元素：position:absolute;

通过top bottom left right进行调整

垂直居中：

```css
top:0;
bottom:0;
margin-top:auto;
margin-bottom:auto;
```

水平居中：

```css
left:0;
right:0;
margin-left:auto;
margin-right:auto;
```

##### 问题：1：父元素有定位属性即可

#####             2：如果父元素没有定位属性则相对于整个文档进行定位

### 固定定位：相对于整个窗口进行定位

position:fixed;

通过top bottom left right进行调整

 层级：z-index: 999;  

鼠标移入：

选择器：hover{

​	属性：属性值;

}

### 20.标签

#### 字体效果标签：

粗体：<b>  </b>	<strong>  </strong>

斜体：i   em

删除线：s 	text-decoration:line-through;

下划线：text-decoration:underline;

水平线：<hr width="100"(宽度)  size="10"(高度)  color="pink"(颜色) >

#### 标题标签：

块标签

一级标签：<h1>  </h1>

总共有6级

#### 段落标签：

p:写一段文字时使用

注意：一般不嵌套其他标签

pre:会按照浏览器中预先定义好的格式去展示

#### 列表标签：

块标签

1、无序列表

```html
<ul type="circle(空心圆)" disc(实心圆) square(方形)>
  <li></li>
</ul>
```

2、有序列表

```html
<ol type="a" 1 A i I>
  <li></li>
</ol>
```

3、自定义列表

```html
<dl>
  <dt></dt>		条目
  <dd></dd>		内容
</dl>
```

####  表单标签（块标签）

收集信息的作用

```html
<form action="a.php" method="post"></form>
```

action:数据提 交的位置

method：数据提交的方式

get: 数据量少，不安全

post：数据量多，安全

####  控件：输入框

```html
<input type="text"  placeholder="请输入用户名" name="username" size="30" maxlength="10"><input>
```

placeholder:提示文本

name：和数据库交换信息

size:设置控件的宽度

maxlength:用来控制最大输入的字符数

readonly：只读

disabled：禁用

value：获取用户的输入内容

#### 密码框

```html
<input type="password"  placeholder="请输入密码" >
```

#### 文件框

上传照片

```html
<input type="file" name="file" >
```

#### 多选框

name值必须相同

```html
<input type="checkbox" name="music[]">爵士
<input type="checkbox" name="music[]">摇滚
```

#### 单选框

name值必须相同

```html
<input type="radio" name="city">运城
<input type="radio" name="city">太原
```

#### 下拉框

```html
<select name="" id="" size="3" 控制显示个数>
  <option value="">新浪</option>
  <option value="">雅虎</option>
  <option value="">搜狐</option>
</select>
```

#### 文本域

```html
<textarea name="" id="" cols="50" rows="10"></textarea>
```

cols:水平宽度

rows：垂直宽度

```css
textarea{
  resize:none;不允许
  resize：both；都允许
  resize：horizon；水平
  resize：vertical；垂直
}
```



#### 提交按钮

```html
<input type="submit">
```

#### 重置按钮

```html
<input type="reset">
```

#### 自定义按钮

```html
<input type="button" name="搜索">
```

#### 分组标签（块标签）

```html
<fieldset>
  <legend>
    基本信息
  </legend>
</fieldset>
```



### 21.H5中语义化标签

```html
<header>头部</header>
<nav>导航</nav>
<aside>侧导航</aside>
<section>页面中的独立内容</section>
<main>主体 内宽</main>
<article>文章的独立内容</article>
<hgroup>文章标题的盒子</hgroup>
<code>代码</code>
```

@import	  url('');	把一个css文件引入另一个css文件中

### 22.动画

transition:all  1s  cublic-bezier()   1s;

过渡：运动状态的控制 		属性名称  运动时间  运动方式  延迟

-propery:属性名称

-duration:持续时间

-timing-function:运动方式

-delay:延迟

transform:	rotate(360deg);

2d转换：旋转

平移：translate(x px,y px)

放大：scale(x,y)  倍数

斜切：skew(x deg,y deg)	角度

阴影：box-shadow:	0px		5px		5px		5px		rgba()       inset(内部阴影);

​					水平		垂直		模糊		大小		颜色          方向(默认外部(outset));

#### display和opacity的不同

opacity：0;   全透明

opacity：1;不透明

display：none;不占据空间的隐藏

opacity：0;占据空间的隐藏

#### :root   选中页面中的根元素html标签

### 边框图片：

引入边框图片：border-img-source

设置边框图片的高度：border-img-width

切片（9个区域）：border-img-slice: 48 fill;   fill中间区域的显示

定义重复：border-img-repeat

1. ​    stretch：拉伸（默认值）

2. repeat：重复（不完整）

   round：重复（完整）

   边框以外进行绘制大小：外凸   border-img-outset：10px

   ### 线性渐变

   属性：background-image：-webkit-linear-gradient(top,red,yellow)

   linear-gradient(top,red,yellow)

   第一个参数：渐变开始的方向

   单词：top bottom  left  right

   角度：0deg=left 90deg

   第二个参数：渐变开始的颜色

   单词  十六进制  rgb  rgba

   第三个参数：渐变结束的颜色

   不均匀渐变：background-image：-webkit-linear-gradient(90deg,red 20%,yellow 60%);

   重复渐变：background-image：-webkit-repeating-linear-gradient(top,red 15%,yellow 20%)；

   ### 径向渐变

   background-image：-webkit-redial-gradient(5px 50px,red,yellow)

   background-image：-webkit-repeating-redial-gradient(5px 50px,red,yellow)

   background-image：-webkit-repeating-redial-gradient( at 5px 50px,red,yellow)改变中心点的位置

   ### 倒影

   box-reflect:(left  10px none)

   第一个参数：倒影的方向  above  below  left right

   第二个参数：倒影与原图之间的间距

   第三个参数：对倒影的遮罩效果  

   1：none  没有遮罩   2：url()    图片的遮罩  

   3：-webkit-linear-gradient(left,rgba(0,0,0,0),rgba(0,0,0,1)); 渐变遮罩  注意1：方向：原图的方向   全黑：看的见  半透明：模糊     

   渐变不占据空间

   第二个参数不能缺少

   ##### 查看兼容网站（caniuse）

   浏览器内核

   -webkit-  谷歌浏览器

   -moz-  火狐浏览器

   -ms-  IE浏览器

   -o-  欧朋

   ### 多列

   ```CSS
   column-count:4;  列数
   column-gap:4em; 列与列之间的间距
   em:当前文本字体大小单位
   column-rule:5px solid red;列与列之间的修饰
   dashed:虚线
   column-width:10em;  列的最小宽度
   ```

   ### 外轮廓

   ```CSS
   outline:10px solid red;外轮廓
   outline-offset:10px;外轮廓的相对偏移位置（不占据空间）
   ```

   文本

   ```CSS
   -webkit-text-fill-color:red   文本填充色
   -webkit-text-stroke-width:2px;   文本宽度
   -webkit-text-stroke-color：yellow；   文本描边颜色
   -webkit-text-shadow：2px 2px 5px blue; 文本阴影  水平  垂直  模糊距离 颜色
   ```

   ​


## 移动端

### 一、调试：

谷歌  真机测试  服务器

没有鼠标移入效果

### 二、视口问题

硬件提供的宽度980px   物理视口

手机宽度                逻辑视口

### 三、移动端布局

以百分比布局为主，以rem布局为辅

百分比是宽度  rem高度

em:当前文本字体大小单位

rem:root 相对根元素（html）的字体大小  100px=1rem

移动端布局步骤

1. 修改视口

   物理视口转换为逻辑视口

   ```html
   <meta name="viewport" content="width=device-width">
   ```

   ​

2. 引入rem.js

   <script src=""></script>

3. 修改js中设计稿的宽度

   ​


box-sizing:boder-box;从盒子内部减去边框的尺寸或者填充的尺寸

一般放在li里



## 弹性布局

参考阮一峰日志

对设计空间更好的分配

容器（父元素）项目（子元素）

父元素添加display：flex ；

子元素属性失效：float   clean vertical-align

容器上水平方向是主轴，垂直方向交叉轴（主轴和交叉轴是垂直）

主轴的起点就是它开始的地方   

默认从左往右

终点是它结束的地方

#### 容器属性

1. 主轴方向：flex-direction

   row:主轴方向在水平方向，项目从左向右排布

   row-reverse:主轴方向在水平方向，项目从右向左排布

   column:主轴方向在垂直方向，项目从上到下排布

   column-reverse:主轴方向在垂直方向，项目从下到上排布

2. 项目换行：flex-wrap

    nowrap:不换行（默认值）

   wrap:换行，项目从上往下排布

   wrap-reverse:换行，项目从下往上排布

3. 项目在主轴方向的对齐方式: justify-content

   flex-start:主轴的起点

   flex-end:主轴的终点

    center:主轴的中点

   space-betweeen:项目两端对齐，剩余空间平均分布

   space-around:项目两端的距离相等

4. 项目在交叉轴上的对齐方式：align-items

   flex-start 交叉轴的起点

   flex-end:交叉轴的终点

    center:交叉的中点

   baseline:基于基线对齐，文本底部对齐

5. 基于多轴，项目在交叉轴方向的对齐方式：align-content

   flex-start:  交叉轴的起点

   flex-end:交叉轴的终点

   center:交叉轴的中点

   space-betweeen:项目两端对齐，剩余空间平均分布

   space-around:项目两端的距离相等

   #### 项目属性

   1. 项目的排列顺序 order

      数值越小越靠前，默认值为0，可以识别负数

   2. 项目的放大比例  flex-grow

      默认值为0，即使存在剩余空间也不放大

      所有项目放大比例为1时，对剩余空间进行等分

   3. 项目的缩小比例  flex-shrink

      默认值为1，空间不足，进行缩小

      值设置为0，即使空间不足，也不进行缩小

   4. 项目占据主轴空间的值 flex-basis 

   5. align-self 给单个项目定义在交叉轴方向的对齐方式

      #### 3d效果

      建立3d场景(灭点)：perspecive;  值越大灭点越近

      子元素利用3d属性：transform-style:preserve-3d;

      3d旋转：tranform:rotate3d(1,1,0,360deg)

      ​               1 代表旋转   默认值为0

      观察者视角：perspective-orign:left top;

      #### 动画步骤：

      1. 定义动画  @keyframes 动画名称

         1、从开始到结束 中间可以添加

         ​     开始 0%    {属性：属性值}  

         ​      20% {属性：属性值}  

         ​     结束100%   {属性：属性值}  

         2、从开始到结束中间不能添加

         ​      开始 from  {属性：属性值}  

         ​       结束 to   {属性：属性值}  

      2. 绑定到相应的选择器上   animation

         最少要写动画名称，时间  

         animation:name 2s ease  1s infinite  alternate  forwards pasused；

         animation-name   动画名称

         animation-duration  动画时间

         animation-timing-function  运动轨迹（运动方式）   贝塞尔曲线

         animation-delay   延迟（只作用于第一次动画）

         animation-iteration-count  动画次数  默认一次   无数次infinite

         animation-direction    是否反向   默认值     反向 alternate

         animation-fill-mode    最终的状态   forwards

         animation-play-state   运动或禁止  running  运动   paused  禁止

         ### 响应式布局：

         一个页面可以适应各个终端

         终端：PC端  平板端  手机端

         优点：灵活适应不同屏幕分辨率

         缺点：代码冗余，影响加载速度

         css3  媒介查询 

         阈值   在哪个值进行变化的页面

         大于1024

         @media  screen and  (min-width:1024px);

         ​                  设备 屏幕     阈值

         ### 删格系统

         快速实现响应式布局

         预定义类：预先定义好的类添加到元素身上

         匹配:三种终端（PC端 平板端  手机端）

         ​        四种屏幕大小  手机端（小于768）平板端（768-992）PC小屏（992-1200） PC大屏（大于1200）

         .container:在每屏情况下的宽度是固定的

         .container-fluid:在每屏情况下宽度为100%；

         .row：每一行

         .col:列

         .col-xs:手机端

         |           | <768px  | 768-992 | 992-1200 | >1200  |
         | --------- | ------- | ------- | -------- | ------ |
         | container |         | 750     | 970      | 1170   |
         | col       | col-xs- | col-sm- | col-md-  | col-lg |
         |           |         |         |          |        |

## 标签

自动聚集标签

```html
<label for="man">
  <input name="sex" type="redio" id="man">
</label>

<label for="woman">
  <input name="sex" type="redio" id="woman">
</label>

```

日期

```html
年月日
<input type="date">
年月
<input type="month">
年周
<input type="week">
时间
<input type="time">
年月日时分
<input type="datetime-local">
```

范围

 min 最小值  max最大值  step步长（以几递增或递减） value默认值

```html
数字范围
<input type="number" min="0" max="10" step="2" value="2">
```

正则

```html
email:<input type="email">
url:<input type="url">
tel:<input type="tel">
颜色：<input type="color">
```

H5的新标签

```html
进度条：<progress min="0" max="10" value="5"></progress>
范围：<meter min="0" max="10" value="5"></meter>
src:引入文件  controls：向用户显示控件  loop:循环播放  autoplay:自动播放
音频：<audio src="" controls="controls" loop="loop" autoplay="autoplay"></audio>
视频：<video src="" controls="controls" loop="loop" autoplay="autoplay"></video>
画布：<canvas style="width:300px;height:300px;background:#fff;"></canvas>
```

帧窗口：可以分为各个窗口去显示不同的页面，各个页面之间有联系，可以相互操作。

```html
<iframe src="frameboder=0">
  frameboder:0表示隐藏  1表显示
</iframe>
```

## 表格(table)

```html
<table border='1px'  cellspacing='0' cellpadding='10px' align='center'>
  border='1px'  边框
  cellspacing='0'   单元格间的距离
  cellpadding='10px'   内容与单元格框的距离
  align='center'    控制表格整体居中
  <tr align='center'> 
   align='center'  文字在水平方向的居中
   valign='center'   文字在垂直方向的居中
    bgcolor='red'   文字颜色
  <td>
    colspan 列合并
    rowspan  行合并
    </td>
  </tr>
</table>
```

## css引入样式

1. 外部引入法：外部样式表  link标签（内容与表现分离）

2. 嵌入式：在head标签中的<style></style>标签对

3. 行内样式：用style属性

4. 导入样式：@import url();一个css文件引入另一个css文件中

   #### 优先级：行内样式最高  嵌入和外部优先级同样高，谁离元素近优先级就高

   ## 鼠标样式

   a标签伪类选择器

   ```html
   a:link{color=green;}   有链接
   a:hover{color=pink;}   鼠标移入
   a:active{color=yellow;}  激活（点击）
   a:vasited{color=red;}  访问过后
   ```

   ​

### 文本属性

单行文本的溢出

文本不换行：white-space:nowrap;

overflow:hidden;

对超出文本进行修饰 以省略号显示text-overflow:ellipsis;

大写：text-transform:uppercase;

小写：text-transform:lowercase；

单词的首字母进行大写：text-transform:capitalize；

字间距：letter-spacing：20px; 可以用px写也可以用em去写

首行缩进：text-indent:2em;

vertical-align用于行内块标签在垂直方向的对齐

默认值：baseline   top middle bottom

设置背景图片大小：background-size:

contain:容器有空白，图片可以完整显示，宽高中的较大者沾满容器

cover:容器没有空白，图片不能完整显示，宽高中的较小者沾满容器

overflow、display、visibility三个属性设置为隐藏状态时的区别

overflow  只是对超出容器的内容进行处理