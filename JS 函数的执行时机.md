# 定义函数

函数是一种对象

* 具名函数：有名字的函数
```
function 函数名(形式参数1, 形式参数2){
  语句
  return 返回值
}
```
* 匿名函数：没有函数名的函数
`let a = function(x, y){ return x+y }`

* 箭头函数
```
let f1 = x => x*x 
let f2 = (x,y) => x+y // 圆括号不能省
let f3 = (x,y) => {return x+y} // 花括号不能省
let f4 = (x,y) => ({name:x, age: y}) //直接返回对象会出错，需要加个圆括号
```
* 用构造函数
`let f = new Function('x', 'y', 'return x+y')`

所有函数都是 Function 构造出来的，包括 Object、Array、Function 也是

# 函数自身
```
let fn = () => console.log('hi')
fn
```
上面代码不会有任何结果，因为fn没有执行
# 函数调用
```
let fn = () => console.log('hi')
fn() //打印出hi

let fn = () => console.log('hi')
let fn2 = fn
fn2()
```
# 函数调用时机

1. 
```
let a = 1
function fn(){
  console.log(a)
}
//没有调用
```
上面没有调用函数，所以不会打印

2. 
```
let a = 1
function fn(){
  console.log(a)
}
fn()
// 打印出1
```
上面的函数调用时a的值是1，所以打印出了1

3. 
```
let a = 1
function fn(){
  console.log(a)
}

a = 2
fn()
// 打印出2
```
上面的函数调用时，a = 2在它之前，所以函数调用时，a的值变成2，打印出2

4.
```
let a = 1
function fn(){
  console.log(a)
}

fn()
a = 2
//打印出1
```
上面的函数调用时，a的值是1，所以打印出1，a = 2在函数调用之后

5. 
```
let a = 1
function fn(){
  setTimeout(()=>{
    console.log(a)
  },0)
}
fn()
a = 2
//打印出2
```
上面的函数调用时，执行的操作是设置了一个定时器（闹钟），这个定时器会在到期后执行console.log(a)
也就是说在定时器到期执行console.log(a)时，a=2已经执行了，因此打印出2

6. 
```
let i = 0
for(i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
//打印出6个6
```
for循环每执行一次，设定一次定时器，从i =0一直到i=5都各设置一个定时器，一共设置了6个定时器，之后执行i++的自增操作，i的值变成了6，也就是说定时器到期执行console.log(i)时，i的值是6，而设定了6个定时器，每一个定时器都是console.log(6)就打印6个6

7. 
```
for(let i = 0; i<6; i++){
  setTimeout(()=>{
    console.log(i)
  },0)
}
//打印出0、1、2、3、4、5
```
for和let搭配使用，进行了特殊的处理，每一轮都复制了一个i记录当时的值，所以打印出的数字是0、1、2、3、4、5
```
let i = 0
for (i = 0; i < 6; i++) {
    function fn(x) {
        setTimeout(() => {
            console.log(x)
        }, 0)
    }
    fn(i)
}
或
let i = 0
for (i = 0; i < 6; i++) {
    !function fn(x) {
        setTimeout(() => {
            console.log(x)
        }, 0)
    }(i)
}
//打印出0、1、2、3、4、5
```
以上代码也可以打印出0、1、2、3、4、5