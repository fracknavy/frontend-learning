### 1.0 移动端基础

常见移动端屏幕尺寸

移动端调试方法
●Chrome DevTools（谷歌浏览器）的模拟手机调试
●搭建本地web服务器，手机和服务器一个局域网内，通过手机访问服务器
●使用外网服务器，直接P或域名访问



#### 视口

视口（viewport）就是浏览器显示页面内容的屏幕区域视口可以分为布局视口、视觉视口和理想视口

**布局视口 layout viewport**

一般移动设备的浏览器都默认设置了一个布局视口，用于解决早期的PC端页面在手机上显示的问题。iOS,Android基本都将这个视口分辨率设置为980px所以PC上的网页大多都能在手机上呈现，只不过元素看上去很小，一般默认可以通过手动缩放网页。

**视觉视口visual viewport**
字面意思，它是用户正在看到的网站的区域。注意：是网站的区域。
我们可以通过缩放去操作视觉视口，但不会影响布局视口，布局视口仍保持原来的宽度。

 **理想视口ideal viewport**

为了使网站在移动端有最理想的浏览和阅读宽度而设定
理想视口，对设备来讲，是最理想的视口尺寸
需要手动添写meta视口标签通知浏览器操作
meta视口标签的主要目的：布局视口的宽度应该与理想视口的宽度一致，简单理解就是设备有多宽，我们布局的视口就多宽
```
<meta name="viewport" content="width-device-width,user-scalable=no,
initial-scale=1.0,maximum-scale=1.0,minfmum-scale=1.0">
```
|属性|解释说明|
|-|-|
|width|宽度设置的是viewport宽度，可以设置device-width特殊值|
|initial-scale|初始缩放比，大于0的数字|
|maximum-scale|最大缩放比，大于0的数字|
|minimum-scale|最小缩放比，大于0的数字|
|user-scalable|用户是否可以缩放，yes或no（1或0）|

#### **标准的viewport设置**

视口宽度和设备保持一致，
视口的默认缩放比例1.0
不允许用户自行缩放
最大允许的缩放比例1.0
最小允许的缩放比例1.0



#### **物理像素&物理像素比**

●物理像素点指的是屏幕显示的最小颗粒，是物理真实存在的。这是厂商在出厂时就设置好了，比如苹果6\7\8是750*1334
●我们开发时候的1px不是一定等于1个物理像素的
●PC端页面，1个px等于1个物理像素的，但是移动端就不尽相同
●一个px的能显示的物理像素点的个数，称为物理像素比或屏幕像素比

不一样的原因

●PC端和早前的手机屏幕/普通手机屏幕：1CSS像素=1物理像素的
●Retina（视网膜屏幕）是一种显示技术，可以将把更多的物理像素点压缩至一块屏幕里，从而达到更高的分辨率，并提高屏幕显示的细腻程度。

对于一张50px*50px的图片,在手机Retina屏中打开，按照刚才的物理像素比会放大倍数，这样会造成图片模糊
在标准的viewport设置中，使用倍图来提高图片质量，解决在高清设备中的模糊问题
背景图片注意缩放问题

```
img{
	/*原始图片100*100px*/
	width: 50px;
	height: 50px;
}
.box(
	/*原始图片100*100px*/
	background-size:50px 50px;
}
```



#### **背景缩放**

**background-size**

background-size属性规定背景图像的尺寸

```
background-size：背景图片宽度 背景图片高度;
```

单位：长度|百分比|cover |contain;
cover把背景图像扩展至足够大，以使背景图像完全覆盖背景区域。
contain把图像图像扩展至最大尺寸，以使其宽度和高度完全适应内容区域



#### 移动端选择

单独移动端页面（主流）
通常情况下，网址域名前面加m(mobile）可以打开移动端。通过判断设备，如果是移动设备打开，则跳到移动端页面。

响应式移动端页面

三星电子官网：www.samsung.com/cn/，通过判断屏幕宽度来改变样式，以适应不同终端。
缺点：制作麻烦，需要花很大精力去调兼容性问题



####  CSS初始化

normalize.css

移动端CSS初始化推荐使用normalize.css/
Normalize.css：保护了有价值的默认值
Normalize.css：修复了浏览器的bug
Normalize.css：是模块化的
Normalize.css：拥有详细的文档
官网地址：http://necolas.github.io/normalize.css/

```
/*Css3盒子模型*/
box-sizing: border-box;
-webkit-box-sizing: border-box;
/*点击高亮我们需要清除清除 设置为transparent完成透明*/
-webkit-tap-highlight-color: transparent;
/*在移动端浏览器默认的外观在iOs上加上这个属性才能给按钮和输入框自定义样式*/
-webkit-appearance: none;
/*禁用长按页面时的弹出菜单*/
img,a｛-webkit-touch-callout:none;}
```

### 2.0 移动端布局

1.单独制作移动端页面（主流）
流式布局（百分比布局）
flex弹性布局（强烈推荐）
less+rem+媒体查询布局
混合布局

2.响应式页面兼容移动端（其次）
媒体查询
bootstarp

#### 2.1 流式布局

流式布局，就是百分比布局，也称非固定像素布局。
通过盒子的宽度设置成百分比来根据屏幕的宽度来进行伸缩，不受固定像素的限制，内容向两侧填充。
流式布局方式是移动web开发使用的比较常见的布局方式。

max-width最大宽度（max-height 最大高度）
min-width 最小宽度（min-height 最小高度）

#### 2.2 flex布局

- flex 弹性布局,操作方便，布局极为简单，移动端应用很广泛
- PC端浏览器支持情况较差
- IE11或更低版本，不支持或仅部分支持

```
<style>
	dispaly:flex;
</style>
<div>
	<span></span>
	<span></span>
	<span></span>
	<span></span>
</div>

```

flex是flexibleBox的缩写，意为“弹性布局”，用来为盒状模型提供最大的灵活性，任何一个容器都可以指定为flex布局。
当我们为父盒子设为flex布局以后，子元素的float、clear和vertical-align属性将失效。
伸缩布局＝弹性布局＝伸缩盒布局＝弹性盒布局=flex布局

采用Flex布局的元素，称为Flex容器（flex container），简称”容器”。它的所有子元素自动成为容
器成员，称为Flex项目（flex item），简称”项目”。

- 体验中 div 就是 flex父容器。
- 体验中 span 就是子容器flex项目
- 子容器可以横向排列也可以纵向排列

**就是通过给父盒子添加flex属性，来控制子盒子的位置和排列方式**

```
flex-direction：设置主轴的方向
justify-content：设置主轴上的子元素排列方式
flex-wrap：设置子元素是否换行
align-content：设置侧轴上的子元素的排列方式（多行）
align-items：设置侧轴上的子元素排列方式（单行）
flex-flow：复合属性，相当于同时设置了 flex-direction和 flex-wrap
```

**1.主轴与侧轴**
在flex布局中，是分为主轴和侧轴两个方向，同样的叫法有：行和列、x轴和y轴
默认主轴方向就是x轴方向，水平向右
默认侧轴方向就是y轴方向，水平向下

**2.属性值**
**flex-direction**属性决定主轴的方向（即项目的排列方向）
注意：主轴和侧轴是会变化的，就看flex-direction设置谁为主轴，剩下的就是侧轴。而我们的子元素是跟着主轴来排列的

|属性值|说明|
|-|-|
|row|默认值从左到右|
|row-reverse|从右到左|
|column|从上到下|
|column-reverse|从下到上|

**justify-content**设置主轴上的子元素排列方式
justify-content属性定义了项目在主轴上的对齐方式
注意：使用这个属性之前一定要确定好主轴是哪个

|属性值|说明|
|--|--|
|flex-start|默认值从头部开始如果主轴是x轴，则从左到右|
|flex-end|从尾部开始排列|
|center|在主轴居中对齐（如果主轴是x轴则水平居中）|
|space-around|平分剩余空间|
|space-between|先两边贴边再平分剩余空间（重要）|

flex-wrap设置子元素是否换行,默认不换行



 **align-items**
设置侧轴上的子元素排列方式（单行）
该属性是控制子项在侧轴（默认是y轴）上的排列方式在子项为单项的时候使用

|属性值|说明|
|-|-|
|flex－start|从上到下|
|flex-end|从下到上|
|center|挤在一起居中（垂直居中）|
|stretch|拉伸（默认值）|


**align-content**
设置侧轴上的子元素的排列方式（多行）
设置子项在侧轴上的排列方式并且只能用于子项出现换行的情况（多行），在单行下是没有效果的。
|属性值|说明|
|-|-|
|flex-start|默认值在侧轴的头部开始排列|
|flex-end|在侧轴的尾部开始排列|
|center|在侧轴中间显示|
|space-around|子项在侧轴平分剩余空间|
|space-between|子项在侧轴先分布在两头，再平分剩余空间|
|stretch|设置子项元素高度平分父元素高度|

**flex-flow** 属性是 flex-direction和 flex-wrap 属性的复合属性

```
flex-flow:row wrap;
```
flex-direction：设置主轴的方向
justify-content：设置主轴上的子元素排列方式
flex-wrap：设置子元素是否换行
align-content：设置侧轴上的子元素的排列方式（多行）
align-items：设置侧轴上的子元素排列方式（单行）
flex-flow：复合属性，相当于同时设置了flex-direction和 flex-wrap

**flex属性**定义子项目分配剩余空间，用flex来表示占多少份数。

```
.item {
	flex:<nurber>;/* default 0 */
}
```



**align-self**属性允许单个项目有与其他项目不一样的对齐方式，可覆盖align-items属性。
默认值为auto，表示继承父元素的align-items属性，如果没有父元素，则等同于stretch。
```
span:nth-child(2) {
	/*设置自己在侧轴上的排列方式*/
	align-self: flex-end;
}
```

order属性定义项目的排列顺序
数值越小，排列越靠前，默认为0。
注意：和z-index不一样。

#### 2.3 rem布局

**rem 单位**

rem(root em)是一个相对单位，类似于em，em是父元素字体大小。
不同的是rem的基准是相必于html元素的字体大小。
比如，根元素（html）设置font-size=12px;非根元素设置width 2rem,则换成px表示就是24px。 

rem的优点就是可以通过修改html改变页面中元素的大小可以整体控制

##### **媒体查询**

媒体查询（Media Query）是CSS3新语法。

使用@media查询，可以针对不同的媒体类型定义不同的样式
@media可以针对不同的屏幕尺寸设置不同的样式
当你重置浏览器大小的过程中，页面也会根据浏览器的宽度和高度重新渲染页面
目前针对很多苹果手机、Android手机，平板等设备都用得到多媒体查询

```
@media mediatype and|not|only (media feature){
	CSS-Code;
}
```
用@media开头 注意@符号



**mediatype媒体类型**

| 值     | 解释说明                         |
| ------ | -------------------------------- |
| all    | 用于所有设备                     |
| print  | 用于打印机和打印预览             |
| screen | 用于电脑屏幕,平板电脑,智能手机等 |

**关键字**
关键字将媒体类型或多个媒体特性连接到一起做为媒体查询的条件。
and：可以将多个媒体特性连接到一起，相当于“且”的意思。
not：排除某个媒体类型，相当于“非”的意思，可以省略。
only：指定某个特定的媒体类型，可以省略。

**媒体特性**

| 值        | 解释说明                       |
| --------- | ------------------------------ |
| width     | 定义输出设备中可见区域的宽度   |
| min-width | 定义输出页面中最小可见区域宽度 |
| max-width | 定义输出页面中最大可见区域宽度 |

```
@media screen and(min-width:320px){
	html{
		font-size:50px;
	}
}
@media screen and(min-width:640px){
	html{
		font-size:100px;
	}
}
.top{
	height:1rem;
	font-size;0.5rem;
	backgroundcolor:blue;
}

```

**引入资源**

当样式比较繁多的时候，我们可以针对不同的媒体使用不同stylesheets（样式表）。
原理，就是直接在link中判断设备的尺寸，然后引角不同的css文件。

```
<link rel="stylesheet"href="style320.css"media="screen and (min-width:32epx）>
<link rel="stylesheet"href="style640.css"media="screen and (min-width: 64opx)">
```



##### **less基础**

维护css 的弊端

- CSS是一门非程序式语言，没有变量、函数、SCOPE（作用域）等概念。
- CSS需要书写大量看似没有逻辑的代码，CSS冗余度是比较高的。
- 不方便维护笈扩展，不利于复用。
- CSS没有很好的计算能力
- 非前端开发工程师来讲，往往会因为缺少CSS编写经验而很难写出组织良好且易于维护的CSS代码项目。

**less介绍**

Less（Leaner Style Sheets 的缩写）是一门CSS 扩展语言，也成为CSS预处理器。
做为CSS的一种形式的扩展，它并没有减少CSS的功能，而是在现有的CSS语法上，为CSS加入程序式语言的特性。它在CSS的语法基础之上，引入了变量，Mixin（混入），运算以及函数等功能，大大简化了CSS的编写，并且降低了CSS的维护成本，就像它的名称所说的那样，Less可以让我们用更少的代码做更多的事情。
Less中文网址：http://lesscss.cn/

**less变量**

变量是指没有固定的值，可以改变的。因为我们CSS中的一些颜色和数值等经常使用。
```
@变量名:值;
```
1.变量命名规范
```
必须有@为前缀
不能包含特殊字符
不能以数学开头
大小写敏感
```

**less编译**

vscode插件easyless会自动把less文件编译成css文件

**less嵌套**

```
.header{
	color:blue;
	a{
		color:red;
	}
}
```

如果遇见（交集|伪类|伪元素选择器）
●内层选择器的前面没有&符号，则它被解析为父选择器的后代；
●如果有&符号，它就被解析为父元素自身或父元素的伪类。

**less运算**

```
@border:5px + 5;
div{
	height:200px - 50;
	width:200px * 2;
	border:@border solid red;
}
```

1.我们运算符的左右两侧必须敲一个空格隔开, 除法运算必须加括号
2.两个数参与运算如果只有一个数有单位，则最后的结果就以这个单位为准
3.两个数参与运算，如果2个数都有单位，而且不一样的单位最后的结果以第一个单位为准

##### rem适配方案

1: less+媒体查询+rem

2: flexible.js+rem

**动态设置html 标签font-size大小**
```
假设设计稿是750px
假设我们把整个屏幕划分为15等份（划分标准不一可以是20份也可以是10等份）
每一份作为html字体大小，这里就是50px
那么在320px设备的时候，字体大小为320/15就是21.33px
用我们页面元素的大小除以不同的htm字体大小会发现他们比例还是相同的
比如我们以750为标准设计稿
一个100*100像素的页面元素在 750屏幕下，就是 100/50 转换为rem 是 2rem*2 rem 比例是 1比1
320屏幕下，html 字体大小为21.33则 2rem=42.66px此时宽和高都是 42.66但是宽和高的比例还是1比1
但是已经能实现不同屏幕下页面元素盒子等比例缩放的效果
```

**元素大小取值方法**
最后的公式：页面元素的rem值=页面元素值（px）/（屏幕宽度／划分的份数）
屏幕宽度/划分的份数就是 html font-size的大小
或者：页面元素的rem值=页面元素值（px）/html font-size字体大小

##### flexible.js

github地址：https://github.com/amfe/lib-flexible

```
注:由于viewport单位得到众多浏览器的兼容，lib-flexible这个过渡方案已经可以放弃使用，不管是现在的版本还是以前的版本，都存有一定的问题。建议大家开始使用viewport来替代此方。
```

vscode插件: px to rem...插件可以自动将px转换为rem

#### 2.4 grid布局

网格布局是一种二维布局模型，允许开发者通过定义行（rows）和列（columns）来精确控制网页元素的位置和尺寸。网格布局的核心是创建好网格并放入各种元素

容器(父盒子)设置`display:grid;`(块级) 或者`display: inline-grid`(行内)

与弹性盒子不同的是，在定义网格后，网页并不会马上发生变化display:grid 的声明只创建了一个只有一列的网格

**grid tracks**

网格轨道(Grid Tracks)决定了网格容器的基础布局结构，为子元素提供放置的位置。

**通俗理解：**Grid 像先画一张表格，再把内容放进格子里。columns 是列，rows 是行，gap 是格子之间的缝。

- display:grid 创建网格容器。
- grid-template-columns 定义列轨道。
- grid-template-rows 定义行轨道。
- gap 设置行列间距。
- Grid 适合二维布局：同时控制行和列。

```
.grid {
  display: grid;
  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  gap: 16px;
}
```

**fr单位**

**通俗理解：**`fr` 像分蛋糕：固定宽度先切走，剩下的空间再按 1fr、2fr 这些份数分。

- `fr` 表示可用空间的一份。
- 1fr 1fr 1fr 表示三列均分。
- 固定宽度和` fr` 可混用，例如 `240px 1fr`。
- `fr `只分配剩余空间，不等同于百分比。

```
.grid { grid-template-columns: 240px 1fr 1fr; }
```

**repeat 与自动填充**

**通俗理解：**repeat 像复制同一种列宽规则；auto-fill 像货架自动摆商品，空间够就多摆一列，不够就少摆一列。

- repeat(4, 1fr) 表示重复 4 次 1fr。
- auto-fill 会尽可能填充更多列。
- minmax(min, max) 可以设置轨道最小和最大尺寸。
- repeat(auto-fill, minmax(180px, 1fr)) 是响应式卡片网格常用写法。

```
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 20px;
}
```

**网格线与项目放置**

- grid-column: 1 / 3 表示从第 1 条列线跨到第 3 条列线。
- grid-row 控制行方向跨度。
- span n 表示跨 n 个轨道。
- 可用于 B 站式复杂卡片布局。

```
.hero-card {
  grid-column: 1 / span 2;
  grid-row: 1 / span 2;
}
```

#### 2.5 响应式布局

**响应式开发原理**

使用媒体查询针对不同宽度的设备进行布局和样式的设置，从而适配不同设备的目的

| 设备划分               | 尺寸区间        |
| ---------------------- | --------------- |
| 超小屏幕(手机)         | <768px          |
| 小屏设备(平板)         | >=768 ~ <992px  |
| 中等屏幕(桌面显示器)   | >=992 ~ <1200px |
| 宽屏设备(大桌面显示器) | >= 1200px       |

响应式开发一般有一个布局容器,一般叫做`.container`

平时我们的响应式尺寸划分
超小屏幕（手机，小于768px）：设置宽度为100%
小屏幕（平板，大于等于768px）：设置宽度为750px
中等屏幕（桌面显示器，大于等于992px）：宽度设置为970px
大屏幕（大桌面显示器，大于等于1200px）：宽度设置为1170px

```
.container{}
@media screen and (max-width: 768px){
	.container {
	width: 100%;
	}
}
@media screen and (min-width: 768px){
	.container {
	width: 750px;
	}
}
@media screen and (min-width: 992px){
	.container {
	width: 970px;
	}
}
@media screen and (min-width: 1200px){
	.container {
	width: 1170px;
	}
}
```

##### **bootstrap**

官网：https://getbootstrap.com/
中文官网：https://v5.bootcss.com/docs

**Bootstrap 基本使用**

- 来源：03-BootStrap基本使用.html；05-BootStrap字体图标使用.html

**要点：**

- Bootstrap 是响应式 UI 框架，提供栅格、组件和工具类。
- 使用前引入 bootstrap.min.css；需要交互组件时再引入 bootstrap.min.js。
- .container 提供固定最大宽度并居中，.container-fluid 宽度 100%。
- Bootstrap Icons 是独立图标库，需单独引入。

**示例代码：**

```html
<link rel="stylesheet" href="./bootstrap/bootstrap.min.css">
<script src="./bootstrap/bootstrap.min.js"><\/script>
```

**Bootstrap 栅格系统**

**断点：**
断点（Breakpoints）时响应式设计的组成部分。通过断点可以控制何
时可以在特定视口（viewport)或设备尺寸下调整布局。

|Breakpoint|Class infix|Dimensions|
|-|-|-|
|Extra small|None|<576px|
|Small|sm|≥576px|
|Medium|md|2768px|
|Large|lg|≥992px|
|Extra large|xl|≥1200px|
|Extra extra large|xxl|≥1400px|

容器是Bootstrap中最基本的布局元素，在使用我们的默认网格系统时是必需的。容器用于将其中的内容居中。包含：默认容器（container）、响应式容器（Responsive containers）、流式容器（Fluid containers）三种
```
Bootstrap附带三种不同的容器：
.container，它在每个响应断点处设置max-width
.container-fluid，所有断点width：100%
.container-{breakpoint}，直到指定的断点width：100%为止
```

 **网格系统（grid）**：
Bootstrap的网格系统（栅格系统）使用一系列容器、行和列来布局和对齐内容。它是用flexbox构建的，并且是完全响应的。
注意：Bootstrap的网格系统每行划分为12份。

|              | xs    | sm       | md       | lg       | xl       | xxl       |
| ------------ | ----- | -------- | -------- | -------- | -------- | --------- |
| container    | none  | 540      | 720      | 960      | 1140px   | 1320px    |
| class prefix | .col- | .col-sm- | .col-md- | .col-lg- | .col-xl- | .col-xxl- |
| # of columns | 12    |          |          |          |          |           |



```
<div class="container">
	<div class="row">
		<div class="col-md-3">1</div>
		<div class="col-md-3">2</div>
		<div class="col-md-3">3</div>
		<div class="col-md-3">4</div>
	</div>
</div>
```

注意：
1.row代表一行
2.col-xx-份数 比如col-md-3
3.可以写多个类名，决定不同宽度下排列个数

**列对齐**

见官网[列 · Bootstrap v5.3 --- Columns · Bootstrap v5.3](https://getbootstrap.com/docs/5.3/layout/columns/)

**字体图标**

Bootstrap Icons 是独立图标库，需单独引入

在线引入

```
<link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.13.1/font/bootstrap-icons.min.css">
```

#### TDK 网站优化标签

TDK是Title、Description和Keywords三个元标签的缩写，它们是网站SEO优化的核心元素。直接影响搜索引擎对网页的理解和排名。

>Title：决定搜索结果的标题显示，是搜索引擎判断页面主题的首要依据。
>Description：生成搜索结果的摘要描述，影响用户点击率（CTR）。
>Keywords：提供页面主题关键词（尽管现代搜索引擎已弱化其权重，仍部分参考）
>三者共同构成网页的“第一印象”，优化不当可能导致排名下降或点击流失

