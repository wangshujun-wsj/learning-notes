[图解JS闭包](https://zhuanlan.zhihu.com/p/27857268)
[闭包 mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)

[闭包详解一](https://juejin.im/post/5b081f8d6fb9a07a9b3664b6)
[闭包详解二：JavaScript中的高阶函数](https://juejin.im/post/5b167b476fb9a01e5b10f19b)

# 什么是闭包
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

1. fn2的词法作用域能访问fn1的作用域

2. 将fn2当做一个值返回

3. fn1执行后，将fn2的引用赋值给fn3

4. 执行fn3，输出了变量name

我们知道通过引用的关系，fn3就是fn2函数本身。执行fn3能正常输出name，这不就是fn2能记住并访问它所在的词法作用域，而且fn2函数的运行还是在当前词法作用域之外了。







# 闭包优缺点
优点:
1. 因为在闭包内部保持了对外部活动对象的访问,但外部的变量却无法直接访问内部,避免了全局污染;
2. 可以当做私有成员,弥补了因js语法带来的面向对象编程的不足;
3. 可以长久的在内存中保存一个自己想要保存的变量.
缺点:
1. 可能导致内存占用过多,因为闭包携带了自身的函数作用域
2. 闭包只能取得外部包含函数中得最后一个值