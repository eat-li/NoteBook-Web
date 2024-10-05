# BOM

## BOM概述

浏览器对象模型BOM，最大的对象为window

文档对象模型DOM，最大的对象为document

BOM在DOM之上，window.document.querySelector

~~~js
var num = 20
console(window.num)//console(num)
function fn() {
    console.log(11);
}
    fn();
    window.fn();
~~~

## window常见事件

###  load和DOMContentLoaded事件

~~~js
	//load整个页面全部加载完毕，再去执行代码包括dom， 图片、flash css等等
    //能够让js代码放在任何地方
<script>
      window.addEventListener('load', function () {
      let btn = document.querySelector('button')
      btn.addEventListener('click', function () {
        alert('你好啊')
      })
    })
// DOM元素加载完就能执行DOMContentLoaded会更快点，不包含图片、flash css等等
    document.addEventListener('DOMContentLoaded', function () {
      alert('你好啊')
    })
</script>

<button>点击</button>

~~~

### 调整窗口大小事件resize

~~~js
window.addEventListener('load', function () {
      let div = document.querySelector('div')
      // 只要窗口大小发生了改变就会执行
      window.addEventListener('resize', function () {
        console.log(window.innerWidth);
        //可以用这个做响应式布局

        console.log('变化了');
        if (window.innerWidth <= 500) {
          div.style.display = 'none'
        }
        else {
          div.style.display = 'block'

        }
      })
    })
<div></div>

~~~

## 定时器

### setTimeout

~~~js
window.setTimeout(调用函数,延时时间)
window可以省略
延时时间到了就执行调用函数
~~~

### setInterval

~~~js
window.setInterval(调用函数,延时时间)
window可以省略
每隔延时时间就执行依次调用函数
~~~

### 清除定时器

~~~js
let timer1 = setTimeout(functon(){执行内容},1000)
let timer2 = setInterval(functon(){执行内容},1000)
//清除定时器

clearTimeout(timer1)
clearInterval(timer2)

~~~

## Location

### location对象

~~~js
 // location.href获取整个url地址
    // location.host返回主机域名
    // location.search返回参数
    // location.hash返回链接锚点
    //locaton.pathname返回路径
    // href searh
~~~

### assign 和replace方法

~~~js
	  // assign记录浏览历史可以后退
      //replace不记录浏览历史不能后退
      // location.assign('http://www.baidu.com')
      // location.replace('http://www.baidu.cn')
      // reload重新加载
      // location.reload('http://www.baidu.cn')
      // true强制刷新
      location.reload(true)
~~~

