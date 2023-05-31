**Chrome**自带开发者工具。它的功能十分丰富，包括元素、网络、安全等等。今天我们主要介绍**JavaScript控制台**部分的功能。

我最早写代码的时候，也就是在JS控制台里输出一些服务器返回的内容，或者一些变量的值。但是后来通过一些深入的学习和了解，我发现Chrome的JS控制台原来还有这么多神奇的功能。

在这里我总结了一些特别有用的功能。要是你凑巧在Chrome里浏览这篇文章的话，现在就打开开发者工具，跟着随手试试吧！

## 1.选取DOM元素

要是你用过两天jQuery的话，一定对 `$`('.className') 或者 `$`('#id') 这种选择器不会陌生。上面这俩货分别是jQuery的类选择器和ID选择器。

在一个网页没有引入jQuery的情况下，在控制台里你也可以通过类似的方法选取DOM.

不管 `$`('tagName') /`$`('.class')/ `$`('#id') 还是 `$`('.class #id') 等类似的选择器，都相当于原生JS的document.querySelector('') 方法。这个方法返回第一个匹配选择规则的DOM元素。

在Chrome的控制台里，你可以通过 `$$`('tagName') 或者 `$$`('.className') 记得是两个`$$`符号来选择所有匹配规则的DOM元素。选择返回的结果是一个数组，可以通过数组的方法来访问其中的单个元素。

  

举个栗子 `$$`('className') 会返回给你所有包含 className 类属性的元素，之后你可以通过 `$$`('className')\[0\] 和`$$`('className')\[1\] 来访问其中的某个元素。

![](https://pic4.zhimg.com/v2-0be76f26dc59fc5a2f910a6557376c3b_b.png)

![](https://pic4.zhimg.com/80/v2-0be76f26dc59fc5a2f910a6557376c3b_720w.webp)

## 2.一秒钟让Chrome变成所见即所得的编辑器

你可能经常会困惑你到底能不能直接在浏览器里更改网页的文本内容。答案是肯定的，你可以只通过一行简单的指令把Chrome变成所见即所得的编辑器，直接在网页上随心所欲地删改文字。

你不需要再傻傻地右键审查元素，编辑源代码了。打开Chrome的开发者控制台，输入

```js
document.body.contentEditable=true
```

然后奇迹就发生啦！要是你正在用Chrome现在就可以试试！

![](https://pic1.zhimg.com/v2-56b77b9da4641560bad6101cd4cd6558_b.png)

![](https://pic1.zhimg.com/80/v2-56b77b9da4641560bad6101cd4cd6558_720w.webp)

## 3.获取某个DOM元素绑定的事件

在调试的时候，你肯定需要知道某个元素上面绑定了什么触发事件。Chrome的开发者控制台可以让你很轻松地找到它们。

getEventListeners(`$`('selector')) 方法以数组对象的格式返回某个元素绑定的所有事件。你可以在控制台里展开对象查看详细的内容。

![](https://pic2.zhimg.com/v2-076155237e53e09b7631913d0e563221_b.png)

![](https://pic2.zhimg.com/80/v2-076155237e53e09b7631913d0e563221_720w.webp)

要是你需要选择其中的某个事件，可以通过下面的方法来访问：

```js
getEventListeners(`$`('selector')).eventName[0].listener
```

这里的 eventName 表示某种事件类型，例如：

```js
getEventListeners(`$`('#firstName')).click[0].listener
```

上面的例子会返回ID为 firstName 元素绑定的click事件。

## 4.监测事件

当你需要监视某个DOM触发的事件时，也可以用到控制台。例如下面这些方法：

- monitorEvents(`$`('selector')) 会监测某个元素上绑定的所有事件，一旦该元素的某个事件被触发就会在控制台里显示出来。
- monitorEvents(`$`('selector'),'eventName') 可以监听某个元素上绑定的具体事件。第二个参数代表事件类型的名称。例如 monitorEvents(`$`('#firstName'),'click') 只监测ID为firstName的元素上的click事件。
- monitorEvents(`$`('selector'),\['eventName1','eventName3',….\]) 同上。可以同时检测具体指定的多个事件类型。
- unmonitorEvents(`$`('selector')) 用来停止对某个元素的事件监测。

## 5.用计时器来获取某段代码块的运行时间

通过 console.time('labelName') 来设定一个计时器，其中的 labelName 是计时器的名称。通过console.timeEnd('labelName') 方法来停止并输出某个计时器的时间。例如：

```js
console.time('myTime'); //设定计时器开始 - myTime
console.timeEnd('mytime'); //结束并输出计时时长 - myTime

//输出: myTime:123.00 ms
```

再举一个通过计时器来计算代码块运行时间的例子：

```js
console.time('myTime'); //开始计时 - myTime

for(var i=0; i < 100000; i++){
  2+4+5;
}

console.timeEnd('mytime'); //结束并输出计时时长 - myTime

//输出 - myTime:12345.00 ms
```

## 6.以表格的形式输出数组

假设我们有一个像下面这样的数组：

```js
var myArray=[{a:1,b:2,c:3},{a:1,b:2,c:3,d:4},{k:11,f:22},{a:1,b:2,c:3}]
```

要是你直接在控制台里输入数组的名称，Chrome会以文本的形式返回一个数组对象。但你完全可以通过console.table(variableName) 方法来以表格的形式输出每个元素的值。例如下图：

![](https://pic2.zhimg.com/v2-abfd37780b085970c42098f8071afefd_b.png)

![](https://pic2.zhimg.com/80/v2-abfd37780b085970c42098f8071afefd_720w.webp)

### 7.通过控制台方法来检查元素

你可以直接在控制台里输入下面的方法来检查元素

- inspect(`$`('selector')) 会检查所有匹配选择器的DOM元素，并返回所有选择器选择的DOM对象。例如inspect(`$`('#firstName')) 选择所有ID是 firstName 的元素，inspect(`$`('a')\[3\]) 检查并返回页面上第四个 p元素。
- `$`0, `$`1, `$`2等等会返回你最近检查过的几个元素，例如 `$`0 会返回你最后检查的元素，`$`1 则返回倒数第二个。

![](https://pic1.zhimg.com/v2-e90e6e4af6d558254f013e1e44be7df0_b.png)

![](https://pic1.zhimg.com/80/v2-e90e6e4af6d558254f013e1e44be7df0_720w.webp)

## 8.列出某个元素的所有属性

你也可以通过控制台列出某个元素的所有属性：

dir(`$`('selector')) 会返回匹配选择器的DOM元素的所有属性，你可以展开输出的结果查看详细内容。

![](https://pic3.zhimg.com/v2-55921f16427b171b529693b3bbbc2342_b.png)

![](https://pic3.zhimg.com/80/v2-55921f16427b171b529693b3bbbc2342_720w.webp)

## 9.获取最后计算结果的值

你可以把控制台当作计算器使用。当你在Chrome控制台里进行计算时，可以通过`$`\_来获取最后的计算结果值，还是直接看例子吧：

```js
2+3+4
9 //- The Answer of the SUM is 9

`$`_
9 // Gives the last Result

`$`_ * `$`_
81  // As the last Result was 9

Math.sqrt(`$`_)
9 // As the last Result was 81

`$`_
9 // As the Last Result is 9
```

![](https://pic2.zhimg.com/v2-0f9403c639ff8182c5d1fb4e5775ea5d_b.png)

![](https://pic2.zhimg.com/80/v2-0f9403c639ff8182c5d1fb4e5775ea5d_720w.webp)

## 10.清空控制台输出

当你需要这么做的时候，只需要输入 clear() 然后回车就好啦！
或者 CTRL+L
**Chrome开发者工具**的强大远远超出你的想象！这只是其中的一部分小技巧而已，希望能够帮到你！