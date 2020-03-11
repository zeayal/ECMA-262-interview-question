# ECMA-262-interview-question

每天一道 JS 面试题

## 1、定义 `var a = {n: 1}; var b = a;`，`a.x=a={n: 2}`, 此时 `console.log(a.x); console.log(b);`， 分别打印出什么？

> 题目出处：未知 

> 知识点：js连续赋值、栈和堆内存的管理

> 详细解析：@see https://www.zhihu.com/question/41220520

答案：

```js
var a = { n: 1 };
var b = a;

// 一般赋值运算为从右到左，但 a.x 的运算优先级比较高，优先运算, 第一步获取到 a.x 不存在，js在 `堆中` 开辟新内存储存 a.x = undefined,
// 接着运行 a = {n: 2}; a 指向了另一个地址，并且这个表达式的范围值是 {n: 2}
// 接着 b.x -> {n: 1}.x = {n: 2}  此时b指向之前a的引用地址，但是 a 已经指向了 {n: 2} 新内存地址
// b = {n: 1, x: {n: 2}}
a.x = a = { n: 2 };

console.log(a.x); // 打印 undefined
console.log(b); // 打印 {n: 1, x: {n: 2}}
```

## 检查给定的一个参数是 `String` 类型,只适用于 string promitives.使用 typeof 检查被分类为 string primitive 的值。
```js
const isString = val => typeof val === 'string';
```

```js
isString('10'); // true
```

