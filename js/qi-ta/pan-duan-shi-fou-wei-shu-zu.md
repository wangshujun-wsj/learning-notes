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



