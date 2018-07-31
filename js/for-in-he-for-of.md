for of 不能循环普通object对象({key:value}) 只能循环可遍历的(iterable),

for in 能够循环出原型和原型链继承下来的属性,可在循环体中使用hasOwnProperty过滤,for in 循环对象时,循环出的是key,循环数组时,循环出的是索引


```
Object.prototype.objCustom = function() {}; 
Array.prototype.arrCustom = function() {};

let iterable = [3, 5, 7];
iterable.foo = 'hello';
for (let i in iterable) {
  // 0, 1, 2 是索引 
  console.log(i); // 0, 1, 2, "foo", "arrCustom", "objCustom"
}
for (let i of iterable) {
  console.log(i); // 3, 5, 7
}
for (let i in iterable) {
  // 过滤掉继承的属性
  if (iterable.hasOwnProperty(i)) {
    console.log(i); // 0, 1, 2, "foo"
  }
}
```

