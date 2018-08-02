[BAT前端经典面试问题：史上最最最详细的手写Promise教程](https://juejin.im/post/5b2f02cd5188252b937548ab)
原文[JavaScript Promise迷你书（中文版）](http://liubin.org/promises-book/)

# promise基本用法
promise对象拥有几个实例方法， 我们使用这些实例方法来为promise对象创建依赖于promise的具体状态、并且只会被执行一次的回调函数。

为promise对象添加处理方法主要有以下两种

promise对象被 resolve 时的处理(onFulfilled)

promise对象被 reject 时的处理(onRejected)
![](/assets/promise-onFulfilled_onRejected.png)
```
function getURL(URL) {
    return new Promise(function (resolve, reject) {
        var req = new XMLHttpRequest();
        req.open('GET', URL, true);
        req.onload = function () {
            if (req.status === 200) {
                resolve(req.responseText);
            } else {
                reject(new Error(req.statusText));
            }
        };
        req.onerror = function () {
            reject(new Error(req.statusText));
        };
        req.send();
    });
}
// 运行示例
var URL = "http://httpbin.org/get";
getURL(URL).then(function onFulfilled(value){
    console.log(value);
}).catch(function onRejected(error){
    console.error(error);
});

```
**注意**
.then() 方法里出现下列两种情况也会进入.catch()方法
* 发生异常的时候
* 返回了一个Rejected状态的promise对象
# promise 中如何传递参数

```
function doubleUp(value) {
    return value * 2;
}
function increment(value) {
    return value + 1;
}
function output(value) {
    console.log(value);// => (1 + 1) * 2
}

var promise = Promise.resolve(1);
promise
    .then(increment)
    .then(doubleUp)
    .then(output)
    .catch(function(error){
        // promise chain中出现异常的时候会被调用
        console.error(error);
    });
这段代码的入口函数是 Promise.resolve(1); ，整体的promise chain执行流程如下所示。

Promise.resolve(1); 传递 1 给 increment 函数

函数 increment 对接收的参数进行 +1 操作并返回（通过return）

这时参数变为2，并再次传给 doubleUp 函数

最后在函数 output 中打印结果
```
**每次调用then都会返回一个新创建的promise对象**





