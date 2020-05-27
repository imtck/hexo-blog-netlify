---
title: JavaScript的数组操作
tags: [JavaScript]
date: 2020-05-26 16:23:41
---

| 数组操作方法                 | 数组操作结果           |
| ---------------------------- | ---------------------- |
| Array.length                 | 查看数组长度           |
| Array.from()                 | 浅拷贝数组实例         |
| Array.isArray()              | 确认是否为数组         |
| Array.of()                   | 创建新数组实例         |
| Array.prototype.concat()     | 连接多个数组           |
| Array.prototype.copyWithin() | 浅复制数组             |
| Array.prototype.filter()     | 过滤数组               |
| Array.prototype.find()       | 查找数组               |
| Array.prototype.forEach()    | 遍历数组               |
| Array.prototype.includes()   | 查看数组是否包含内容   |
| array.prototype.indexOf()    | 查找某个元素的索引     |
| array.prototype.join()       | 组合数组元素返回字符串 |
| array.prototype.push()       | 向数组末尾插入元素     |
| array.prototype.pop()        | 删除数组末尾的元素     |
| array.prototype.unshift()    | 向数组首位插入元素     |
| array.prototype.shift()      | 删除数组首位的元素     |
| array.prototype.reverse()    | 颠倒数组               |
| array.prototype.sort()       | 数组排序               |


+ `Array.length` 查看数组的长度
```javascript
const arr = ['a','b','c','d','e']
console.log(arr.length)
// 5
```

+ `Array.from()` 浅拷贝数组或可迭代对象
```javascript
const array = ['a','b','c','d','e']
const str = 'this'
console.log(Array.from(array))
// ["a", "b", "c", "d", "e"]
console.log(Array.from(str))
// ["t", "h", "i", "s"]
```

+ `Array.isArray()` 确认是否为数组
```javascript
const arr = ['a','b','c','d','e']
console.log(Array.isArray(arr))
// true
```

+ `Array.of()` 创建具有可变数量参数的新数组实例
```javascript
console.log(Array.of(5))
// [5]
console.log(Array(5))
// [undefined, undefined, undefined, undefined, undefined]
```

+ `Array.prototype.concat()` 连接多个数组
```javascript
const arr1 = ['a1','b1','c1']
const arr2 = ['a2','b2','c2']
console.log(arr1.concat(arr2))
// ["a1", "b1", "c1", "a2", "b2", "c2"]
console.log(arr2.concat(arr1))
// ["a2", "b2", "c2", "a1", "b1", "c1"]
```

+ `Array.prototype.copyWithin()` 浅复制数组 [详细用法](https://developer.mozilla.org/zh-CN/docs/Web/JavaScript/Reference/Global_Objects/Array/copyWithin)
```javascript
const arr = ['a','b','c','d','e']
console.log(arr)
// ["a", "b", "c", "d", "e"]
arr.copyWithin(2,1,3)
console.log(arr)
// ["a", "b", "b", "c", "e"]
```

+ `Array.prototype.filter()` 过滤数组
```javascript
const arr = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present']
const arr1 = []
arr.filter((item) => {
  if (item.length > 5) {
    arr1.push(item)
  }
})
console.log(arr1)
// ["exuberant", "destruction", "present"]
```

+ `Array.prototype.find()` 查找数组
```javascript
const arr = [
  {name:'libai', age: 20},
  {name:'dufu', age: 24},
  {name:'baijuyi', age: 12},
  {name:'hanyu', age: 40}
]
arr.find((item) => {
  if (item.name === 'baijuyi'){
    console.log(item.age)
  }
})
// 12
```

+ `Array.prototype.indexOf()` 找出某个元素在数组中的索引
```javascript
const arr = ['a','b','c','d','e']
console.log(arr.indexOf('c'))
// 2
```

+ `Array.prototype.join()` 组合数组元素返回字符串
```javascript
const arr = ['a','b','c','d','e']
console.log(arr.join())
// "a,b,c,d,e"
```


+ `Array.prototype.push()` 添加元素到数组的头部
```javascript
const arr = ['a','b','c','d','e']
arr.unshift('123')
console.log(arr)
// ["123", "a", "b", "c", "d", "e"]
```

+ `Array.prototype.push()` 添加元素到数组的末尾
```javascript
const arr = ['a','b','c','d','e']
arr.push('123')
console.log(arr)
// ["a", "b", "c", "d", "e", "123"]
```

+ `Array.prototype.shift()` 删除数组最前面（头部）的元素
```javascript
const arr = ['a','b','c','d','e']
arr.shift()
console.log(arr)
// ["b", "c", "d", "e"]
```

+ `Array.prototype.pop()` 删除数组末尾的元素
```javascript
const arr = ['a','b','c','d','e']
arr.pop()
console.log(arr)
// ["a", "b", "c", "d"]
```

+ `Array.prototype.reverse()` 颠倒数组的顺序
```javascript
const arr = ['a','b','c','d','e']
arr.reverse()
console.log(arr)
// ["e", "d", "c", "b", "a"]
```

+ `Array.prototype.sort()` 数组排序
```javascript
const arr = [1, 30, 9, 21, 100000, 564]
console.log(arr.sort())
// [1, 100000, 21, 30, 564, 9]
```
