# DOM

##  获取元素的方法

### 通过Id获取元素

~~~html
<body>
    <div id="time">2024-9-28</div>
  <script>
    //根据id获取元素
    //getElementBYid()
    const times = document.getElementById('time');
    //参数为大小写敏感的字符串
    // console.log(times);
    //打印元素对象，更好的查看里面的属性和方法
    //console.dir(times)
  </script>
</body>
~~~

### 通过标签获取元素

~~~~js
const ans = document.getElementsByTagName('li')
//返回的是获取过来的元素对象的集合以伪数组的形式
    //如果只有一个li还是返回的伪数组
    //没有元素也是返回空的伪数组
    //可以指定父元素
~~~~

### HTML5新增的获取的方式

~~~js
<body>
  <div class="box">盒子</div>
  <div class="box">盒子</div>
  <div id="nav">
    <ul>
      <li>首页</li>
      <li>产品</li>
    </ul>
  </div>
  <script>
    //类名
    let boxs = document.getElementsByClassName('box');
    console.log(boxs);
    //qs返回指定选择器的第一元素对象,切记里面的选择器要加符号
    let box1 = document.querySelector('.box');
    console.log(box1);
    let nav = document.querySelector('#nav');
    console.log(nav);
    let li = document.querySelector('li')
    console.log(li);

    let boxs1 = document.querySelectorAll('.box');
    console.log(boxs1);

    let lis = document.querySelectorAll('li')
    console.log(lis);

  </script>
</body>
~~~

### 获取body和html标签

~~~js
<script>
    //body
    let bodyele = document.body;
    console.log(bodyele);
    //html
    let hemlele = document.documentElement;
    console.log(hemlele);

  </script>
~~~

## 事件基础

### 什么是事件

事件三部分：事件源 事件类型 事件处理程序——即事件三要素

- 获取元素
- 事件类型
- 事件处理程序

## 操作元素

### 修改元素内容

~~~js
	//innerhtml和innertext
    //区别:innertext不识别html标签,去除空格和换行
	//innnerhtml能够识别html标签，空格和换行
	//这两个属性是可以读写的，可以获取里面的内容
    p.innerHTML = '<strong>hello word</strong>'
    
~~~

### 修改元素属性

~~~
element.属性名 = ''
~~~

~~~html
<div class='hello'>你好</div>
<img src="/images/photo1.jpg" alt="" title="hello">

    <script>
        //1获取元素
    	const img = document.querySelector('img')
        //2添加事件
        img.onclick = function(){
            img.title = '你好'
            img.src = '/images/photo2.jpg'
        }
    </script>
~~~

### 修改元素样式属性

~~~js
element.style.属性名=' '
~~~

~~~html
<style>
    div {
      width: 200px;
      height: 200px;
      background-color: pink;
    }
  </style>
~~~

~~~html
<body>
  <div></div>
  <script>
    const div = document.querySelector('div')
    div.addEventListener('click', function () {
      this.style.backgroundColor = 'red';
      this.style.width = '50px'
    })
  </script>
</body>
~~~

### 通过className修改元素样式属性

~~~js
element.className = '类名'
//但是这样使用会覆盖原来的元素的类名
//可以这样来添加新的类名
element.className = '类名 新类名'
~~~

### 通过classList修改元素样式属性

~~~js
//添加类
element.classList.add('类名')
//删除类
element.classList.remover('类名')
~~~

### 修改表单属性

~~~js
//利用DOM可以修改以下表单元素的属性
type、value、checked、selected、disabled
~~~



## 节点操作

### 什么是节点

**获取元素的方法：**

1. 利用 DOM 提供的方法获取元素
2. 利用节点层级关系获取元素

不过通过节点的操作能够更方便获取元素

一般地，节点至少拥有nodeType（节点类型）、nodeName（节点名称）和nodeValue（节点值）这三个

基本属性。

- 元素节点 nodeType 为 1
- 属性节点 nodeType 为 2
- 文本节点 nodeType 为 3 （文本节点包含文字、空格、换行等）

### 父节点

~~~js
node.parentNode
//得到的是离元素最近的父级节点
//如果找不到父节点那么返回为空
~~~

### 子节点

~~~js
 parentNode.childNodes
//返回值里面包含了所有的子节点，包括元素节点，文本节点等。

~~~

~~~js
 parentNode.children
//返回值里面包含了所有的子元素节点，虽然非标准但是得到了各个浏览器的支持
~~~

~~~js
 parentNode.firstChild
 parentNode.lastChild
//这两个方法分别返回的是第一个和最后一个节点，同样包括所有节点
//找不到则返回null
~~~

~~~js
 parentNode.firstElementChild
 parentNode.lastElementChild
 //这两个方法分别返回第一个子元素节点和最后一个子元素节点
//找不到则返回null
~~~

**为了解决各种兼容性问题，可以这样来获取第一个和最后一个子元素**

~~~js
parentNode.children[0]
parentNode.children[parentNode.children.length-1]
~~~

### 兄弟节点

~~~js
node.nextSibling
//返回当前元素的下一个兄弟节点，找不到返回null，同样包含所有节点
~~~

~~~js
node.previousSibling
//返回当前元素上一个兄弟节点，找不到则返回null，同样包含所有节点
~~~

**以下两种获取兄弟元素节点，有兼容性问题 ，IE9以上才支持，可以通过自己封装一个函数来解决兼容性问题**

****

~~~js
node.nextElementSibling
// 返回当前元素下一个兄弟元素节点，找不到则返回null。
~~~

~~~JS
node.previousElementSibling
//返回当前元素上一个兄弟元素节点，找不到则返回null
~~~

### 创建节点

~~~js
document.createElement('tagName')
//通过这个方法动态创建元素节点
~~~

### 添加节点

~~~js
node.appendChild(child)
//这个方法将一个节点添加到指定父节点列表末尾
node.insertBefore(child,指定元素)
//这个方法将一个节点添加到指定元素的前面
~~~

### 删除节点

~~~js
node.removeChild(child)
//从DOM中删除一个子节点，返回的是删除的节点
~~~

### 复制节点（克隆节点）

~~~js
node.cloneNode()
//1 参数为false 或者空，则称为浅拷贝，只复制节点本身，不复制里面的子节点
//2 参数为true，则是深拷贝，会复制节点本身以及里面的子节点
~~~

### 三种动态创建节点的方式

~~~js
document.write()

element.innerHTML

document.createElement()
~~~

- document.write是直接将内容写入页面的内容流， **但是文档流执行完毕，则它会导致页面全部重绘** 
- innerHTML是将内容写入某个DOM节点，不会导致页面全部重绘
- createElement 创建多个元素的效率稍微低一点点，但是结构更清晰
- innerHTML 不通过拼接字符串，采取数组形式拼接，创建多个元素效率更高结构稍微复杂

**不同浏览器下，innerHTML效率比createElement高**



