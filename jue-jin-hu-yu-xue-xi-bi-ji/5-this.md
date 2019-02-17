[this绑定机制的解析](https://juejin.im/post/5b3715def265da59af40a630)

# this的绑定规则：
1. 在非严格模式下，默认绑定的this指向全局对象，严格模式下this指向undefined
2. 函数调用  foo() 这里的this也会指向全局对象
3. test.foo()    this指向test对象,  指向调用者
4. new foo()     在函数内部，this 指向新创建的对象。
5. 当使用 Function.prototype 上的 call 或者 apply 方法时，函数内的 this 将会被 显式设置为函数调用的第一个参数。


# 箭头函数的this

```
function foo() {
  return () => {
    console.log(this.a);
  };
}
let obj1 = {
  a: 2
};
let obj2 = {
  a: 22
};
let bar = foo.call(obj1); // foo this指向obj1
bar.call(obj2); // 输出2 这里执行箭头函数 并试图绑定this指向到obj2

```

从上述栗子可以得出，箭头函数的this规则：
1. 箭头函数中的this继承于它外面第一个不是箭头函数的函数的this指向。
2. 箭头函数的 this 一旦绑定了上下文，就不会被任何代码改变。







