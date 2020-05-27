---
title: JavaScript-数组去重
tags: [JavaScript]
date: 2020-05-26 20:03:36
---
在JavaScript操作中，经常有关于Array的操作，常见的操作有增删改查，排序去重等等，但是数组的去重经常要用到自己手写的代码，网上查询关于JavaScript的数组去重操作都有很多方法，但是关于数组的操作不是copy代码就可以做到高枕无忧的。不同的方法会有不同的耗时，对于性能的影响也各不相同，在数据量小的时候尚不明显，但是在大数据的情况下，如果数据量很是庞大，那么耗时是很明显的，所以这么多关于数组去重的方法，到底那种方法更好呢。
为了知道数组去重对于时间的消耗，手动进行了测试


| 去重方法            | 10000 | 100000  | 1000000 | 10000000 |
| ------------------- | ----- | ------- | ------- | -------- |
| 利用ES6 Set去重     | 5ms   | 15ms    | 252ms   | 4148ms   |
| for循环，splice去重 | 273ms | 27422ms | 未测试  | 未测试   |
| 利用indexOf去重     | 138ms | 13487ms | 未测试  | 未测试   |
| 利用sort()          | 5ms   | 47ms    | 375ms   | 4018ms   |
| 利用includes        | 150ms | 15134ms | 未测试  | 未测试   |
| 利用Map结构数据     | 8ms   | 36ms    | 471ms   | 5873ms   |


+ 创建数组
```javascript
const ArrStart = new Date().getTime()
const arr = []
Array.from(new Array(100000), (item, index) => {
  arr.push(index)
  arr.push(index + index)
})
const ArrEnd = new Date().getTime()
console.log('创建数据耗时：' + (ArrEnd - ArrStart) + 'ms')
```
+ 去重方法
```javascript
const Start = new Date().getTime()
function Deduplication(arr) {
  // 去重的具体方法
}
Deduplication(arr)
const End = new Date().getTime()
console.log('去重耗时：' + (End - Start) + 'ms')
```

+ 排序方法
```javascript
const StartSort = new Date().getTime()
const sortResult = arr.sort((a, b) => {
  return a - b
})
const EndSort = new Date().getTime()
console.log('排序耗时：' + (EndSort - StartSort) + 'ms')
```

#### 利用ES6 Set去重(ES6常见)
```javascript
function Deduplication(arr) {
  return Array.from(new Set(arr))
}
```
#### 利用for嵌套for，然后splice去重(ES5常见)
```javascript
function Deduplication(arr) {
  for(var i=0; i<arr.length; i++){
    for(var j=i+1; j<arr.length; j++){
      if(arr[i]==arr[j]){         //第一个等同于第二个，splice方法删除第二个
        arr.splice(j,1);
        j--;
      }
    }
  }
  return arr;
}
```
#### 利用IndexOf
```javascript
function Deduplication(arr) {
  if (!Array.isArray(arr)) {
    console.log('type error!')
    return
  }
  var array = [];
  for (var i = 0; i < arr.length; i++) {
    if (array.indexOf(arr[i]) === -1) {
      array.push(arr[i])
    }
  }
  return array;
}
```
#### 利用sort()
```javascript
function Deduplication(arr) {
  if (!Array.isArray(arr)) {
    console.log('type error!')
    return;
  }
  arr = arr.sort()
  var arrry = [arr[0]];
  for (var i = 1; i < arr.length; i++) {
    if (arr[i] !== arr[i - 1]) {
      arrry.push(arr[i]);
    }
  }
  return arrry;
}
```
#### 利用includes
```javascript
function Deduplication(arr) {
  if (!Array.isArray(arr)) {
    console.log('type error!')
    return
  }
  var array = [];
  for (var i = 0; i < arr.length; i++) {
    if (!array.includes(arr[i])) {//includes 检测数组是否有某个值
      array.push(arr[i]);
    }
  }
  return array
}
```
#### 利用Map结构数据
```javascript
function Deduplication(arr) {
  let map = new Map();
  let array = new Array();  // 数组用于返回结果
  for (let i = 0; i < arr.length; i++) {
    if (map.has(arr[i])) {  // 如果有该key值
      map.set(arr[i], true);
    } else {
      map.set(arr[i], false);   // 如果没有该key值
      array.push(arr[i]);
    }
  }
  return array;
}
```

经过一轮测试
+ 利用ES6 Set去重
+ 利用sort()
+ 利用Map结构数据
均可在百万数据量的时候实现快速去重，千万级数据也能较快去重


