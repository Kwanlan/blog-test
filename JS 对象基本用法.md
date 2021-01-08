# JS 数据类型
## 七种数据类型
* number, string, bool, symbol
* undefined, null
* object
### 四基两空一对象
## 五个 flasy 值
* undefined, null  （两空）
* 0, NaN （两数字）
* '' （空字符串）
## JS 学习的三座大山
* 对象（原型）
* this
* AJAX


# 声明对象
1. 对象定义
* 无序的数据集合
* 键值对的集合 ( key: value )
object 是七种数据类型中唯一一种复杂类型。
2. 声明对象的两种语法

```
// 第①种，简单写法，用得多
let obj = {'name': 'Mia', 'age': 18}

// 第②种，正规写法
let obj = new Object({'name': 'Mia'})

// 匿名对象写法
console.log({'name': 'Mia', 'age': 18})
```

注意 ：
键名'name'， 'age'加了引号说明是字符串，引号可省略，就算省略掉引号还是字符串
键名是字符串，不是标识符，∵ 键名可以用数字开头

## 属性名和属性值
每个 key 都是对象的 属性名(property)
每个 value 都是对象的 属性值
`Object.keys(obj) `可以得到 obj 所有的 key

## 变量作属性名
ES6 新语法，之前都是用常量作属性名

* []代表用a 这个变量的值作属性名，而不是字符串'a'作属性名；
```
let a = 'xxx'
let obj = { [a]: 1111 }
```

* 变量值如果不是字符串，则会自动变成字符串
```
var obj = {
  [1+2+3+4]: '十'
}
console.log(obj)  // { 10: "十" }
Object.keys(obj)  // [ "10" ]
```
3. 对象的隐藏属性（原型⭐）
* JS中每一个对象都有一个 隐藏属性__proto__，该隐藏属性存着其 共有属性组成的对象 的地址，
* 这些 共有属性组成的对象 叫作 原型 ，即 隐藏属性存着原型的地址 。

## 原型（共有属性）(重难点▲)
JS中每个对象的隐藏属性__proto__ 存储了一个地址，这个地址所在的内存空间中的对象，叫做原型（共有属性）。

# 删除对象的属性
```
let obj = {name: 'Mia', age: 18}

// 法①
obj.name = undefined

// 法②
delete obj.name    或      delete obj['name']
```
二者区别： 法②删的是属性名和属性值；法①仅删除属性值

* 判断属性名 'xxx' 是否在对象 obj 中

`'xxx' in obj       // true在，false不在`

* 当确定 obj 有属性名 'xxx' 时，判断属性值是否为 undefined

`'xxx' in obj && obj.xxx === undefined`

仅用`obj.xxx === undefined`不能判断属性值是否为`undefined`，因为不确定定`'xxx'`是否为obj的属性
# 查看对象的属性 （读属性）
1. 查看所有属性
## 1.1查看自身属性
```
let obj = {name: 'Mia', age: 18}

Object.keys(obj)     // 查看自身属性名
Object.values(obj)   // 查看自身属性值
Object.entries(obj)     或      obj       // 查看对象
```
## 1.2查看 自身属性 和 共有属性
`console.dir(obj)`

## 1.3查看共有属性（不推荐）
`obj.__proto__    // 不推荐`

## 1.4判断一个属性 'xxx' 是自身的还是共有的
obj.hasOwnProperty('xxx')     // true就是自身的，false就是共有或不存在


* 'xxx' in obj 不能判断出这个属性是否是自身属性还是共有属性,可以验证是否在该对象中
* obj.hasOwnProperty('xxx') 可以判断出这个属性是否是自身属性

2. 查看某个属性

## ① 中括号语法 （刚开始优先使用这种）
`obj['key']      // 'key'是字符串, 不加引号指的是变量`

## ② 点语法
`obj.key       // key 也是字符串'key'`

## ③ 坑新人语法
`obj[变量名]`


# 修改 / 增加对象的【自身】属性 （写属性）

增加 和 修改 基本相同： 已有属性则改；没有属性则增

1. 直接赋值
```
obj.name = 'Mia'  或   obj['name'] = 'Mia'
/* name 属性已存在，就相当于修改属性值；
   name 属性不存在，就会新增这个属性，值为 Mia */
```
2. 批量赋值 (ES6新出的API)
```
let obj = {name: 'mou'}
Object.assign(obj, {name: 'Mia', age: 18, gender: 'female'})
```
* 无法通过自身修改或增加共有属性（读的时候可以读共有属性，写的时候只能写自身属性）
* 可以修改原型的属性，但不推荐，会引起很多问题Object.prototype.toString = 'xxx'

3. 换原型
规范的意思是，要改一开始就改，不要后面再改，会非常影响性能。
`let obj = Object.create(common)      // 推荐写法`

原型链
```
let common = {'国籍': '中国', hairColor: 'black'}
let person = Object.create(common)
Object.assign(person, {name: 'Mia', age: 18})
```