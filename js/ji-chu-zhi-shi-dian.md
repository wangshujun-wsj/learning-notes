# 变量类型

## 6种原始类型\(值类型\)：

1. boolean
2. string
3. number
4. **null**
5. undefined
6. symbol \(es6\)

## 引用类型

在 JS 中，除了原始类型那么其他的都是对象类型了。对象类型和原始类型不同的是，原始类型存储的是值，对象类型存储的是地址（指针）。当你创建了一个对象类型的时候，计算机会在内存中帮我们开辟一个空间来存放值，但是我们需要找到这个空间，这个空间会拥有一个地址（指针）

```
function test(person) {
  person.age = 26
  person = {
    name: 'yyy',
    age: 30
  }

  return person
}
const p1 = {
  name: 'yck',
  age: 25
}
const p2 = test(p1)
console.log(p1) // -> ?
console.log(p2) // -> ?
```

* test\(p1\) 将p1的对象地址当作函数参数
* person.age = 26 会将对象p1的age也修改
* person = {name: 'yyy',age: 30} person对象的地址重新指向新对象，和p1不在绑定
* const p2 = test\(p1\) 将方法里person的地址传递给p2

按值传递的类型，复制一份存入栈内存，这类类型一般不占用太多内存，而且按值传递保证了其访问速度。按共享传递的类型，是复制其引用，而不是整个复制其值（C 语言中的指针），保证过大的对象等不会因为不停复制内容而造成内存的浪费

## typeof

能检测出七种类型，值类型中null的结果是object，引用类型中出来函数显示为Function,其他都是object，所以能检测出七种（5个值类型对应的+1个object+1个Function。typeof 并不能准确判断对象变量到底是什么类型

| type | 结果 |
| :--- | :--- |
| typeof 123 | number |
| typeof '123' | string |
| typeof true | boolean |
| typeof undefined | undefined |
| typeof Symbol\(\) | symbol |
| typeof function | Function |
| typeof null | object |
| typeof \[1,2\] | object |
| typeof {} | object |

## instanceof

instanceof运算符用于测试构造函数的prototype属性是否出现在对象的原型链中的任何位置

```
[1, 2] instanceof Array
const Person = function() {}
const p1 = new Person()
p1 instanceof Person
```

instanceof更多是用来检测自定义对象

## 判断对象变量到底是什么类型的方法

```
function is(type, obj) {
    var clas = Object.prototype.toString.call(obj).slice(8, -1);
    return obj !== undefined && obj !== null && clas === type;
}

is('String', 'test'); // true
is('String', new String('test')); // true
Object.prototype.toString 返回一种标准格式字符串，所以上例可以通过 slice 截取指定位置的字符串，如下所示：
Object.prototype.toString.call([])    // "[object Array]"
Object.prototype.toString.call({})    // "[object Object]"
Object.prototype.toString.call(2)    // "[object Number]"
```

# 类型转换

![](/assets/js基础知识/类型转换.jpg)

# this

## this的绑定规则：

1. 在非严格模式下，默认绑定的this指向全局对象，严格模式下this指向undefined
2. 函数调用  foo\(\) 这里的this也会指向全局对象
3. test.foo\(\)    this指向test对象,  指向调用者
4. new foo\(\)     在函数内部，this 指向新创建的对象。
5. 当使用 Function.prototype 上的 call 或者 apply 方法时，函数内的 this 将会被 显式设置为函数调用的第一个参数。

```
function a() {
  return () => {
    return () => {
      console.log(this)
    }
  }
}
console.log(a()()())
```

首先箭头函数其实是没有 this 的，箭头函数中的 this 只取决包裹箭头函数的第一个普通函数的 this。在这个例子中，因为包裹箭头函数的第一个普通函数是 a，所以此时的 this 是 window。另外对箭头函数使用 bind 这类函数是无效的。

```
let a = {}
let fn = function () { console.log(this) }
fn.bind().bind(a)() // => ?
```

可以从上述代码中发现，不管我们给函数 bind 几次，fn 中的 this 永远由第一次 bind 决定，所以结果永远是 window。

```
var foo=function(m,n){
 console.log(n);
return {
    foo:function(o){
      console.log(o);
      return foo(o,m);
    }
  }
}


//问题一:
var result=foo(1);
result.foo(2);
result.foo(3);
result.foo(4);


//问题二:
var result=foo(2).foo(3).foo(4).foo(5);


//问题三:
var result=foo(1);
result.foo(2).foo(3);
result.foo(4).foo(5);

//问题一二三分别输出什么？ 说出执行步骤
```

# == 和 ===

== 如果对比双方的类型不一样的话，就会进行类型转换  
![](/assets/js基础知识/==规则.jpg)

```
[] == ![]  //
```

=== 就是判断两者类型和值是否相同

true， ！ 的优先级比 == 大，所以 !\[\] 转为1 即 \[\] == 1 ,对象和number判断会将对象转为基本类型，即 1==1 结果为true

# let var const

let 、const与var的区别  
1. 变量不会提示，块级作用域，使用前需要先定义，如果在声明之前访问这些变量，会导致报错  
2. 重复声明报错  
3. 不绑定全局作用域，全局作用域中，let 声明的变量不会挂在window上，var声明的会  
let和const的区别  
const 用于声明常量，其值一旦被设定不能再被修改，否则会报错

# 闭包

## 什么是闭包

《JavaScript高级程序设计》这样描述：

```
闭包是指有权访问另一个函数作用域中的变量的函数；
```

《JavaScript权威指南》这样描述：

```
从技术的角度讲，所有的JavaScript函数都是闭包：它们都是对象，它们都关联到作用域链。
```

《你不知道的JavaScript》这样描述：

```
当函数可以记住并访问所在的词法作用域时，就产生了闭包，即使函数是在当前词法作用域之外执行。
```

```
function fn1() {
    var name = 'iceman';
    function fn2() {
        console.log(name);
    }
    return fn2;
}
var fn3 = fn1();
fn3();
```

这样就清晰地展示了闭包：  
自由变量将从作用域链中去寻找，但是 依据的是**函数定义时的作用域链，而不是函数执行时**，

1. fn2的词法作用域能访问fn1的作用域

2. 将fn2当做一个值返回

3. fn1执行后，将fn2的引用赋值给fn3

4. 执行fn3，输出了变量name

## 循环中使用闭包解决 `var` 定义函数的问题

for \(var i = 1; i &lt;= 5; i++\) {  
  \(function\(j\) {  
    setTimeout\(function timer\(\) {  
      console.log\(j\)  
    }, j \* 1000\)  
  }\)\(i\)  
}

## 闭包优缺点

优点:  
1. 因为在闭包内部保持了对外部活动对象的访问,但外部的变量却无法直接访问内部,避免了全局污染;  
2. 可以当做私有成员,弥补了因js语法带来的面向对象编程的不足;  
3. 可以长久的在内存中保存一个自己想要保存的变量.  
缺点:  
1. 可能导致内存占用过多,因为闭包携带了自身的函数作用域  
2. 闭包只能取得外部包含函数中得最后一个值

# 深浅拷贝

## 浅拷贝

对象类型在赋值的过程中其实是复制了地址，从而会导致改变了对象里的数据，其他也都会被改变，且不会拷贝对象的内部的子对象。

## 深拷贝

JSON.parse\(JSON.stringify\(object\)\)  
  1. 会忽略 undefined  
  2. 会忽略 symbol  
  3. 不能序列化函数  
  4. 不能解决循环引用的对象

# 原型

* 所有的引用类型（数组、对象、函数），都具有对象特性，即可自由扩展属性（null除外）
* 所有的引用类型（数组、对象、函数），都有一个**proto**属性，属性值是一个普通的对象
* 所有的函数，都有一个prototype属性，属性值也是一个普通的对象
* 所有的引用类型（数组、对象、函数），**proto**属性值指向它的构造函数的prototype属性值

创建原型的三种方式：

第一种：字面量

```
var o1 = {name: '01}
var o2 = new Object({name: 'o2'});
```

第二种：构造函数

```
function Person(name) {this.name = name;}
var o3 = new M('o3');
```

第三种：Object.create

```
var p = {name: 'p'};
var o4 = Object.create(p);
```

# 原型链

当试图得到一个对象的某个属性时，如果这个对象本身没有这个属性，那么会去它的**proto**（即它的构造函数的prototype）中寻找，没有找到，还会继续往上找。这样一直往上找，你会发现是一个链式的结构，所以叫做“原型链”。如果一直找到最上层都没有找到，那么就宣告失败，返回undefined。最上层是什么 —— Object.prototype.**proto** === null

![](file:///C:\Users\wang\AppData\Roaming\Tencent\Users\1115693174\QQ\WinTemp\RichOle\J0TQD4E%29QADQQAA2FTK7TAO.png)  
![](/assets/js基础知识/原型链.jpg)

