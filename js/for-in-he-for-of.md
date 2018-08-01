[mdn for...of](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...of)

[mdn for...in](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Statements/for...in)

# for...of
for...of语句在可迭代对象（包括 Array，Map，Set，String，TypedArray，arguments 对象等等）上创建一个迭代循环，调用自定义迭代钩子，并为每个不同属性的值执行语句
# for...in
for...in语句以任意顺序遍历一个对象的可枚举属性。对于每个不同的属性，语句都会被执行。
**for...in不应该用于迭代一个索引顺序很重要的 Array**


# for...of与for...in的区别
1. for...of不能循环普通object对象({key:value}),
2. for...in循环对象时循环出的是key,循环数组时循环出的是索引,for...of循环出的是value
3. for...in 能够循环出原型和原型链继承下来的属性,可在循环体中使用hasOwnProperty过滤
4. for...in循环除了遍历数组元素以外,还会遍历自定义属性(下方例子的iterable.foo = 'hello';)
5. for...of 不会出现3和4的情况

无论是for...in还是for...of语句都是迭代一些东西。它们之间的主要区别在于它们的迭代方式。

for...in 语句以原始插入顺序迭代对象的可枚举属性。

for...of 语句遍历可迭代对象定义要迭代的数据

以下示例显示了与Array一起使用时，for...of循环和for...in循环之间的区别。
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
