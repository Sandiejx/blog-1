# Fomatting context 

## Box: CSS布局的基本单位
`Box`是CSS布局的对象和基本单位。文档会根据元素和display属性生成不同的`Box`，类型不同的`Box`又会参与不同的`Formatting context`（拥有一套渲染规则的独立区域, 下面会提到）， 因此被渲染的方式也不同。 让我们来看看有哪些盒子：

- `block-level box`: display属性为block, list-item, table的元素，会生成`block-level box`。并且参与`block fomatting context`。

- `inline-level box`: display属性为inline, inline-block, inline-table的元素，会生成`inline-level box`。并且参与`inline formatting context`。

- `run-in box`: css3中才有， 这儿先不讲了

## Formatting context

### Formatting context是什么？

`Formatting context`是W3C CSS2.1规范中的一个概念。它是页面中的一块渲染区域，并且有一套渲染规则，它决定了其子元素将如何定位，以及和其他元素的关系和相互作用。  

CSS2.1 中只有BFC和IFC, CSS3中还增加了GFC和FFC

### BFC

#### 内部布局规则：
1. 内部的`Box`会在垂直方向，一个接一个地放置。
2. `Box`垂直方向的距离由margin决定。属于同一个`BFC`的两个相邻`Box`的margin会发生重叠  
(通过触发BFC放置margin折叠，见Demo)
3. 每个元素的margin box的左边， 与包含块border box的左边相接触
4. `BFC`的区域不会与`float box`重叠。  
(因此可以通过触发BFC清浮动， 见Demo)
5. `BFC`就是页面上的一个隔离的独立容器，容器里面的子元素会影响到外面的元素。反之也如此。

#### BFC能用来做什么?
1. 自适应两栏布局。(根据布局规则4)
2. 清除元素内部浮动。(根据布局规则5)
3. 解决margin重叠(根据布局规则2)

#### 如何产生BFC:

可由一下任意条件触发：  

1. 是根元素
2. float属性不为none
3. position为absolute或fixed
4. display为inline-block, table-cell, table-caption, flex, inline-flex
5. overflow不为visible

### IFC
待续。
