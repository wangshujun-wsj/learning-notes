[词法作用域](https://github.com/mqyqingfeng/Blog/issues/3)
[深入理解闭包之前置知识→作用域与词法作用域](https://juejin.im/post/5afb0ae56fb9a07aa2138425)



# 作用域
作用域就是一套规则，用于确定在何处以及如何查找变量（标识符）的规则
JavaScript 采用的是**词法作用域**,也就是**静态作用域**
**函数的作用域是定义时候的作用域不是调用的时候**
```
function fn() {
    var a = 100;
    return function() {
        console.log(a);
    }
}
var fn1 = fn();
var a = 200;
fn1();   //  100
```
因为 JavaScript采用的静态作用域所以结果会是100,执行过程如下:
执行fn1()函数,先从fn1()函数内部查询是否存在变量a,如果没有就根据函数的定义位置,查找上一级作用域的代码,也就是a=100

