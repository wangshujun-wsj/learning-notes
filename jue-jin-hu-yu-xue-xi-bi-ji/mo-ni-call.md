call() 方法在使用一个指定的 this 值和若干个指定的参数值的前提下调用某个函数或方法。

call 功能:

	1  call 改变了 this 的指向，指向到 第一个参数
	2  call 的调用函数执行了
	3  call 函数还能给定参数执行函数
	4  第一个参数可以传 null，当为 null 的时候，视为指向 window
	5  函数是可以有返回值的！

所以我们模拟的步骤可以分为：

	1 将函数设为对象的属性
	2 判断第一个参数是否为空,取arguments第二个开始的参数
	3 使用eval执行带参数的该函数
	4 删除该函数
	5 返回该函数
测试一下
~~~
var value = 2;

var obj = {
    value: 1
}

function bar(name, age) {
    console.log(this.value);
    return {
        value: this.value,
        name: name,
        age: age
    }
}

bar.call2(null); // 2

console.log(bar.call2(obj, 'kevin', 18));
// 1
// Object {
//    value: 1,
//    name: 'kevin',
//    age: 18
// }
~~~


实现代码
~~~
Function.prototype.call2 = function (context) {
    var context = context || window;
    context.fn = this;

    var args = [];
    for(var i = 1, len = arguments.length; i < len; i++) {
        args.push('arguments[' + i + ']');
    }

    var result = eval('context.fn(' + args +')');

    delete context.fn
    return result;
}

~~~
