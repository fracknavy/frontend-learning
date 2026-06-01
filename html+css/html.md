### 0 web 规范
结构:用于对网页元素进行整理和分类,现主要使用html
表现:用于设置网页元素的版式,颜色,大小等外观样式,主要用css
行为:页面模型的定义以及交互的编写,主要是js

### 1.1 html 语法规范
html标签由尖括号包围,一般是成对出现如<html> </html>,只有少量的的单独出现如<br />

### 1.2 标签关系
包含关系与并列关系
```html
<!-- 根标签 <html> 包含所有内容 -->
<html>
  <!-- <head> 是 <html> 的子标签（包含关系） -->
  <head>
    <!-- <meta>、<title> 是 <head> 的子标签，彼此并列（并列关系） -->
    <meta charset="UTF-8">
    <title>综合示例</title>
  </head>

  <!-- <body> 和 <head> 并列（并列关系） -->
  <body>
    <!-- <p> 是 <body> 的子标签（包含关系） -->
    <p>
      <!-- <h1>、<p> 是 <p> 的子标签，彼此并列（并列关系） -->
      <h1>这是标题</h1>
      <p>这是段落</p>
    </p>
  </body>
</html>

```
### 1.3 常见标签

全部标签参考[HTML 标签参考手册](https://www.w3school.com.cn/tags/index.asp)

#### 标题标签
标题标签:<h1> - <h6> 对应一级到六级标题
```html
<h1> 我是一个标题 </h1>
```
#### 段落标签
段落标签:<p>
```html
<p> 我是一个段落 </p>
```
#### 换行标签
换行标签:` <br>`
```html
需要换行<br/>这是一行文字
```

#### 水平线标签

`<hr>`标签在html页面中定义主题分隔,通常显示为水平线

`<hr>`元素用于分隔html页面的内容

例子:

```html
<html>
  <head>
    <meta charset="UTF-8">
    <title>综合示例</title>
  </head>
  <body>
    <h1>水花61分伊戈达拉制胜抢断西决勇士再胜开拓者总分2-0</h1>
    <h3>数据统计：水花兄弟合砍61分<h3>
    <p>库里22投11中，三分14投4中，罚球11罚全中得到37分8篮板8助攻，职业生涯季后赛得分30+次数来到35次，超过哈登排名现役第3位，仅次于詹姆斯和杜兰特。</p>
    <p>汤普森22投8中，三分8投4中得到24分3篮板2助攻，德拉蒙德-格林得到16分10篮板7助攻5盖帽，凯文-鲁尼得到14分7篮板2助攻，今天勇士有7名替补出场。</p>
    <h3>兄弟对决升级：小库里给哥哥造成压力</h3>
    <p>库里兄弟是NBA历史上第一对在分区决赛相遇的兄弟。在西决第1场中，小库里没有给哥哥造成压力，他出场19分钟，7投1中只得到3分3篮板2助攻，在场期间输掉10分。</p>
	<p>但在西决第2场中，小库里攻防两端都打出杰出的表现，全场送出4次抢断，包括直接抢断自己的哥哥库里，在防守端给库里造成了极大的困扰。</p>
  </body>
</html>
```
#### 文本格式化标签:
1.加粗: <strong></strong>或者<b></b>
2.倾斜:<em></em>或<i></i>
3.删除线: <del></del> 或<s></s>
4.下划线:<Ins></ins>或<u></u>
注:前者比后者语义更强烈(其实更好记)


#### 无语义标签
作为一个盒子用来装内容
<p> 标签: 分割,独占一行
<span>标签: 跨距,一行可以放多个

#### 图像标签:<img>
```
<img src="url"> // src用于指令图片的路径名和文件名
```
图片标签的其他属性

| 属性   | 属性值   | 说明                               |
| ------ | -------- | ---------------------------------- |
| src    | 图片路径 | 必须属性                           |
| alt    | 文本     | 替换文本.图像不能显示的文字        |
| title  | 文本     | 提示文本.鼠标放到图像上,显示的文本 |
| width  | 像素     | 设置图像的宽度                     |
| height | 像素     | 设置图像的高度                     |
| border | 像素     | 设置图像的边框粗细                 |

注意:属性必须在img标签后,不分先后顺序,采取键对格式

#### 超链接标签:<a>
 语法格式
 ```
 <a href="跳转目标" target="目标窗口弹出方式">文本或图像</a>
 ```
超链接标签属性的作用
 |属性|作用     |
 |----- |----- |
 |href|用于指定链接目标的url地址,(必须属性)                           |
 |target|用于指定链接页面的打开方式,其中_self为默认值,_blank为在新窗口打开|

1. 外部链接:`a herf="http://qq.com" target="_blank">腾讯</a>`
2. 内部链接:网页内部页面之间的相互链接,`a href="index.html">首页</a>`
3. 空连接:如果当时没有确定链接目标时,`a href="#">首页</a>`
4. 下载链接:herf里的链接是一个文件或压缩包
5. 网页元素链接:在网页中的各种网页元素,如文本,图像,表格,音频,视频等都可以添加超链接
6. 锚点链接:点击链接后可以快速定位到页面中的某个位置	
	在链接文本的href属性中，设置属性值为#名字的形式，如:`<a href="#two">第二级</a>`
	找到目标位置标签，里面添加一个id属性=刚才的名字，如:`<h3 id="two”>第2集介绍</h3>`

#### 注释
html中的注释:`<!-- 注释内容 -->`

#### 特殊字符

![QQ_1778131722852](img\QQ_1778131722852.png)

### 1.4表格标签
#### 基本语法
```html
<table>
	<tr>
		<td></td>
	<tr>
    </tr>
</table>
```
#### 表头单元格标签

相较于`<td><td>` ,`<th><th>`的文字会加粗

| 属性名      | 属性值            | 描述                                           |
| ----------- | ----------------- | ---------------------------------------------- |
| align       | left,center,right | 规定表格相对元素的对齐方式                     |
| border      | 1或""             | 规定表格单元是否拥有边框,默认为"",表示没有边框 |
| cellpadding | 像素值            | 归定单元边沿与其内容之间的空白,默认1像素       |
| cellspacing | 像素值            | 规定单元格之间的空白,默认2像素                 |
| width       | 像素值或百分比    | 规定表格的宽度                                 |

示例:

```
<table align="center" border="1" cellpadding="0" cellspacing="0>
	...
</table>
```

#### 表格结构标签

<thead>标签表格的头部区域

<tbody>标签表格的主题区域

```html
<table>
    <thead>
    	<tr>
            <th></th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td></td>
        </tr>
    </tbody>
</table>    
```

#### 合并单元格

合并单元格的方式:

跨行合并: rowspan="合并单元格的个数"    (最上侧单元格为目标单元格)

跨列合并: colspan="合并单元格的个数"      (最左侧单元格为目标单元格)

```html
<table>
    <tr>
        <td></td>
        <td colspan="2"></td>
    </tr>
    <tr>
        <td roespan="2"></td>
        <td></td>
        <td></td>
    </tr>
    <tr>
        <td></td>
        <td></td>
    </tr>
</table>
```

### 2.列表标签

根据使用场景不同,分为无序列表,有序列表和自定义列表

#### 无序列表

```html
<ul>
    <li>列表项1</li>
    <li>列表项2</li>
    <li>列表项3</li>
</ul>
```

"<ul>"标签只能放"<li>",而"<li>"标签可以容纳所有元素

无序列表的各个列表项之间没有顺序之分

#### 有序列表

```
<ol>
	<li>排行榜1</li>
	<li>排行榜2</li>
	<li>排行榜3</li>
</ol>
```

"<ol>"标签只能放"<oi>",而"<li>"标签可以容纳所有元素

有序列表的各个列表项之间有顺序之分

#### 自定义列表

```
<dl>
	<dt>名词1</dt>
	<dd>名词1解释</dd>
	<dd>名词2结婚</dd>
</dl>
```

"<dl>"里面只能放"<dt>"和"<dd>","<dt>''和"<dd>"可以容纳所有元素



### 表单标签

使用表单用来收集用户信息

"<form>"用于定义表单域

```
<form action="url地址" method="提交方式" name="表单域名称">
	各种表单元素控件
</form>
```

| 属性   | 属性值   | 作用                                              |
| ------ | -------- | ------------------------------------------------- |
| action | url地址  | 用于指定接收并处理表单数据的服务器程序的url地址   |
| method | get/post | 用于设置表单数据的提交方式,其取值为get或post      |
| name   | 名称     | 用于指定表单的名称,以区分用一个页面中的多个表单域 |

#### input标签

1.<input>输入表单元素

```
<input type="属性值" />
```

<input />标签为单标签

type属性设置不同的属性值用来指定不同的控件类型

| 属性值   | 描述                                                     |
| -------- | -------------------------------------------------------- |
| button   | 定义可点击按钮(多数情况下,用于通过JavaScript启动脚本)    |
| checkbox | 定义复选框                                               |
| file     | 定义输入字段和"浏览"按钮,共文件上传                      |
| hidden   | 定义隐藏的输入字段                                       |
| password | 定义密码字段.该字段中的字符被掩码                        |
| radio    | 定义单选按钮                                             |
| reset    | 定义重置按钮.重置按钮会清除表单的所有数据                |
| submit   | 定义提交按钮.提交按钮会把表单数据发送到服务器            |
| text     | 定义单行的输入字段,用户可在其中刻入文本,默认宽度为20字符 |
| image    | 定义图像形式的提交按钮                                   |

例子

```html
<form>
    用户名:<input type="text" name=username> <br>
    密码:<input type="password" name-password> <br>
    性别:男 <input type="radio" name="sex"> 女 <input type="radio" name="sex"> <br>
    爱好:吃<input type="checkbox" name="hobby"> 喝<input type="checkbox" name="hobby"> 玩	<input type="checkbox" name="hobby"> <br>
    <input type="submit" value="免费注册">
    <input type="reset" value="重新填写">
    <input type="button" value="获取验证码">
    上传照片: <input type="file">
</form>    
```

| 属性      | 属性值       | 描述                                |
| --------- | ------------ | ----------------------------------- |
| name      | 由用户自定义 | 定义input元素的名称                 |
| value     | 由用户自定义 | 规定input元素的值                   |
| checked   | checked      | 规定此input元素首次加载时应当被选中 |
| maxlength | 正整数       | 规定输入字段中的字符最大长度        |

1.name和value是每个表单元素都有的属性值.主要给后台人员使用

2.name表单元素的名字,单选框和复选框需要有相同的name

3.checked属性主要针对于单选按钮和复选框,主要作用是一打开页面,可以默认选中某个表单元素

4.maxlength是用户在表单元素输入的最大字符数

label标签

label标签为input元素定义标注,用于绑定一个表单元素,当点击label标签内的内容时浏览器会自动将焦点或光标转到或选择对应的表单元素,用于增加用户体验

```
<label for="sex">男</label>
<input type="radio" name="sex" id="sex" />
```

label标签的for属性必须和input标签的id属性一致

#### select标签

```
<form>
	<select>
		<option>选项1</option>
		<option>选项2</option>
		<option>选项3</option>
	</select>
</form>
```

1,select中至少包含一对option

2,在select中定义selected="selected"时,当前项为默认选中项

#### textarea标签

当用户输入内容较多的情况下,使用testarea,此标签可以用于定义多行文本输入的控件,常见于留言板,评论

```
<form>
	<testarea rows="4" clos="30">
	</testarea>
</form>
```

rows控制显示多少行

clos控制一行多少字符

### html5的新特性

```
<header>：头部标笨
<nav>：导航标签
<article>：内容标签
<section>：定义文档某个区域
<aside>：侧边栏标签
<footer>：尾部标签
```

注意：
●这种语义化标准主要是针对搜索引擎的
●这些新标签页面中可以使用多次
●在IE9中，需要把这些元素转换为块级元素
●其实，我们移动端更喜欢使用这些标签
●HTML5还增加了很多其他标签，我们后面再慢慢学

![](D:\Programing\github_project\frontend-learning\img\Snipaste_2026-05-21_19-10-04.png)



#####  html5新增多媒体标签

视频`<video>`

video元素支持三种视频格式: mp4, webm ,ogg(最好使用mp4格式)

```
<video src="文件路径" controls="controls"></video>

<video width="320" height="240" controls>
	<source src="movie.mp4" type="video/mp4">
	<source src="movie.ogg" type="video/ogg"
	您的浏览器不支持video标签。
</vidEo>
```

1. 视频`<video>`-常见属性

| 属性     | 值                                       | 描述                                                         |
| -------- | ---------------------------------------- | ------------------------------------------------------------ |
| autoplay | autoplay                                 | 视频就绪自动播放（谷歌浏览器需要添加muted来解决自动播放问题） |
| controls | controls                                 | 向用户显示播放控件                                           |
| width    | pixels(像素)                             | 设置播放器宽度                                               |
| height   | pixels(像素）                            | 设置播放器高度                                               |
| loop     | loop                                     | 播放完是否继续播放该视频，循环播放                           |
| preload  | auto（预先加载视频）none（不应加载视频） | 规定是否预加载视频（如果有了autoplay就忽略该属性)            |
| src      | url                                      | 视频ur地址                                                   |
| poster   | Imgurl                                   | 加载等待的画面图片                                           |
| muted    | muted                                    | 静音插放                                                     |

音频`<audio>`

audio元素支持三种格式: mp4, wav, ogg

```
<audio src="文件地址" controls="controls"></audio>

<audio controls="controls">
	<source src="happy.mp3" type= "audio/mpeg">
	<source src="happy.ogg" type= "audio/ogg">
	您的浏览器不支持<audio>标签
</ audio>
```



| 属性     | 值       | 描述                                           |
| -------- | -------- | ---------------------------------------------- |
| autoplay | autoplay | 如果出现该属性,则音频在就绪后马上播放          |
| controls | controls | 如果出现该属性,则向用户展示控件,比如说播放按钮 |
| loop     | loop     | 如果出现该属性,则每当音频结束时重新开始播放    |
| src      | url      | 要播放音频的url                                |



#####  html5新增input类型

| 属性值        | 说明                        |
| ------------- | --------------------------- |
| type="email"  | 限制用户输入必须为Email类型 |
| type="url"    | 限制用户输入必须为URL类型   |
| type="date"   | 限制用户输入必须为日期类型  |
| type="time"   | 限制用户输入必须为时间类型  |
| type="month"  | 限制用户输入必须为月类型    |
| type="week"   | 限制用户输入必须为周类型    |
| type="number" | 限制用户输入必须为数字类型  |
| type="tel"    | 手机号码                    |
| type="search" | 搜索框                      |
| type="color"  | 生成一个颜色选择表单        |



#####  html5新增的表单属性

| 属性         | 值        | 说明                                                         |
| ------------ | --------- | ------------------------------------------------------------ |
| required     | required  | 表单拥有该属性表示其内容不能为空，必填                       |
| placeholder  | 提示文本  | 表单的提示信息，存在默认值将不显示                           |
| autofocus    | autofocus | 自动聚焦属性，页面加载完成自动聚焦到指定表单                 |
| autocomplete | off /on   | 当用户在字段开始键入时，浏览器基于之前键入过的值，应该显示出在字段中填写的选项。 默认已经打开，如 autocomplete="on”，关闭 autocomplete ="off"”需要放在表单内，同时加上name属性，同时成功提交 |
| multiple     | multiple  | 可以多选文件提交                                             |

