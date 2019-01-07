#变量类型
## 6种原始类型(值类型)：

1. boolean
2. string
3. number
4. **null**
5. undefined
6. symbol (es6)

## 引用类型
在 JS 中，除了原始类型那么其他的都是对象类型了。对象类型和原始类型不同的是，原始类型存储的是值，对象类型存储的是地址（指针）。当你创建了一个对象类型的时候，计算机会在内存中帮我们开辟一个空间来存放值，但是我们需要找到这个空间，这个空间会拥有一个地址（指针）


```
function test(person) {
  person.age = 26
  person = {
    name: 'yyy',
    age: 30
  }

  return person
}
const p1 = {
  name: 'yck',
  age: 25
}
const p2 = test(p1)
console.log(p1) // -> ?
console.log(p2) // -> ?
```

* test(p1) 将p1的对象地址当作函数参数
* person.age = 26 会将对象p1的age也修改
* person = {name: 'yyy',age: 30} person对象的地址重新指向新对象，和p1不在绑定
* const p2 = test(p1) 将方法里person的地址传递给p2

按值传递的类型，复制一份存入栈内存，这类类型一般不占用太多内存，而且按值传递保证了其访问速度。按共享传递的类型，是复制其引用，而不是整个复制其值（C 语言中的指针），保证过大的对象等不会因为不停复制内容而造成内存的浪费

## typeof
| type| 结果 |
|-----|-----|-----|
|typeof 123| number|
|typeof '123'| string |
|typeof true| boolean |
|typeof undefined| undefined |
||
|typeof null| object |