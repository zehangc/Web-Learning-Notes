#CSS 的学习笔记

学习教程来自:[千古壹号](https://github.com/qianguyihao/Web)
##一些常用的CSS


###CSS样式中，常见的文本属性有以下几种：
+ **letter-spacing**: 0.5cm ; 单个字母之间的间距
+ **word-spacing**: 1cm; 单词之间的间距
+ **text-decoration**: none; 字体修饰：none 去掉下划线、underline 下划线、line-through 中划线、overline 上划线
+ **text-transform**: lowercase; 单词字体大小写。uppercase大写、lowercase小写、capitalize（每个单词的首字母大写）
+ **vertical-align** 属性设置元素的垂直对齐方式。

    JavaScript 语法：

         object.style.verticalAlign="bottom"
    一些可能的值：
    middle	把此元素放置在父元素的中部。
    baseline	默认。元素放置在父元素的基线上。
    
+ **list-style-image**属性的效果：

      ul li{
      list-style-image:url(images/2.gif) ;  /*列表项前设置为图片*/
      margin-left:80px;  /*公有属性*/
      }
    如图：
![e.g](images/大圣归来2.JPG)

**overflow属性**：超出范围的内容要怎么处理
  
+  visible：默认值。多余的内容不剪切也不添加滚动条，会全部显示出来。
+  hidden：不显示超过对象尺寸的内容。
+  auto：如果内容不超出，则不显示滚动条；如果内容超出，则显示滚动条。
+  scroll：Windows 平台下，无论内容是否超出，总是显示滚动条。Mac 平台下，和 auto 属性相同。

background-attachment: fixed;
+ fixed（背景就会被固定住，不会被滚动条滚走）。
+ scroll（与fixed属性相反，默认属性）

多个属性写在一起：background: blue url(images/wuyifan.jpg) no-repeat 100px 100px;

**渐变：**
background-image: linear-gradient(to right, yellow, green);

选中div：   div:nth-child(n){}  第n个div

background-image: radial-grandient(at center,
    yellow, green
)

CSS的属性名和冒号之间最好不要有空格（经验）。

引入外部样式表css文件的方式。这种引入方式又分为两种：

    1、 采用<link>标签。例如：<link rel = "stylesheet" type = "text/css" href = "a.css"></link>
    2、采用import，必须写在<style>标签中，并且必须是第一句。例如：@import url(a.css) ;

可以**备选样式**：

    <link rel = "stylesheet" type = "text/css" href = "a.css"></link>
    <link rel = "alternate stylesheet" type = "text/css" href = "b.css" title="第二种样式"></link>
    <link rel = "alternate stylesheet" type = "text/css" href = "c.css" title="第三种样式"></link>

（1）不要去试图用一个类名，把某个标签的所有样式写完。这个标签要多携带几个类，共同完成这个标签的样式。

（2）每一个类要尽可能小，有“公共”的概念，能够让更多的标签使用。

（3）尽可能的用class，除非极特殊的情况可以用id。

（4）原因：id是js用的。也就是说，js要通过id属性得到标签，所以css层面尽量不用id，要不然js就很别扭。另一层面，我们会认为一个有id的元素，有动态效果。
**我们记住这句话：类上样式，id上行为。意思是说，class属性交给css使用，id属性交给js使用。**

---
###CSS伪类

1.**静态伪类**只能用于超链接的样式

- **:link** 超链接被点击之前
- **:visited** 超链接被点击之后

2.**动态伪类**针对**所有标签**都适用

- **:hover** “悬停”：鼠标放在标签上的时候
- **:active** “激活”：鼠标点击标签，但不松手时
- **:focus** 某个标签获得焦点的时候

记住，在css中，这四种状态必须按照固定的顺序写：

    a:link 、a:visited 、a:hover 、a:active
如果不按照顺序，那么将失效。“爱恨准则”：love hate。必须先爱，后恨。

**a{}和a:link{}的区别：**

- a{}定义的样式针对所有的超链接(包括锚点)
- a:link{}定义的样式针对所有写了href属性的超链接(不包括锚点)

在写a:link、a:visited这两个伪类的时候，要么同时写，要么同时不写。如果只写a属性和a:link属性，不规范。

---

###继承性
- 关于文字样式的属性，都具有继承性，属性包括：color、 text-开头的、 line-开头的、 font-开头的
- 关于盒子、定位、布局的属性都不能继承
  
###层叠性：计算权重
层叠性就是css处理冲突的能力。所有权重计算，没有任何兼容问题！
当多个选择器，选择上了某个元素的时候，要按照如下顺序统计权重：
1. id 选择器
2. 类选择器、属性选择器、伪类选择器
3. 标签选择器、伪元素选择器
对于相同方式的样式表，其选择器排序的优先级为：ID选择器 > 类选择器 > 标签选择器

    #box1 .hezi2 p{//1个id选择器，1个类选择器，1个标签选择器，权重计算：（1，1，1）}

**1. 统计各个选择器的数量，计算他们的权重进行对比，优先级高的胜出。**
PS：不进位，实际上能进位（奇淫知识点：255个标签，等于1个类名）但是没有实战意义！

实际使用时：为了防止权重不够，比较稳妥的做法是：把第二个样式表照着第一个样式表来写，在此基础上，给第二个样式表再加一个权重。

    .hezi ul li{color:blue;}
    .hezi ul li .teshu{color:red;}
**2. 如果不能直接选中某个元素，样式是通过继承性影响的话，那么它的权重是0。**
**3. 如果大家的权重相同，那么就采用就近原则：谁的描述靠目标标签更近，就听谁的。**
**4. 如果描述的一样近，比如选择器权重，如果权重再一样重，谁写在后面听谁的。**

+ 选择上了，数权重，(id的数量，类的数量，标签的数量)。如果权重一样，谁写在后面听谁的。
+ 没有选择上，通过继承影响的，就近原则，谁描述的近听谁的。如果描述的一样近，比如选择器权重，如果权重再一样重，谁写在后面听谁的。

####CSS样式表的冲突的总结
1. 对于相同的选择器（比如同样都是类选择器），其样式表排序：行级样式 > 内嵌样式表 > 外部样式表（就近原则）
2. 对于相同类型的样式表（比如同样都是内部样式表），其选择器排序：ID选择器 > 类选择器 > 标签选择器
3. 外部样式表的ID选择器 > 内嵌样式表的标签选择器
总结：就近原则。ID选择器优先级最大。
4. !important; 权重无限大 (e.g.font-size:16px !important;) !important提升的是一个属性，而不是一个选择器, !important无法提升继承的权重，该是0还是0. !important也无法影响就近原则。（PS：做网站的时候，!important 尽量不要用。否则会让css写的很乱。）

#####class和id的区别

class用于css的，id用于js的。

1）class页面上可以重复。id页面上唯一，不能重复。 2）一个标签可以有多个class，用空格隔开。但是id只能有id。

###盒模型详解

**标准盒子模型**
标准W3C盒子模型范围包括 margin padding border content,且content不包含其他部分

**IE盒子模型**
IE盒子模型范围也包括 margin padding border content,不同的是content包含了border和padding。IE盒子模型中，width 和 height 指的是内容区域+border+padding的宽度和高度。

比较稳定的border-style就几个：*solid、dashed、dotted*。

---

###浮动

####行内元素和块级元素的区别：（非常重要）

行内元素：

+ 与其他行内元素并排；
+ 不能设置宽、高。默认的宽度，就是文字的宽度。

块级元素：

+ 霸占一行，不能与其他任何元素并列；
+ 能接受宽、高。如果不设置宽度，那么宽度将默认变为父亲的100%。

从HTML的角度来讲，标签分为：

+ 文本级标签：p、span、a、b、i、u、em。
+ 容器级标签：div、h系列、li、dt、dd。
*PS：为甚么说p是文本级标签呢？因为p里面只能放文字&图片&表单元素，p里面不能放h和ul，p里面也不能放p。*

我们可以通过display属性将块级元素和行内元素进行相互转换。display即“显示模式”。

标准流里面的限制非常多，导致很多页面效果无法实现。如果我们现在就要并排、并且就要设置宽高，办法是：**脱离标准流！**

css中一共有三种手段，使一个元素脱离标准文档流：

（1）浮动
（2）绝对定位
（3）固定定位

**一旦一个元素浮动了，那么，将能够并排了，并且能够设置宽高了。无论它原来是个div还是个span。** 所有标签，浮动之后，已经不区分行内、块级了。

标准流中的文字不会被浮动的盒子遮挡住。

**关于浮动我们要强调一点，浮动这个东西，为避免混乱，我们在初期一定要遵循一个原则：永远不是一个东西单独浮动，浮动都是一起浮动，要浮动，大家都浮动。**

###浮动的清除

    这里所说的清除浮动，指的是清除浮动与浮动之间的影响。

####方法一：给浮动元素的祖先元素加高度

造成盒子塌陷的根本原因是：li的父亲div没有设置高度，导致这两个div的高度均为0px（我们可以通过网页的审查元素进行查看）。div的高度为零，导致不能给自己浮动的孩子，撑起一个容器。
撑不起一个容器，导致自己的孩子没办法在自己的内部进行正确的浮动。
但是就算给这个div设置高度，可如果div自己的高度小于孩子的高度，也会出现不正常的现象

如果一个元素要浮动，那么它的**祖先元素一定要有高度**。

**有高度的盒子，才能关住浮动。（记住这句过来人的经验之语）**

只要浮动在一个有高度的盒子中，那么这个浮动就不会影响后面的浮动元素。所以就是清除浮动带来的影响了。

####方法二：clear:both;
clear就是清除，both指的是左浮动、右浮动都要清除。clear:both的意思就是：不允许左侧和右侧有浮动对象。

这种方法有一个非常大的、**致命的问题，它所在的标签，margin属性失效了**。读者可以试试看。

margin失效的本质原因是：上图中的box1和box2，高度为零。

####方法三：隔墙法
设置个div：
    <div style="clear:both;height:15px;"></div>

内墙法，在div内设置个div,<div style="clear:both;"></div>
为了讲内墙法，我们先记住一句重要的话：**一个父亲是不能被浮动的儿子撑出高度的。**

与外墙法相比，内墙法的优势（本质区别）在于：内墙法可以给它所在的家撑出宽度（让box1有高）。即：box1的高度可以自适应内容。

而外墙法，虽然一道墙可以把两个div隔开，但是这两个div没有高，也就是说，无法wrap_content。

####清除浮动方法4：overflow:hidden;

overflow:hidden;的本意是清除溢出到盒子外面的文字。但是，前端开发工程师发现了，它能做偏方。如下：

一个父亲不能被自己浮动的儿子，撑出高度。但是，只要给父亲加上overflow:hidden; 那么，父亲就能被儿子撑出高了。这是一个偏方。

---

###浏览器兼容问题

**兼容性1（微型盒子）**

**兼容性的第一条：**IE6不支持小于12px的盒子，任何小于12px的盒子，在IE6中看都大。即：IE 6不支持微型盒子。

我们现在介绍一下浏览器hack。hack就是“黑客”，就是使用浏览器提供的后门，针对某一种浏览器做兼容。

IE6留了一个后门：只要给css属性之前，加上下划线，这个属性就是IE6的专有属性。

比如说，我们给背景颜色这个属性加上下划线，就变成了_background-color: green;

于是乎，为了解决微型盒子（即height小于12px）的问题，正确写法：（注意不要忘记下划线）

    height: 10px;
    _font-size:0;

**兼容性2**

**兼容性的第二条：**IE6不支持用overflow:hidden;来清除浮动。

解决办法，以毒攻毒。追加一条：

    _zoom:1;
    完整写法：

    overflow: hidden;
    _zoom:1;

实际上，_zoom:1;能够触发浏览器hasLayout机制。这个机制，不要深究了，因为只有IE6有。我们只需要让IE6好用，具体的实现机制，可以自行查阅。

需要强调的是，overflow:hidden;的本意，就是让溢出盒子的border的内容隐藏，这个功能是IE6兼容的。不兼容的是overflow:hidden;清除浮动的时候。

**margin这个属性，本质上描述的是兄弟和兄弟之间的距离； 最好不要用这个marign表达父子之间的距离。**
所以，如果要表达父子之间的距离，我们一定要善于使用父亲的padding，而不是儿子的margin。

####关于margin的IE6兼容问题
**IE6的双倍margin的bug：**当出现连续浮动的元素，携带与浮动方向相同的margin时，队首的元素，会双倍marign。

解决方案：

（1）使浮动的方向和margin的方向，相反。

所以，你就会发现，我们特别喜欢，浮动的方向和margin的方向相反。并且，前端开发工程师，把这个当做习惯了。

	float: left;
	margin-right: 40px;
（2）使用hack：（没必要，别惯着这个IE6）

单独给队首的元素，写一个一半的margin：

    <li class="no1"></li>
    ul li.no1{
    	_margin-left:20px;
    }
PS：双倍margin的问题，面试经常问哦。

**IE6的3px bug**
解决办法：不用管，因为根本就不允许用儿子踹父亲（即描述父子之间的距离，请用padding，而不是margin）。所以，如果你出现了3px bug，说明你的代码不标准。

---

###定位属性

####1.相对定位 position:relative;
**不会脱离标准流**，位置不会被人挤走
**用途：**
1. 微调元素
2. 做绝对定位的参考，子绝父相

####2.绝对定位 position:absolute;
**会脱离标准流**，因此不会区分行内、块级元素，不需要display:block;就可以设置宽、高。

**绝对定位的参考点（重要）**
如果只有一个元素设置了absolute，那么这个参考点就是首屏（打开浏览器看到的首个页面，将会参考这个页面定位）

如果有个盒子包裹着且设置了relative，子绝父相，就以这个盒子作为参考点
以下几点需要注意。

（1） 该元素参考最近的已经设置position:relative;相对定位的祖先元素定位，不一定是父级元素，可能是爷爷级

（2）不一定是相对定位，任何定位，都可以作为儿子的参考点：

子绝父绝、**子绝父相**、子绝父固，都是可以给儿子定位的。但是在工程上，如果子绝、父绝，没有一个盒子在标准流里面了，所以页面就不稳固，没有任何实战用途。

（3）绝对定位的元素，无视参考元素那个盒子的padding，参考点是盒子border内侧

**让绝对定位中的盒子在父亲里居中**

我们知道，如果想让一个标准流中的盒子在父亲里居中（水平方向看），可以将其设置margin: 0 auto属性。

可如果盒子是绝对定位的，此时已经脱标了，如果还想让其居中（位于父亲的正中间），可以这样做：
   left:50%; margin-left:负的宽度的一半


####3.固定定位 position:fixed;

####页面结构

1. header 头部，放导航栏，是个通栏
2. banxin 版心，看情况，有时候是1000px
3. banner 轮播图，加上版心类名
4. content 内容主体，加上版心的类名

我们给logo写布局的时候，错误写法：

    <div class="logo">
        <img src="images/logo.png " alt="">
    </div>
然后设置样式，但这样子只能达到视觉效果，搜索引擎无法搜索到图片，不利于SEO

正确写法：将超链接作为logo的布局，可以放文字（文字可以被SEO）

			<h1 class="logo">
				<a href="#">
					博雅互动-世界上最好的游戏公司
				</a>
			</h1>
然后设置样式：

		.header .logo{
			float: left;
			padding-left: 12px;
			margin-right: 39px;
			width: 174px;
			height: 58px;
		}
		.header .logo a{
			display: block;
			width: 174px;
			height: 58px;
			background:url(images/logo.png) no-repeat;
			text-indent: -999em;
		}
通过设置 **text-indent: -999em;** 把文字赶走了，是**SEO的一个重要技巧**

**CSS3 对盒模型做出了新的定义，即允许开发人员指定盒子宽度和高度的计算方式**

CSS默认是外加方式：

    box-sizing: content-box;
此时设置的width和height是内容区域的宽高，盒子实际宽度=设置的width+padding+margin+border
此时改变padding和border的大小，也不会改变内容的宽高，而是盒子的总宽高发生变化

内减模式

    box-sizing: border-box;
此时设置的width和height是盒子的总宽高，盒子的实际宽度= 设置的width。此时改变padding和border的大小，会改变内容的宽高，盒子的总宽度不变。

处理兼容性问题的常见方法：为属性添加**私有前缀**。

如此方法不能解决，应尽量避免使用，无需刻意去处理CSS3的兼容性问题。

**边框阴影：box-shadow 属性**

格式举例：

	box-shadow: 水平偏移 垂直偏移 模糊程度 阴影大小 阴影颜色

	box-shadow: 15px 21px 48px -2px #666;

参数解释：

    水平偏移：正值向右 负值向左。

    垂直偏移：正值向下 负值向上。

    模糊程度：不能为负值。

注意：设置边框阴影不会改变盒子的大小，即不会影响其兄弟元素的布局。

我们还可以设置多重边框阴影，实现更好的效果，增强立体感。

我们知道，如果想让一个标准流中的盒子在父亲里居中（水平方向看），可以将其设置margin: 0 auto属性。

可如果盒子是绝对定位的，此时已经脱标了，如果还想让其居中（位于父亲的正中间），可以这样做：

	div {
		width: 600px;
		height: 60px;
		position: absolute;  绝对定位的盒子
		left: 50%;           首先，让左边线居中
		top: 0;
		margin-left: -300px;  然后，向左移动宽度（600px）的一半
	}

如上方代码所示，我们先让这个宽度为600px的盒子，左边线居中，然后向左移动宽度（600px）的一半，就达到效果了。

现在，我们还可以利用偏移 translate 来做，这也是比较推荐的写法：

	div {
	    width: 600px;
	    height: 60px;
	    background-color: red;
	    position: absolute;       绝对定位的盒子
	    left: 50%;               首先，让左边线居中
	    top: 0;
	    transform: translate(-50%);    然后，利用translate，往左走自己宽度的一半【推荐写法】
	}

---

####弹性布局： display:flex;
1. flex 布局的子元素不会脱离文档流

2. flex 是一种现代的布局方式，是 W3C 第一次提供真正用于布局的 CSS 规范。

*flex 唯一的缺点就在于，它不支持低版本的 IE 浏览器。*

**弹性盒子**：指的是使用 display:flex 或 display:inline-flex 声明的父容器。

**子元素/弹性元素**：指的是父容器里面的子元素们（父容器被声明为 flex 盒子的情况下）。

![主轴和侧轴](images/cross.png)

**声明定义**：display:flex;和 display:inline-flex;
**设置子元素排列方向**： **flex-direction:**

**属性：**
+ row（默认从左到右） 
+ column（从上到下）
+ row-reverse （从右到左）
+ column-reverse（从下到上）

**flex-wrap**（控制子元素溢出时的换行处理）

**justify-content**（控制子元素在主轴方向的排列顺序）
+ flex-start（从主轴的起点对齐）
+ flex-end（从主轴的终点对齐）
+ center（居中对齐）
+ space-around（在父盒子里平分）
+ space-between（两端对齐 平分）

**align-items**(设置子元素在侧轴上的对齐方式。)
+ flex-start（从侧轴的开始方向对齐）
+ flex-end（从侧轴结束的方向对齐）
+ baseline（基线）
+ center（中间对齐）
+ stretch（拉伸）
