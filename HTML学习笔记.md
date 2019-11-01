HTML学习笔记
=

来源自[ Github/qianguyihao](https://github.com/qianguyihao/Web/tree/master/01-html)
### 记录一些自己不熟悉的地方

+ **HTML对换行不敏感，对tab不敏感**
+ **空白折叠现象** HTML中所有的文字之间，如果有空格、换行、tab都将被折叠为一个空格显示。markdown也是如此。
+ 标签要严格封闭

面试题：
  问：网页的head标签里面，表示的是页面的配置，有什么配置？
  答：字符集、关键词、页面描述、页面标题、IE适配、视口、iphone小图标等等

+     <title>:指定整个网页的标题，在浏览器最上方显示。
+     <base>：为页面上的所有链接规标题栏显示的内容定默认地址或默认目标。
+     <meta>：提供有关页面的基本信息
+     <body>：用于定义HTML文档所要显示的内容，也称为主体标签。我们所写的代码必须放在此标签內。
+     <link>：定义文档与外部资源的关系。
有一个meta标签是需要记住的：

    <meta http-equiv="refresh" content="3;http://www.baidu.com">  //这个标签的意思是说，3秒之后，自动跳转到百度页面。


**我们为什么可以查看网页的源代码呢？**
因为这个打开的网页已经存到我的临时文件夹里了，临时文件夹里的html是纯文本文件，纯文本文件自然剋以查看网页的源代码了。

**字符集在这里看:**

    <meta charset="utf-8">

    <meta http-equiv="Content-Type" content="text/html;charset=UTF-8">

浏览器通过meta来看网页使用什么字符集，如果meta写的和声明的不一样，浏览器就会乱码。

**视口viewport:**

    <meta name="viewport" content="width=device-width, initial-scale=1.0">

*width=device-width ：表示视口宽度等于屏幕宽度。*

***meta除了可以设置字符集，还可以设置关键字和页面描述***

**关键词 keywords:**

    <meta name="Keywords" content="网易,邮箱,游戏,新闻,体育,娱乐,女性,亚运,论坛,短信" />

**页面描述 Description:**

    <meta name="Description" content="网易是中国领先的互联网技术公司，为用户提供体育等30多个内容频道，及博客、视频、论坛等互动交流，网聚人的力量。" />
*只要设置Description页面描述，那么百度搜索结果，就能够显示这些语句，这个技术叫做SEO（search engine optimization，搜索引擎优化）*。

p标签： 段落，是英语paragraph“段落”缩写。
HTML标签是分等级的，HTML将所有的标签分为两种：

**文本级标签：** p、span、a、b、i、u、em。文本级标签里只能放文字、图片、表单元素。（a标签里不能放a和input）

**容器级标签：** div、h系列、li、dt、dd。容器级标签里可以放置任何东西。

从学习p的第一天开始，就要死死记住：p标签是一个文本级标签，p里面只能放文字、图片、表单元素。其他的一律不能放。
**错误写法：**

    <p>
        我是一个小段落
		<h1>我是一级标题</h1>
    </p>

**div的语义是division“分割”； span的语义就是span“范围、跨度”。**

#### 一些常用的转义字符

+ &nbsp;：空格 （non-breaking spacing，不断打空格）
+ &lt;：小于号（less than）
+ &gt;：大于号（greater than）
+ &amp;：符号&
+ &quot;：双引号
+ &apos;：单引号
+ &copy;：版权©
+ &trade;：商标™
+ &#32464;：文字绐。其实，#32464是汉字绐的unicode编码。

   0<sup>2上标   H<sub>2下标

**a标签**

    <a href="mailto:smyhvae@163.com">点击进入我的邮箱</a>
    <a href="a.html#name1">回到锚点name1</a>

**img标签**
+    能够插入的图片类型是：jpg(jpeg)、gif、png、bmp。
+    不能往网页中插入的图片格式是：psd、ai
align：指图片的水平对齐方式，属性值可以是：left、center、right

**ul li标签**的属性的type属性，disc(实心原点，默认)，square(实心方点)，circle(空心圆)。 效果如下：
<ul type="circle">
<li type="disc">实心圆点</li>
<li type="square">实心方点</li>
<li>空心圆点</li>
</ul>

**定义列表<dl>**

*定义列表的作用非常大。*

<dl>英文单词：definition list，没有属性。dl的子元素只能是dt和dd。

    <dt>：definition title 列表的标题，这个标签是必须的
    <dd>：definition description 列表的列表项，如果不需要它，可以不加

备注：dt、dd只能在dl里面；dl里面只能有dt、dd

网页中99.9999%需要换行的时候，是因为另起了一个段落，所以要用p，而不要用<br />。不到万不得已，不要用br标签。

标准的div+css页面，只会用到种类很少的标签：

    div  p  h1  span   a   img   ul   ol    dl    input

---

什么是 HTML5 ？
-
HTML5并不仅仅只是做为HTML标记语言的一个最新版本，更重要的是它**制定了Web应用开发的一系列标准，成为第一个将Web做为应用开发平台的HTML语言。**

HTML5不等于 HTML next version。HTML5 包含： HTML的升级版、CSS的升级版、JavaScript API的升级版

传统的做法中，我们通过增加类名如class="header"、class="footer"，使HTML页面具有语义性，但是不具有通用性。

HTML5 则是通过新增语义标签的形式来解决这个问题，例如
    
    <header></header>、<footer></footer>等，这样就可以使其具有通用性。
    HTML5通过<audio>标签来解决音频播放的问题。

使用举例：

	<audio src="music/yinyue.mp3" autoplay controls> </audio>
#### 解决音频问题：为了做到多浏览器支持，可以采取以下兼容性写法：

     <!--推荐的兼容写法：-->
     <audio controls loop>
         <source src="music/yinyue.mp3"/>
         <source src="music/yinyue.ogg"/>
         <source src="music/yinyue.wav"/>
         抱歉，你的浏览器暂不支持此音频格式
     </audio>

#### HTML5通过**video**标签来解决视频播放的问题。
使用举例：

	<video src="video/movie.mp4" controls autoplay></video>
兼容性写法：

    <video controls autoplay>
        <source src="video/movie.mp4"/>
        <source src="video/movie.ogg"/>
        <source src="video/movie.webm"/>
        抱歉，不支持此视频
    </video>

---

#### 拖拽元素的事件监听：（应用于拖拽元素）

    ondragstart当拖拽开始时调用

    ondragleave	当鼠标离开拖拽元素时调用

    ondragend	当拖拽结束时调用

    ondrag 整个拖拽过程都会调用

    ondrop 拖拽到目标后放下会调用

    two.ondragover = function(e){
        e.preventDefault();
     }//阻止默认拖拽事件，注意要有这行代码才能实现后面的ondrop方法
---

#### 历史
在HTML5中可以通过 window.history 操作访问历史状态，让一个页面可以有多个历史状态
- window.history.forward(); // 前进
- window.history.back(); // 后退
- window.history.go(); // 刷新
- 通过JS可以加入一个访问状态
- history.pushState; //放入历史中的状态数据, 设置title(现在浏览器不支持改变历史状态)

#### 地理位置 HTML5 Geolocation(地理位置定位) 规范提供了一套保护用户隐私的机制。必须先得到用户明确许可，才能获取用户的位置信息。



+ navigator.getCurrentPosition(successCallback, errorCallback, options) 获取当前地理信息

+ navigator.watchPosition(successCallback, errorCallback, options) 重复获取当前地理信息

1、当成功获取地理信息后，会调用**succssCallback**，并返回一个包含位置信息的对象position：（Coords即坐标）

+ position.coords.latitude纬度

+ position.coords.longitude经度

2、当获取地理信息失败后，会调用errorCallback，并返回错误信息error。

3、可选参数 options 对象可以调整位置信息数据收集方式

---

#### 全屏
HTML5规范允许用户自定义网页上**任一元素**全屏显示

	requestFullscreen()   //让元素开启全屏显示

	cancleFullscreen()    //让元素关闭全屏显示
为考虑兼容性问题，不同的浏览器需要在此基础之上，添加私有前缀，比如：（注意 screen 是大写）

	webkitRequestFullScreen
	webkitCancleFullScreen

	mozRequestFullScreen
	mozCancleFullScreen

**检测当前是否处于全屏状态**

    document.fullScreen
不同浏览器需要加私有前缀，比如：

     document.webkitIsFullScreen

     document.mozFullScreen

**全屏的伪类**

+ :full-screen .box {}

+ :-webkit-full-screen {}

+ :moz-full-screen {}

---

#### 有时候我们需要在本地存储大量数据，H5 中有两种存储的方式
1. window.sessionStorage 会话存储 ：
+ 保存在本地中
+ **生命周期**为关闭浏览器窗口。就是关闭窗口会销毁数据。
+ 在同一窗口下可以共享
  
2. window.localStorage 本地存储 ：
+ 有可能保存在浏览器内存里，有可能在硬盘里。
+ 永久生效，除非手动删除（比如清理垃圾的时候）。
+ 可以多窗口共享。
Web 存储的特性
（1）设置、读取方便。
（2）容量较大，sessionStorage 约5M、localStorage 约20M。
（3）只能存储字符串，可以将对象 JSON.stringify() 编码后存储。

**常见 API**

设置存储内容：

	setItem(key, value);

PS：可以新增一个 item，也可以更新一个 item。

读取存储内容：

	getItem(key);

根据键，删除存储内容：

	removeItem(key);

清空所有存储内容：

	clear();

根据索引值来获取存储内容：

	key(n);

    
