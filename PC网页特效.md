# PC网页特效

## offset

### 父与子

~~~html
<div class="father">
    <div class="son"></div>
  </div>
  <div class="w"></div>

~~~

~~~css
 * {
      margin: 0;
      padding: 0;
    }

    .father {
      height: 200px;
      width: 200px;
      background-color: pink;
      margin: 150px;
    }

    .son {
      width: 100px;
      height: 100px;
      background-color: purple;
      margin-left: 45px;
    }
~~~

~~~js
    // 3返回带有定位的父亲，否则返回body
    console.log(son.offsetParent);
    // 区别：返回的是最近一级的父亲，不管有没有定位
    console.log(son.parentNode);
~~~

### offset和style的区别

~~~css
.box{
    width:200px;
    height:200px;
}
~~~

~~~js
offset和style
console.log(box.offsetWidth)
console.log(box.style.width)
~~~

~~~js
offsetWidth返回的是：
200
style.width返回的是：
200px
~~~

## client

~~~js
    let div = document.querySelector('div')
    // 和offset区别，不包含边框但是包含内边距
    console.log(div.clientWidth);
    console.log(div.clientHeight);
~~~

## scroll

~~~js
    let div = document.querySelector('div')
    // 和offset区别，不包含边框但是包含内边距
    // scroll得到的是实际的元素的大小，文字
    console.log(div.scrollHeight);
    console.log(div.clientHeight);
    // 滚动事件
    div.addEventListener('scroll', function () {
      console.log(div.scrollTop);

    })
~~~

## 动画函数

~~~js
function animate(obj, target, callback) {
  clearInterval(obj.timer)
  obj.timer = setInterval(function () {
    let step = (target - obj.offsetLeft) / 10
    step = step > 0 ? Math.ceil(step) : Math.floor(step);
    if (obj.offsetLeft == target) {
      clearInterval(obj.timer)
      if (callback) {
        callback()
      }
    }
    obj.style.left = obj.offsetLeft + step + 'px'
  }, 15)
}

~~~

## 本地存储

### sessionStorage

~~~js

    // window.sessionStorage生命周期为关闭浏览器窗口

    // 在同一个窗口下可以共享

    // 以键值对的形式存储使用

     // 用户数据存储在浏览器中

     // 只能存储字符串
~~~

~~~html
  <input type="text">
  <button class="set">存储数据</button>
  <button class="get">获取数据</button>
  <button class="remove">删除数据</button>
  <button class="del">清空所有数据</button>
~~~

~~~js
存储表单元素中的值
sessionStorage.setItem('key', value)
~~~

~~~js
获取数据
sessionStorage.getItem('key')
~~~

~~~js
删除数据
sessionStorage.removeItem('key')
~~~

~~~js
清空数据
sessionStorage.clear()
~~~

### localStorage

~~~js
  // 用户数据存储在浏览器中 
   //只能存储字符串 
    // window.localStorage生命周期为关闭浏览器窗口
    // 在同一个窗口下可以共享
    // 以键值对的形式存储使用
~~~

```js
存储表单元素中的值
localStorage.setItem('key', value)
```

```js
获取数据
localStorage.getItem('key')
```

```js
删除数据
localStorage.removeItem('key')
```

```js
清空数据
localStorage.clear()
```