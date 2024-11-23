# 一、常用的自定义函数

## 倒计时

~~~js
function countDown(time) {
      let nowTime = +new Date();//当前的毫秒数
      let inputTime = +new Date(time);//永辉输入时间的毫秒数
      let times = inputTime - nowTime;//times是剩余的时间的总的毫秒数
      times = times / 1000;//1s = 1000ms
      let d = parseInt(times / 60 / 60 / 24);
      d = d < 10 ? '0' + d : d;
      let h = parseInt(times / 60 / 60 % 24);
      h = h < 10 ? '0' + h : h;
      let m = parseInt(times / 60 % 60);
      m = m < 10 ? '0' + m : m;
      let s = parseInt(times % 60);
      s = s < 10 ? '0' + s : s;
      return d + '天' + h + '时' + m + '分' + s + '秒';
    }
~~~

## 范围随机数

~~~js
 function getRandom(min, max) {
      return Math.floor(Math.random() * (max - min + 1)) + min;
    }
~~~

## sort函数排序

~~~js
let arr1 = [1, 13, 72, 4, 1, 8]
    arr1.sort(function (a, b) {
      return a - b;//升序的顺序排列
      //return b-a就是降序排列
    });
~~~

## 数组去重函数

~~~js
function unique(arr) {
      let new_arr = new Array();
      for (let i = 0; i < arr.length; i++) {
        if (new_arr.indexOf(arr[i]) === -1) {
          new_arr.push(arr[i]);
        }
      }
      return new_arr;
    }
~~~

## 获取当前系统时间年月日

~~~js
function gettime(){
    var date = new Date();
        console.log(date.getFullYear()); // 返回当前日期的年  2019
        console.log(date.getMonth() + 1); // 月份 返回的月份小1个月   记得月份+1 呦
        console.log(date.getDate()); // 返回的是 几号
        console.log(date.getDay()); // 3  周一返回的是 1 周六返回的是 6 但是 周日返回的是 0
        // 我们写一个 2019年 5月 1日 星期三
        var year = date.getFullYear();
        var month = date.getMonth() + 1;
        var dates = date.getDate();
        var arr = ['星期日', '星期一', '星期二', '星期三', '星期四', '星期五', '星期六'];
        var day = date.getDay();
        return '今天是：' + year + '年' + month + '月' + dates + '日 ' + arr[day];
}
~~~

## 获取当前系统时间时分秒

~~~js
function getTimer() {
            var time = new Date();
            var h = time.getHours();
            h = h < 10 ? '0' + h : h;
            var m = time.getMinutes();
            m = m < 10 ? '0' + m : m;
            var s = time.getSeconds();
            s = s < 10 ? '0' + s : s;
            return h + ':' + m + ':' + s;
        }
~~~

## 解决兄弟节点兼容性问题函数

~~~js
function getNextElementSibling(element) {
      let el = element
      while (el = el.nextSibling) {
        if (el.nodeType === 1) {
          return el;
        }
      }
      return null
    }
~~~



