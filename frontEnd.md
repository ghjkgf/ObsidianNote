当`<script>`标签具有`src`属性的时候，标签内的代码会被忽略

webpack是一个**打包器（bundler）**，它能将多个js文件打包成一个文件（其实不止能打包js文件，也能打包其他类型的文件，比如css文件，json文件等）
在项目根目录下执行 npm init，然后根据提示一步步输入相应的内容完成后即可自动创建 package.json文件

[撰写隐藏元素规则 | X浏览器 (xbext.com)](https://www.xbext.com/docs/how-to-write-hide-element-rule.html)

**图形编辑器**，如 [GIMP](https://www.gimp.org/) 、[Figma](https://www.figma.com/) 、[Paint.NET](https://www.getpaint.net/) 、[Photoshop](https://www.adobe.com/products/photoshop.html) 、[Sketch](https://www.sketch.com/) 或 [XD](https://www.adobe.com/products/xd.html)

**自动化构建工具**，如 [Webpack](https://webpack.js.org/) 、[Grunt](https://gruntjs.com/) 或 [Gulp](https://gulpjs.com/) ，以自动执行重复性任务，如简化代码和运行测试

这个链接左侧目录没有,只有文中跳转链接
[如何设置一个本地测试服务器？ - 学习 Web 开发 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/Tools_and_setup/set_up_a_local_testing_server)

[Chrome DevTools - Chrome Developers](https://developer.chrome.com/docs/devtools/)

可以用类似 [JSBin](http://jsbin.com/) 或 [Glitch](https://glitch.com/) 这些在线编辑器

事件处理器=事件监听器
	网络事件不是 JavaScript 语言的核心——它们被定义成内置于浏览器的 JavaScript APIs
```md
值得注意的是并不是只有 JavaScript 使用事件——大多的编程语言都有这种机制，并且它们的工作方式不同于 JavaScript。实际上，JavaScript 网页上的事件机制不同于在其他环境中的事件机制。

比如，[Node.js](https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/Express_Nodejs) 是一种非常流行的允许开发者使用 JavaScript 来建造网络和服务器端应用的运行环境。[Node.js event model](https://nodejs.org/docs/latest-v5.x/api/events.html) 依赖定期监听事件的监听器和定期处理事件的处理器——虽然听起来好像差不多，但是实现两者的代码是非常不同的，Node.js 使用像 on ( ) 这样的函数来注册一个事件监听器，使用 once ( ) 这样函数来注册一个在运行一次之后注销的监听器。 [HTTP connect event docs](https://nodejs.org/docs/latest-v5.x/api/http.html#http_event_connect) 提供了很多例子。

另外一个例子：您可以使用 JavaScript 来开发跨浏览器的插件（使用 [WebExtensions](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions) 开发技术。事件模型和网站的事件模型是相似的，仅有一点点不同——事件监听属性使用驼峰命名法（如`onMessage`而不是`onmessage`），还需要与 `addListener` 函数结合，参见 [runtime.onMessage page](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions/API/runtime/onMessage#examples) 上的一个例子。

您现在不需要掌握这些，我们只想表明不同的编程环境下事件机制是不同的
```

https://github.com/iMaldway/shield 好难用....先学会它

**图形编辑器**，如 [GIMP](https://www.gimp.org/) 、[Figma](https://www.figma.com/) 、[Paint.NET](https://www.getpaint.net/) 、[Photoshop](https://www.adobe.com/products/photoshop.html) 、[Sketch](https://www.sketch.com/) 或 [XD](https://www.adobe.com/products/xd.html)

**自动化构建工具**，如 [Webpack](https://webpack.js.org/) 、[Grunt](https://gruntjs.com/) 或 [Gulp](https://gulpjs.com/) ，以自动执行重复性任务，如简化代码和运行测试

这个链接左侧目录没有,只有文中跳转链接
[如何设置一个本地测试服务器？ - 学习 Web 开发 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/Tools_and_setup/set_up_a_local_testing_server)

[Chrome DevTools - Chrome Developers](https://developer.chrome.com/docs/devtools/)

可以用类似 [JSBin](http://jsbin.com/) 或 [Glitch](https://glitch.com/) 这些在线编辑器

事件处理器=事件监听器
	网络事件不是 JavaScript 语言的核心——它们被定义成内置于浏览器的 JavaScript APIs
```md
值得注意的是并不是只有 JavaScript 使用事件——大多的编程语言都有这种机制，并且它们的工作方式不同于 JavaScript。实际上，JavaScript 网页上的事件机制不同于在其他环境中的事件机制。

比如，[Node.js](https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/Express_Nodejs) 是一种非常流行的允许开发者使用 JavaScript 来建造网络和服务器端应用的运行环境。[Node.js event model](https://nodejs.org/docs/latest-v5.x/api/events.html) 依赖定期监听事件的监听器和定期处理事件的处理器——虽然听起来好像差不多，但是实现两者的代码是非常不同的，Node.js 使用像 on ( ) 这样的函数来注册一个事件监听器，使用 once ( ) 这样函数来注册一个在运行一次之后注销的监听器。 [HTTP connect event docs](https://nodejs.org/docs/latest-v5.x/api/http.html#http_event_connect) 提供了很多例子。

另外一个例子：您可以使用 JavaScript 来开发跨浏览器的插件（使用 [WebExtensions](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions) 开发技术。事件模型和网站的事件模型是相似的，仅有一点点不同——事件监听属性使用驼峰命名法（如`onMessage`而不是`onmessage`），还需要与 `addListener` 函数结合，参见 [runtime.onMessage page](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions/API/runtime/onMessage#examples) 上的一个例子。

您现在不需要掌握这些，我们只想表明不同的编程环境下事件机制是不同的
```

https://github.com/iMaldway/shield 好难用....先学会它

**图形编辑器**，如 [GIMP](https://www.gimp.org/) 、[Figma](https://www.figma.com/) 、[Paint.NET](https://www.getpaint.net/) 、[Photoshop](https://www.adobe.com/products/photoshop.html) 、[Sketch](https://www.sketch.com/) 或 [XD](https://www.adobe.com/products/xd.html)

**自动化构建工具**，如 [Webpack](https://webpack.js.org/) 、[Grunt](https://gruntjs.com/) 或 [Gulp](https://gulpjs.com/) ，以自动执行重复性任务，如简化代码和运行测试

这个链接左侧目录没有,只有文中跳转链接
[如何设置一个本地测试服务器？ - 学习 Web 开发 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/Tools_and_setup/set_up_a_local_testing_server)

[Chrome DevTools - Chrome Developers](https://developer.chrome.com/docs/devtools/)

可以用类似 [JSBin](http://jsbin.com/) 或 [Glitch](https://glitch.com/) 这些在线编辑器

事件处理器=事件监听器
	网络事件不是 JavaScript 语言的核心——它们被定义成内置于浏览器的 JavaScript APIs
```md
值得注意的是并不是只有 JavaScript 使用事件——大多的编程语言都有这种机制，并且它们的工作方式不同于 JavaScript。实际上，JavaScript 网页上的事件机制不同于在其他环境中的事件机制。

比如，[Node.js](https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/Express_Nodejs) 是一种非常流行的允许开发者使用 JavaScript 来建造网络和服务器端应用的运行环境。[Node.js event model](https://nodejs.org/docs/latest-v5.x/api/events.html) 依赖定期监听事件的监听器和定期处理事件的处理器——虽然听起来好像差不多，但是实现两者的代码是非常不同的，Node.js 使用像 on ( ) 这样的函数来注册一个事件监听器，使用 once ( ) 这样函数来注册一个在运行一次之后注销的监听器。 [HTTP connect event docs](https://nodejs.org/docs/latest-v5.x/api/http.html#http_event_connect) 提供了很多例子。

另外一个例子：您可以使用 JavaScript 来开发跨浏览器的插件（使用 [WebExtensions](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions) 开发技术。事件模型和网站的事件模型是相似的，仅有一点点不同——事件监听属性使用驼峰命名法（如`onMessage`而不是`onmessage`），还需要与 `addListener` 函数结合，参见 [runtime.onMessage page](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions/API/runtime/onMessage#examples) 上的一个例子。

您现在不需要掌握这些，我们只想表明不同的编程环境下事件机制是不同的
```

https://github.com/iMaldway/shield 好难用....先学会它

**图形编辑器**，如 [GIMP](https://www.gimp.org/) 、[Figma](https://www.figma.com/) 、[Paint.NET](https://www.getpaint.net/) 、[Photoshop](https://www.adobe.com/products/photoshop.html) 、[Sketch](https://www.sketch.com/) 或 [XD](https://www.adobe.com/products/xd.html)

**自动化构建工具**，如 [Webpack](https://webpack.js.org/) 、[Grunt](https://gruntjs.com/) 或 [Gulp](https://gulpjs.com/) ，以自动执行重复性任务，如简化代码和运行测试

这个链接左侧目录没有,只有文中跳转链接
[如何设置一个本地测试服务器？ - 学习 Web 开发 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/Tools_and_setup/set_up_a_local_testing_server)

[Chrome DevTools - Chrome Developers](https://developer.chrome.com/docs/devtools/)

可以用类似 [JSBin](http://jsbin.com/) 或 [Glitch](https://glitch.com/) 这些在线编辑器

事件处理器=事件监听器
	网络事件不是 JavaScript 语言的核心——它们被定义成内置于浏览器的 JavaScript APIs
```md
值得注意的是并不是只有 JavaScript 使用事件——大多的编程语言都有这种机制，并且它们的工作方式不同于 JavaScript。实际上，JavaScript 网页上的事件机制不同于在其他环境中的事件机制。

比如，[Node.js](https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/Express_Nodejs) 是一种非常流行的允许开发者使用 JavaScript 来建造网络和服务器端应用的运行环境。[Node.js event model](https://nodejs.org/docs/latest-v5.x/api/events.html) 依赖定期监听事件的监听器和定期处理事件的处理器——虽然听起来好像差不多，但是实现两者的代码是非常不同的，Node.js 使用像 on ( ) 这样的函数来注册一个事件监听器，使用 once ( ) 这样函数来注册一个在运行一次之后注销的监听器。 [HTTP connect event docs](https://nodejs.org/docs/latest-v5.x/api/http.html#http_event_connect) 提供了很多例子。

另外一个例子：您可以使用 JavaScript 来开发跨浏览器的插件（使用 [WebExtensions](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions) 开发技术。事件模型和网站的事件模型是相似的，仅有一点点不同——事件监听属性使用驼峰命名法（如`onMessage`而不是`onmessage`），还需要与 `addListener` 函数结合，参见 [runtime.onMessage page](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions/API/runtime/onMessage#examples) 上的一个例子。

您现在不需要掌握这些，我们只想表明不同的编程环境下事件机制是不同的
```

https://github.com/iMaldway/shield 好难用....先学会它

**图形编辑器**，如 [GIMP](https://www.gimp.org/) 、[Figma](https://www.figma.com/) 、[Paint.NET](https://www.getpaint.net/) 、[Photoshop](https://www.adobe.com/products/photoshop.html) 、[Sketch](https://www.sketch.com/) 或 [XD](https://www.adobe.com/products/xd.html)

**自动化构建工具**，如 [Webpack](https://webpack.js.org/) 、[Grunt](https://gruntjs.com/) 或 [Gulp](https://gulpjs.com/) ，以自动执行重复性任务，如简化代码和运行测试

这个链接左侧目录没有,只有文中跳转链接
[如何设置一个本地测试服务器？ - 学习 Web 开发 | MDN (mozilla.org)](https://developer.mozilla.org/zh-CN/docs/Learn/Common_questions/Tools_and_setup/set_up_a_local_testing_server)

[Chrome DevTools - Chrome Developers](https://developer.chrome.com/docs/devtools/)

可以用类似 [JSBin](http://jsbin.com/) 或 [Glitch](https://glitch.com/) 这些在线编辑器

事件处理器=事件监听器
	网络事件不是 JavaScript 语言的核心——它们被定义成内置于浏览器的 JavaScript APIs
```md
值得注意的是并不是只有 JavaScript 使用事件——大多的编程语言都有这种机制，并且它们的工作方式不同于 JavaScript。实际上，JavaScript 网页上的事件机制不同于在其他环境中的事件机制。

比如，[Node.js](https://developer.mozilla.org/zh-CN/docs/Learn/Server-side/Express_Nodejs) 是一种非常流行的允许开发者使用 JavaScript 来建造网络和服务器端应用的运行环境。[Node.js event model](https://nodejs.org/docs/latest-v5.x/api/events.html) 依赖定期监听事件的监听器和定期处理事件的处理器——虽然听起来好像差不多，但是实现两者的代码是非常不同的，Node.js 使用像 on ( ) 这样的函数来注册一个事件监听器，使用 once ( ) 这样函数来注册一个在运行一次之后注销的监听器。 [HTTP connect event docs](https://nodejs.org/docs/latest-v5.x/api/http.html#http_event_connect) 提供了很多例子。

另外一个例子：您可以使用 JavaScript 来开发跨浏览器的插件（使用 [WebExtensions](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions) 开发技术。事件模型和网站的事件模型是相似的，仅有一点点不同——事件监听属性使用驼峰命名法（如`onMessage`而不是`onmessage`），还需要与 `addListener` 函数结合，参见 [runtime.onMessage page](https://developer.mozilla.org/zh-CN/docs/Mozilla/Add-ons/WebExtensions/API/runtime/onMessage#examples) 上的一个例子。

您现在不需要掌握这些，我们只想表明不同的编程环境下事件机制是不同的
```
事件处理程序实际上就是异步编程的一种形式：你提供的函数（事件处理程序）将在事件发生时被调用（而不是立即被调用）。如果“事件”是“异步操作已经完成”，那么你就可以看到事件如何被用来通知调用者异步函数调用的结果的。
事件处理程序是一种特殊类型的回调函数。而回调函数则是一个被传递到另一个函数中的会在适当的时候被调用的函数。正如我们刚刚所看到的回调函数曾经是 JavaScript 中实现异步函数的主要方式。
回调地狱,厄运金字塔   -------------------->   使用 Promise
**Promise** 是现代 JavaScript 中异步编程的基础，是一个由异步函数返回的可以向我们指示当前操作所处的状态的对象。在 Promise 返回给调用者的时候，操作往往还没有完成，但 Promise 对象可以让我们操作最终完成时对其进行处理（无论成功还是失败）
在上一篇文章中，我们谈到使用回调实现异步函数的方法。在这种设计中，我们需要在调用异步函数的同时传入回调函数。这个异步函数会立即返回，并在操作完成后调用传入的回调。
在基于 Promise 的 API 中，异步函数会启动操作并返回 [`Promise`](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Promise) 对象。然后，你可以将处理函数附加到 Promise 对象上，当操作完成时（成功或失败），这些处理函数将被执行。
fetch() 替换掉 xmlHttpRequest
```note
Promise 有三种状态：
待定（pending）：初始状态，既没有被兑现，也没有被拒绝。这是调用 `fetch()` 返回 Promise 时的状态，此时请求还在进行中。
已兑现（fulfilled）：意味着操作成功完成。当 Promise 完成时，它的 `then()` 处理函数被调用。
已拒绝（rejected）：意味着操作失败。当一个 Promise 失败时，它的 `catch()` 处理函数被调用。
已敲定（settled）这个词来同时表示 已兑现（fulfilled） 和 已拒绝（rejected） 两种情况
fetch() 认为服务器返回一个错误（如404）时请求成功，但如果网络错误阻止请求被发送，则认为请求失败

有时你需要所有的 Promise 都得到实现，但它们并不相互依赖。在这种情况下，将它们一起启动然后在它们全部被兑现后得到通知会更有效率。这里需要 Promise.all()方法。它接收一个 Promise 数组，并返回一个单一的 Promise
```

