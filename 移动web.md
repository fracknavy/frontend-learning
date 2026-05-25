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

#### 2.1流式布局

流式布局，就是百分比布局，也称非固定像素布局。
通过盒子的宽度设置成百分比来根据屏幕的宽度来进行伸缩，不受固定像素的限制，内容向两侧填充。
流式布局方式是移动web开发使用的比较常见的布局方式。

max-width最大宽度（max-height 最大高度）
min-width 最小宽度（min-height 最小高度）