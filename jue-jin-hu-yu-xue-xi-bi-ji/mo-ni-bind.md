bind() 方法会创建一个新函数。当这个新函数被调用时，bind() 的第一个
参数将作为它运行时的 this，之后的一序列参数将会在传递的实参前传入
作为它的参数。(来自于 MDN )

bind 功能:
1 返回一个函数
2 可以传入参数

关于指定 this 的指向，我们可以使用 call 或者 apply 实现
但是在这个写法中，我们直接将 fBound.prototype = this.prototype，我们
直接修改 fBound.prototype 的时候，也会直接修改绑定函数的 prototype。
这个时候，我们可以通过一个空函数来进行中转

测试
~~~
var value = 2;

var foo = {
    value: 1
};

function bar(name, age) {
    this.habit = 'shopping';
    console.log(this.value);
    console.log(name);
    console.log(age);
}

bar.prototype.friend = 'kevin';

var bindFoo = bar.bind2(foo, 'daisy');

var obj = new bindFoo('18');
// undefined
// daisy
// 18
console.log(obj.habit);
console.log(obj.friend);
// shopping
// kevin
~~~
实现代码
~~~
Function.prototype.bind2 = function(context) {
	var that = this;
	var args = Array.prototype.slice.call(arguments,1);
	var fn = function(){}
	var result = function() {
	var bindArgs = Array.prototype.slice.call(arguments);
	that.apply(this instanceof result ? this : context,args.concat(bindArgs));
    }
	fn.prototype = this.prototype;
	result.prototype = Fn.prototype;
	return result;
}

~~~