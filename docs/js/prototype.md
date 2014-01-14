# 重新理解Prototype

## 什么是Prototype
原型链是Javascript实现继承的主要方式。其基本思想是利用原型让一个引用类型继承另一个引用类型的属性和方法。

## 哪些引用类型拥有prototype

除了`undefined`和`null`，一切有继承属性或方法的引用类型都有一个属性`__proto__`，指向一个原型对象，并拥有该原型对象的属性和方法。
```js
// 因为a.__proto__指向Number.prototype，因此a继承了原型对象的toString, toFix等方法
var a = 1;
a.__proto__ === Number.prototype; // true

// 因为b.__proto__指向Array.prototype，因此b继承了原型对象的push, join等方法。
var b = [];
b.__proto__ === Array.prototype; // true
```

## 区分'prototype'和'\__proto__'

每个构造函数都有一个原型对象，通过`prototype`属性引用。在使用new创建实例时，生成的引用对象，拥有有`__proto__`属性，指向这个原型对象。  

两者的区别：  
1. `prototype`属性只有类型为function的引用类型拥有，而`__proto__`属性除了undefined, null的引用类型都有。只要有继承的属性或方法，都会有`__proto__`属性
2. 引用对象不会继承其`prototype`属性引用的对象。但会继承其`__proto__`属性引用的对象。

## 为何叫做原型“链”

在读取`a.attr`时，首先会尝试读取`a`的属性`attr`， 若a无这个属性，那就尝试从`a.__proto__`读取`attr`，若无，继续查找`a.__proto__.__proto__`。以此类推，直到找到或为null。

### 原型链的尽头，继承的源头
除了undefined, null，一切都继承自Object。因此，
```js
var arr = [];

arr.__proto__ === Array.prototype; // true
arr.__proto__.__proto__ === Object.prototype; // true
arr.__proto__.__proto__.__proto__ === null; // true
```


