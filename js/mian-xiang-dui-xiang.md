## 原型继承

```
function Student() {}
Student.prototype.name="小明";
Student.prototype.age = 20;
Student.prototype.say = function() {
    console.log("haha");
}

function Xiaoming(){}
Xiaoming.prototype = new Student();
var xiaoming= new Xiaoming();
console.log(xiaoming.age);
```

