##  垃圾回收机制

- 内存泄漏：程序中分配的内存无法释放或者无法释放

## 闭包

- 闭包：闭包=内层函数+外层函数变量

~~~js
// i很容易被修改，因为是全局变量
     let i = 0
     function fn() {
       i++
       console.log(`函数被调用了${i}次`)
     }
~~~

闭包的应用

~~~js
function count() {
      let i = 0
      function fn() {
        i++
        console.log(`函数被调用了${i}次`)

      }
      return fn
    }
    const fun = count()


~~~

## 动态参数Arguments

- 当我们不知道函数形式参数到底有多少个的时候，比如说设计一个求和函数getSum()
- 这个时候可以使用arguments对象，可以引用函数的参数，这是一个伪数组，所以没有pop，push这样的数组的方法，但是具有数组的长度
- 非箭头函数中使用

~~~js
function getSum() {
      let sum = 0
      for (let i = 0; i < arguments.length; i++) {
        sum += arguments[i]
      }
      return sum
    }
getSum(1,2,3,4,5)	//15
~~~

## 剩余参数

- 剩余参数是真数组，能够使用Array的方法
- 同样以求不定参数的和为例子

~~~js
function getSum(...arr) {
      let sum = 0
      for (let i = 0; i < arr.length; i++) {
        sum += arr[i]
      }
      console.log(sum);
    }
getSum(1,2,3,4,5) //15
~~~

- 能够规定至少求几个数的和

~~~js
function getSum(a, b, ...arr) {
      let sum = 0
      sum = a + b
      for (let i = 0; i < arr.length; i++) {
        sum += arr[i]
      }
      console.log(sum);

    }
    getSum(1, 2)
    getSum(1, 2, 3)
~~~

## 展开运算符

- 展开运算符和剩余参数的形式很类似，但是有以下作用

  - 1、得到一堆数字中的最大最小值

    ~~~js
        const arr1 = [1, 2, 3]
        //1 和得到最大值、最小值
        console.log(Math.max(...arr1));	//3
        console.log(Math.min(...arr1)); //1
    ~~~

    ​

  - 2、用于合并数组

    ~~~js
        //2 用于合并数组
        const arr1 = [1, 2, 3]
        const arr2 = [3, 4, 5]
        const arr = [...arr1, ...arr2]
        console.log(arr);	//[1,2,3,3,4,5]
    ~~~



## 箭头函数

- 是es6新增的语法

- 基本语法

  - ~~~js
        //普通函数	
        const fn1 = function () {
              console.log(123)
            }
        //箭头函数
        const fn2 = () => {
          		console.log(345)
        	}
    ~~~

- 一个形参可以省略小括号

  - ~~~js
        const fn = x => {
          console.log(x);
        }
        fn(1)
    ~~~

- 只有一行代码可以省略大括号

  - ~~~js
        const fn2 = x => console.log(x);
        fn2(2)
    ~~~

- 省略return

  - ~~~js
        const fn3 = x => x + x
        console.log(fn3(3))
    ~~~

- 创建对象

  - ~~~js
    const createPerson = (name, age, job) => ({
      name: name,
      age: age,
      job: job
    });

    const person = createPerson('周杰伦', 46, '歌手');
    console.log(person);
    ~~~



​	