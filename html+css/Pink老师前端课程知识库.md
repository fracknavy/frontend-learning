# Pink老师前端课程知识库

- 顶级章节：9
- 知识点总数：143

## 目录

- HTML5 语义标签（基础）
- CSS3 核心技术（重点）
- 现代网页布局（布局）
- 交互动效设计（动效）
- 前沿技术拓展（拓展）
- 移动网页开发（移动端）
- 响应网页开发（响应式）
- 前端网页托管（发布）
- 综合复习路线（路线）

## 1 HTML5 语义标签

- 标签：基础
- 来源：01-HTML5语义标签/笔记/HTML5_20250901094806.pdf；01-HTML5语义标签/代码/01-20 示例

**概述：** 对应 01-HTML5语义标签，重点是页面结构、文本、媒体、链接、列表、表格、表单和特殊字符。

### 1.1 HTML 文档骨架

- 来源：01-我的第一个页面.html；03-认识html.html

**概述：** HTML 页面通常由文档声明、html 根元素、head 元信息和 body 可视内容组成。

**要点：**
- &lt;!doctype html&gt; 声明使用 HTML5 标准模式，避免浏览器进入怪异模式。
- &lt;html lang="zh-CN"&gt; 用来声明页面主语言，利于浏览器、搜索引擎和辅助技术识别。
- &lt;meta charset="UTF-8"&gt; 决定文档字符编码，中文页面建议统一使用 UTF-8。
- &lt;meta name="viewport" content="width=device-width, initial-scale=1.0"&gt; 是移动端和响应式布局的基础。

**示例代码：**

```html
<!doctype html>
<html lang="zh-CN">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>页面标题</title>
</head>
<body>
  页面内容
</body>
</html>
```

### 1.2 标签关系

- 来源：04-标签关系.html

**概述：** HTML 标签之间主要有父子、兄弟、祖先、后代关系，CSS 选择器和 DOM 操作都依赖这些关系。

**通俗理解：** 把 HTML 想成家谱：外层标签是父母，里面直接包着的是孩子；同一层的几个标签是兄弟。CSS 选择器很多时候就是按这张家谱找人。

**要点：**
- 父子关系：一个标签直接包裹另一个标签，例如 &lt;ul&gt; 与内部 &lt;li&gt;。
- 兄弟关系：拥有同一个父级的多个元素，例如多个 &lt;li&gt;。
- 后代关系：只要被包含在祖先元素内部，不要求直接相邻。
- 写结构时先思考内容语义，再决定标签嵌套，避免为了样式乱套标签。

### 1.3 标题和段落

#### 1.3.1 标题 h1-h6

- 来源：05-标题和段落.html

**概述：** 标题用来表达文档层级，h1 最大且通常每页只保留一个主标题。

**要点：**
- h1 表示页面主标题，h2 表示主要小节，h3-h6 逐级细分。
- 不要只因为字体大小选择标题级别，标题级别首先是语义。
- 搜索引擎和屏幕阅读器会根据标题结构理解页面内容。

**示例代码：**

```html
<h1>课程标题</h1>
<h2>第一章 HTML</h2>
<h3>1.1 文档骨架</h3>
```

#### 1.3.2 段落 p 与换行 br

- 来源：05-标题和段落.html

**概述：** p 表示完整段落，br 只表示强制换行，不能把 br 当作段落间距工具。

**要点：**
- 段落之间的距离应该由 CSS 的 margin 控制。
- &lt;br&gt; 用在诗歌、地址等确实需要文本换行的位置。
- 普通文字直接写在 body 中也能显示，但结构化程度低，不利于维护。

**示例代码：**

```html
<p>这是一个完整段落。</p>
<p>地址：北京市<br>海淀区</p>
```

### 1.4 语义化页面结构

**概述：** 语义化标签让结构更清楚，也让维护、SEO、无障碍访问更友好。

#### 1.4.1 header / nav / main / section / article / aside / footer

- 来源：06-语义化页面.html；14-网页结构标签以及div和span标签.html

**要点：**
- &lt;header&gt; 通常表示页面头部或某个模块的头部。
- &lt;nav&gt; 表示导航链接区域。
- &lt;main&gt; 表示页面主体内容，一个页面通常只出现一个。
- &lt;section&gt; 表示有主题的小节，通常配合标题使用。
- &lt;article&gt; 表示独立完整内容，例如文章、帖子、商品评论。
- &lt;aside&gt; 表示侧边栏、推荐、广告、补充信息。
- &lt;footer&gt; 表示页面底部或模块底部。

**示例代码：**

```html
<header>网站头部</header>
<nav>导航</nav>
<main>
  <section>
    <h2>新鲜好物</h2>
  </section>
</main>
<footer>版权信息</footer>
```

#### 1.4.2 div 与 span

- 来源：14-网页结构标签以及div和span标签.html

**通俗理解：** div 像一个大收纳箱，适合装一整块内容；span 像给一句话里的几个字贴标签，适合做局部样式。

**要点：**
- &lt;div&gt; 是块级通用容器，本身没有语义，常用于布局分组。
- &lt;span&gt; 是行内容器，适合包裹一小段文字做局部样式。
- 当存在更准确的语义标签时，优先使用语义标签，再考虑 div/span。

### 1.5 文本强调标签

- 来源：07-强调与重要性标签.html

**概述：** 强调标签既影响默认样式，也表达内容语义。

**要点：**
- &lt;strong&gt; 表示重要内容，默认加粗，语义强于 &lt;b&gt;。
- &lt;em&gt; 表示语气强调，默认倾斜，语义强于 &lt;i&gt;。
- &lt;ins&gt; 表示插入内容，默认下划线。
- &lt;del&gt; 表示删除内容，默认删除线。

**示例代码：**

```html
<p><strong>重要：</strong>表单提交前请检查信息。</p>
<p>这句话需要<em>特别强调</em>。</p>
```

### 1.6 元素分类

#### 1.6.1 块级元素

- 来源：08-元素分类.html

**通俗理解：** 块级元素像一排货架，默认自己占一整行，后面的内容通常要到下一行开始。

**要点：**
- 常见块级元素：div、p、h1-h6、ul、ol、li、table、form、header、section。
- 默认独占一行，可以设置 width、height、margin、padding。
- 块级元素宽度默认尽量占满父容器。

#### 1.6.2 行内元素

- 来源：08-元素分类.html

**通俗理解：** 行内元素像一句话里的词，默认跟其他文字挤在同一行，大小主要由内容撑开。

**要点：**
- 常见行内元素：span、a、strong、em、label。
- 默认一行显示多个，宽高一般由内容撑开。
- 水平方向 margin/padding 生效明显，垂直方向对布局影响有限。

#### 1.6.3 行内块元素

- 来源：08-元素分类.html

**要点：**
- 常见行内块元素：img、input、button。
- 既可以一行排列，又可以设置 width 和 height。
- 常用于图文按钮、表单控件、图片排列。

### 1.7 图片与路径

#### 1.7.1 img 标签

- 来源：09-图像标签.html

**要点：**
- src 表示图片地址，是必需属性。
- alt 表示替代文本，图片无法加载或屏幕阅读器读取时使用。
- width/height 可以设置显示尺寸，但通常建议交给 CSS 控制。
- 图片是行内块元素，底部可能出现默认空隙，常用 display:block 或 vertical-align 调整。

**示例代码：**

```html
<img src="./img/pic.webp" alt="商品图片">
```

#### 1.7.2 相对路径

- 来源：10-路径.html；上一级路径/上一级.html

**通俗理解：** 相对路径像从当前教室找房间：./ 是本教室，../ 是上一层楼，img/logo.png 是当前楼层里的 img 房间。

**要点：**
- ./ 表示当前目录，可省略但写出来更清楚。
- ../ 表示上一级目录。
- 子目录路径直接写目录名，例如 img/logo.png。
- 课堂项目里 HTML、CSS、images、uploads 分目录管理，就是路径练习的核心场景。

### 1.8 音视频标签

- 来源：11-音视频标签.html；20-综合案例

**要点：**
- &lt;audio&gt; 用来嵌入音频，常配合 controls 显示播放控件。
- &lt;video&gt; 用来嵌入视频，可设置 controls、autoplay、muted、loop、poster。
- 现代浏览器通常要求 autoplay 与 muted 一起使用才允许自动播放。
- poster 是视频未播放前的封面图。

**示例代码：**

```html
<video src="./media/demo.mp4" controls muted poster="./img/poster.jpg"></video>
<audio src="./media/demo.mp3" controls></audio>
```

### 1.9 链接与锚点

#### 1.9.1 a 标签

- 来源：12-链接标签.html

**要点：**
- href 是跳转地址，可以是网页、文件、邮箱、电话或锚点。
- target="_blank" 表示新标签页打开。
- 空链接可写 href="#"，真实项目中要避免无意义跳转影响体验。
- 链接文字应该描述目的地，不建议大量使用“点击这里”。

**示例代码：**

```html
<a href="https://example.com" target="_blank">打开网站</a>
```

#### 1.9.2 锚点链接

- 来源：13-锚点链接.html；资料/13-锚点链接素材.html

**要点：**
- 给目标元素设置 id，例如 id="chapter1"。
- 链接写 href="#chapter1" 即可跳到对应位置。
- 锚点适合长文章目录、页面内导航、返回顶部。

**示例代码：**

```html
<a href="#form">跳到表单</a>
<section id="form">...</section>
```

### 1.10 列表标签

- 来源：15-列表标签.html

**要点：**
- &lt;ul&gt; 无序列表，内部必须以 &lt;li&gt; 作为直接子元素。
- &lt;ol&gt; 有序列表，适合步骤、排名。
- &lt;dl&gt; 自定义列表，由 &lt;dt&gt; 术语和 &lt;dd&gt; 描述组成，适合名词解释。
- 导航、商品分类、新闻列表常用 ul/li 再配合 CSS 去掉默认圆点。

**示例代码：**

```html
<ul>
  <li>首页</li>
  <li>课程</li>
</ul>
```

### 1.11 表格标签

#### 1.11.1 table / tr / th / td

- 来源：16-表格标签.html

**要点：**
- &lt;table&gt; 表示表格整体。
- &lt;tr&gt; 表示一行。
- &lt;th&gt; 表示表头单元格，默认加粗居中。
- &lt;td&gt; 表示普通单元格。
- thead、tbody、tfoot 可以进一步划分表头、主体、表尾。

#### 1.11.2 合并单元格

- 来源：17-合并单元格.html

**要点：**
- rowspan 表示跨行合并。
- colspan 表示跨列合并。
- 合并后要删除被占用的多余单元格，否则表格结构会错位。
- 先确定从哪个单元格开始合并，再数跨几行或几列。

**示例代码：**

```html
<td rowspan="2">跨两行</td>
<td colspan="3">跨三列</td>
```

### 1.12 表单标签

#### 1.12.1 form 容器

- 来源：18-表单标签.html；笔记/md笔记.md

**要点：**
- &lt;form&gt; 用来包裹一组表单控件。
- action 表示提交目标地址。
- method 常见值为 get 和 post。
- 表单项的 name 是提交数据的字段名，没有 name 通常不会随表单提交。

**示例代码：**

```html
<form action="/login" method="post">
  <input name="username">
</form>
```

#### 1.12.2 input 常用 type

- 来源：18-表单标签.html

**通俗理解：** type 决定输入框扮演什么角色：text 像普通填空题，password 像遮住答案的填空题，radio 像单选题，checkbox 像多选题。

**要点：**
- text：单行文本框。
- password：密码框，输入内容会被遮挡。
- radio：单选框，同一组必须设置相同 name。
- checkbox：复选框，适合多选。
- file：文件上传，可配合 multiple 和 accept。
- submit、reset、button：提交、重置、普通按钮。

#### 1.12.3 label 提升可用性

- 来源：18-表单标签.html

**要点：**
- 方式一：label 的 for 与控件 id 对应，点击文字可聚焦或选中控件。
- 方式二：label 直接包裹控件和文字。
- 单选框、复选框尤其适合配 label，点击区域更大。

**示例代码：**

```html
<input id="male" type="radio" name="gender">
<label for="male">男</label>
<label><input type="checkbox" name="hobby"> 足球</label>
```

#### 1.12.4 select / textarea / button

- 来源：18-表单标签.html

**要点：**
- &lt;select&gt; 配合 &lt;option&gt; 实现下拉选择，selected 表示默认选中。
- &lt;textarea&gt; 表示多行文本，内容区域不要写成 input。
- &lt;button&gt; 默认在表单里可能触发表单提交，必要时写 type="button"。
- disabled 禁用控件，placeholder 提示输入内容。

### 1.13 特殊字符

- 来源：19-特殊字符.html

**要点：**
- &amp;nbsp; 表示不换行空格。
- &amp;lt; 表示小于号 &lt;。
- &amp;gt; 表示大于号 &gt;。
- &amp;amp; 表示 &amp; 符号。
- 当你想在页面上展示 HTML 标签本身，而不是让浏览器解析它，就要使用实体字符。

**示例代码：**

```
&lt;div&gt;这会显示标签文本&lt;/div&gt;
```

## 2 CSS3 核心技术

- 标签：重点
- 来源：02-CSS3核心技术/笔记/CSS3核心技术_20250901094937.pdf；02-CSS3核心技术/代码/01-40 示例

**概述：** 对应 02-CSS3核心技术，课程目录包含 CSS 基础、选择器、盒子模型、精灵图、字体图标。

### 2.1 CSS 引入方式

#### 2.1.1 行内样式

- 来源：01-内联和内部样式表.html

**要点：**
- 写在标签 style 属性中，优先级高，但结构和样式混杂。
- 适合临时调试，不适合大量项目代码。

**示例代码：**

```html
<p style="color:red; font-size:20px;">文字</p>
```

#### 2.1.2 内部样式表

- 来源：01-内联和内部样式表.html

**要点：**
- 写在 head 中的 &lt;style&gt; 标签里。
- 适合单个页面的小练习或演示。
- 多个页面复用困难。

**示例代码：**

```html
<style>
  p { color: red; }
</style>
```

#### 2.1.3 外部样式表

- 来源：02-外部样式表.html；css/my.css

**要点：**
- 使用 &lt;link rel="stylesheet" href="..."&gt; 引入 CSS 文件。
- 结构和样式分离，适合真实项目。
- 可被多个页面复用，也便于浏览器缓存。

**示例代码：**

```html
<link rel="stylesheet" href="./css/index.css">
```

### 2.2 CSS 选择器

#### 2.2.1 基础选择器

- 来源：03-类型选择器以及注释.html；04-类选择器.html；05-id和通配符选择器.html

**要点：**
- 类型选择器：p、div、a，按标签名选中。
- 类选择器：.box，复用性强，是项目中最常用的选择器。
- id 选择器：#app，页面中 id 应保持唯一。
- 通配符选择器：*，常用于清除默认 margin/padding，但范围大。

**示例代码：**

```css
p { color: red; }
.box { width: 200px; }
#app { min-height: 100vh; }
* { box-sizing: border-box; }
```

#### 2.2.2 层级选择器

- 来源：07-后代选择器和子代选择器.html；08-兄弟选择器.html

**要点：**
- 后代选择器：.box p，选择 box 内所有后代 p。
- 子代选择器：.box &gt; p，只选择直接子元素 p。
- 相邻兄弟选择器：h2 + p，选择紧跟 h2 后的第一个 p。
- 通用兄弟选择器：h2 ~ p，选择 h2 后面同级的所有 p。

**示例代码：**

```css
.nav a { color: #333; }
.list > li { margin-bottom: 10px; }
h2 + p { margin-top: 0; }
h2 ~ p { color: #666; }
```

#### 2.2.3 伪类选择器

- 来源：14-链接伪类选择器.html；15-用户行为伪类.html；16-结构伪类选择器.html

**要点：**
- 链接伪类常见顺序：:link、:visited、:hover、:active。
- :hover 表示鼠标悬停，是导航、按钮、卡片交互的常用入口。
- :focus 表示获得焦点，常用于表单输入框。
- 结构伪类如 :first-child、:last-child、:nth-child(n) 可按位置选中元素。

**示例代码：**

```css
a:hover { color: red; }
input:focus { border-color: skyblue; }
li:nth-child(2n) { background: #f5f5f5; }
```

#### 2.2.4 伪元素选择器

- 来源：20-伪元素选择器.html

**要点：**
- ::before 在元素内容前创建虚拟子元素。
- ::after 在元素内容后创建虚拟子元素。
- 必须设置 content 属性，哪怕 content: ""。
- 常用于清除浮动、装饰线、图标、遮罩层。

**示例代码：**

```css
.box::after {
  content: "";
  display: block;
  clear: both;
}
```

#### 2.2.5 属性选择器

- 来源：21-属性选择器.html

**要点：**
- [type] 选择拥有 type 属性的元素。
- [type="text"] 选择 type 值等于 text 的元素。
- [class^="icon-"] 选择 class 以 icon- 开头的元素。
- [href$=".pdf"] 选择 href 以 .pdf 结尾的链接。

**示例代码：**

```css
input[type="text"] { border: 1px solid #ccc; }
a[href$=".pdf"]::after { content: " PDF"; }
```

### 2.3 CSS 三大特性

#### 2.3.1 层叠性

- 来源：22-CSS权重优先级.html

**通俗理解：** 把 CSS 想成多人给同一个盒子提意见：都说颜色时，浏览器要按权重和先后顺序决定听谁的。权重一样，就听后写的。

**要点：**
- 同一个元素、同一个属性被多条规则设置时，会根据权重、来源和书写顺序决定最终样式。
- 权重相同，后写的覆盖先写的。
- 层叠不是冲突本身，而是 CSS 解决冲突的规则。

#### 2.3.2 继承性

- 来源：12-font简写和继承性.html

**通俗理解：** 像家里的统一着装要求：父元素设置了字体和颜色，子元素通常会跟着用；但宽高、边框、外边距这类盒子尺寸不会自动传下去。

**要点：**
- 文本相关属性常能继承，例如 color、font、line-height、text-align。
- 盒模型属性通常不继承，例如 width、height、margin、padding、border。
- 把全站字体和基础颜色写在 body 上，就是利用继承。

#### 2.3.3 优先级与权重

- 来源：22-CSS权重优先级.html

**通俗理解：** 可以把选择器当成指令级别：id 像点名，class 像按小组叫人，标签像按身份叫人。点名通常比按小组更具体，所以更容易生效。

**要点：**
- !important 权重最高，但会破坏可维护性，慎用。
- 行内样式 &gt; id 选择器 &gt; 类/伪类/属性选择器 &gt; 标签/伪元素选择器 &gt; 通配符。
- 复合选择器权重按组成累计，不是简单看长度。
- 继承来的样式权重最低。

**示例代码：**

```css
#box .title { color: red; } /* id + class */
.card h2 { color: blue; }   /* class + tag */
```

### 2.4 字体与文本

#### 2.4.1 字体样式

- 来源：10-字体样式.html；12-font简写和继承性.html

**要点：**
- font-size 设置字号，浏览器默认常为 16px。
- font-weight 设置字重，常用 normal、bold、400、700。
- font-style 设置字体样式，常用 normal、italic。
- font-family 设置字体族，中文字体名建议加引号并提供兜底字体。

**示例代码：**

```css
body {
  font: 16px/1.6 "Microsoft YaHei", Arial, sans-serif;
}
```

#### 2.4.2 文本布局

- 来源：02-设置字体缩进.html；11-文本布局.html

**要点：**
- color 设置文字颜色。
- text-align 设置行内内容水平对齐。
- text-indent 设置首行缩进，中文段落常用 2em。
- line-height 设置行高，可用数值、px、em、百分比。
- text-decoration 控制下划线、删除线等。

**示例代码：**

```css
p {
  text-indent: 2em;
  line-height: 1.8;
  text-align: justify;
}
```

#### 2.4.3 单行/多行省略号

- 来源：37-多行文本显示省略号.html

**要点：**
- 单行省略号需要 white-space: nowrap、overflow: hidden、text-overflow: ellipsis。
- 多行省略号常用 -webkit-line-clamp，需要配合弹性盒旧语法。
- 省略号只影响视觉显示，原始文本仍在 DOM 中。

**示例代码：**

```css
.one-line {
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}
.multi-line {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
```

### 2.5 盒子模型

#### 2.5.1 盒子组成

- 来源：23-盒子模型-边框设置.html；25-盒子模型-内边距.html；26-盒子模型之外边距.html

**通俗理解：** 盒子模型像快递盒：content 是商品，padding 是防震泡沫，border 是纸箱外壳，margin 是这个快递盒和其他快递盒之间的距离。

**要点：**
- content：内容区域，由 width/height 控制。
- padding：内边距，内容与边框之间的距离。
- border：边框，包在 padding 外面。
- margin：外边距，盒子与其他盒子的距离。
- 标准盒模型下，元素实际占用宽度 = width + padding-left/right + border-left/right。

**示例代码：**

```css
.box {
  width: 200px;
  padding: 20px;
  border: 2px solid #333;
  margin: 30px;
}
```

#### 2.5.2 边框 border

##### 2.5.2.1 border-width / border-style / border-color

- 来源：23-盒子模型-边框设置.html

**要点：**
- border-width 设置边框粗细。
- border-style 设置边框样式，常用 solid、dashed、dotted。
- border-color 设置边框颜色。
- border 简写常用顺序：宽度 样式 颜色。

**示例代码：**

```css
.box {
  border: 1px solid #ddd;
  border-top: 3px solid #e1251b;
}
```

##### 2.5.2.2 边框圆角 border-radius

- 来源：24-圆角边框.html

**要点：**
- border-radius 用来设置盒子四个角的圆角。
- 写一个值：四个角相同。
- 写两个值：左上/右下为第一个，右上/左下为第二个。
- 写三个值：左上、右上/左下、右下。
- 写四个值：左上、右上、右下、左下，顺时针。
- 圆形：正方形盒子设置 border-radius: 50%。
- 胶囊按钮：圆角设置为宽高较小值的一半，例如 200x40 的盒子写 20px。
- 圆角实际最多只能到盒子边长的一半；超过一半会按浏览器规则压缩，视觉上不会继续变得更圆。

**示例代码：**

```css
.circle {
  width: 100px;
  height: 100px;
  border-radius: 50%;
}
.pill {
  width: 200px;
  height: 40px;
  border-radius: 20px;
}
.card {
  border-radius: 10px 30px 50px 70px;
}
```

#### 2.5.3 内边距 padding

- 来源：25-盒子模型-内边距.html

**要点：**
- padding 会撑大标准盒模型的实际尺寸。
- 一个值：四边相同；两个值：上下、左右；三个值：上、左右、下；四个值：上右下左。
- padding 适合控制内容与边框之间的留白，例如按钮内部空间。

**示例代码：**

```css
.btn { padding: 8px 16px; }
```

#### 2.5.4 外边距 margin

- 来源：26-盒子模型之外边距.html；27-块级盒子水平居中.html；28-外边距合并和塌陷.html

**通俗理解：** margin 像人与人之间保持的距离；两个上下相邻的人都说要留距离时，浏览器常常只取较大的那个距离，而不是简单相加。

**要点：**
- margin 控制盒子外部距离。
- 块级盒子水平居中常用 width + margin: 0 auto。
- 相邻块级元素垂直 margin 可能发生合并，最终距离取较大值。
- 父子元素顶部 margin 可能发生塌陷，可用 border、padding、overflow、display: flow-root 等方式处理。

**示例代码：**

```css
.container {
  width: 1200px;
  margin: 0 auto;
}
```

#### 2.5.5 盒子尺寸 box-sizing

- 来源：29-盒子尺寸计算boxsizing.html

**通俗理解：** content-box 像只量商品本身，泡沫和纸箱另算；border-box 像直接规定快递盒最终尺寸，里面的泡沫和纸箱都算在这个尺寸里。

**要点：**
- content-box 是默认标准盒模型，width/height 只包含内容区域。
- border-box 表示 width/height 包含 content、padding、border。
- 项目中常用 * { box-sizing: border-box; } 降低尺寸计算成本。
- 使用 border-box 时，设置 padding/border 不会让盒子的总宽高超出指定 width/height。

**示例代码：**

```css
* { box-sizing: border-box; }
.box { width: 200px; padding: 20px; border: 1px solid #ddd; }
```

#### 2.5.6 盒子阴影 box-shadow

- 来源：34-盒子阴影.html；36-盒子模型综合案例-小米卡片.html

**要点：**
- 常用参数：水平偏移、垂直偏移、模糊半径、扩散半径、颜色。
- 默认是外阴影，inset 可改为内阴影。
- 卡片 hover 状态常用阴影增强层次，但不要过度影响可读性。

**示例代码：**

```css
.card:hover {
  box-shadow: 0 8px 24px rgba(0,0,0,.12);
}
```

### 2.6 背景技术

#### 2.6.1 背景颜色与图片

- 来源：30-盒子背景.html；31-视差滚动效果.html

**要点：**
- background-color 设置背景色。
- background-image: url(...) 设置背景图。
- background-repeat 控制是否平铺。
- background-position 控制背景位置。
- background-size 控制背景尺寸，常用 cover、contain、具体宽高。
- background-attachment: fixed 可做视差滚动效果。

**示例代码：**

```css
.hero {
  background: url("./img/bg.jpg") center / cover no-repeat;
}
```

#### 2.6.2 线性渐变 linear-gradient

- 来源：32-背景渐变.html

**要点：**
- linear-gradient 可以作为 background-image 使用。
- 可指定方向，如 to right、45deg。
- 渐变可以叠加背景图做遮罩效果。

**示例代码：**

```css
.btn {
  background: linear-gradient(90deg, #ff7a59, #1e88e5);
}
```

#### 2.6.3 径向渐变 radial-gradient

- 来源：33-2背景径向渐变.html

**要点：**
- radial-gradient 从中心向外扩散。
- 可指定形状 circle 或 ellipse。
- 适合做光斑、按钮高光、舞台光感，但真实项目要控制使用量。

**示例代码：**

```css
.light {
  background: radial-gradient(circle, #fff 0%, #85c7ff 50%, transparent 70%);
}
```

### 2.7 CSS 初始化

- 来源：35-CSS初始化.html；css/normalize.css

**要点：**
- 不同浏览器自带默认样式不完全一致，初始化可以减少差异。
- 常见做法：清除 margin/padding，设置 box-sizing，统一字体，去掉列表圆点。
- normalize.css 不是完全清零，而是保留合理默认样式并修复浏览器差异。
- 大型项目会在 base.css 或 reset.css 中统一基础样式。

**示例代码：**

```css
* { margin: 0; padding: 0; box-sizing: border-box; }
ul, ol { list-style: none; }
a { text-decoration: none; color: inherit; }
```

### 2.8 字体图标与精灵图

#### 2.8.1 字体图标 iconfont

- 来源：39-字体图标.html；iconfont1/demo_index.html

**要点：**
- 字体图标本质是把图标做进字体文件，通过字符或 class 显示。
- 优点：体积小、可通过 color/font-size 改颜色和大小。
- 常见引入方式：@font-face + iconfont class。
- 适合单色图标，不适合复杂彩色图片。

#### 2.8.2 CSS 精灵图 sprites

- 来源：40-精灵图.html

**要点：**
- 把多个小图标合成一张大图，减少 HTTP 请求。
- 通过 background-position 显示大图中的某一块。
- 需要给元素固定 width/height。
- 现代项目中常被 SVG symbol、iconfont、打包工具替代，但仍是重要基础概念。

**示例代码：**

```css
.icon {
  width: 24px;
  height: 24px;
  background: url("./img/sprite.png") -48px 0 no-repeat;
}
```

## 3 现代网页布局

- 标签：布局
- 来源：03-现代网页布局/笔记/现代网页布局_20250901095105.pdf；03-现代网页布局/代码/01-32 示例

**概述：** 对应 03-现代网页布局，覆盖显示模式、浮动、Flex、定位、Grid、多栏和项目布局。

### 3.1 display 显示模式转换

- 来源：01-display显示模式转换.html

**要点：**
- display:block 把元素变成块级盒子。
- display:inline 把元素变成行内盒子。
- display:inline-block 让元素一行排列且可设置宽高。
- display:none 会让元素不显示且不占位。
- display:flex 和 display:grid 是现代布局的核心入口。

**示例代码：**

```css
.nav a {
  display: inline-block;
  width: 120px;
  height: 40px;
}
```

### 3.2 浮动 float

#### 3.2.1 浮动特点

- 来源：02-浮动.html

**通俗理解：** float 最初像报纸排版：图片靠左浮起来，文字从旁边绕过去。后来被拿来做布局，所以经常需要清除浮动来让父盒子重新包住内容。

**要点：**
- float:left/right 让元素脱离普通文档流，并向左或向右排列。
- 浮动最早常用于文字环绕图片，后来大量用于 PC 端布局。
- 浮动元素会影响后面的行内内容，但父元素可能因为子元素浮动而高度塌陷。

#### 3.2.2 清除浮动

- 来源：03-清除浮动.html

**要点：**
- 额外标签法：在浮动元素后添加空块并设置 clear: both。
- 父级 overflow:hidden 可以触发 BFC，包住浮动。
- clearfix 伪元素法最常用：父级 ::after 清除浮动。
- 现代布局优先使用 Flex/Grid，浮动主要用于维护老项目和理解历史布局。

**示例代码：**

```css
.clearfix::after {
  content: "";
  display: block;
  clear: both;
}
```

### 3.3 Flex 弹性布局

#### 3.3.1 容器 display:flex

- 来源：04-弹性布局示例.html；05-弹性布局-容器flex.html

**要点：**
- 给父元素设置 display:flex 后，直接子元素变成 flex item。
- 默认主轴为水平方向，从左到右排列。
- 子项默认高度会拉伸到容器高度，除非设置 align-items 或自身高度。
- Flex 适合一维布局：一行或一列。

**示例代码：**

```css
.box {
  display: flex;
  width: 500px;
  height: 100px;
}
```

#### 3.3.2 主轴方向 flex-direction

- 来源：08-弹性布局-修改主轴方向.html

**通俗理解：** Flex 先决定队伍往哪里排。row 是横着排队，column 是竖着排队；队伍方向变了，所谓“主轴对齐”的方向也会跟着变。

**要点：**
- row：默认，从左到右。
- row-reverse：从右到左。
- column：从上到下。
- column-reverse：从下到上。
- 主轴方向改变后，justify-content 和 align-items 的作用方向也会跟着改变。

**示例代码：**

```css
.box { display: flex; flex-direction: column; }
```

#### 3.3.3 主轴对齐 justify-content

- 来源：06-弹性布局-主轴对齐.html

**通俗理解：** 把它想成一排座位怎么分配：center 是大家坐中间，space-between 是第一个坐最左、最后一个坐最右，中间的人均匀分开。

**要点：**
- flex-start：主轴起点对齐。
- flex-end：主轴终点对齐。
- center：居中。
- space-between：两端贴边，中间均分。
- space-around：每个项目两侧空间相等，边缘空间是中间的一半。
- space-evenly：所有间距完全相等。

**示例代码：**

```css
.box {
  display: flex;
  justify-content: space-between;
}
```

#### 3.3.4 交叉轴对齐 align-items

- 来源：07-弹性布局-交叉轴对齐.html；15-图片和文字垂直居中效果.html

**要点：**
- stretch：默认拉伸。
- flex-start：交叉轴起点对齐。
- flex-end：交叉轴终点对齐。
- center：交叉轴居中，常用于垂直居中。
- baseline：按文字基线对齐。

**示例代码：**

```css
.box {
  display: flex;
  align-items: center;
}
```

#### 3.3.5 换行 flex-wrap

- 来源：09-弹性布局-强制换行.html；10-弹性布局-多行交叉轴对齐.html

**要点：**
- nowrap：默认不换行，空间不足时项目可能被压缩。
- wrap：允许换行。
- wrap-reverse：反向换行。
- 多行布局时可用 align-content 控制多行在交叉轴的整体分布。

**示例代码：**

```css
.box {
  display: flex;
  flex-wrap: wrap;
  align-content: space-between;
}
```

#### 3.3.6 项目伸缩 flex

- 来源：11-弹性布局-flex项目伸缩尺寸.html；flex项目伸缩尺寸演示.html

**要点：**
- flex-grow 控制剩余空间如何放大。
- flex-shrink 控制空间不足时如何缩小。
- flex-basis 控制项目在主轴方向的基础尺寸。
- flex: 1 常表示项目均分剩余空间。
- 移动端底部导航、卡片列表、搜索栏都常用 flex:1。

**示例代码：**

```css
.item { flex: 1; }
.sidebar { flex: 0 0 240px; }
```

### 3.4 定位布局 position

#### 3.4.1 相对定位 relative

- 来源：16-定位布局-相对定位.html

**通俗理解：** relative 像人从座位上挪了一点拍照，但原来的座位还被他占着，别人不会补上来。

**要点：**
- 相对定位仍占据原来的位置。
- top/right/bottom/left 是相对自身原位置偏移。
- 常作为绝对定位子元素的定位参照。

**示例代码：**

```css
.card { position: relative; }
```

#### 3.4.2 绝对定位 absolute

- 来源：17-定位布局-绝对定位.html

**通俗理解：** absolute 像把便利贴贴到最近的定位父盒子上，它不再占原来的排版位置，其他内容会当它不存在。

**要点：**
- 绝对定位脱离文档流，不占原位置。
- 相对于最近的有定位祖先元素定位；没有则相对于初始包含块。
- 常用于轮播箭头、角标、遮罩、下拉菜单。
- 口诀：子绝父相。

**示例代码：**

```css
.parent { position: relative; }
.badge {
  position: absolute;
  right: 8px;
  top: 8px;
}
```

#### 3.4.3 固定定位 fixed

- 来源：19-定位布局-固定定位.html

**要点：**
- 固定定位相对于浏览器视口定位。
- 页面滚动时位置不变。
- 常用于返回顶部、固定导航、客服按钮。

**示例代码：**

```css
.backtop {
  position: fixed;
  right: 30px;
  bottom: 30px;
}
```

#### 3.4.4 粘性定位 sticky

- 来源：20-定位布局-粘性定位.html；21-定位布局-表格的粘性定位.html

**要点：**
- sticky 是 relative 和 fixed 的混合效果。
- 滚动到指定阈值前按普通流排列，达到阈值后像 fixed 一样固定。
- 必须设置 top/bottom/left/right 中至少一个阈值。
- 父容器 overflow 设置不当可能导致 sticky 失效。

**示例代码：**

```css
thead {
  position: sticky;
  top: 0;
  background: white;
}
```

#### 3.4.5 z-index 叠放次序

- 来源：22-定位布局-z-index叠放次序.html

**通俗理解：** z-index 像桌面上叠纸片的层级，数字大的一般盖在上面；但如果纸片被装进不同文件夹，先比较文件夹层级，再比较里面的纸片。

**要点：**
- z-index 只对定位元素或特定布局上下文中的元素生效。
- 数值越大越靠上。
- 不要随意写巨大数值，应建立清晰层级，如 dropdown=100、modal=1000。
- 父元素形成新的层叠上下文时，子元素无法越出父级层级比较。

### 3.5 Grid 网格布局

#### 3.5.1 容器与轨道

- 来源：23-网格布局-gird容器以及网格轨道.html；24-网格布局-fr分配以及gap间隙.html

**通俗理解：** Grid 像先画一张表格，再把内容放进格子里。columns 是列，rows 是行，gap 是格子之间的缝。

**要点：**
- display:grid 创建网格容器。
- grid-template-columns 定义列轨道。
- grid-template-rows 定义行轨道。
- gap 设置行列间距。
- Grid 适合二维布局：同时控制行和列。

**示例代码：**

```css
.grid {
  display: grid;
  grid-template-columns: 200px 1fr 200px;
  grid-template-rows: auto 1fr auto;
  gap: 16px;
}
```

#### 3.5.2 fr 单位

- 来源：24-网格布局-fr分配以及gap间隙.html

**通俗理解：** fr 像分蛋糕：固定宽度先切走，剩下的空间再按 1fr、2fr 这些份数分。

**要点：**
- fr 表示可用空间的一份。
- 1fr 1fr 1fr 表示三列均分。
- 固定宽度和 fr 可混用，例如 240px 1fr。
- fr 只分配剩余空间，不等同于百分比。

**示例代码：**

```css
.grid { grid-template-columns: 240px 1fr 1fr; }
```

#### 3.5.3 repeat 与自动填充

- 来源：26-网格布局-repeat自动填充.html；27-网格布局-仿字体图标响应式布局效果.html

**通俗理解：** repeat 像复制同一种列宽规则；auto-fill 像货架自动摆商品，空间够就多摆一列，不够就少摆一列。

**要点：**
- repeat(4, 1fr) 表示重复 4 次 1fr。
- auto-fill 会尽可能填充更多列。
- minmax(min, max) 可以设置轨道最小和最大尺寸。
- repeat(auto-fill, minmax(180px, 1fr)) 是响应式卡片网格常用写法。

**示例代码：**

```css
.cards {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(180px, 1fr));
  gap: 20px;
}
```

#### 3.5.4 网格线与项目放置

- 来源：28-网格布局-网格线仿B站布局.html；29-网格布局-网格填充方式以及图片缩放.html

**要点：**
- grid-column: 1 / 3 表示从第 1 条列线跨到第 3 条列线。
- grid-row 控制行方向跨度。
- span n 表示跨 n 个轨道。
- 可用于 B 站式复杂卡片布局。

**示例代码：**

```css
.hero-card {
  grid-column: 1 / span 2;
  grid-row: 1 / span 2;
}
```

#### 3.5.5 项目对齐

- 来源：30-网格布局-项目对齐方式.html

**要点：**
- justify-items 控制项目在单元格内的水平方向对齐。
- align-items 控制项目在单元格内的垂直方向对齐。
- place-items 是 align-items 和 justify-items 的简写。
- justify-content/align-content 控制整个网格在容器中的分布。

### 3.6 多栏布局 column

- 来源：31-多栏布局column.html

**要点：**
- column-count 设置列数。
- column-width 设置期望列宽。
- column-gap 设置列间距。
- column-rule 设置列之间的分隔线。
- 适合瀑布式文本、报纸式排版，不适合需要精确控制每个卡片位置的复杂布局。

**示例代码：**

```css
.article {
  column-count: 3;
  column-gap: 32px;
  column-rule: 1px solid #ddd;
}
```

### 3.7 项目实战：小兔鲜首页

- 来源：03-现代网页布局/代码/16-小兔鲜首页项目

**要点：**
- base.css 负责基础样式和初始化。
- common.css 负责头部、底部等公共模块。
- index.css 负责首页独有模块。
- images 放公共图片，uploads 放内容图片。
- 真实项目要把布局、公共组件、页面样式拆开，避免所有 CSS 堆在一个文件中。

## 4 交互动效设计

- 标签：动效
- 来源：04-交互动效设计/笔记/交互动效设计_20250901095241.pdf；04-交互动效设计/代码/01-20 示例

**概述：** 对应 04-交互动效设计，包含 2D/3D transform、transition、animation 和动效案例。

### 4.1 2D transform

#### 4.1.1 位移 translate

- 来源：01-2D变化-位移translate.html

**要点：**
- translate(x, y) 按自身坐标系移动元素。
- translateX/translateY 分别控制单方向。
- 百分比位移相对于元素自身尺寸，而不是父元素。
- 位移不会影响其他元素布局位置，适合动画。

**示例代码：**

```css
.box:hover { transform: translateX(60px); }
```

#### 4.1.2 旋转 rotate

- 来源：02-2D变化-旋转rotate.html；06-2D变化-汽车滚动效果.html

**要点：**
- rotate(角度) 控制元素围绕变换原点旋转。
- 角度单位 deg，正值通常顺时针。
- transform-origin 可修改旋转中心。
- 轮子滚动、加载图标、卡片翻转都常用旋转。

**示例代码：**

```css
.wheel { transform: rotate(360deg); }
```

#### 4.1.3 缩放 scale

- 来源：03-2D变化-缩放scale.html

**要点：**
- scale(1.2) 放大到 1.2 倍。
- scale(0.8) 缩小到 0.8 倍。
- scaleX/scaleY 可单独控制方向。
- hover 放大图片时建议父级 overflow:hidden，避免溢出。

**示例代码：**

```css
.card:hover img { transform: scale(1.08); }
```

#### 4.1.4 斜切 skew

- 来源：04-2D变化-斜切skew.html

**要点：**
- skew(x, y) 让元素沿坐标轴倾斜。
- 适合做平行四边形按钮、动感背景条。
- 文本也会被斜切，必要时给内部元素反向 skew 还原。

#### 4.1.5 多组 transform 顺序

- 来源：05-2D变化多组变化.html

**要点：**
- 多个 transform 写在同一个 transform 属性里。
- 后写 transform 会覆盖先写 transform，不能分多条写。
- 变换顺序会影响最终结果，例如先旋转再位移和先位移再旋转不同。

**示例代码：**

```css
.box:hover {
  transform: translateX(600px) rotate(360deg);
}
```

### 4.2 transition 过渡

- 来源：04-交互动效设计/代码 多个 hover 案例

**通俗理解：** transition 像给状态变化加缓冲：按钮从普通状态变成 hover 状态时，不是瞬间跳过去，而是在指定时间里慢慢变过去。

**要点：**
- transition 让属性变化在一段时间内平滑完成。
- 常用组成：transition-property、transition-duration、transition-timing-function、transition-delay。
- 简写：transition: all .3s ease;
- 只有能计算中间值的属性才适合过渡，例如颜色、尺寸、透明度、transform。
- display:none 到 block 无法直接过渡，常用 opacity/visibility/transform 替代。

**示例代码：**

```css
.btn {
  transition: transform .25s ease, background-color .25s ease;
}
.btn:hover {
  transform: translateY(-2px);
}
```

### 4.3 3D transform

#### 4.3.1 rotate3d / rotateX / rotateY / rotateZ

- 来源：07-3D变化-旋转rotate3D.html；09-3D变化-两面翻转的图片.html

**要点：**
- rotateX 沿 X 轴旋转，常做上下翻转。
- rotateY 沿 Y 轴旋转，常做左右翻牌。
- rotateZ 等同普通 2D rotate。
- 3D 旋转要配合 perspective 才有空间透视感。

#### 4.3.2 透视 perspective

- 来源：08-3D变化-透视效果.html

**通俗理解：** perspective 像你离舞台的距离：距离越近，前后大小差异越夸张；距离越远，3D 变化看起来越平缓。

**要点：**
- perspective 设置观察者与 Z=0 平面的距离。
- 值越小透视越强，变形越夸张。
- 一般设置在父元素上，让子元素产生 3D 透视。
- transform-style: preserve-3d 让子元素保留 3D 空间。

**示例代码：**

```css
.scene { perspective: 800px; }
.card { transform-style: preserve-3d; }
```

#### 4.3.3 translate3d

- 来源：10-3D变化-3D位移translate3d.html；19-动效案例-3D悬停相册.html；20-动效案例-3d导航.html

**要点：**
- translate3d(x, y, z) 在 3D 空间移动。
- translateZ 正值靠近观察者，负值远离观察者。
- 常和 rotateY、perspective 搭配制作 3D 导航、相册。

#### 4.3.4 背面隐藏 backface-visibility

- 来源：09-3D变化-两面翻转的图片.html；素材/练习案例/01-翻转卡片

**通俗理解：** 把卡片想成扑克牌：翻到背面时，如果不隐藏背面，正反两面的内容可能同时透出来；hidden 就像只让朝向你的那一面可见。

**要点：**
- 元素翻转到背面时，默认背面可能可见。
- backface-visibility: hidden 可隐藏背面。
- 两面翻转卡片通常让正反两面 absolute 重叠，并分别旋转 0deg/180deg。

**示例代码：**

```css
.face {
  backface-visibility: hidden;
}
.back {
  transform: rotateY(180deg);
}
```

### 4.4 animation 动画

#### 4.4.1 @keyframes

- 来源：11-动画animation-基本使用.html

**要点：**
- @keyframes 定义动画关键帧。
- from/to 等同 0%/100%。
- 可以写多个百分比阶段控制复杂过程。
- 关键帧只定义变化，元素需要通过 animation 调用。

**示例代码：**

```css
@keyframes move {
  0% { transform: translateX(0); }
  100% { transform: translateX(300px); }
}
```

#### 4.4.2 animation 完整写法

- 来源：12-动画animation完整写法.html

**通俗理解：** animation 像一段提前写好的剧本：元素不需要用户 hover，也能按关键帧、时长、次数、方向自己播放。

**要点：**
- animation-name：动画名称。
- animation-duration：持续时间。
- animation-timing-function：速度曲线。
- animation-delay：延迟。
- animation-iteration-count：播放次数，infinite 表示无限。
- animation-direction：方向，例如 alternate 往返。
- animation-fill-mode：结束前后样式保持方式。
- animation-play-state：running/paused。

**示例代码：**

```css
.box {
  animation: move 2s linear 0s infinite alternate both;
}
```

#### 4.4.3 逐帧动画 steps

- 来源：14-动画animation-逐帧动画仿360官网效果.html

**要点：**
- steps(n) 让动画分 n 步跳变，不做平滑过渡。
- 适合精灵图帧动画，例如人物走路、加载序列。
- 需要配合 background-position 移动整张帧图。

**示例代码：**

```css
.sprite {
  animation: run 1s steps(8) infinite;
}
```

### 4.5 典型动效案例

- 来源：15-动效案例-流光渐变边框按钮.html；16-20 动效案例；素材/练习案例

**要点：**
- 流光渐变边框按钮：伪元素 + 渐变背景 + filter blur + animation。
- 卡片折叠效果：hover 改变宽度、透明度或 transform。
- 图片轮播滚动：容器 overflow:hidden，内部列表用 animation 横向移动。
- 3D 导航：transform-style: preserve-3d，hover 时旋转到另一面。
- 悬停侧边栏：宽度/transform 过渡，图标和提示文字联动。

## 5 前沿技术拓展

- 标签：拓展
- 来源：05-前沿技术拓展/笔记/前沿技术拓展_20250901095349.pdf；05-前沿技术拓展/代码/01-20 示例

**概述：** 对应 05-前沿技术拓展，包含 SVG、clip-path、filter、backdrop-filter、CSS 变量、calc、vh、滚动时间线等。

### 5.1 SVG

#### 5.1.1 SVG 基本使用

- 来源：01-svg基本使用.html

**要点：**
- SVG 是矢量图，放大不失真。
- 可以直接写在 HTML 中，也可以作为 img、background、object 引入。
- viewBox 决定 SVG 内部坐标系，是响应式缩放的关键。
- 常见形状：rect、circle、ellipse、line、polyline、polygon、path。

**示例代码：**

```html
<svg viewBox="0 0 100 100" width="100" height="100">
  <circle cx="50" cy="50" r="40" fill="pink" />
</svg>
```

#### 5.1.2 描边 stroke

- 来源：02-svg常见属性以及描边效果.html

**要点：**
- stroke 设置描边颜色。
- stroke-width 设置描边粗细。
- fill 设置填充颜色。
- stroke-linecap 控制线段端点，round 可做圆头线。
- stroke-linejoin 控制连接处样式。

#### 5.1.3 SVG 描边动画

- 来源：03-svg描边动画效果.html；04-svg案例-仿voppo里程碑效果.html

**要点：**
- stroke-dasharray 设置虚线长度。
- stroke-dashoffset 设置虚线偏移。
- 把 dasharray 设为路径长度，再动画 dashoffset，可实现线条逐渐画出的效果。
- 适合 Logo 描边、路径加载、时间轴线条。

**示例代码：**

```css
path {
  stroke-dasharray: 1000;
  stroke-dashoffset: 1000;
  animation: draw 2s linear forwards;
}
@keyframes draw { to { stroke-dashoffset: 0; } }
```

### 5.2 clip-path 裁剪

- 来源：06-clip-path基本使用.html；07-clip-path文字裁剪.html；鼠标移动裁剪效果

**要点：**
- clip-path 可以按形状裁剪元素可见区域。
- circle() 圆形裁剪，ellipse() 椭圆裁剪，polygon() 多边形裁剪。
- inset() 可以做矩形裁剪并支持圆角。
- 适合文字裁剪、图片特殊形状、鼠标跟随显隐效果。
- 被裁剪掉的区域不可见，但元素盒子仍按原尺寸参与布局。

**示例代码：**

```css
.avatar { clip-path: circle(50% at center); }
.banner { clip-path: polygon(0 0, 100% 0, 85% 100%, 0 100%); }
```

### 5.3 CSS filter 滤镜

- 来源：09-css filter滤镜效果.html；10-3D悬停相册添加模糊.html；小兔鲜首页项目改为灰色

**要点：**
- filter 作用于元素自身内容。
- blur() 模糊，grayscale() 灰度，brightness() 亮度，contrast() 对比度。
- saturate() 饱和度，hue-rotate() 色相旋转，drop-shadow() 投影。
- 多个滤镜可以连写，顺序会影响结果。
- 图片灰色处理可用 filter: grayscale(100%)。

**示例代码：**

```css
.photo:hover {
  filter: grayscale(0) saturate(120%) contrast(105%);
}
```

### 5.4 背景滤镜 backdrop-filter

- 来源：11-CSS背景滤镜.html

**通俗理解：** filter 是给自己加滤镜，backdrop-filter 是给身后的画面加滤镜。玻璃效果看的不是玻璃本身模糊，而是玻璃后面的内容被模糊了。

**要点：**
- backdrop-filter 作用于元素背后的内容，而不是元素自身。
- 常见玻璃拟态写法：半透明背景 + backdrop-filter: blur(10px)。
- 需要元素背景有透明度，否则看不出背后模糊。
- 部分浏览器可能需要 -webkit-backdrop-filter。

**示例代码：**

```css
.glass {
  background: rgba(255,255,255,.35);
  backdrop-filter: blur(12px);
}
```

### 5.5 CSS 变量 var()

- 来源：14-变量var的使用.html

**通俗理解：** CSS 变量像给颜色和间距起外号：先说 --brand 是粉色，后面所有按钮都用 var(--brand)。以后换主题，只改这个外号对应的值。

**要点：**
- CSS 自定义属性以 -- 开头，例如 --main-color。
- 使用 var(--main-color) 读取变量。
- 变量有作用域，定义在 :root 上可全局使用。
- var() 可以提供兜底值：var(--gap, 16px)。
- 主题切换常通过修改根元素上的 CSS 变量实现。

**示例代码：**

```css
:root { --brand: #d83f87; }
.btn { background: var(--brand); }
```

### 5.6 calc() 计算函数

- 来源：15-计算函数calc函数使用.html；16-变量和calc计算函数的应用.html

**通俗理解：** calc 像 CSS 里的计算器：比如页面宽度是 100%，侧边栏固定 240px，正文就可以写成 calc(100% - 240px)。

**要点：**
- calc() 可混合不同单位做计算。
- 运算符 + - * / 两侧建议保留空格，尤其是 + 和 -。
- 常用于宽度减固定侧栏、高度减头部、间距动态计算。
- calc 可以和 CSS 变量结合。

**示例代码：**

```css
.main {
  width: calc(100% - 240px);
  min-height: calc(100vh - var(--header-height));
}
```

### 5.7 视口单位 vh

- 来源：20-vh单位.html

**要点：**
- 1vh 等于视口高度的 1%。
- 100vh 常用来让首屏或容器占满一屏高度。
- 移动端浏览器地址栏会影响 vh 的实际体验，现代浏览器提供 svh、lvh、dvh 作为补充。
- 课程中的 vh 示例适合理解视口单位与百分比的区别。

**示例代码：**

```css
.screen { min-height: 100vh; }
```

### 5.8 滚动驱动动画

- 来源：12-动画时间线-滚动时间线.html；13-动画时间线-视图时间线.html；综合案例4-页面滚动的卡片网页

**要点：**
- scroll-timeline 可以让动画进度跟随滚动容器。
- view-timeline 可以让动画进度跟随元素进入视口的过程。
- 这类能力属于较新的 CSS 特性，使用前要关注浏览器兼容性。
- 适合页面滚动卡片、进度条、进入视口渐显等效果。

## 6 移动网页开发

- 标签：移动端
- 来源：06-移动网页开发/笔记/移动网页布局_20250901095447.pdf；06-移动网页开发/代码

**概述：** 对应 06-移动网页开发，核心是移动端基础、视口、vw/rem 适配和移动端项目实践。

### 6.1 移动端基础

- 来源：01-移动端知识.html

**要点：**
- 移动端页面必须设置 viewport，否则会按桌面页面缩放显示。
- 移动端布局要考虑屏幕宽度多样、触摸操作、图片清晰度、网络环境。
- 常用布局方式：Flex、百分比、vw、rem、媒体查询。
- 点击区域要足够大，按钮和表单控件不要过小。

**示例代码：**

```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### 6.2 vw / vmin 适配

- 来源：02-vw单位和插件使用.html；03-m-home/index-vmin.html；03-m-home/css/index-vmin.css

**通俗理解：** vw 像用屏幕宽度当尺子：屏幕越宽，1vw 就越大。375px 设计稿里 100px，大约就是 26.6667vw。

**要点：**
- 1vw 等于视口宽度的 1%。
- 设计稿宽度为 375px 时，1px 可换算为 100/375 vw。
- vmin 表示 vw 和 vh 中较小的值，可用于横竖屏都需要保持比例的场景。
- vw 适配不依赖 JS，写法直接，但复杂项目可结合插件自动转换。

**示例代码：**

```css
.box {
  width: 26.6667vw; /* 100px / 375px * 100 */
}
```

### 6.3 rem 适配

- 来源：03-rem单位和动态修改html元素大小.html；04-rem适配方案和插件使用.html；js/flexible.js

**通俗理解：** rem 像全站共用一把尺子：html 的 font-size 是尺子刻度，所有 rem 尺寸都会跟着这把尺子一起放大或缩小。

**要点：**
- rem 是相对于 html 根元素 font-size 的单位。
- 通过 JS 或媒体查询动态修改 html 字号，可以让页面整体等比缩放。
- flexible.js 的思路是根据视口宽度计算根字号。
- rem 适合大量尺寸跟随屏幕整体缩放的移动端页面。

**示例代码：**

```css
document.documentElement.style.fontSize = document.documentElement.clientWidth / 10 + 'px';
.box { width: 2rem; }
```

### 6.4 移动端项目 m-home

- 来源：06-移动网页开发/代码/03-m-home

**要点：**
- base.css 处理移动端基础样式和通用重置。
- index.css 写首页布局，login.css 写登录页布局。
- 底部 tab 栏、搜索、卡片、图标按钮都适合用 Flex。
- 图片和 SVG 图标要注意显示尺寸与实际资源清晰度。

## 7 响应网页开发

- 标签：响应式
- 来源：07-响应网页开发/笔记/响应网页开发_20250901095556.pdf；07-响应网页开发/代码

**概述：** 对应 07-响应网页开发，覆盖媒体查询、响应式布局、Bootstrap 和 vivo 响应式案例。

### 7.1 媒体查询 @media

- 来源：01-媒体查询语法.html

**通俗理解：** 媒体查询像给不同屏幕准备不同衣服：手机穿一列布局，平板穿两列布局，电脑穿更宽的布局。

**要点：**
- @media 媒体类型 and (媒体特性) { 样式 }。
- screen 表示屏幕设备，是网页最常见的媒体类型。
- min-width 表示视口宽度大于等于某值时生效。
- max-width 表示视口宽度小于等于某值时生效。
- 多个条件可以用 and 连接，形成区间。

**示例代码：**

```css
@media screen and (min-width: 1200px) {
  body { background: green; }
}
@media screen and (min-width: 768px) and (max-width: 1200px) {
  body { background: orange; }
}
@media screen and (max-width: 768px) {
  body { background: red; }
}
```

### 7.2 响应式断点思路

- 来源：02-仿京东响应式布局.html；03-响应式国外网站

**通俗理解：** 断点不是固定背几个数字，而是看内容什么时候放不下。就像搬家时箱子装不下了才换大箱子，不是每次都固定换同一个箱子。

**要点：**
- 常见断点不是死规则，要根据内容和设计决定。
- 移动优先：先写小屏样式，再用 min-width 增强大屏。
- 桌面优先：先写大屏样式，再用 max-width 覆盖小屏。
- 断点附近要重点检查文字换行、图片裁切、导航收纳、卡片列数。

### 7.3 Bootstrap 基本使用

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

### 7.4 Bootstrap 栅格系统

- 来源：04-BootStrap布局(重点).html

**通俗理解：** Bootstrap 栅格像把一行切成 12 份：col-6 占半行，col-4 占三分之一，col-md-4 表示到 md 尺寸及以上才按三分之一排。

**要点：**
- 一行使用 .row。
- 列使用 .col、.col-6、.col-md-4 等 class。
- Bootstrap 栅格默认一行 12 份。
- 断点前缀 sm、md、lg、xl、xxl 表示在对应屏幕及以上生效。
- g-*、gx-*、gy-* 控制网格间距。

**示例代码：**

```html
<div class="container">
  <div class="row g-3">
    <div class="col-12 col-md-6 col-lg-4">卡片</div>
  </div>
</div>
```

### 7.5 响应式项目案例

- 来源：02-仿京东响应式布局.html；03-响应式国外网站；06-vivo响应式网站

**要点：**
- 仿京东响应式布局用于理解不同屏幕下模块宽度和排列变化。
- 响应式国外网站案例包含导航收纳、卡片栅格、图片和内容重排。
- vivo 响应式网站结合 Bootstrap、轮播图、产品卡片和响应式图片。
- 真实响应式页面不是简单缩放，而是根据空间重新组织信息。

## 8 前端网页托管

- 标签：发布
- 来源：08-前端网页托管/前端网页托管_20250901095646.pdf

**概述：** 对应 08-前端网页托管，重点是把静态网页发布到可访问地址。

### 8.1 静态网页托管概念

**要点：**
- HTML、CSS、JS、图片等纯前端资源可以部署为静态站点。
- 托管平台会把你的文件放到服务器上，并提供访问地址。
- 入口文件通常是 index.html。
- 路径大小写、中文文件名、相对路径在发布时都要认真检查。

### 8.2 发布前检查清单

**要点：**
- 确认 index.html 位于站点根目录或平台指定目录。
- 确认 CSS、JS、图片路径在浏览器中没有 404。
- 确认页面标题、favicon、meta viewport 已设置。
- 确认移动端和桌面端主要页面都能正常显示。
- 确认不上传无关的大文件，例如安装包、压缩包、临时文件。

## 9 综合复习路线

- 标签：路线

**概述：** 把课程知识串起来，形成从结构到样式、布局、动效、适配、发布的学习路线。

### 9.1 第一阶段：HTML 结构

**要点：**
- 先掌握文档骨架、语义标签、图片、链接、列表、表格、表单。
- 能独立写出一个结构清晰的静态页面。
- 重点习惯：先写内容结构，再写 CSS。

### 9.2 第二阶段：CSS 美化

**要点：**
- 掌握选择器、字体文本、盒子模型、背景、阴影、圆角。
- 重点理解盒子尺寸、margin 合并、border-box。
- 能做卡片、导航、侧边栏、文章排版。

### 9.3 第三阶段：布局能力

**要点：**
- 理解 display、浮动历史用法、定位、Flex、Grid。
- Flex 解决一维排列，Grid 解决二维网格。
- 定位用于局部叠放和固定元素，不应滥用来做整页布局。

### 9.4 第四阶段：交互与视觉增强

**要点：**
- transition 负责状态之间的平滑变化。
- transform 负责位移、旋转、缩放、3D 空间。
- animation 负责不依赖用户触发的持续或关键帧动画。
- filter、clip-path、SVG 让视觉表达更丰富。

### 9.5 第五阶段：移动端与响应式

**要点：**
- 移动端先理解 viewport，再学习 vw/rem 适配。
- 响应式重点是媒体查询和断点设计。
- Bootstrap 可以快速搭建响应式页面，但仍要理解底层栅格和 CSS。
