### Web APIs 介绍

严格意义上讲，我们在 JavaScript 阶段学习的知识绝大部分属于 ECMAScript 的知识体系，ECMAScript 简称 ES 它提供了一套语言标准规范，如变量、数据类型、表达式、语句、函数等语法规则都是由 ECMAScript 规定的。浏览器将 ECMAScript 大部分的规范加以实现，并且在此基础上又扩展一些实用的功能，这些被扩展出来的内容我们称为 Web APIs。

ECMAScript 运行在浏览器中然后再结合 Web APIs 才是真正的 JavaScript，Web APIs 的核心是 DOM 和 BOM。

### JavaScript 组成

- **ECMAScript**：规定了js基础语法核心知识，比如：变量、分支语句、循环语句、对象等等
- **Web APIs**：
  - **DOM**：文档对象模型，定义了一套操作HTML文档的API
  - **BOM**：浏览器对象模型，定义了一套操作浏览器窗口的API

---

### DOM 基础

**概念**

DOM（Document Object Model）是将整个 HTML 文档的每一个标签元素视为一个对象，这个对象下包含了许多的属性和方法，通过操作这些属性或者调用这些方法实现对 HTML 的动态更新，为实现网页特效以及用户交互提供技术支撑。

简言之 DOM 是用来动态修改 HTML 的，其目的是开发网页特效及用户交互。

#### DOM 树

将 HTML 文档以树状结构直观的表现出来，我们称之为文档树或 DOM 树，**文档树直观的体现了标签与标签之间的关系。**

#### DOM 节点

节点是文档树的组成部分，**每一个节点都是一个 DOM 对象**，主要分为元素节点、属性节点、文本节点等。

1. 【元素节点】其实就是 HTML 标签，如 `head`、`div`、`body` 等都属于元素节点。
2. 【属性节点】是指 HTML 标签中的属性，如 `a` 标签的 `href` 属性、`div` 标签的 `class` 属性。
3. 【文本节点】是指 HTML 标签的文字内容，如 `title` 标签中的文字。
4. 【根节点】特指 `html` 标签。

#### document

`document` 是 JavaScript 内置的专门用于 DOM 的对象，该对象包含了若干的属性和方法，`document` 是学习 DOM 的核心。

```html
<script>
  // document 是内置的对象
  // 1. 通过 document 获取根节点
  console.log(document.documentElement); // 对应 html 标签

  // 2. 通过 document 获取 body 节点
  console.log(document.body); // 对应 body 标签

  // 3. 通过 document.write 方法向网页输出内容
  document.write('Hello World!');
</script>
```

### 获取 DOM 对象

使用css选择器来获取dom元素

1. `querySelector`：满足条件的第一个元素

2. `querySelectorAll`：满足条件的元素集合，返回**伪数组**(不能增删改)

3. 了解其他方式：(现在不怎么使用)
   - ```
     /根据id获取一个元素
     document.getElementById('nav')
     //根据标签获取一类元素获取页面所有div
     document.getElementsByTagName('div')
     //根据类名获取元素 获取页面所有类名为w的
     document.getElementsByClassName('w')
     ```

```html
<script>
  const p = document.querySelector('p')  // 获取第一个p元素
  const lis = document.querySelectorAll('li')  // 获取所有li元素
</script>
```

### 操作元素内容

通过修改 DOM 的文本内容，动态改变网页的内容。

**innerText**

将文本内容添加/更新到任意标签位置，**文本中包含的标签不会被解析。**

```html
<script>
  const intro = document.querySelector('.intro')
  intro.innerText = '嗨~ 我叫李雷！'
  intro.innerText = '<h4>嗨~ 我叫李雷！</h4>'  // h4标签不会被解析
</script>
```

**innerHTML**

将文本内容添加/更新到任意标签位置，**文本中包含的标签会被解析。**

```html
<script>
  const intro = document.querySelector('.intro')
  intro.innerHTML = '嗨~ 我叫韩梅梅！'
  intro.innerHTML = '<h4>嗨~ 我叫韩梅梅！</h4>'  // h4标签会被解析
</script>
```

> 总结：如果文本内容中包含 `html` 标签时推荐使用 `innerHTML`，否则建议使用 `innerText` 属性。

### 操作元素属性

有3种方式可以实现对属性的修改：

#### 常用属性修改

直接通过属性名修改，最简洁的语法

```html
<script>
  const pic = document.querySelector('.pic')
  pic.src = './images/lion.webp'
  pic.width = 400;
  pic.alt = '图片不见了...'
</script>
```

#### 控制样式属性

**1. 通过 style 属性修改样式**

通过元素节点获得的 `style` 属性本身的数据类型也是对象，如 `box.style.color`、`box.style.width` 分别用来获取元素节点 CSS 样式的 `color` 和 `width` 的值。

```html
<script>
  const box = document.querySelector('.box')
  box.style.color = 'red'
  box.style.width = '300px'
  // css 属性的 - 连接符与 JavaScript 的减运算符冲突，所以要改成驼峰法
  box.style.backgroundColor = 'pink'
</script>
```

> 注意：如要遇到 `css` 属性中包含字符 `-` 时，要将 `-` 去掉并将其后面的字母改成大写，如 `background-color` 要写成 `box.style.backgroundColor`

**2. 通过 className 操作CSS**

如果修改的样式比较多，直接通过style属性修改比较繁琐，我们可以通过借助于css类名的形式。

```html
<script>
  const box = document.querySelector('.box')
  box.className = 'pink'
</script>
```

> 注意：
>
> 1. 由于class是关键字，所以使用className去代替
> 2. className是使用新值换旧值，如果需要添加一个类，需要保留之前的类名

**3. 通过 classList 操作类控制CSS**

为了解决className 容易覆盖以前的类名，我们可以通过classList方式追加和删除类名

```html
<script>
  let box = document.querySelector('div')
  // add() 添加类
  box.classList.add('active')
  // remove() 移除类
  box.classList.remove('one')
  // toggle() 切换类
  box.classList.toggle('one')
</script>
```

#### 操作表单元素属性

表单很多情况，也需要修改属性，比如点击眼睛，可以看到密码，本质是把表单类型转换为文本框

获取：DOM对象.属性名
设置：DOM对象.属性名 = 新值

```html
<script>
  let input = document.querySelector('input')
  input.value = '小米手机'
  input.type = 'password'

  let btn = document.querySelector('button')
  btn.disabled = false  // 启用按钮

  let checkbox = document.querySelector('.agree')
  checkbox.checked = false  // 取消勾选
</script>
```

#### 自定义属性

**标准属性**：标签天生自带的属性，比如class、id、title等，可以直接使用点语法操作

**自定义属性**：在HTML5中推出了专门的 `data-` 自定义属性

- 在标签上一律以 `data-` 开头
- 在DOM对象上一律以 `dataset` 对象方式获取

```html
<div data-id="1"> 自定义属性 </div>
<script>
  let div = document.querySelector('div')
  console.log(div.dataset.id)  // 1
</script>
```

---

### 事件

事件是编程语言中的术语，它是用来描述程序的行为或状态的，**一旦行为或状态发生改变，便立即调用一个函数。**

#### 事件监听

结合 DOM 使用事件时，需要为 DOM 对象添加事件监听，等待事件发生（触发）时，便立即调用一个函数。

`addEventListener` 是 DOM 对象专门用来添加事件监听的方法，它的两个参数分别为【事件类型】和【事件回调】。

```html
<script>
  const btn = document.querySelector('#btn')
  btn.addEventListener('click', function () {
    console.log('等待事件被触发...')
    let text = document.getElementById('text')
    text.style.color = 'red'
  })
</script>
```

完成事件监听分成3个步骤：

1. 获取 DOM 元素
2. 通过 `addEventListener` 方法为 DOM 节点添加事件监听
3. 等待事件触发，如用户点击了某个按钮时便会触发 `click` 事件类型
4. 事件触发后，相对应的回调函数会被执行

#### 事件类型

将众多的事件类型分类可分为：鼠标事件、键盘事件、表单事件、焦点事件等。

**鼠标事件**

鼠标事件是指跟鼠标操作相关的事件，如单击、双击、移动等。

| 事件类型 | 说明 |
|---------|------|
| click | 鼠标单击 |
| dblclick | 鼠标双击 |
| mouseenter | 鼠标移入 |
| mouseleave | 鼠标移出 |

```html
<script>
  const box = document.querySelector('.box')
  
  // 监听鼠标移入
  box.addEventListener('mouseenter', function () {
    this.innerText = '鼠标移入了...'
    this.style.cursor = 'move'
  })
  
  // 监听鼠标移出
  box.addEventListener('mouseleave', function () {
    this.innerText = '鼠标移出了...'
  })
</script>
```

**键盘事件**

| 事件类型 | 说明 |
|---------|------|
| keydown | 键盘按下触发 |
| keyup | 键盘抬起触发 |

**焦点事件**

| 事件类型 | 说明 |
|---------|------|
| focus | 获得焦点 |
| blur | 失去焦点 |

**文本框输入事件**

| 事件类型 | 说明 |
|---------|------|
| input | 文本框输入触发 |
| change | 值被修改并且失去焦点后触发 |

#### 事件对象

任意事件类型被触发时与事件相关的信息会被以对象的形式记录下来，我们称这个对象为事件对象。

```html
<script>
  const box = document.querySelector('.box')
  box.addEventListener('click', function (e) {
    console.log(e)  // 事件对象
  })
</script>
```

事件回调函数的【第1个参数】即所谓的事件对象，通常习惯性的将这个对象命名为 `event`、`ev`、`e`。

事件对象中包含的有用信息：

1. `ev.type`：当前事件的类型
2. `ev.clientX/Y`：光标相对浏览器窗口的位置
3. `ev.offsetX/Y`：光标相对于当前 DOM 元素的位置
4. `ev.target`：真正触发事件的元素

`trim()`方法可以去除字符串左右的空格

**环境对象**

环境对象：指的是函数内部特殊的变量 this ，它代表着当前函数运行时所处的环境

作用：弄清楚this的指向，可以让我们代码更简洁 
函数的调用方式不同，this 指代的对象也不同  
【谁调用， this 就是谁】 是判断 this 指向的粗略规则
直接调用函数，其实相当于是 window.函数，所以 this 指代 window

**回调函数**

如果将函数 A 做为参数传递给函数 B 时，我们称函数 A 为回调函数 

简单理解： 当一个函数当做参数来传递给另外一个函数的时候，这个函数就是回调函数

```
function fn() {
	console.log('我是回调函数...')
}
//fn传递给了setInterval，fn就是回调函数
setInterval(fn,1000)
```

```
box.addEventListener('click',function () {
console.log('我也是回调函数'）
})
```

#### 事件流

事件流是对事件执行过程的描述，了解事件的执行过程有助于加深对事件的理解，提升开发实践中对事件运用的灵活度。

任意事件被触发时总会经历两个阶段：【捕获阶段】和【冒泡阶段】。

- **捕获阶段**：从父到子的传导过程
- **冒泡阶段**：从子向父的传导过程

```html
<script>
  const outer = document.querySelector('.outer')
  const inner = document.querySelector('.inner')
  
  // 默认是冒泡模式（false）
  outer.addEventListener('click', function () {
    console.log('outer...')
  })
  
  // 设置为捕获模式（true）
  inner.addEventListener('click', function () {
    console.log('inner...')
  }, true)
</script>
```

> 结论：
>
> 1. `addEventListener` 第3个参数决定了事件是在捕获阶段触发还是在冒泡阶段触发
> 2. `addEventListener` 第3个参数为 `true` 表示捕获阶段触发，`false` 表示冒泡阶段触发，默认值为 `false`
> 3. 事件流只会在父子元素具有相同事件类型时才会产生影响
> 4. 绝大部分场景都采用默认的冒泡模式

#### 阻止冒泡

阻止冒泡是指阻断事件的流动，保证事件只在当前元素被执行，而不再去影响到其对应的祖先元素。

```html
<script>
  const inner = document.querySelector('.inner')
  inner.addEventListener('click', function (ev) {
    console.log('inner...')
    ev.stopPropagation()  // 阻止事件冒泡
  })
</script>
```

> 鼠标经过事件：
>
> - `mouseover` 和 `mouseout` 会有冒泡效果
> - `mouseenter` 和 `mouseleave` 没有冒泡效果（推荐）

**阻止默认行为**

1.4阻止冒泡
我们某些情况下需要阻止默认行为的发生，比如阻止链接的跳转，表单域跳转
语法：
```
e.preventDefault()
<form action="http://www.baidu.com&quot;&gt;
	<inputtype="submit"value="提交">
</form>
<script>
	const form= document.querySelector('form')
	form.addEventListener('click',function (e){
	//阻止表单默认提交行为
	e.preventDefault()
})
```
**事件解绑**

on事件方式，直接使用null覆盖偶就可以实现事件的解绑
语法：

```
//绑定事件
btn.onclick = function (){
	alert('点击了'）
}
//解绑事件
btn.onclick= null
```

addEventListener方式，必须使用：
removeEventListener(事件类型，事件处理函数，[获取捕获或者冒泡阶段])
例如：

```html
<script>
	function fn() {
	alert(`点击了')
	}
//绑定事件
	btn.addEventListener('click',fn)
//解绑事件
	btn.removeEventListener('click',fn)
<script>
```

**注意：匿名函数无法被解绑**



**两种注册事件的区别** l 

传统on注册（L0） 
1.同一个对象,后面注册的事件会覆盖前面注册(同一个事件)
2.直接使用null覆盖偶就可以实现事件的解绑
3.都是冒泡阶段执行的 

事件监听注册（L2）
1.语法: addEventListener(事件类型, 事件处理函数, 是否使用捕获) 
2.后面注册的事件不会覆盖前面注册的事件(同一个事件) 
3.可以通过第三个参数去确定是在冒泡或者捕获阶段执行 
4.必须使用removeEventListener(事件类型, 事件处理函数, 获取捕获或者冒泡阶段) 
5.匿名函数无法被解绑

#### 事件委托

事件委托是利用事件流的特征解决一些现实开发需求的知识技巧，主要的作用是提升程序效率。

大量的事件监听是比较耗费性能的，利用事件流的特征，可以对代码进行优化：

```html
<script>
  // 假设页面中有 10000 个 button 元素
  const buttons = document.querySelectorAll('table button')
  
  // 假设上述的 10000 个 button 元素共同的祖先元素是 table
  const parents = document.querySelector('table')
  parents.addEventListener('click', function (ev) {
    // 通过 ev.target 判断真正触发事件的元素
    if(ev.target.tagName === 'BUTTON') {
      // 执行的逻辑
    }
  })
</script>
```

事件对象中的属性 `target` 或 `srcElement` 属性表示真正触发事件的元素，它是一个元素类型的节点。

#### 其他事件

**页面加载事件**

加载外部资源（如图片、外联CSS和JavaScript等）加载完毕时触发的事件

```javascript
window.addEventListener('load', function() {
    // 页面资源全部加载完毕后执行
})
document.addEventListener('DOMContentLoaded', function() {
    // 初始html文档加载完毕后执行
})
```

**元素滚动事件**

滚动条在滚动的时候持续触发的事件

```javascript
window.addEventListener('scroll', function() {
    // 滚动时执行
})
```

scrollLeft和scrollTop（属性）

>获取被卷去的大小
>获取元素内容往左、往上滚出去看不到的距离
>这两个值是可读写的
>尽量在scroll事件里面获取被卷去的距离

```
div.addEventListener('scroll',function(){
	console.log(this.scrollTop)
	const n =document.documentElement.scrollTop
	console.log(n)
})
注意:document.documentElement html文档返回对象为html

window.scrollTo(x,y)
```

#### 

**页面尺寸事件**

会在窗口尺寸改变的时候触发事件

```javascript
window.addEventListener('resize', function() {
    // 窗口尺寸改变时执行
})
```

`clientWidth` `clientHeight`不包含padding、border

#### 元素尺寸与位置

获取元素的自身宽高、包含元素自身设置的宽高、padding、border

`offsetWidth` 和 `offsetHeight`：获取出来的是数值，方便计算

> 注意：获取的是可视宽高，如果盒子是隐藏的，获取的结果是0

获取位置：
>获取元素距离自己定位父级元素的左、上距离
>offsetLeft和offsetTop注意是只读属性

### 定时器

#### 间歇函数

`setInterval` 是 JavaScript 中内置的函数，它的作用是间隔固定的时间自动重复执行另一个函数，也叫定时器函数。

```
setInterval(函数,时间) 时间单位为ms
```



```html
<script>
  function repeat() {
    console.log('不知疲倦的执行下去....')
  }
  // 间隔 1000 毫秒，重复调用 repeat
  setInterval(repeat, 1000)
  let n=setInterval(repeat, 1000)
  clearInterval(n)      关闭间歇函数
</script>
```

#### 延迟函数

JavaScript 内置的一个用来让代码延迟执行的函数，叫 `setTimeout`

**语法：**

```javascript
setTimeout(回调函数, 延迟时间)
```

`setTimeout` 仅仅只执行一次，所以可以理解为就是把一段代码延迟执行

```html
<script>
  // 1. 开启延迟函数
  let timerId = setTimeout(function () {
    console.log('我只执行一次')
  }, 3000)

  // 2. 关闭延迟函数
  clearTimeout(timerId)
</script>
```

> 注意点：
>
> 1. 延时函数需要等待，所以后面的代码先执行
> 2. 返回值是一个正整数，表示定时器的编号

---

### 日期对象

ECMAScript 中内置了获取系统时间的对象 Date，使用 Date 时需要借助 `new` 关键字才能使用。

#### 实例化

```javascript
const date = new Date(); // 系统默认时间
const date = new Date('2020-05-01') // 指定时间
```

#### 方法

| 方法 | 说明 |
|------|------|
| getFullYear() | 获取四位年份 |
| getMonth() | 获取月份，取值为 0 ~ 11 |
| getDate() | 获取月份中的每一天 |
| getDay() | 获取星期，取值为 0 ~ 6 |
| getHours() | 获取小时，取值为 0 ~ 23 |
| getMinutes() | 获取分钟，取值为 0 ~ 59 |
| getSeconds() | 获取秒，取值为 0 ~ 59 |

```javascript
const date = new Date();
const year = date.getFullYear(); // 四位年份
const month = date.getMonth(); // 0 ~ 11
```

#### 时间戳

时间戳是指1970年01月01日00时00分00秒起至现在的总秒数或毫秒数，它是一种特殊的计量时间的方式。

注：ECMAScript 中时间戳是以毫秒计的。

```javascript
const date = new Date()
// 获取时间戳的方法
console.log(date.getTime())
console.log(+new Date())
console.log(Date.now())
```

---

### DOM 节点操作

#### 插入节点

在已有的 DOM 节点中插入新的 DOM 节点时，需要关注两个关键因素：首先要得到新的 DOM 节点，其次在哪个位置插入这个节点。

```html
<script>
  const btn = document.querySelector('.btn')
  btn.addEventListener('click', function () {
    // 1. 获得一个 DOM 元素节点
    const p = document.createElement('p')
    p.innerText = '创建的新的p标签'
    p.className = 'info'
    
    // 复制原有的 DOM 节点
    const p2 = document.querySelector('p').cloneNode(true)
    p2.style.color = 'red'

    // 2. 插入盒子 box 盒子
    document.querySelector('.box').appendChild(p)
    document.querySelector('.box').appendChild(p2)
  })
</script>
```

**结论：**

- `createElement`：动态创建任意 DOM 节点
- `cloneNode`：复制现有的 DOM 节点，传入参数 true 会复制所有子节点
- `appendChild`：在末尾（结束标签前）插入节点
- `insertBefore`：在父节点中任意子节点之前插入新节点

#### 删除节点

删除现有的 DOM 节点，也需要关注两个因素：首先由父节点删除子节点，其次是要删除哪个子节点。

```html
<script>
  const btn = document.querySelector('button')
  btn.addEventListener('click', function () {
    let ul = document.querySelector('ul')
    let lis = document.querySelectorAll('li')
    // 删除节点
    ul.removeChild(lis[0])
  })
</script>
```

> 结论：`removeChild` 删除节点时一定是由父子关系。

#### 查找节点

DOM 树中的任意节点都不是孤立存在的，它们要么是父子关系，要么是兄弟关系，我们可以依据节点之间的关系查找节点。

**父子关系**

| 属性 | 说明 |
|------|------|
| parentNode | 获取父节点 |
| childNodes | 获取全部的子节点，回车换行会被认为是空白文本节点 |
| children | 只获取元素类型节点 |

```html
<script>
  const ul = document.querySelector('ul')
  
  // 所有的子节点
  console.log(ul.childNodes)
  // 只包含元素子节点
  console.log(ul.children)
</script>
```

**兄弟关系**

| 属性 | 说明 |
|------|------|
| previousSibling | 获取前一个节点 |
| nextSibling | 获取后一个节点 |

```html
<script>
  const lis = document.querySelectorAll('ul li')
  for(let i = 0; i < lis.length; i++) {
    lis[i].addEventListener('click', function () {
      console.log(this.previousSibling)  // 前一个节点
      console.log(this.nextSibling)  // 下一个节点
    })
  }
</script>
```

---

### BOM 操作

#### window 对象

**BOM** (Browser Object Model) 是浏览器对象模型

- window对象是一个全局对象，也可以说是JavaScript中的顶级对象
- 像document、alert()、console.log()这些都是window的属性，基本BOM的属性和方法都是window的
- 所有通过var定义在全局作用域中的变量、函数都会变成window对象的属性和方法
- window对象下的属性和方法调用的时候可以省略window

#### location 对象

location (地址) 它拆分并保存了 URL 地址的各个组成部分，它是一个对象

| 属性/方法 | 说明 |
|----------|------|
| href | 属性，获取完整的 URL 地址，赋值时用于地址的跳转 |
| search | 属性，获取地址中携带的参数，符号 ? 后面部分 |
| hash | 属性，获取地址中的哈希值，符号 # 后面部分 |
| reload() | 方法，用来刷新当前页面，传入参数 true 时表示强制刷新 |

```html
<script>
  // 1. href属性（重点）得到完整地址，赋值则是跳转到新地址
  console.log(location.href)

  // 2. search属性 得到 ? 后面的地址
  console.log(location.search)

  // 3. hash属性 得到 # 后面的地址
  console.log(location.hash)

  // 4. reload 方法 刷新页面
  location.reload() // 页面刷新
  location.reload(true) // 强制页面刷新 ctrl+f5
</script>
```

#### navigator 对象

navigator是对象，该对象下记录了浏览器自身的相关信息

常用属性和方法：

- 通过 `userAgent` 检测浏览器的版本及平台

```javascript
// 检测 userAgent（浏览器信息）
(function () {
  const userAgent = navigator.userAgent
  // 验证是否为Android或iPhone
  const android = userAgent.match(/(Android);?[\s\/]+([\d.]+)?/)
  const iphone = userAgent.match(/(iPhone\sOS)\s([\d_]+)/)
  // 如果是Android或iPhone，则跳转至移动站点
  if (android || iphone) {
    location.href = 'http://m.itcast.cn'
  }
})();
```

#### history 对象

history (历史)是对象，主要管理历史记录，该对象与浏览器地址栏的操作相对应，如前进、后退等

| 方法 | 说明 |
|------|------|
| forward() | 前进 |
| back() | 后退 |
| go(1) | 前进 |
| go(-1) | 后退 |

```html
<script>
  // 前进
  history.forward() 
  history.go(1)
  
  // 后退
  history.back()
  history.go(-1)
</script>
```

---

### 本地存储

本地存储：将数据存储在本地浏览器中

好处：

1. 页面刷新或者关闭不丢失数据，实现数据持久化
2. 容量较大，sessionStorage和 localStorage 约 5M 左右

#### localStorage

**作用**：数据可以长期保留在本地浏览器中，刷新页面和关闭页面，数据也不会丢失

**特性**：以键值对的形式存储，并且存储的是字符串，省略了window

```html
<script>
  // 1. 存储
  localStorage.setItem('age', 18)

  // 2. 获取
  console.log(localStorage.getItem('age'))

  // 3. 删除
  localStorage.removeItem('age')
</script>
```

#### sessionStorage

**特性**：

- 用法跟localStorage基本相同
- 区别是：当页面浏览器被关闭时，存储在 sessionStorage 的数据会被清除

```javascript
// 存储
sessionStorage.setItem(key, value)
// 获取
sessionStorage.getItem(key)
// 删除
sessionStorage.removeItem(key)
```

#### localStorage 存储复杂数据类型

**问题**：本地只能存储字符串，无法存储复杂数据类型

**解决**：需要将复杂数据类型转换成 JSON 字符串，再存储到本地

**语法**：`JSON.stringify(复杂数据类型)`

```html
<script>
  const goods = {
    name: '小米',
    price: 1999
  }
  
  // 1. 把对象转换为JSON字符串
  localStorage.setItem('goods', JSON.stringify(goods))
  
  // 2. 把JSON字符串转换为对象
  console.log(JSON.parse(localStorage.getItem('goods')))
</script>
```

---

### 环境对象

环境对象指的是函数内部特殊的变量 `this`，它代表着当前函数运行时所处的环境。

```html
<script>
  function sayHi() {
    console.log(this);
  }

  let user = {
    name: '张三',
    sayHi: sayHi
  }
  
  let person = {
    name: '李四',
    sayHi: sayHi
  }

  // 直接调用
  sayHi() // window
  window.sayHi() // window

  // 作为对象方法调用
  user.sayHi() // user
  person.sayHi() // person
</script>
```

**结论：**

1. `this` 本质上是一个变量，数据类型为对象
2. 函数的调用方式不同 `this` 变量的值也不同
3. 【谁调用 `this` 就是谁】是判断 `this` 值的粗略规则
4. 函数直接调用时实际上 `window.sayHi()` 所以 `this` 的值为 `window`

#### 回调函数

如果将函数 A 做为参数传递给函数 B 时，我们称函数 A 为回调函数。

```html
<script>
  function foo(arg) {
    console.log(arg);
  }

  function bar() {
    console.log('函数也能当参数...');
  }
  // 函数也可以做为参数
  foo(bar);
</script>
```

**结论：**

1. 回调函数本质还是函数，只不过把它当成参数使用
2. 使用匿名函数做为回调函数比较常见

---

### 正则表达式

**正则表达式**（Regular Expression）是一种字符串匹配的模式（规则）

**使用场景：**

- 例如验证表单：手机号表单要求用户只能输入11位的数字（匹配）
- 过滤掉页面内容中的一些敏感词（替换），或从字符串中获取我们想要的特定部分（提取）等

#### 正则基本使用

```javascript
// 1. 定义规则
const reg = /表达式/

// 2. 使用正则 test() 方法
console.log(reg.test(str))  // 如果符合规则匹配上则返回true，否则false
```

#### 元字符

**普通字符**：大多数的字符仅能够描述它们本身，这些字符称作普通字符，例如所有的字母和数字。

**元字符（特殊字符）**：是一些具有特殊含义的字符，可以极大提高了灵活性和强大的匹配功能。

#### 边界符

正则表达式中的边界符（位置符）用来提示字符所处的位置。

| 边界符 | 说明 |
|--------|------|
| ^ | 表示匹配行首的文本（以谁开始） |
| $ | 表示匹配行尾的文本（以谁结束） |

```javascript
const reg = /^web/  // 以web开头
console.log(reg.test('web前端'))  // true
console.log(reg.test('前端web'))  // false

const reg1 = /web$/  // 以web结尾
console.log(reg1.test('前端web'))  // true

const reg2 = /^web$/  // 精确匹配
console.log(reg2.test('web'))  // true
console.log(reg2.test('webweb'))  // false
```

> 如果 ^ 和 $ 在一起，表示必须是精确匹配

#### 量词

量词用来设定某个模式重复次数

| 量词 | 说明 |
|------|------|
| * | 重复次数 >= 0 次 |
| + | 重复次数 >= 1 次 |
| ? | 重复次数 0 或 1 次 |
| {n} | 重复 n 次 |
| {n,} | 重复次数 >= n 次 |
| {n,m} | n <= 重复次数 <= m 次 |

```javascript
const reg1 = /^w*$/  // >= 0 次
const reg2 = /^w+$/  // >= 1 次
const reg3 = /^w?$/  // 0 或 1 次
const reg4 = /^w{3}$/  // 正好 3 次
const reg5 = /^w{2,}$/  // >= 2 次
const reg6 = /^w{2,4}$/  // 2 到 4 次
```

> 注意：逗号左右两侧千万不要出现空格

#### 范围

表示字符的范围，定义的规则限定在某个范围

| 范围 | 说明 |
|------|------|
| [abc] | 匹配包含的单个字符，多选1 |
| [a-z] | 匹配a到z之间的单个字符 |
| [^a-z] | 取反，匹配除了a到z之间的字符 |

```javascript
const reg1 = /^[abc]$/  // 匹配a或b或c
const reg2 = /^[a-z]$/  // 匹配a到z之间的单个字符
const reg3 = /^[a-zA-Z0-9]$/  // 匹配字母或数字
const reg4 = /^[^a-z]$/  // 匹配除了小写字母以外的字符
```

#### 字符类

某些常见模式的简写方式

| 字符类 | 说明 |
|--------|------|
| \d | 匹配0-9之间的任一数字，相当于[0-9] |
| \D | 匹配所有0-9以外的字符，相当于[^0-9] |
| \w | 匹配任意的字母、数字和下划线，相当于[A-Za-z0-9_] |
| \W | 除所有字母、数字和下划线以外的字符，相当于[^A-Za-z0-9_] |
| \s | 匹配空格（包括换行符、制表符、空格符等），相当于[\t\r\n\v\f] |
| \S | 匹配非空格的字符，相当于[^\t\r\n\v\f] |

#### 替换和修饰符

**replace 替换方法**：可以完成字符的替换

```javascript
const str = '欢迎大家学习前端，相信大家一定能学好前端，都成为前端大神'
const strEnd = str.replace(/前端/g, 'web')
console.log(strEnd)
```

**修饰符**：约束正则执行的某些细节行为

| 修饰符 | 说明 |
|--------|------|
| i | 忽略大小写 |
| g | 全局匹配 |

```javascript
// 全局替换
const strEnd = str.replace(/前端/g, 'web')
```

---

## 综合案例

### 数组 map 方法

**使用场景**：map 可以遍历数组处理数据，并且返回新的数组

```javascript
const arr = ['red', 'blue', 'pink']
const newArr = arr.map(function (ele, index) {
  return ele + '颜色'
})
console.log(newArr)  // ['red颜色', 'blue颜色', 'pink颜色']
```

> map 也称为映射。映射是个术语，指两个元素的集之间元素相互"对应"的关系。
> map重点在于有返回值，forEach没有返回值（undefined）

### 数组 join 方法

**作用**：join() 方法用于把数组中的所有元素转换一个字符串

```javascript
const arr = ['red', 'blue', 'pink']

console.log(arr.join())  // red,blue,pink
console.log(arr.join(''))  // redbluepink
console.log(arr.join('|'))  // red|blue|pink
```
