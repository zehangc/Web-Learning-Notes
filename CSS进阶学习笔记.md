# CSS进阶学习笔记

学习教程资源来自:[千古壹号](https://github.com/qianguyihao/Web)

先来复习一些HTML中的元素：

    <base href="/">
**base标签** 为页面上的所有链接规定默认地址或默认目标。

    包括 <a>、<img>、<link>、<form> 标签中的 URL。
通常情况下，浏览器会从当前文档的 URL 中提取相应的元素来填写**相对URL**中的空白。

使用 base 标签可以改变这一点。浏览器随后将**不再使用当前文档的URL**，而**使用指定的基本URL**来解析所有的相对 URL。

**案例：**

    <html>
        <head>
            <base href="http://www.w3school.com.cn/i/"  />
            <base target="_blank" />
        </head>

        <body>
            <img src="eg_smile.gif" /><br />
        </body>
    </html>

**section标签** 定义文档中的节（section、区段）。比如章节、页眉、页脚或文档中的其他部分。

**option** 元素定义下拉列表 **select** 中的一个选项（一个条目）。

**案例：**

    <html>
        <body>
            <select>
                <option>Volvo</option>
                <option>Saab</option>
                <option>Mercedes</option>
                <option>Audi</option>
            </select>
        </body>
    </html>

**aside 标签** 是HTML5的新标签，定义其所处内容之外的内容，aside 的内容应该与附近的内容相关。

 *提示：* aside 的内容可用作文章的侧栏。

 **inline-block**： *比如form表单元素。*对外的表现是行内元素（不会独占一行），对内的表现是块级元素（可以设置宽高），可以当作盒子使用。

 在 HTML5 中 a > div 是合法的， div > a > div是不合法的 ；但是在 html 4.0.1 中， a > div 仍然是不合法的。

 #### CSS Reset

将所有默认样式设置清零。

 **方案一：**

**CSS Tools: Reset CSS**。链接：[https://meyerweb.com/eric/tools/css/reset/](https://meyerweb.com/eric/tools/css/reset/)
可以直接复制下面代码使用:

    html, body, div, span, applet, object, iframe,
    h1, h2, h3, h4, h5, h6, p, blockquote, pre,
    a, abbr, acronym, address, big, cite, code,
    del, dfn, em, img, ins, kbd, q, s, samp,
    small, strike, strong, sub, sup, tt, var,
    b, u, i, center,
    dl, dt, dd, ol, ul, li,
    fieldset, form, label, legend,
    table, caption, tbody, tfoot, thead, tr, th, td,
    article, aside, canvas, details, embed, 
    figure, figcaption, footer, header, hgroup, 
    menu, nav, output, ruby, section, summary,
    time, mark, audio, video {
        margin: 0;
        padding: 0;
        border: 0;
        font-size: 100%;
        font: inherit;
        vertical-align: baseline;
    }
    /* HTML5 display-role reset for older browsers */
    article, aside, details, figcaption, figure, 
    footer, header, hgroup, menu, nav, section {
        display: block;
    }
    body {
        line-height: 1;
    }
    ol, ul {
        list-style: none;
    }
    blockquote, q {
        quotes: none;
    }
    blockquote:before, blockquote:after,
    q:before, q:after {
        content: '';
        content: none;
    }
    table {
        border-collapse: collapse;
        border-spacing: 0;
    }
**方案二：**
使用雅虎的：[https://yuilibrary.com/yui/docs/cssreset/](https://yuilibrary.com/yui/docs/cssreset/)
可以直接用CDN引入：

    <link rel="stylesheet" type="text/css" href="http://yui.yahooapis.com/3.18.1/build/cssreset/cssreset-min.css">

**方案三：**

    *{
        margin: 0;
        padding: 0;
    }
这个方法比较简洁，但是可能导致css选择器的性能问题，因此会有争议。

#### 多字体 fallback

多字体 fallback 机制：当指定的字体找不到（或者某些文字不支持这个字体）时，那就接着往后找。比如：

    .div1{
        font-family: "PingFang SC", "Microsoft Yahei", monospace;
    }
上方 CSS 代码的意思是：让 div1 在 Mac & iOS 平台用苹方字体，在 Win 平台用微软雅黑字体，如果这两个字体都没有，就随便找一个等宽的字体进行渲染。

#### font-weight
font-weight: 400相当于normal，bold相当于700，我们在设置字体大小时，会发现设置为400 500 600 的时候字体大小不变化，之所以没有看到任何变化，是因为所使用的字体不支持。
例如微软雅黑只支持400和700两种粗细。苹果的苹方字体能支持100到900的各种粗细。

---
#### 文字换行

+ overflow-wrap: normal;表示在正常的单词结束处换行
+ overflow-wrap: break-word;表示如果行内没有多余的地方容纳该单词到结尾，则那些正常的不能被分割的单词会被强制分割换行
+ white-space:nowrap;将文本放在一行中,不够放也不换行

#### CSS Hack

CSS hack 是一种不合法但可以生效的写法，是通过在CSS样式中加入一些特殊的符号，让不同的浏览器识别不同的符号（什么样的浏览器识别什么样的符号是有标准的，CSS hack就是让你记住这个标准），以达到应用不同的CSS样式的目的
##### 简单地讲，css hack指各版本及各品牌浏览器之间对CSS解释后出现网页内容的误差(比如我们常说错位)的处理。由于各浏览器的内核不同，所以会造成一些误差就像JS一样，一个JS网页特效，在微软IE6、IE7、IE8浏览器有效果，但可能在火狐（Mozilla Firefox）谷歌浏览器无效，这样就叫做JS hack ，所以我们对于CSS来说他们来解决各浏览器对CSS解释不同所采取的区别不同浏览器制作不同的CSS样式的设置来解决这些问题就叫作CSS Hack。

+ 作用:CSS hack用来解决有些css属性在不同浏览器中显示的效果不一样的问题 可以用来解决一些浏览器的兼容性问题
+ 缺点：难理解、难维护、易失效（比如浏览器升级后，hack可能会失效）。
+ 替代方案：特性检测。
+ 替代方案：针对性加 class

#### 3.浏览器识别字符标准对应表

##### 从上图可以分析出以下几种情况：

    1.大部分特殊字符IE浏览器支持，其他主流浏览器    firefox，chrome，opera，safari不支持 (opera可   识别除外)。
    2.\9    ：所有IE浏览器都支持
    3._和-  ：仅IE6支持
    4.*     ：IE6、E7支持
    5.\0    ：IE8、IE9支持，opera部分支持
    6.\9\0  ：IE8部分支持、IE9支持
    7.\0\9  ：IE8、IE9支持

#### CSS 效果
我们可以利用 CSS 实现各种效果，常见的效果属性有：
+ box-shadow：盒子的阴影
+ text-shadow：文本的阴影
+ border-radius
+ background
+ clip-path


#### 常见的布局方法

1、**table 表格布局**：早期使用的布局，如今用得很少。
2、**float 浮动 + margin**：为了兼容低版本的IE浏览器，很多网站（比如腾讯新闻、网易新闻、淘宝等）都会采用 float 布局。(是 CSS 中一种比较麻烦的属性，涉及到 BFC 和清除浮动（面试的重点）。)
3、**inline-block 布局**：对外的表现是行内元素（不会独占一行），对内的表现是块级元素（可以设置宽高）。
4、**flex 布局**：为布局而生，非常灵活，是最为推荐的布局写法。
flex 布局不支持 IE9 及以下的版本。如果你的页面不需要处理 IE浏览器的兼容性问题，则可以放心大胆地使用 flex 布局。
flex 是一种现代的布局方式，是 W3C 第一次提供真正用于布局的 CSS 规范。

**float 属性的特点**
+ 元素浮动
+ **脱离文档流，但不脱离文本流**，这是float属性的作用，float本身是用来做图片文本混合排版的，能做出文字环绕的效果。
+ float会让自身形成块（BFC）
+ 从父级的布局中“消失”
+ 造成父级元素的高度塌陷：父级元素撑开 div1 之后（父级元素里没有其他元素的情况下），如果设置 div1 为 float 之后，，会让父级元素的高度变为0。

文本和文本之间，本身就会存在间隙。因此会导致display:inline-block;产生间隙。

为了去掉这个间隙，可以有几种解决办法：

+ 办法1：设置父元素container的字体大小为0，即font-size: 0，然后设置子元素 div1、div2的字体font-size: 12px。

+ 办法2：在写法上，去掉div1和div2之间的换行。改为：

        <div class="div1">div1的inline-block 属性</div><div class="div2">div2的inline-block 属性</div>

#### 设置盒子的半透明

方式一：pacity: 0.4。优点是方便。缺点是：里面的内容也会半透明

方式二：css3的技术来解决半透明。如下：

    background: rgba(0,0,0,0.3);

    background: rgba(0,0,0,.3);

备注：a指的是alpha透明度。

#### 隐藏盒子的几种方式
+ overflow：hidden;   //隐藏盒子超出的部分
+ display: none;	  隐藏盒子，而且不占位置(用的最多)
+ visibility: hidden;   //隐藏盒子，占位置。
  visibility: visible;   //让盒子重新显示
+ pacity: 0;       //设置盒子的透明度（不建议，因为内容也会半透明），占位置
+ Position/top/left/...-999px   //把盒子移得远远的，占位置。
+ margin-left: 1000px;//同理

行内元素尽量不要设置font属性。对于行内元素而言，如果它和父亲都设置了行高，就不要去给自己设置font属性了。要么就，不要同时设置行高

#### 背景图不能撑开盒子

高和行高都可以城开盒子，但背景图不能撑开盒子。

#### 超链接 <code>a</code> 的href跳转

一个空白的超链接如下：

    <a href=""></a>

当点击超链接时，由于 href 的属性值的不同，可以产生很多种情况：

	href=""                    //刷新页面

	href="#"                   //跳转到当前页面的顶部（不会刷新）

	href="javascript:void(0)"  // 什么都不做

	href="javascript:;"        // 什么都不做

---

### 居中

*分为标准流和脱离标准流两种情况：*

#### 标准流：
1. 行内元素水平居中：

    text-align:center;
2. 单行文本高度居中：
    设置行高line-height = 高度height

3. 块级元素水平居中：

    //方式一
    margin: auto;
    //方式二
    margin: 0 auto;

根据规范：margin-top: auto; 和margin-bottom: auto;的计算值为0
所以margin: 0 auto;效果和margin: auto;一样

#### 脱离标准流

##### 垂直居中/水平居中
1. 元素的高度已知:

    position: absolute;
    width: 200px;
    height: 100px;
    top: 50%;
    left: 50%;
    margin-left: -100px;
    margin-top: -50px;

2. 元素的高度未知: 

    .parent{
        display: table;
    }
    .child{
        display: table-cell;
        vertical-align: middle;
        height: 200px;
        width: 200px;
    }

3. 水平居中: 绝对定位 + margin: auto;

    position: absolute;
    top:0;bottom:0;left:0;right:0;
    margin:auto;

4. 水平居中+垂直居中: 绝对定位 + top:50%; left: 50%; + transform: translate(-50%,-50%);

    position: absolute;
    top:50%;
    left: 50%;
    transform: translate(-50%,-50%);

5. flex布局

    display: flex;/* flex布局 */
    display: -webkit-flex;/* Safari */
    justify-content: center;
    align-items: center;
