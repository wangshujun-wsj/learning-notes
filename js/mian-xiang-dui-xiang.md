## 原型继承

```
function People() {}
People.prototype.name="小明";
People.prototype.age = 20;
People.prototype.say = function() {
    console.log("haha");
}

function Student(){}
Student.prototype = new People();
var student= new Student();
console.log(student.age);
```
## 原型继承的优缺点
优点:

1. 实现简单,可实现属性和方法的共享

缺点:

1. 创建子类实例时，无法向父类构造函数传参
2. 属性包含引用类型时,更改子类会将所有的子类都修改

## 构造函数继承

```
function People(name, age) {
    this.name = name;
    this.age = age;
}
function Student(name, age) {
    People.call(this,name,age);
}
var student = new Student("xiaoming", 20);
console.log(student);
```
## 构造函数继承的优缺点

优点:

1. 解决子类共享父类引用属性的问题
2. 解决创建子类实例时，不可以向父类传递参数
3. 可以实现多继承（call多个父类对象）

缺点:

1. 只能继承父类的实例属性和方法，不能继承原型属性/方法
2. 无法实现函数复用，每个子类都有父类实例函数的副本，影响性能

## 组合构造函数+原型

```
function People(name, age) {
    this.name = name;
    this.age = age;
    // 仅在第一次调用的初始化
    if (typeof this.say !== 'function') {
        People.prototype.say = function() {
            console.log("haha");
        }
    }
}

function Student(name, age) {
    People.call(this,name,age);
}
Student.prototype = new People();
var student = new Student("xiaoming", 20);
console.log(student);

```
## 优缺点
优点:

1. 解决子类共享父类引用属性的问题
2. 可以向父类传递参数
3. 函数可以复用

缺点:

1. 调用了两次父类构造函数，生成了两份实例(仅仅多消耗一点内存)

## 寄生组合模式









