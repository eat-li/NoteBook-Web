## Vuex

![73234942664](C:\Users\13518\AppData\Local\Temp\1732349426641.png)

原理图如上，

一、个人理解，Vc要操作数据，通过在methods方法中调用

```js
this.$store.dispatch('Action对象中的方法名',data)
```

二、然后在index.js中的actions对象中添加这个方法

```js
const actions={
    Action方法名(content,value){
        content.commit("mutations对象中的方法名",value)
    }
}
```

三、最后在index.js中mutations对象中操作

```js
const mutations={
    mutation方法名(state,value){
        //进行的操作
    }
}
```

**特殊之处：**

Vc中methods中的方法不经过actions，直接对mutations进行操作,类似于我不让服务员为我点餐，我直接对厨师进行传递

```js
methods:{
    func(){
        //相当于省去了dispatch的这一步
        this.$store.commit('mutation中的方法',data);
    }
}
```

另外，Vuex中的actions不止能有一个，当一件事情非常的复杂，我们需要多个"动作"来为我们服务，如下，类似于让一个服务员为我们点菜，一个为我们上菜，一个为我们服务

```js
const actions={
    func(context,value){
        context.dispatch('demo1',value);
    }
     demo1(context,value){
        context.dispatch('demo2',value);
    }
 	demo2(context,value){
        context.commit('mutation中方法',value);
    }

}
```

建议，aciton中的方法写为小写，然后mutation中的方法写成大写，这样更能够体现出这才是我们调用操作数据的重点

1. context类似是一个精简版本的store，能够提供我们想要的基本的操作

2. value是从vc中传递过来的数据参数

3. 数据存在state对象中,拿到数据需要找到state

4. Vue.use(Vuex)应该写在index.js中

   因为在js中，存在变量提升，倘若写在main.js中的话，会在使用插件之前就调用，那就会出现报错的提示

5. vue开发者工具中vuex的使用





**Vuex的环境配置**



1. 首先安装Vuex

   ```js
   npm i vuex@3//支持vue2
   npm i vuex //默认安装vue3版本的
   ```

   后续的操作都在src下新建的文件夹store下的index.js中操作

2. 引入Vue和Vuex

   ```js
   //引入vue
   import Vue from "vue";
   //引入vuex
   import Vuex from "vuex";
   ```

   ​

2. 应用插件vues

   ```js
   Vue.use(vuex)
   ```

   ​

3. 准备actions

   ```js
   //action用于响应组件中的动作
   const actions={}
   ```

   ​

4. 准备mutations

   ```js
   //mutations用于操作数据(state)
   const mutations={}
   ```

   ​

5. 准备states

   ```js
   //state用于存储数据(state)
   const state = {}
   ```

   ​

7. 创建并导出Store

   ```js
   export default new Vuex.Store({
     actions,
     mutations,
     state,
   });
   ```

   **main.js**

8. 引入插件vuex

   ```js
   import Vuex from 'vuex'
   ```

9. Vm组件中配置store配置项

   ```js
   new Vue({
     el: "#app",
     render: (h) => h(App),
     store,
     beforeCreate() {
       Vue.prototype.$bus = this;
     },
   });
   ```

   ​