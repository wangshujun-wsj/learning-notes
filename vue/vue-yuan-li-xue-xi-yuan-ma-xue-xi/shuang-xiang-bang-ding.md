# 效果
![](/assets/vue/myvue.gif)


## html

```
<!DOCTYPE html>
<html lang="zh-cn">
<head>
    <meta charset="UTF-8">
    <title>my-vue</title>
</head>
<style>
    #app {
        text-align: center;
    }
</style>

<body>
    <div id="app">
        <h2>{{title}}</h2>
        <input v-model="name">
        <h1>{{name}}</h1>
        <button v-on:click="clickButton">click me!</button>
    </div>
</body>
<script src="js/observer.js"></script>
<script src="js/watcher.js"></script>
<script src="js/compile.js"></script>
<script src="js/index.js"></script>
<script type="text/javascript">
    var vue = new Vue({
        el: '#app',
        data: {
            title: 'hello world',
            name: 'canfoo'
        },
        methods: {
            clickButton: function () {
                this.title = this.name;
            }
        },
        mounted: function () {
            this.name = "这是mounted改变的"
            window.setTimeout(() => {
                this.title = '你好';
                window.setTimeout(()=> {
                    this.clickButton();
                },2000);
            }, 1000);
        }
    });
</script>

</html>
```

## index.js

```
function Vue(options) {
    this.data = options.data;
    this.el = document.querySelector( options.el);
    this.methods = options.methods;
    this.options = options;
    var that = this;
    Object.keys(this.data).forEach((key)=> {
        that.proxyKeys(key);
    });
    Object.keys(this.methods).forEach((method)=> {
        that.proxyMethods(method,that.methods[method]);
    });
    observerFactory(this.data);
    new Compile(this.el,that);
    // 执行 mounted方法
    options.mounted.call(this);
}

Vue.prototype = {
    // 将劫持的数据绑定到Vue对象上面
    // 实现 this.xxx  获取 或 赋值
    proxyKeys: function(key) {
        var that = this;
        Object.defineProperty(this, key, {
            configurable: true,
            enumerable: true,
            get: function() {
                return that.data[key];
            },
            set: function(newVal) {
                that.data[key] = newVal;
            }
        })
    },
    // 将methods对象里的方法绑定到Vue对象上面, this.方法 调用
    proxyMethods: function(method, fn) {
        this[method] = fn;
    }
}
```
## observer.js

```
function observerFactory(data) {
    for (const property in data) {
        if (data.hasOwnProperty(property)) {
            addObserver(data, property, data[property]);
            const val = data[property];
            // 结果是数组,处理数组内置的方法
            if (val && val instanceof Array) {
                addFunction(data, property, val);
            } else if(val && val instanceof Object) {
                // 结果是对象就再次递归处理
                observerFactory(val);
            }
        }
    }
}

// 添加数据劫持
function addObserver(data, key, val) {
    const dep = new Dep();
    Object.defineProperty(data, key, {
        configurable: true,
        enumerable: true,
        get: function() {
            if (Dep.target) {
                dep.addSub(Dep.target);
            }
            return val;
        },
        set: function(newVal) {
            if (val !== newVal) {
                val = newVal;
                dep.notify();
            }
        }
    })
}
// 处理数组中的内置方法
function addFunction(data, key, val) {
    ["shift","unshift","pop","push","reverse","sort"].forEach((mothod)=>{
        const __o__ = Array.prototype[mothod];
        val[mothod] = function() {
            // 调用原来的方法,获取执行结果
            const result = __o__.apply(this, arguments);
            // 添加要处理的内容
            console.log("使用 "+mothod+" 方法, 返回结果为: "+__o__);
            return result;
        }
        
    });
}

function Dep() {
    this.subs = [];
}

Dep.prototype = {
    addSub: function(sub) {
        this.subs.push(sub);
    },
    notify: function() {
        this.subs.forEach((sub)=> {
            sub.update();
        })
    }
}
Dep.target = null;
```
## Watcher.js
```
function Watcher(vm, exp, cb) {
    this.vm = vm;
    this.cb = cb;
    this.exp = exp;
    this.value = this.get();
}

Watcher.prototype = {
    update: function() {
        console.log("update 方法更新了数据");
        var newVal = this.vm.data[this.exp];
        var oldVal = this.value;
        if (oldVal !== newVal) {
            this.value = newVal;
            this.cb.call(this.vm,newVal);
        }
    },
    get: function() {
        Dep.target = this;
        const value = this.vm.data[this.exp];
        Dep.target = null;
        return value;
    }
}

```
## compile.js
```
function Compile(el, vm) {
    this.el = el;
    this.vm = vm;
    this.fragment = null;
    this.init();
}

Compile.prototype = {
    init: function () {
        if (this.el) {
            this.fragment = this.nodeToFragment(this.el);
            this.compileElement(this.fragment);
            this.el.appendChild(this.fragment);
        }
    },
    // 虚拟dom (使用循环将真实dom添加到
    // document.createDocumentFragment创建的虚拟dom中)
    nodeToFragment: function (el) {
        // https://developer.mozilla.org/zh-CN/docs/Web/API/Document/createDocumentFragment
        var fragment = document.createDocumentFragment(),
            child;
        while (child = el.firstChild) {
            fragment.appendChild(child);
        }
        return fragment;
    },
    // 标签属性方法 http://www.runoob.com/jsref/dom-obj-all.html
    // 处理标签
    compileElement: function (el) {
        var that = this;
        var childNodes = el.childNodes;
        Array.prototype.slice.call(childNodes).forEach(node => {

            var textContent = node.textContent;
            // console.log(textContent)
            var reg = /\{\{\s*(\w+)\s*\}\}/
            // 判断node节点类型
            if (that.isElementNode(node)) {
                that.compile(node);
            } else if (this.isTextNode(node) && reg.exec(textContent)) {
                // console.log(reg.exec(textContent));
                this.compileText(node, reg.exec(textContent)[1]);
            }
            if (node.childNodes && node.childNodes.length) {
                this.compileElement(node);
            }
        });
    },
    // 处理文本内容
    compileText: function (node, exp) {
        var that = this;
        var val = this.vm.data[exp];
        that.updateText(node, val);
        new Watcher(this.vm, exp, function (val) {
            that.updateText(node, val);
        });
    },
    compile: function (node) {
        var that = this;
        var attributes = node.attributes;
        Array.prototype.slice.call(attributes).forEach(attribute => {

            var attrName = attribute.name,
                attrValue = attribute.value;
            if (that.isDirective(attrName)) {
                var dir = attrName.substring(2);
                if (that.isEventDirective(dir)) {
                    // 事件
                    that.compileEvent(node, that.vm, attrValue, dir);
                } else {
                    // v-model
                    that.compileModel(node, that.vm, attrValue);
                }
                node.removeAttribute(attrName);
            }
        });
    },
    compileEvent: function(node, vm, exp, dir) {
        var method = dir.split(":")[1];
        var cb = vm.methods && vm.methods[exp];
        if (method && cb) {
            node.addEventListener(method, cb.bind(vm));
        }
    },
    compileModel: function (node, vm, exp) {
        var that = this;
        var val = vm.data[exp];
        that.updateModel(node, val);
        new Watcher(vm, exp, function (value) {
            that.updateModel(node, value);
        });
        // http://www.runoob.com/jsref/met-element-addeventlistener.html
        // 触发input事件,修改变量
        node.addEventListener("input", function (e) {
            var newVal = e.target.value;
            if (newVal !== val) {
                vm.data[exp] = newVal;
            }
            
        });
    },
    updateText: function (node, value) {
        node.textContent = typeof value === 'undefined' ? '' : value;
    },
    updateModel: function (node, value) {
        node.value = typeof value === 'undefined' ? '' : value;
    },
    isDirective: function (attr) {
        return attr.indexOf('v-') === 0;
    },
    isEventDirective: function (dir) {
        return dir.indexOf('on:') === 0;
    },
    // 元素节点
    isElementNode: function (node) {
        return node.nodeType == 1;
    },
    isTextNode: function (node) {
        return node.nodeType == 3;
    }
}

```