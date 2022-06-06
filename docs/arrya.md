# 方法
[toc]{type: "ol", level: [1,2,3]}
## fill

```js
//--run--
const arr = Array() // creates an an empty array
console.log(arr)

const eightXvalues = Array(8).fill('X') // it creates eight element values filled with 'X'
console.log(eightXvalues) // ['X', 'X','X','X','X','X','X','X']

const eight0values = Array(8).fill(0) // it creates eight element values filled with '0'
console.log(eight0values) // [0, 0, 0, 0, 0, 0, 0, 0]

const four4values = Array(4).fill(4) // it creates 4 element values filled with '4'
console.log(four4values) // [4, 4, 4, 4]
```


填充预创建的arrya
## 判断是否包含某个值
```js
// --run--
let a=['ck','kl','io']
console.log(a.indexOf('ji'))
```
如果有那么返回的是index，没有的话就是-1了。
不过这个是不是有点麻烦？哈哈，当然有直接进行真假判断的方法
```js
// --run--
let a=['ck','kl','io']
console.log(a.includes('op'))
```
yes,if 有就是ture, else false
## 删除和替换
splice()
它需要三个参数：起始位置，要删除的次数和要添加的项目数。
```js
// --run--
 const numbers = [1, 2, 3, 4, 5]
  numbers.splice()
  console.log(numbers)// -> remove all items
  console.log(numbers.splice())
```
输出原来的数组就是改变后的新数组，numbers.splice()就是代表被移除的数据
```js
// --run--
const numbers = [1, 2, 3, 4, 5, 6,7,8,9]	
  console.log(numbers.splice(3, 3, 7, 8, 9)) 
  console.log(numbers)
```
这里就是3个参数都有的，从index 3开始删除3个元素，然后在这个位置替换上新的内容