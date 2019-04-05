# 来源：[https://www.cnblogs.com/heshan1992/p/6927690.html](https://www.cnblogs.com/heshan1992/p/6927690.html)

# **JavaScript中检测对象的方法**

## **1.typeof操作符**

这种方法对于一些常用的类型来说那算是毫无压力，比如Function、String、Number、Undefined等，但是要是检测Array的对象就不起作用了。 利用typeof除了array和null判断为object外，其他的都可以正常判断

```
alert(typeof null); // "object"
alert(typeof function () {
return 1;
}); // "function"
alert(typeof '梦龙小站'); // "string"
alert(typeof 1); // "number"
alert(typeof a); // "undefined"
alert(typeof undefined); // "undefined"
alert(typeof []); // "object"
```

## **2.instanceof操作符**

这个操作符和JavaScript中面向对象有点关系，了解这个就先得了解JavaScript中的面向对象。因为这个操作符是检测对象的原型链是否指向构造函数的prototype对象的。

```
var arr = [1,2,3,1];
alert(arr instanceof Array); // true 
```

## **3.对象的constructor属性**

除了instanceof，每个对象还有constructor的属性，利用它似乎也能进行Array的判断。

```
var arr = [1,2,3,1];
alert(arr.constructor === Array); // true
```

第2种和第3种方法貌似无懈可击，但是实际上还是有些漏洞的，当你在多个frame中来回穿梭的时候，这两种方法就亚历山大了。由于每个iframe都有一套自己的执行环境，跨frame实例化的对象彼此是不共享原型链的，因此导致上述检测代码失效

```
var iframe = document.createElement('iframe'); //创建iframe
document.body.appendChild(iframe); //添加到body中
xArray = window.frames[window.frames.length-1].Array;
var arr = new xArray(1,2,3); // 声明数组[1,2,3]
alert(arr instanceof Array); // false
alert(arr.constructor === Array); // false 
```

**检测数组类型方法**

以上那些方法看上去无懈可击，但是终究会有些问题，接下来向大家提供一些比较不错的方法，可以说是无懈可击了。

## **1.Object.prototype.toString**

Object.prototype.toString的行为：首先，取得对象的一个内部属性\[\[Class\]\]，然后依据这个属性，返回一个类似于"\[object Array\]"的字符串作为结果\(看过ECMA标准的应该都知道，\[\[\]\]用来表示语言内部用到的、外部不可直接访问的属性，称为“内部属性”\)。利用这 个方法，再配合call，我们可以取得任何对象的内部属性\[\[Class\]\]，然后把类型检测转化为字符串比较，以达到我们的目的。

```
function isArrayFn (o) {
return Object.prototype.toString.call(o) === '[object Array]';
}
var arr = [1,2,3,1];
alert(isArrayFn(arr));// true 
```

call改变toString的this引用为待检测的对象，返回此对象的字符串表示，然后对比此字符串是否是'\[object Array\]'，以判断其是否是Array的实例。为什么不直接o.toString\(\)?嗯，虽然Array继承自Object，也会有 toString方法，但是这个方法有可能会被改写而达不到我们的要求，而Object.prototype则是老虎的屁股，很少有人敢去碰它的，所以能一定程度保证其“纯洁性”：\)  


JavaScript 标准文档中定义: \[\[Class\]\] 的值只可能是下面字符串中的一个： Arguments, Array, Boolean, Date, Error, Function, JSON, Math, Number, Object, RegExp, String.

这种方法在识别内置对象时往往十分有用，但对于自定义对象请不要使用这种方法。

## **2.Array.isArray\(\)**

ECMAScript5将Array.isArray\(\)正式引入JavaScript，目的就是准确地检测一个值是否为数组。IE9+、 Firefox 4+、Safari 5+、Opera 10.5+和Chrome都实现了这个方法。但是在IE8之前的版本是不支持的。

## **3.较好参考**

```
var arr = [1,2,3,1];
var arr2 = [{ abac : 1, abc : 2 }];
function isArrayFn(value){
if (typeof Array.isArray === "function") {
return Array.isArray(value);
}else{
return Object.prototype.toString.call(value) === "[object Array]";
}
}
alert(isArrayFn(arr));// true
alert(isArrayFn(arr2));// true
```



