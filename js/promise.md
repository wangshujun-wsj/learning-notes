[JavaScript Promise迷你书（中文版）](http://liubin.org/promises-book/)

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
.then() 方法里出现下列两种情况也会进入.catch()方法
* 发生异常的时候
* 返回了一个Rejected状态的promise对象





