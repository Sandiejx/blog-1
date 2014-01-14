# Web component

## 什么是Web component
W3C中一套关于定义Web组件的标准。

## 传统组件的缺点
用户需要在HTML中写许多自己不关心的内容。

## Shadows
<vedio>标签使用了Shadow DOM。
Shadow dom可隐藏和封装关于某个节点的代码，避免与外部css, js相互影响。

## Templates
跟handlebars中的template概念类似。定义组件html模板，需要时才进行加载和渲染。

## Shadow DOM

为避免内部和外部HTML， CSS相互影响，我们通常的做法是使用iframe实现。Shadow DOM提供了iframe的这些特性，它很好地封装了style, html结构。

### 新建shadow dom
    ele.createShadowRoot();
返回了一个文档片段，可以往里面添内容

### shadow host
在inspect窗口中唯一可被用户看见的东东。我们要求使用者在host中填写内容。

### shadow root
被调用createShadowRoot方法的那个家伙。在inspect窗口中对用户隐藏，但渲染后真正被现实在页面的东东。

### shadow boundary
避免内部和外部js, css影响的界限。

### insertion points
让用户输入内容的地方。template中的content标签通过select属性，指定用户在host中填写内容的节点。来把host中的内容插入到模板中。

## custom element
 In Web Components speak, this new element is a Custom Element, and the only two requirements are that its name must contain a dash, and its prototype must extend `HTMLElement`.

## shim
google的polymer, 和mozilla的x-tags

