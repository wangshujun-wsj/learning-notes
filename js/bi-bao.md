[闭包 mdn](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Closures)

[闭包详解一](https://juejin.im/post/5b081f8d6fb9a07a9b3664b6)
[闭包详解二：JavaScript中的高阶函数](https://juejin.im/post/5b167b476fb9a01e5b10f19b)
[JavaScript 闭包](https://juejin.im/entry/59db3f68f265da43294cfe61?utm_medium=fe&utm_source=weixinqun)

# 闭包优缺点
优点:
1. 因为在闭包内部保持了对外部活动对象的访问,但外部的变量却无法直接访问内部,避免了全局污染;
2. 可以当做私有成员,弥补了因js语法带来的面向对象编程的不足;
3. 可以长久的在内存中保存一个自己想要保存的变量.
缺点:
1. 可能导致内存占用过多,因为闭包携带了自身的函数作用域
2. 闭包只能取得外部包含函数中得最后一个值