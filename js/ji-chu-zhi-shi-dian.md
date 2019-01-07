#变量类型
## 6种原始类型(值类型)：

1. boolean
2. string
3. number
4. **null**
5. undefined
6. symbol (es6)

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

* test(p1) 将p1的对象地址当作函数参数
* person.age = 26 会将对象p1的age也修改
* person = {name: 'yyy',age: 30} person对象的地址重新指向新对象，和p1不在绑定
* const p2 = test(p1) 将方法里person的地址传递给p2

按值传递的类型，复制一份存入栈内存，这类类型一般不占用太多内存，而且按值传递保证了其访问速度。按共享传递的类型，是复制其引用，而不是整个复制其值（C 语言中的指针），保证过大的对象等不会因为不停复制内容而造成内存的浪费

## typeof
能检测出七种类型，值类型中null的结果是object，引用类型中出来函数显示为Function,其他都是object，所以能检测出七种（5个值类型对应的+1个object+1个Function。typeof 并不能准确判断对象变量到底是什么类型

| type| 结果 |
|-----|-----|-----|
|typeof 123| number|
|typeof '123'| string |
|typeof true| boolean |
|typeof undefined| undefined |
|typeof Symbol()| symbol |
|typeof function| Function |
|typeof null| object |
|typeof [1,2]| object |
|typeof {}| object |

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
2. 函数调用  foo() 这里的this也会指向全局对象
3. test.foo()    this指向test对象,  指向调用者
4. new foo()     在函数内部，this 指向新创建的对象。
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
![](/assets/js基础知识/==规则.jpg)


```
[] == ![]  // 
```


# let var const
let 、const与var的区别
1. 变量不会提示，块级作用域，使用前需要先定义，如果在声明之前访问这些变量，会导致报错
2. 重复声明报错
3. 不绑定全局作用域，全局作用域中，let 声明的变量不会挂在window上，var声明的会
let和const的区别
const 用于声明常量，其值一旦被设定不能再被修改，否则会报错

