# vue

![image-20230410193730459](vue.assets/image-20230410193730459.png)



**渐进式**：逐步实现新特性，慢慢实现模块化开发、路由、状态管理等新特性。综合了Angular（模块化）和React（虚拟DOM）的优点



Axios：前端通信框架，因为vue就是只关注视图层，为了处理DOM，不具备通信能力，就需要额外使用一个通信框架和服务器交互。当然也可以直接选择JQuery提供的AJAX通信功能



## UI框架

Ant-design ： 阿里巴巴出品，基于React的UI框架

ElementUI、iview、ice ： 饿了么出品，基于Vue的UI框架

Bootstrap：Twitter推出的一个用于前端开发的开源工具包

AmazeUI ： HTML5跨屏前端框架

## JavaScript构架工具

Banel： JS编译工具，主要用于浏览器不支持的ES新特性，比如用于编译TypeScript

WebPack： 模块打包器，主要用来打包、压缩、合并及按序加载





## 前后端分离史



![image-20230410203342564](vue.assets/image-20230410203342564.png)



MVC是一个不错的协作模式，能够有效的降低代码的耦合度，从架构上能够让开发者明白代码模块。为了使View更加纯粹，还可以使用Thymeleaf、Freemarker等模板引擎，使模板里无法写入java代码，让前后端分工更加清晰。



**缺点：**

![image-20230410203740204](vue.assets/image-20230410203740204.png)



### web1.0

早期的JSP、PHP可以称为web1.0时代



### web2.0

05年AJAX被正式提出并开始使用CDN作为静态资源存储，于是出现了JavaScript火起来的SPA(Single Page Application)单页面应用时代

![image-20230410204137617](vue.assets/image-20230410204137617.png)



**优点**：前后端的分工清晰，前后端的关键协作点是Ajax接口。其实和JSP时代差别不大，复杂度从服务器端的JSP里移到了浏览器的JavaScript，浏览器端变得复杂，类似MVC，浏览器端的分层架构开始出现：

![image-20230410204328967](vue.assets/image-20230410204328967.png)

**缺点**： 

![image-20230410204446770](vue.assets/image-20230410204446770.png)

### 大前端时代

前端为主的MV*时代

![image-20230410204718183](vue.assets/image-20230410204718183.png)

后端 轻松了，研究分布式、微服务、大数据...

为了降低前端开发复杂度，涌现了大量的前端框架，如：AngularJS  React  Vue.js   EmberJS

这些框架总的原则是先按类型分层，比如Templates 、Controllers 、Models，然后再在层内做切分

![image-20230410204923720](vue.assets/image-20230410204923720.png)



![image-20230410205008465](vue.assets/image-20230410205008465.png)



![image-20230410205020491](vue.assets/image-20230410205020491.png)



### NodeJS-全栈时代

随着NodeJS的兴起，JavaScript开始有能力运行在服务端，新的研发模式

![image-20230410210102349](vue.assets/image-20230410210102349.png)

在这种模式下，前后端职责分明，对于前端，两个UI层各司其职

**Front-end** UI Layer处理浏览器层的展现逻辑。通过CSS渲染样式，通过JavaScript添加交互功能，Html的生成也可以放在这层

**Back-end** UI Layer处理路由、模板、数据获取、Cookie等。通过路由，前端可以自主把控URL Desin，这样无论是单页面应用还是多页面应用，前端都可以自由调控。后端也可以摆脱对展现的强关注，转而可以专心于业务逻辑层的开发



![image-20230410210544897](vue.assets/image-20230410210544897.png)

![image-20230410210644583](vue.assets/image-20230410210644583.png)



Html： 超文本标记语言，用来写网页的基本结构

CSS： 层叠样式表，用来让页面更加生动好看

JavaScript： 解释性或即时编译型的高级编程语言



## Vue初识

Vue 是 MVVM模式

Model： 模型层，这里表示JavaScript对象

View： 视图层，这里表示DOM （HTML操作的元素）

ViewModel ： 连接视图和数据的中间件，Vue.js 就是MVVM中的ViewModel层的实现者



在MVVM框架中，是不允许数据和视图直接通信的，只能通过ViewModel来通信

+ ViewModel 能够观察到数据的变化，并对视图对应的内容进行更新
+ ViewModel能够监听到视图的变化，并能够通知数据发生改变



![image-20230410213400658](vue.assets/image-20230410213400658.png)

![image-20230410213158086](vue.assets/image-20230410213158086.png)



MVVM 实现了视图View和模型Model的分离



vue.js 就是一个MVVM的实现者，核心就是实现了DOM监听和数据绑定



### Hello Vue

使用VScode编写Vue项目

**编译器打开本地创建的VueTest文件夹，新建一个index.html，**

![image-20230411094117712](vue.assets/image-20230411094117712.png)

打开index.html后，直接输入html，直接选择html:5 会自动生成html的基本结构，也可以输入一个感叹号 ！，一样的直接生成html基本结构

引入vue3.x的源码

官方提供直接引入CDN的服务地址，只要用<script>标签 ，就可以直接引入Vue3，（学习期间暂时不需要使用vue-cli、webpack或Vite这些构建工具来构建项目）

```html
<script src="https://unpkg.com/vue@next"></script>
```



**引入框架后，就可以写Vue的代码了**

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id = "app"></div>
</body>
<script>
    Vue.createApp({ //创建一个Vue实例
        template:'<div>Hello Vue</div>'
    }).mount("#app")
</script>
</html>
```



打开index.html文件，显示测试结果  “Hello Vue”



### 计数器

特性：不改变DOM，面向数据编程，数据传到DOM中

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id="app"></div>
    
</body>
<script>
    Vue.createApp({
        data(){
            return{
                counter:1
            }
        },
        mounted(){
            setInterval(()=>{
                this.counter += 1
                //this.$data.counter +=1
            },1000)

        },
        template:'<div>{{counter}}</div>' //字面量
    }).mount("#app")
</script>
</html>
```



### 欢迎语

method() 中声明方法

v-on 点击响应事件

v-if 如果为false DOM值就不显示， 

没有改变DOM，修改数据，传到DOM，来改变显示内容

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id = "app"></div>
</body>
<script>
    Vue.createApp({ //创建一个Vue实例
        data(){
            return{
                content:"",
                setMeal:'真空套餐 帝王套餐 夏日套餐',
                isShowMeal:false
            }
        },
        methods:{
            welcomeBtnClick(){
                this.content="欢迎光临"
            },
            byeBtnClick(){
                this.content="走好不送"
            },
            showOrHideBtnClick(){
                this.isShowMeal = !this.isShowMeal
            }
        },
        //&nbsp分开按钮
        template:`
            <div>
            <div>{{content}}</div>
            <button v-on:click="welcomeBtnClick">有顾客来</button>&nbsp; 
            <button v-on:click="byeBtnClick">有顾客走</button>
            <div>
                <div v-if="isShowMeal">{{setMeal}}</div>
                <button v-on:click="showOrHideBtnClick">显示/隐藏套餐</button>
            </div>
            </div>
        `
        
    }).mount("#app")
</script>
</html>
```



### 循环和数据双向绑定

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>佳丽列表</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id = "app"></div>
</body>
<script>
    Vue.createApp({ //创建一个Vue实例
        data(){
            return{
                list:[],
                inputValue:''
            }
        },
        methods:{
            handleAddItem(){
                this.list.push(this.inputValue)
                this.inputValue=''
            }
        },

        template:`
            <div>
                <input v-model="inputValue">
                <button v-on:click="handleAddItem">增加佳丽</button>
                <ul>
                    <li v-for= "(item,index) of list">[{{index}}]{{item}}</li>
                </ul>
            </div>
        `
    }).mount("#app")
</script>
</html>
```



### 组件化开发

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>佳丽列表</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id = "app"></div>
</body>
<script>
    const app = Vue.createApp({ //创建一个Vue实例
        data(){
            return{
                list:[],
                inputValue:''
            }
        },
        methods:{
            handleAddItem(){
                this.list.push(this.inputValue)
                this.inputValue=''
            }
        },

        template:`
            <div>
                <my-title />
                <input v-model="inputValue">
                <button v-on:click="handleAddItem">增加佳丽</button>
                <ul>
                    <my-jiali
                        v-for="(item,index) of list"
                        v-bind:item = "item"
                        v-bind:index = "index"
                    />
                </ul>
            </div>
        `
    })
    //静态组件
    app.component('my-title',{
        template:'<h1 style="text-align:center">象牙山洗脚城</h1>'
    })
    //动态组件
    app.component('my-jiali',{
        props:['index','item'],
        template:`<li>[{{index}}]-{{item}}</li>`
    })
    app.mount("#app")
</script>
</html>
```



<script> 标签内第一行 声明一个变量 “app”，声明过后就可以把 **mount** 部分独立出来了

```html
const app = Vue.createApp({ //创建一个Vue实例
	//...
app.mount("#app")
```

有了app变量，可以非常方便的自定义组件并使用了。比如写一个关于标题的静态组件

```html
//静态组件
app.component('my-title',{
template:'<h1 style="text-align:center">象牙山洗脚城</h1>'
})
```

将这个定义的组件 **'my-title'** 使用在app的模板部分，比如放在template的最上面，



![image-20230411161025161](vue.assets/image-20230411161025161.png)

页面效果如下：

![image-20230411160833046](vue.assets/image-20230411160833046.png)



#### 动态组件

所谓动态组件，就是指显示内容不固定，通过父组件或者程序控制而输出的内容



```html
//动态组件
app.component('my-jiali',{
props:['index','item'],
template:`<li>[{{index}}]-{{item}}</li>`
})
```

这个组件会绑定一些**props**，用于接受父组件传递过来的参数，然后动态显示出内容。

动态组件有一个关键的指令是v-bind，用这种方法，组件可以通过**props**取得对应的值

![image-20230411161407224](vue.assets/image-20230411161407224.png)



## 基础部分

### creatApp( ) & mount( )

```html
const app = Vue.createApp({ })
app.mount("#app")
```

Vue.createApp( ) , 创建一个Vue的应用



mount( )方法

mount( )方法就是挂载到某个html的DOM节点上，接受一个字符串型参数，参数可以使用CSS选择器，一般都是ID选择器的i形式，指定挂载的DOM元素



+ createApp( ) 基本参数详解

首先该方法接受一个对象形式的参数 **{ }**，这个对象告诉Vue应该如何展示最外层的组件。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id = "app"></div>
</body>
<script>
    const app = Vue.createApp({ 
        data(){
            return{
                message:'lk.com' //在这里定义了一个数据 Model
            }
        },
        template:"<h2>{{message}}</h2>"  //模板  View
        // 定义后，View自动关联，vm
    }) //创建一个Vue实例
    const vm = app.mount("#app")
    console.log(vm)  
</script>
</html>
```



当使用了createApp( )方法创建了一个Vue应用时，如何获取根组件？

实际上使用mount( )方法时，就会返回跟组件，可以声明一个变量来获取根组件，并打印出来，通过打印可以看出根组件是一个proxy形式的对象

```
const vm = app.mount("#app")
console.log(vm)
```

![image-20230411163510616](vue.assets/image-20230411163510616.png)

### mvvm设计模式

Vue的编程设计模式为MVVM的设计模式，

+ M: model 代表数据
+ V：View 视图，模板

+ VM： viewmodel视图数据连接层

![image-20230411163734802](vue.assets/image-20230411163734802.png)



model数据是我们自己定义的，view模板也是我们自己定义的，但是vm是Vue自动给我们关联的



### 生命周期函数

### <img src="vue.assets/生命周期函数.png" alt="生命周期函数" style="zoom:67%;" />



```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id = "app"></div>
</body>

<script>
    // 生命周期函数，在某一时刻会自动执行的函数
    const app = Vue.createApp({ 
        data(){
            return{
                message:'lk.com' 
            }
        },
        methods:{
            handleItemClick(){
                this.message = this.message == 'lk.com'?'里鸡':'lk.com'
            }
        },
        beforeCreate(){ //在实例声明前执行的函数
            console.log('beforeCreate')
        },
        created(){  //在实例生成之后会自动执行的函数
            console.log('created')
        },
        beforeMount(){ //在模板渲染完成之前执行
            console.log('beforeMount')
        },
        mounted(){  //在模板渲染完成之后
            console.log('mounted')
        },
        beforeUpdate(){ //当data中数据变化时，会立即自动执行的函数
            console.log('beforeUpdate')
            console.log(document.getElementById('app').innerHTML)
        },
        updated(){  //当data中数据变化时，页面重新渲染完成后，会立即自动执行的函数
            console.log('updated')
            console.log(document.getElementById('app').innerHTML)
        },
        beforeUnmount(){  //当Vue应用失效时，会自动执行的函数
            console.log('beforeUnmount')
            console.log(document.getElementById('app').innerHTML)
        },
        unmounted(){ //当Vue应用失效时，且DOM完全销毁之后，会自动执行的函数
            console.log('unmounted')
            console.log(document.getElementById('app').innerHTML)
        },

        template:"<h2 v-on:click='handleItemClick'>{{message}}</h2>"  
    }) //创建一个Vue实例
    const vm = app.mount("#app")
    console.log('vm')
</script>
</html>
```



测试效果

![image-20230411172355868](vue.assets/image-20230411172355868.png)



==beforeUpdate和updated生命周期函数==

这两个生命周期函数在Vue中data数据发生变化时，才会被执行，一个是在变化之前，一个是在变化之后。

为了能展示这个效果，写了一个数据变化的功能，每次点击文字都进行改变，在之前编写的`handleItemClick`方法中，改变 `message` 的值。使用了三元运算符：

```html
handleItemClick(){
                this.message = this.message == 'lk.com'?'里鸡':'lk.com'
            }
```





通过如下方式编写测试函数

```html
beforeUpdate(){ //当data中数据变化时，会立即自动执行的函数
            console.log('beforeUpdate')
            console.log(document.getElementById('app').innerHTML)
        },
        updated(){  //当data中数据变化时，页面重新渲染完成后，会立即自动执行的函数
            console.log('updated')
            console.log(document.getElementById('app').innerHTML)
        },
```

![image-20230411172849646](vue.assets/image-20230411172849646.png)

通过结果可以看出，在`beforeUpdate`时，DOM的内容并没有渲染更新，而到了`updated`中DOM内容已经进行了更新。



==beforeUnmount和unmounted生命周期函数==

这两个生命周期函数是在Vue销毁时自动执行的函数，一个是销毁前执行，一个是销毁后执行。

- beforeUnmount( ) :当Vue应用失效时，会自动执行的函数
- unmounted() : 当Vue应用失效时，且DOM完全销毁之后，会自动执行

我们可以先把这两个生命周期函数写在页面上，代码如下：

![image-20230411173233147](vue.assets/image-20230411173233147.png)

为了能够看到效果，需要在浏览器的控制台中输入销毁代码

![image-20230411173310194](vue.assets/image-20230411173310194.png)

在 `beforeUnmount`方法中还是有DOM内容的，然后到了 `unmounted`方法中，就已经没有DOM内容了





#### 总结

- beforeCreate( ) ：在实例生成之前会自动执行的函数
- created( ) : 在实例生成之后会自动执行的函数
- beforeMount( ) : 在模板渲染完成之前执行的函数
- mounted( ) : 在模板渲染完成之后执行的函数
- beforeUpdate ：当data中的数据变化时， 会立即自动执行的函数
- updated：当data中的数据发生变化，页面重新渲染完后，会自动执行的函数
- beforeUnmount( ) :当Vue应用失效时，会自动执行的函数
- unmounted() : 当Vue应用失效时，且DOM完全销毁之后，会自动执行

这些生命周期虽然多，你可以成对的去记忆，这样就有四个关键节点了：创建、渲染、更新、销毁。最主要的理解是他们是**自动执行的函数**



### 插值表达式

之前提到的字面量，其实正确叫法就是  插值表达式，

大部分还是叫字面量，就是我们经常看到的 {{xxxx}} 这样的东西

上个demo把生命周期相关内容删除，

留下的template属性中的 {{message}}就是插值表达式，意味着用这种形式，可以使用data中的变量展示在模板中

![image-20230411192014228](vue.assets/image-20230411192014228.png)

==插值表达式输出html标签==



**v-html**指令

如果我想在变量里编写一些html的标签，然后输出展现在页面中，如下

在message中加入 <i> 标签

![image-20230411192201112](vue.assets/image-20230411192201112.png)

其他什么都不做 直接输出，在浏览器中看到的就是

![image-20230411192432231](vue.assets/image-20230411192432231.png)



为了解决这一问题，需要使用`v-html` 标签解决，把template属性的部分改成

![image-20230411192609134](vue.assets/image-20230411192609134.png)

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id = "app"></div>
</body>

<script>
    const app = Vue.createApp({ 
        data(){
            return{
                message:'<i>lk.com<i>' 
            }
        },
        methods:{
            handleItemClick(){
                this.message = this.message == 'lk.com'?'里鸡':'lk.com'
            }
        },


        template:`<h2
                        v-on:click='handleItemClick'
                        v-html="message"
                        v-once
                ></h2>` 
    }) //创建一个Vue实例
    const vm = app.mount("#app")
    
</script>
</html>
```



预览效果

![image-20230411192632952](vue.assets/image-20230411192632952.png)



==v-once==标签 插值表达式 只作一次渲染



现在这种插值表达式，是跟着data中的数据一起变化的，也就是常说的数据双向绑定。如果我希望一个插值表达式，只有在第一次渲染取data中的值，而以后不再跟随data变化，这时候就要用到 `v-once`指令

```html
template: `<h2 v-on:click="handleItemClick" v-html="message"> </h2>`
```



这时，每点击一次h2标签， `message`的值都是变化的。再改一下代码

```html
template: `<h2 
                v-on:click="handleItemClick" 
                v-html="message"
                v-once
            > </h2>`
```

加入了 `v-once`后，无论data中的数据如何变化，模板也不会再次重新渲染了



==插值表达式中可以使用JS表达式==

最常用的表达式是三元运算符。比如，在data中新声明一个变量`count`，用三元运算符判断是否大于2

![image-20230411194549346](vue.assets/image-20230411194549346.png)



也可以使用代码下面一些简单的表达式

==v-bind==

如果给h2标签加入一个title属性，属性的值也想使用`message`。 代码如下

![image-20230411195004512](vue.assets/image-20230411195004512.png)

这时浏览器中鼠标放上时显示的是 `message`这个单词，并没有出现我们想要的结果，可以使用v-bind标签，如下

![image-20230411195319511](vue.assets/image-20230411195319511.png)

这时鼠标放在浏览器消息上，显示的就是data中message的值`lk.com`了



v-bind 简写方法，v-bind可以省去 只写一个冒号 `:` 

`v-on:`同样也有简写方法 ：只需用@替换即可

![image-20230411200141279](vue.assets/image-20230411200141279.png)

### 模板动态参数

现在绑定的事件 `click`和 `title`都是固定死的，Vue也提供了动态参数，叫做动态属性的功能。

比如上面的 `title` 是来自 `data`中的，可以这样写：

```html
const app = Vue.createApp({ 
        data(){
            return{
                message:'lk.com' ,
                name:'title'          
            }
        },
....
        template:`

                  <h2 

                  :[name] = "message"
                  @click = "handleItemClick"

                  >
                  {{message}}
                  </h2>                
        ` 
    }) //创建一个Vue实例
```



在`data`中，定义了一个name的变量，值是一个字符串，然后再绑定属性时，使用了 `[]`方括号加上data中变量名的形式。这时候绑定的属性就变得灵活了，这种形式就是模板动态参数，



如果要修改，如  `name:'title'`修改为 `name:'title1'`，网页端通过检查的范式，可以看到浏览器中也会跟随改变，形成动态效果



==事件动态绑定==

动态绑定也可以用到`v-on`事件绑定当中，比如在`data`中声明一个`event`的变量，然后给他一个 `click`，然后在模板中同样方法实现事件动态绑定

```html
const app = Vue.createApp({ 
        data(){
            return{
                message:'lk.com' ,
                name:'title',
                event:'click'
            }
        },
        methods:{
            handleItemClick(){
                alert('lk.com')
            },
            handleButton(){
                alert('lkkk')
            }
        },


        template:`

                  <h2 

                  :[name] = "message"
                  @[event] = "handleItemClick"

                  >
                  {{message}}
                  </h2>

        ` 
    }) //创建一个Vue实例
```



测试，浏览器中点击 `<h2>`标签时，也会弹出相应的alert效果。当改变data中event的值时，如将`event:'click'`修改为`event:'mouseenter'`，实现修改点击事件为鼠标滑动事件，触发相应的弹出效果



### 阻止默认事件

最常见的默认事件就是表单的默认提交事件，比如，写一个属性为`submit`的按钮，当点击按钮时，表单就会默认提交到对应的网址

```html
<form action="https://jspang.com">
    <button type="submit">默认提交</button>
</form>
```

打开浏览器，点击”默认提交“按钮，就会立即跳转到 https://jspang.com 页面上去，这就是==默认响应事件==。但在开发中经常需要阻止这种默认响应事件，比如：

```html
methods:{
    hanldeClick(){
        alert('lkkkk')
    },
    hanldeButton(e){
        e.preventDefault()
    }
},
//...
template:`
      //....
<form action="https://jspang.com" @click="hanldeButton">
    <button type="submit">默认提交</button>
</form>
`
```

这样写，引入一个阻止默认事件的方法，每次写就比较麻烦，Vue给提供了一个模板修饰符，直接可以阻止默认行为

```
<form action="https://jspang.com" @click.prevent="handleButton">
<button type="submit">submit</button>

</form>
```



### 模板中的条件判断

模板中使用条件判断，控制页面的样式，是最常见的应用。Vue提供了两种基本的方法，一种是之前用过的三元运算符，另一种就是 `v-if`

==三元运算符进行判断==

```html
<script>
    const app = Vue.createApp({ 
        data(){
            return{
                message:'lk.com' ,
                
            }
        },
        methods:{
            handleItemClick(){
                this.message = this.message == 'lk.com'?'里鸡':'lk.com'
            }
        },

//三元运算符形式进行判断
        template:`
                  <h2 :class="message == 'lk.com'?'one':'two'"
                  @click = "handleItemClick"
                  >
                    {{message}}
                  </h2>
        ` 
    }) //创建一个Vue实例
    const vm = app.mount("#app")
    
</script>
<style>
    .one{color: brown;}
    .two{color: chartreuse;}
    .three{color: coral;}
</style>
</html>
```

![image-20230411214235462](vue.assets/image-20230411214235462.png)

![image-20230411212103836](vue.assets/image-20230411212103836.png)



![image-20230411212113426](vue.assets/image-20230411212113426.png)





==v-if判断==

三元运算符的限制还是比较明显的，就是只能判断两个值，如果这时候再加入一个值，想要它显示橙色，这时三元运算符就满足不了需求了。

这里使用`v-if`判断



编写模板

```html
 template:`
<h2 @click = "handleItemClick" v-if= "message == 'lk.com'" class= "one">{{message}}</h2>
<h2 @click = "handleItemClick" v-if= "message == '里鸡'" class = "two">{{message}}</h2>
<h2 @click = "handleItemClick" v-if= "message == 'bilibili'" class = "three">{{message}}</h2>
        ` 
```

当然也可以使用v-else，如

```html
 template:`
<h2 @click = "handleItemClick" v-if= "message == 'lk.com'" class= "one">{{message}}</h2>
<h2 @click = "handleItemClick" v-else class = "two">{{message}}</h2>
        ` 
```



### 计算属性

计算属性的特性：**当计算属性依赖的内容发生变更时，才会重新执行计算。**

在data中声明两个变量： **price**和**count**

![image-20230411222021871](vue.assets/image-20230411222021871.png)

在template中打印两个变量乘积的结果

```html
template:` <h2> {{price * count}}</h2>`
```

打开浏览器显示结果 40 ，这种做法当然可以，但不够优雅，也没有语义化，如果想进行语义化，可能想到的第一个办法就是写一个getToal的方法



![image-20230411222222070](vue.assets/image-20230411222222070.png)

```html
template:` <h2> {{getTotal()}}</h2>`
```

此时，如果通过页面console改变页面的message值，即message值被重新渲染了，这个方法其实也会被重新执行（可以将getTotal方法返回一个时间戳，改变message，时间戳的值也会随之改变）





使用`comuputed`计算属性来传递值，起名叫**total( )**

![image-20230411222605817](vue.assets/image-20230411222605817.png)



修改`template`中 获取计算总价的参数

```html
template:` 
    <h2>{{message}}</h2>
    <h2> {{total}}</h2>
`
```

这时到浏览器中，手动修改 `message`的值，total的值就不会改变，使用时间戳进行测试也不会改变

以上可以得出总结：

1. **方法methods：只要页面重新渲染，就会重新执行方法**
2. **计算属性computed: 当计算属性依赖的内容发生变更时，才会重新执行计算**



==改变计算属性==

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id = "app"></div>
</body>

<script>
    const app = Vue.createApp({ 
        data(){
            return{
                message:'bilibili' ,
                price:20,
                count:2
        
                
            }
        },
        computed:{
            //计算属性的特性，当计算属性依赖的内容发生改变时，才会重新执行计算
            total(){
                return this.price * this.count
            }
        },
        methods:{
            handleItemClick(){
                this.message = this.message == 'lk.com'?'里鸡':'lk.com'
            },
            //只要页面重新渲染，就会重新执行方法
            getTotal(){
                return this.price * this.count
            },
            addCount(){
                this.count++
            }
        },

        template:`
            <h2>{{message}}</h2>
            <h2>总和：{{total}}</h2>
            <button @click="addCount">再买一个</button>


        ` 
    }) //创建一个Vue实例
    const vm = app.mount("#app")
    
</script>
<style>
    .one{color: brown;}
    .two{color: chartreuse;}
    .three{color: coral;}
</style>
</html>
```



点击**再买一个**按钮，执行addCount方法，增加count，总价增加，按理返回的值也会自动改变，测试显示是这样的



理解计算属性和普通methods方法的区别，明白区别后，做项目时可以清楚知道什么时候该用计算属性，什么时候用vue方法了



### 监听器-watch

可以监听data中的值的变化，做出响应的操作。和计算属性（computed）很像，但仍有一些区别



==监听器的基本写法==

```html
watch:{
    count(){
    	console.log('count changed')
    }
```

改监听器来监听`count`的数据变化，当`count`变化后立即在控制台打印出 `count changed`



监听器中的方法还可以接收两个参数，一个是现在的值，一个是变化前的值

```html
watch:{
    count(current,prev){
        console.log('watch changed')
        console.log('现在的值：',current)
        console.log('变化前的值：',prev)
    }
},
```

![image-20230411224445720](vue.assets/image-20230411224445720.png)

注意两个参数的先后顺序



==**侦听器和计算属性的区别**==

计算属性也是可以根据变化执行一些操作的，那二者有何区别

先给出结论，计算属性computed必须要返回一个值，而且在页面渲染的同时就会执行里边的业务逻辑，也就是会先执行一遍你写的业务逻辑，而`watch`只有发生变化时才会执行，也就是说值没有变化，它是不执行里边业务逻辑的。为了验证结果，先注释掉侦听器watch相关的内容，在计算属性`total`中写这样的代码。



```html
computed:{
    total(){
        console.log('....count changed')
        return this.price * this.count
    }
},
```

![image-20230411224821956](vue.assets/image-20230411224821956.png)

此时数据没发生变化，watch没有执行

数据发生变化后

![image-20230411224851474](vue.assets/image-20230411224851474.png)



**另外，计算数学更加简洁**

再来思考一个问题，用watch侦听器，可以写出类似计算属性的代码吗？答案是肯定的。现在我们就就写一个类似计算属性效果。

先在data中声明一个新的变量，叫做`newTotal`，给出一个`40`的值。

![image-20230411225023051](vue.assets/image-20230411225023051.png)

然后修改watch中代码，写一个乘法表达式算出`总和`，赋值给`this.newTotal`

![image-20230411225040117](vue.assets/image-20230411225040117.png)

最后把模板中的渲染值，改为`newTotal`就可以了

![image-20230411225057575](vue.assets/image-20230411225057575.png)

写完这些，你在浏览器中看到的效果和计算是属性是一样的。但是从代码简洁性上，显然侦听器的写法是麻烦并冗余，所以建议优先使用计算属性来完成同样的操作。



==method、watch和computed三者使用优先级==

如果三者都能实现相同的功能

- `computed` 和 `method`都能实现的功能，建议使用computed,因为有缓存，不用渲染页面就刷新。
- `computed` 和 `watch` 都能实现的功能，建议使用 computed，因为更加简洁。





### 模板样式绑定

先写三个基本样式，引入到模板

![image-20230412090440944](vue.assets/image-20230412090440944.png)

template传入 lk.com 字符串

可以通过简单的方式 ，直接将字体变色，（和普通的html方法一样）直接写class加上类名就可以了

![image-20230412090638809](vue.assets/image-20230412090638809.png)

如果希望程序足够灵活，样式也是可以控制的，这样引入样式的方法就不行了。需要在Data中声明变量，然后在模板 `template` 中进行绑定



声明data变量

![image-20230412090837435](vue.assets/image-20230412090837435.png)

分别是 普通声明，对象形式和数组形式，

通过绑定的方式，即可实现

![image-20230412091010149](vue.assets/image-20230412091010149.png)



可以在CSS样式中增加`!important`设置样式优先级

如下

![image-20230412091120975](vue.assets/image-20230412091120975.png)

![image-20230412091207361](vue.assets/image-20230412091207361.png)

字体并没有显示红色，而是绿色

![image-20230412091258861](vue.assets/image-20230412091258861.png)

修改 red 对应的优先级后

![image-20230412091314422](vue.assets/image-20230412091314422.png)



==子组件的样式绑定==

编写一个子组件 `SonCom`

```html
app.component('sonCom',{
        template:`
                <div>SonCom</div>
        `
    })
```

有了子组件后，就可以在父组件的模板中进行使用了，使用就是直接写一个类似html的标签进去就可以

![image-20230412092824367](vue.assets/image-20230412092824367.png)



**如何区分父子组件**

在Vue.createApp( )方法中使用对象形式 `{ }`配置的一般叫做父组件，而下面使用的其他组件，叫做子组件。也可以这么理解，主动调用的是父组件，被调用的是子组件



**子组件添加样式方法**

在调用子组件的地方加上 `class`

![image-20230412093037714](vue.assets/image-20230412093037714.png)

也可以在子组件处加上 `class`

![image-20230412093309776](vue.assets/image-20230412093309776.png)



子组件使用样式可能遇到的小坑

如果在子组件再添加一个`<div>`进去，

如果在调用子组件的地方修改样式，

![image-20230412093534486](vue.assets/image-20230412093534486.png)

会发现，样式不起作用了，

如果让它起作用，只有在两个并列的 `<div>`外层，再加上一个包括性的标签就可以了，也就是说让子组件最外层只有一个根元素

![image-20230412093700379](vue.assets/image-20230412093700379.png)



==行内样式的编写==

行内样式就是自己在模板的DOM元素上写CSS样式

```html
<h2 style="color:orange">lk.com</h2>
```

除了这种写法以外，Vue中也为我们扩展了一些内容，让行内样式的写法更直观和令狐。你可以直接在data中编写样式，比如在Data中这样写

![image-20230412093954917](vue.assets/image-20230412093954917.png)

然后用绑定行内样式的形式，在模板上进行绑定

```html
 <h2 :style="styleString">lk.com</h2>
```

也可以使用对象的形式在data中编写CSS样式，

![image-20230412094125131](vue.assets/image-20230412094125131.png)

然后再进行绑定



### v-show & v-if

之前学习了 `v-if` 和`三元运算符`，`v-show`和`v-if`是很类似的

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id = "app"></div>
</body>

<script>
    const app = Vue.createApp({ 
        data(){
            return{
                show:false
                }
           
        },
        template:`
            <h2 v-show="show">lk.com</h2>
            <h2 v-if="show">lk.com</h2>        
        ` 
    }) //创建一个Vue实例

    const vm = app.mount("#app")
    
</script>

</html>
```

数据中声明一个show的变量，可以在模板中使用 `v-show`来控制CSS样式，从而控制DOM元素是否显示

```html
<h2 v-show="show">lk.com</h2>
```

打开浏览器，可以看到 lk.com 这个DOM元素不见了，但是在element审查时，是可以看见DOM元素还在的

![image-20230412095013961](vue.assets/image-20230412095013961.png)

只是display了而已

但是 使用`v-if`后，

![image-20230412095042116](vue.assets/image-20230412095042116.png)

DOM元素直接没有了



==二者区别==

`v-if`**更加灵活**，可以增加多个判断，比如`v-else-iif`和`else`，而`v-show`**不具备这样的灵活性**。

`v-show`控制DOM元素显示，其实控制的是css样式，也就是`display:none`

```html
<h2 style="display:none;">lk.com</h2>
```

用`v-if`进行判断。再次在浏览器中预览，会发现整个DOM元素都不见了。

如何使用他们。这个就要看具体的需求了，如果显示和隐藏的状态切换比较频繁，并且没有什么多余复杂的业务逻辑，建议使用`v-show`,因为他不会一直渲染你的页面DOM元素，这或多或少对性能和稳定性有点提升。反之可以使用`v-if`。



### v-for

==v-for循环数组==

data中声明一个数组 `listArray`

```html
data(){
            return{
                listArray:['谢大脚','刘英','小红'],
                }           
        },
```

在`tmplate`中循环出这些数组

```HTML
<ul>
                <li
                    v-for="(item,index) in listArray"
                    :key="index + item"
                >
                    [{{index}}]{{item}}
                </li>
</ul>    
```

![image-20230412122950777](vue.assets/image-20230412122950777.png)

![image-20230412123024048](vue.assets/image-20230412123024048.png)

加入索引 index



==循环时的key值==

为了提高循环时性能，在数组其中一项变化后，整个数组不进行全部重新渲染，Vue提供了绑定key值的使用方法，目的就是增加渲染性能，避免重复渲染。

编写出一个按钮，然后每次点击按钮后向数组中增加`push`一个新值。

![image-20230412123116469](vue.assets/image-20230412123116469.png)

![image-20230412123126566](vue.assets/image-20230412123126566.png)

如果不写 `:key="index + item"` ，当点击按钮时，表面上看只增加了一个新的内容，实际整个列表都被渲染了。在实际工作中，这样的代码是不被允许的，它会降低页面的性能，在数据量变多的时候，用户用起来会变的卡顿。

这时，可以加唯一性`key`值，增加后vue就会辨认出哪些内容被渲染后并没有变化，而只渲染新变化的内容。

官方不建议使用索引`index`为key值，但此时又为了保持唯一性，所以这里使用了`index+item`进行绑定key值



==v-for循环对象==

在`data`中建立一个对象

![image-20230412123353863](vue.assets/image-20230412123353863.png)

在`template`中循环

```html
<ul>
                <li
                    v-for="(value,key,index) in listObject"
                    :key="key"
                >
                    [{{index}}]{{key}}:{{value}}
                </li>
            </ul>  
```

![image-20230412123445205](vue.assets/image-20230412123445205.png)



`v-for`是可以用来循环数字的，比如要循环1-99的数字

```html
 <span v-for="count in 99"> {{count}} |</span>
```

![image-20230412143408823](vue.assets/image-20230412143408823.png)



==v-for中如何使用判断==

如果不想展示谢大脚，只显示刘英和小红，可能会想到这样写

![image-20230412143527075](vue.assets/image-20230412143527075.png)

浏览器中浏览 `谢大脚`这一循环项并没有消失，因为`v-for` 的优先级要高于`v-if`，所以 `v-if` 判断失效

正确的写法应该是在 <li> 外层独立出一个标签，在 <li> 上做循环

![image-20230412143717568](vue.assets/image-20230412143717568.png)

![image-20230412143742490](vue.assets/image-20230412143742490.png)

谢大脚成功消失



==template标签的使用==

上面结果并不完美，打开控制台，看Elements选项卡时，会发现DOM结构有问题，明明只循环出两项，却有3个 `<div>` ,

![image-20230412143948285](vue.assets/image-20230412143948285.png)

而且这种外层套用 `<div>` 里边使用 `<li>`的形式，不符合HTML语法的基本结构



VUE给提供了 `tmplate`标签，就是一个空的占位符，目的就是解决模板中为完成业务逻辑，而使用无用的html标签的线性

![image-20230412144212828](vue.assets/image-20230412144212828.png)



![image-20230412144242251](vue.assets/image-20230412144242251.png)



### 绑定事件详解

#### 方法和参数

新建一个页面

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo19</title>
    <script src="https://unpkg.com/vue@next" ></script>
</head>
<body>
    <div id="app"></div>
</body>
<script>
    const app=Vue.createApp({ 
    data(){
        return{
            count:0
        }
    },
    methods:{},
    template:`
      <div>目前已点佳丽数量{{count}}.</div>
      <button>增加一位佳丽</button>
        ` 
    }) 
    const vm=app.mount("#app")

</script>

</html>
```

在method中写一个方法 `addCountClick()`

```html
methods:{
    addCountClick(){
        this.count++;
    },
},
```

然后在Button上绑定这个响应事件

![image-20230412152201043](vue.assets/image-20230412152201043.png)

实现效果，点击按钮，佳丽数量逐个增加



当然，也可以直接使用表达式实现

```html
<button @click="count++">增加一位佳丽</button>
```

如果要实现每次点击增加2个佳丽，就不能直接使用表达式实现，还是需要引入 method



==事件中的event对象==

在编写响应事件时，是可以接受一个event参数的，这个参数就是关于响应事件的一些内容，直接打印出event

![image-20230412152537083](vue.assets/image-20230412152537083.png)

可以在浏览器的控制台中看到，内容还是挺多的

![image-20230412152730931](vue.assets/image-20230412152730931.png)

![image-20230412152739652](vue.assets/image-20230412152739652.png)



可以通过 `event.target` 直观看到是哪个DOM元素触发事件

![image-20230412152851744](vue.assets/image-20230412152851744.png)

==单参数/多参数的传递==

比如实现每次点击增加两个

向addCountClick()传入一个num，每次点击实现 count+=num

![image-20230412153031194](vue.assets/image-20230412153031194.png)

![image-20230412153041269](vue.assets/image-20230412153041269.png)

有参数的情况下使用 `event`

![image-20230412153218172](vue.assets/image-20230412153218172.png)

![image-20230412153228492](vue.assets/image-20230412153228492.png)

这是传递 `event`需要加上 `$event`



**一个按钮调用两个方法**

![image-20230412153341250](vue.assets/image-20230412153341250.png)

![image-20230412153419945](vue.assets/image-20230412153419945.png)

这里需要注意的是，调用方法时候，要加上 `()`，方法之间 `,`隔开。如果不加调用时无效的

#### 事件修饰符

绑定事件中的修饰符有很多种，如`stop` `prevent` `capture` `self` `once` `passive`

==通过修饰符解决冒泡事件==

冒泡事件是最常处理的，先手动创造一个冒泡事件

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo20</title>
    <script src="https://unpkg.com/vue@next" ></script>
</head>
<body>
    <div id="app"></div>
</body>
<script>
    const app=Vue.createApp({ 
    data(){
        return{
            count:0
        }
    },
    methods:{
        addCountClick(){
            this.count++

        },
        handleBtnClick1(){
            alert(1)
        }

    },
    
    template:`
    <div @click.self="handleBtnClick1">
      <div>目前已点佳丽数量{{count}}.</div>
      <button @click="addCountClick()">增加一位佳丽</button>
    </div>
        ` 
    }) 
    const vm=app.mount("#app")

</script>

</html>
```

上面代码，

`method`中增加了一个冒泡方法

最外层增加了一个 `<div>` 并添加click事件

形成冒泡效果，就是有嵌套的DOM元素时，两个都有绑定事件，JS会自动向上传递事件

点击按钮或其他空白地方，都会跳出`alert(1)`

==stop==修饰符

在Vue中要停止冒泡是非常简单的，只要加加一个事件修饰符`stop`就可以了

![image-20230412155034994](vue.assets/image-20230412155034994.png)

点击按钮不再跳出 弹窗

==self==修饰符

使用`self`修饰符，意思是只有点击自己的时候才会被执行，加的时候要加在外层DOM元素的事件上

![image-20230412155206218](vue.assets/image-20230412155206218.png)

这时候会发现点击无论点哪里，都没办法触发`hanldeBtnClick1`方法了，这是因为目前最外层div下都是独立的DOM元素，就是都有成对标签出现，都不属于最外自己，都是他们的子元素。

可以编写一段专属最外层DIV的文字。

![image-20230412155304986](vue.assets/image-20230412155304986.png)

当点击 `我是最外层...文字`时，就会触发 `handleBtnClick1`方法了





==prevent==修饰符：阻止默然行为的修饰符，这个以前讲过，例如阻止`form`表单的默认提交行为。（不在重复介绍，如果你还没有掌握，可以复习以前课程）

==capture==修饰符：改成捕获模式，默认的模式都是冒泡模式，也就是从下到上，但是你用capture后，是从上到下的。

修改一下模板部分的代码，不在 使用修饰符，而是让事件存在冒泡。

![image-20230412155440209](vue.assets/image-20230412155440209.png)

==once==修饰符：事件只执行一次

![image-20230412155549280](vue.assets/image-20230412155549280.png)

点击按钮，事件只执行一次



==passive==修饰符：解决滚动时性能的修饰符

#### 按键、鼠标修饰符

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo21</title>
    <script src="https://unpkg.com/vue@next" ></script>
</head>
<body>
    <div id="app"></div>
</body>
<script>
    const app=Vue.createApp({ 
    data(){
        return{}
    },
    methods:{
    },
    template:`
        <div">
            <input />
        </div>
        ` 
    }) 
    const vm=app.mount("#app")

</script>

</html>
```

method 部分写一个方法 `handleKeyDown()`, 

![image-20230412160934854](vue.assets/image-20230412160934854.png)

在`template`中的 `<input />`中绑定键盘按下时响应 `keydown`

![image-20230412161058990](vue.assets/image-20230412161058990.png)

在页面按下键盘输入内容，控制台都会有输出日志 'keydown...'



==单个按键修饰符==：指定键盘上某个特殊的按键时才会响应事件方法

`enter`

![image-20230412161207192](vue.assets/image-20230412161207192.png)

实现了只有按下 `enter` 才会响应事件



还有其他的按键修饰符：`enter tab delete esc up down left right`

鼠标修饰符同按键修饰符一样，做一个简单测试

![image-20230412161359942](vue.assets/image-20230412161359942.png)

![image-20230412161430913](vue.assets/image-20230412161430913.png)

点击右键会响应事件



### 双向数据绑定

一个简单的双向绑定方式

```html
<script>
    const app=Vue.createApp({ 
    data(){
        return{
            name:''
        }
    },
    template:`
        <div>
            <div>{{name}}</div>
            <input v-model="name" />
        </div>
        ` 
    }) 
    const vm=app.mount("#app")
</script>
```

当`input`框改变时，对应的变量也会变化，页面中的值也会变化

==双向绑定：==data中的变量改变时，绑定的数据会跟随变化，这是一项修改；通过页面修改数据，data中的变量也会随之改变，这是另一项修改。两个彼此依存改变，九尾双向数据绑定



**textarea的数据双向绑定**

在vue中实现textarea的双向数据绑定，这时只要写单标签就可以了，剩下的事情Vue底层完成

![image-20230412163155595](vue.assets/image-20230412163155595.png)

![image-20230412163223101](vue.assets/image-20230412163223101.png)



**checkbox的数据双向绑定**

checkbox 是一个勾选框，

在data中新声明一个变量：checked：false

然后在`template`进行双向数据绑定

![image-20230412163428048](vue.assets/image-20230412163428048.png)

![image-20230412163453826](vue.assets/image-20230412163453826.png)

checkbox还有一个功能就是复选，可以选择多个

data中传入girls:[] 空数组

![image-20230412163549901](vue.assets/image-20230412163549901.png)

这样就实现了多选的双向数据绑定

![image-20230412163624286](vue.assets/image-20230412163624286.png)



**radio单选按钮 实现双向绑定**

data中传入新变量 `girl:''`

![image-20230412163735770](vue.assets/image-20230412163735770.png)

![image-20230412163745796](vue.assets/image-20230412163745796.png)



上面演示了复选框被选择时显示为`true`没选中显示`false`

现在的需求是，选中时显示`lk.com` 未选中时显示`李坤`

vue提供了 `true-value` 和 `false-value` 两个属性，在data中声明一个变量 `name`

![image-20230412165238439](vue.assets/image-20230412165238439.png)

![image-20230412165254451](vue.assets/image-20230412165254451.png)

浏览器中结果显示：

![image-20230412165320138](vue.assets/image-20230412165320138.png)

![image-20230412165335698](vue.assets/image-20230412165335698.png)



==v-model数据双向绑定修饰符==



`lazy number trim`

**lazy修饰符**

将data中一个变量和`template`中的 `<input />`双向绑定

![image-20230412165750570](vue.assets/image-20230412165750570.png)

![image-20230412165806062](vue.assets/image-20230412165806062.png)

当在文本框中输入任何内容时候，插值表达式会跟着变。如果不想马上显示，可以使用`lazy`修饰符，可以实现输入完成后，失去焦点再进行改变

输入时：

![image-20230412165929583](vue.assets/image-20230412165929583.png)

失去焦点后：

![image-20230412165939984](vue.assets/image-20230412165939984.png)

**number修饰符**

`<input />`输入的内容无论是数字还是字母，最终都会变为`字符串`。如果想最终输入的变成数字，你就可以使用`number`修饰符了。

比如我们现在去掉`lazy`修饰符，直接输入数字，这时候你修改插值表达式的结果，输出当前类型。

![image-20230412170027535](vue.assets/image-20230412170027535.png)

这时候你预览，就会发现最终input绑定的值会变成字符串类型。这是html的底层逻辑造成的，这时候我们可以使用`number`修饰付，解决这个问题。加上`number`修饰符后，**你输入的值只要是数字**，就变成了number类型。（也就是说，如果你输入的是字母，它还会是字符串类型）

![image-20230412170052763](vue.assets/image-20230412170052763.png)



**trim修饰符**

用来消除`input`框输入内容前后的空格





## 组件

![image-20230413143526021](vue.assets/image-20230413143526021.png)

Vue中的组件是页面的一部分，通过层层拼装，最终形成了一个完整组件。



### 根组件

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <script src="https://unpkg.com/vue@next"></script>
</head>
<body>
    <div id="app"></div>
</body>
</html>
```

用`createApp( )`创建Vue的实例，然后用`mount( )`方法挂载到`DOM`节点上

![image-20230413153336916](vue.assets/image-20230413153336916.png)



这里的 `Vue.createApp` 实际就是建立一个Vue实例，就是第一个 `根组件`，可以通过对象属性的形式来定义根组件的具体样式和放过发，比如在根组件上定义一个模板

```html
const app=Vue.createApp({
    template:`<h2>lk.com</h2>`
})
```

再加上一行字，

```html
const app=Vue.createApp({
    template:`
    	<h2>lk.com</h2>
    	<div>李坤</div>
    `
})
```

### 全局组件

页面由两串文字组成，即两部分，可以将这两部分拆分成两个全局的子组件

```html
<script>
    const app = Vue.createApp({
        template:`
            <website />
            <describe />

        `
        
    })

    app.component('website',{
        template:`<h2>lk.com</h2>`
    })
    app.component('describe',{
        template:`<div>李坤</div>`
    })

    const vm = app.mount("#app")
</script>
```

现在页面上元素，就被拆分了，一个根组件下面有两个子组件。这里我们并没有什么业务逻辑，所以看起来还没有太多的作用，但是如果一旦业务逻辑复杂，我们这样拆分，会降低开发难度。



#### 组件的可复用性

```html
<script>
    const app=Vue.createApp({

        template:
        `
            <website />
            <describe />
            <count />
                <count />
                <count />

        `
    })
    app.component('website',{
        template:`<h2>lk.com</h2>`
    })
    app.component('describe',{
        template:`<div>李坤</div>`
    })
    app.component('count',{
        data(){
            return{
                count:0
            }
        },
        template:`
            <div>{{count}} <button @click="count++">增加1</button></div>
        `
    })

    const vm=app.mount("#app")
</script>
```

![image-20230413154534766](vue.assets/image-20230413154534766.png)

![image-20230413154548205](vue.assets/image-20230413154548205.png)

浏览页面发现  `count` 组件的调用是互不干扰的，因此，Vue中的组件也就具有了复用性



#### 全局组件的弊端

全局组件编写起来确实非常方便，当时全局组件就是你一旦定义了，就会占用系统资源。它是一直存在的，你在任何地方都可以使用这个全局组件。这势必会对性能产生影响，比如一个真实的项目，会有上千个组件，这些组件由不同人编写，如果全部是全局组件，那这个应用打开速度一定是极慢的，而且流畅度也会受到影响



**只要定义了，处处可以使用，性能不高，使用起来简单**





### 局部组件

可以把局部组件看成一个变量，然后在使用的地方注册这个组件，才可以使用。局部组件的最大好处就是只有在使用的时候，才会耗费系统资源，不像全局组件一样，一直都存在

+ 创建一个局部组件

```html
    const counter = {
        data(){
            return{
                count:0
            }
        },
        template:`
            <div>{{count}} <button @click="count++">增加1</button></div>
        `
    }
```

理解成创建一个变量，最外层使用花括号，里面和使用 `vue.createApp` 时传递的参数是一样的

需要在`vue.createApp`方法里进行注册才能使用



+ 注册局部组件

直接用`components`属性声明就OK

![image-20230413161639713](vue.assets/image-20230413161639713.png)



有时候我们的组件名字会比较长，比如写一个`xieDaJiao`组件。

![image-20230413161850220](vue.assets/image-20230413161850220.png)

现在变量的名字有大小写，这时候在组测组件时，要使用这种形式（用`-`切割单词）。

![image-20230413161906852](vue.assets/image-20230413161906852.png)

产生这种问题是因为一个矛盾点，就是变量中不能使用`-`,而组件调用确实可以的。所以为了区分组件，在定义局部组件的时候，潜规则是首进行大写，然后使用驼峰命名法。





### 父子组件的静态和动态传值

```html
<script>
    const app = Vue.createApp({
        template:`
            <h2>lk.com</h2>
            <Son />
        
        `
        
    })

    app.component('Son',{
        template:`<div>Son</div>`
    })

    const vm= app.mount("#app")
</script>
```

声明一个全局组件，浏览显示正常，此时就已经形成了父子组件关系

#### 父组件向子组件传值（静态）

子组件中的`Son`是写死的，如果想动态的从父组件传递，可以使用属性方式，然后子组件使用props进行接受

比如，

在调用子组件的地方，通过属性`name`传递一个`李坤`的文字进去。

传递后 用`props`在子组件中进行接收，然后用插值表达式的形式打印出来

![image-20230413163128553](vue.assets/image-20230413163128553.png)

这样就实现了参数的接收和显示



#### 动态数据作为参数

动态参数传递首先要把传递参数放到Vue的数据项中，即`data`属性里

例如在`data`中声明一个name属性，然后赋值为`李坤`。这时候需要在`template`中绑定这个name属性。这样你的值就不是静态的了，而是动态值。

![image-20230413163839611](vue.assets/image-20230413163839611.png)



==ps==静态参数传递只能是字符串类型，而动态传参就可以是多种类型，甚至是一个函数/方法



`静态传参传“123”是String类型，动态传参“123”变成了数字类型`

==参数为函数时==

编写一个全局子组件

```html
app.component('XiaoJieJie',{
        props:['pay'],
        methods:{
            handleClick(){
                alert('请付钱...')
                this.pay()
            }
        },

        template:`
            <div @click="this.handleClick">和小姐姐 打招呼！</div>
        `
    })
```

父组件调用时候， `pay`是一个定义在data中的函数，然后用动态参数的形式调用



```html
const app = Vue.createApp({
        data(){
            return{
                name:'李坤',
                pay:()=>{
                    alert('给你500块')
                }
            }
        },
        template:`
            <h2>lk.com</h2>
            <Son :name="name"/>
            <xiao-jie-jie :pay="pay"/>
        
        `
        
    })
```



#### 组件传值的校验操作

不同于前端验证，组件中也需要基本的验证

##### 对类型的校验

传递数据项中的`123`

在传递的参数声明属性

```html
app.component('Son', {
        props: {
            name: String
        },
        template: `<div>{{name}} div </div>`
    })
```

可以通过打开控制台 `console`就可以看到提示，即使传递类型不是Strin，也会正常显示，`console`中提示warning，这种报错不会阻断程序

这时把数据项中`123`修改为字符串，程序就不会报错了

Vue支持的校验类型包括:**String、Boolean、Array、Object、Function和Symbol**



##### 必填校验和默认值

`required`实现校验

```html
app.component('Son', {
        props: {
            name: {
                type: String,
                required: true
            }
        },
        template: `<div>{{name}} div </div>`
    })
```

校验规则就是，name的值必须是字符串，并且不可以省略。这时候可以去掉父组件调用时传递的参数，在浏览器中打开控制台看一下警告信息。

`default默认值`

```html
app.component('Son', {
        props: {
            name: {
                type: String,
                default: 'likun'
            }
        },
        template: `<div>{{name}} div </div>`
    })
```

在调用组件时，如果不传递参数，则默认值为`likun`。

##### 精准校验

`validator`

进行精准校验。比如现在要求传递的字符串中必须包括`li`这几个字符，就可以用`validator`来进行校验。它是一个函数，并接受一个`value`值，这个value就是传递过来的值。

```
app.component('Son', {
    props: {
        name: {
            type: String,
            validator: function (value) {
                console.log(value.search("JSPang"))
                return value.search("li") != -1
            },
            default: 'likun'
        }
    },
    template: `<div>{{name}} div </div>`
})
```

因为使用`search`来验证，返回来的是字符串出现的位置，没有找到时才显示`-1`。所以这里判定如果不为`-1`就是通过验证。

当没有通过验证时，就是在控制台给出警告。



#### 单项数据流机制

保证组件独立性



==单向数据流==：所有的prop都使得其父子prop之间形成了一个单向下行绑定：父级prop的更新会向下流动到子组件中，但是反过来则不行

简单的说：**数据从父级组件传递给子组件，只能单向绑定。子组件内部不能直接修改从父组件传递过来的数据**



```html
<script>
    const app = Vue.createApp({
        data() {
            return {
                counter:0

            }
        },
        template: `
            <h2>lk.com</h2>
            <counter :counter="counter"/>
        `
    })
    app.component(`Counter`,{
        props:['counter'],
        template:`
            {{counter}}<button @click="counter+=1">增加数量</button>
        `
    })

    const vm = app.mount("#app")
</script>
```

编写了一个全局组件，接受一个参数“counter”

在浏览器中预览的时候，你会发现点击按钮根本不起作用。这就是单向数据流机制限制的结果



如何修改这个程序，让其好用那，方法很简单，在组件内的数据项中声明一个变量，把父组件传递过来的变量赋值给内部变量，然后就可以随意修改了

```html
app.component('Counter', {
    props: ['counter'],
    data() {
        return {
            newCounter: this.counter
        }
    },
    template: `
        {{newCounter}}<button @click="this.newCounter+=1">增加数量</button>
    `
})
```

**单向数据流就是父组件可以向子组件传递数据，但是子组件不能修改数据。**



单项数据流的最终目的，就是为了降低组件的耦合度和独立性。比如现在页面上同时调用了三个`<counter/>`组件，没有单项数据流的机制，很容易变成一个组件数值变化，其他组件的数值也跟着变化的现象。让页面组件的数据耦合在一起，没办法独立使用。

```
template: `
    <h2>lk.com</h2>
    <counter :counter="counter"/>
    <counter :counter="counter"/>
    <counter :counter="counter"/>
`
```



#### Non-props

`Non-props`属性，其实就是子组件没有接受父组件传递过来的参数，而子组件完全不变的复制了属性到自己的标签上，就叫做`Non-props`属性

```html
<script>
    const app = Vue.createApp({
        template: `
            <h2>lk.com/h2>
            <Hello />
            
        `
    })
    app.component(`Hello`,{
        template:`<h3>Hello World</h3>`
    })
    const vm = app.mount("#app")
</script>
```

上段代码，没有在子组件里接受任何传递过来的参数，就根本没有写`props`,但这时候在调用的时候，是仍然可以传值的。

```html
const app = Vue.createApp({
    template: `
    <h2>lk.com</h2>
    <hello msg="lkun" />
`
})
```

打开浏览器中的控制台，查看`Elements`标签，可以看到此时的`<h3>`标签上已经由了`msg=lkun`这样的属性，也就是父组件直接把属性移植给了子属性。

![image-20230418112403336](vue.assets/image-20230418112403336.png)

如果要消除 这种移植，或者是复制，可以在子组件里接受这个属性，但并不使用他。

```html
app.component('Hello', {
     props: ['msg'],
     template: `<h3>Hello World</h3>`
 })
```

![image-20230418112532541](vue.assets/image-20230418112532541.png)

这时候在打开浏览器的`Elements`标签查看，就没有多余的属性了。



`Non-prop`属性，它就是父组件向子组件传递参数的时候，子组件不写任何的接受方法。这个时候父组件就会直接把属性完全复制给子组件，子组件也是可以得到属性值的。

------

最常见的使用案例就是直接在标签上写CSS样式。



```html
const app = Vue.createApp({
    template: `
        <h2>JSPang.com</h2>
        <hello style="color:red;" />
    `
})
```

子组件会直接得到这个属性，也就把字体变成了红色。



##### inheritAttrs 属性

有些时候我们就是不想接受参数，也不想让`Non-props`属性起作用，这时候可以在子组件上使用`inheritAttrs`属性来解决这个问题。

```html
app.component('Hello', {
    inheritAttrs: false,
    template: `<h3>Hello World</h3>`
})
```

这时候style标签就不会再被复制到子组件上了，组件上的`Hello World`也不会变成红色了。

##### non-prop 多节点失效解决方法

组件在没有接受参数时，会把属性自动复制到组件的根节点上，如果组件不是一个根节点，比如写成下面的样子。

```html
app.component('Hello', {
    template: `
        <h3>Hello World</h3>
        <h3>Hello World</h3>
        <h3>Hello World</h3>
    `
})
```

这时候复制就会失效。你当然可以给他们增加一个根节点，但是在不增加根节点的条件下，也是有办法解决的。比如现在我们想让第一个组件中的`<h3>`标签复制父组件传递过来的属性，就可以写成下面的样子。

```html
    app.component(`Hello`,{
        
        template:`
            <h3 v-bind="$attrs">Hello World</h3>
            <h3>Hello World</h3>
            <h3>Hello World</h3>
        `
    })
```

测试的`$attrs`不是单指某一个属性，而是指全部属性。当然这里只有一个属性，所以只复制了一个，比如你再写一个属性，它也是可以复制过来的。

```html
const app = Vue.createApp({
    template: `
    <h2>JSPang.com</h2>
    <hello style="color:red;" msg="jspang" />
`
})
```

打开浏览器，会看到两个属性都复制到了第一个`<h3>`标签上。

![image-20230418161843549](vue.assets/image-20230418161843549.png)

这点需要注意一下，`v-bind="$attrs"`的意思是把父组件传递的所有参数属性都复制到子组件当中。

如果想只复制一个属性，比如现在我们只复制一个属性`style`，就这么写。

```html
app.component('Hello', {
    template: `
        <h3 v-bind="$attrs">Hello World</h3>
        <h3 v-bind:style="$attrs.style">Hello World</h3>
        <h3>Hello World</h3>
    `
})
```

第二个`<h3>`标签就只复制了`style`属性。当然你也可以简写，去掉`v-bind`，而是用`:`代表



![image-20230418162352129](vue.assets/image-20230418162352129.png)

##### 在业务逻辑中使用Non-props属性

如果想在业务逻辑中使用`Non-props`属性也是可以的。比如在生命周期中使用。

```html
app.component('Hello', {
    mounted() {
        console.log(this.$attrs.msg)
    },
    template: `
    <h3 v-bind="$attrs">Hello World</h3>
    <h3 v-bind:style="$attrs.style">Hello World</h3>
    <h3>Hello World</h3>
    `
})
```

到浏览器中的控制台进行查看，就可以看到打印出了`lkun`字样。其实`this.$attrs`是Vue的一个常用属性，需要善于利用。



#### 组件中通过事件进行通信



```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo07</title>
    <script src="https://cdn.bootcdn.net/ajax/libs/vue/3.0.2/vue.global.js"></script>
</head>

<body>
    <div id="app"></div>
</body>
<script>
    const app = Vue.createApp({
        data() {
            return {
                counter: 0
            }
        },
        template: `
                    <h2>JSPang.com</h2>
                    <counter :counter="counter"/>  
             `
    })
    app.component('Counter', {
        props: ['counter'],
        template: `
        {{counter}}<button @click="this.counter+=1">增加数量</button>
    `
    })

    const vm = app.mount("#app")
</script>

</html>
```

上面的代码，当我们在浏览器中点击增加时，是不能增加`counter`的值的，这就是Vue`单向数据流`的限制。但是有时候，我们就是想在子组件里改变父组件传递过来的值，怎么办？



##### 子组件调用父组件事件

这时候就需要子组件调用父组件的事件，从而改变父组件里的值。我们先在父组件里编写一个方法，叫做`handleAddCounter`。这个方法就作一件事，每执行一次，数据项里的`counter`加一。

```html
methods: {
    handleAddCounter() {
        this.counter += 1
    }
},
```

父组件有了这个方法，就可以改变`couter`数据行的值了，有方法后，现在问题就变成了，如何在子组件中调用这个方法了。



这时候可以先在`子组件`的模板`template`中编写一个`click`事件。

![image-20230418164003887](vue.assets/image-20230418164003887.png)

子组件调用的并不是父组件中的方法，而是子组件中的方法。如果想调用父组件中的`handleAddConter`方法，这时候可以在子组件中新建一个方法`handleClick`，然后用`$emit`调用父组件的响应事件`add`。具体代码如下.

```html
app.component('Counter', {
    props: ['counter'],
    emits: ['add'],
    methods: {
        handleClick() {
            this.$emit('add')
        }
    },
    template: `
    {{counter}}<button @click="handleClick">增加数量</button>
`
})
```



这时候的`add`是什么？`add`就是响应事件，在父组件的模板`template`中，添加一个`add`响应事件，然后响应事件再调用方法`handleAdCounter`。



父组件的模板：

```html
template: `
                    <h2>lk.com</h2>
                    <counter :counter="counter" @add="handleAddCounter" />  
             `
```



整段代码

```html
<script>
    const app = Vue.createApp({

        data() {
            return {
                counter: 0
            }
        },
        methods:{
            handleAddCounter(){
                this.counter += 1
            }
        },
        template: `
                    <h2>lk.com</h2>
                    <counter :counter="counter" @add="handleAddCounter" />  
             `
    })
    app.component('Counter', {
        props: ['counter'],
        emits:['add'],
        methods:{
            handleClick(){
                this.$emit('add')
            }
        },
        template: `
        {{counter}}<button @click="handleClick">增加数量</button>
    `
    })

    const vm = app.mount("#app")
</script>
```





##### 子组件向父组件传递参数

当我们不是每次想加1的时候，比如这个值是`子组件`决定的，比如是`2`吧。这时候子组件需要向父组件传值，也是可以做到的。你可以在子组件中这样编写。

```html
methods: {
    handleClick() {
        this.$emit('add', 2)
    }
},
```

在父组件中接受这个参数`param` (这个参数的名字你可以随便起)，为了看的方便，在控制台进行打印。

```html
methods: {
    handleAddCounter(param) {
        console.log(param)
        this.counter += param
    }
},
```

这时候子组件的参数就传递给了父组件，并且可以使用了。当然你还有**更好的选择**，就是把所有业务逻辑都放在子组件中，然后把结果传递给父组件。比如代码可以写成下面的样子。 业务逻辑写在子组件里

```html
methods: {
    handleClick() {
        this.$emit('add', this.counter + 3)
    }
},
```

父组件直接接受结果

```html
methods: {
    handleAddCounter(param) {
        console.log(param)
        this.counter = param
    }
},
```

##### 对传递值得校验

在子组件向父组件传递值的时候，还可以开启校验功能。校验是通过`emits`这个选项来声明的。比如现在我们要求传递到add中的值，不大于20。如果大于20就进行警告。

```html
emits: {
    add: (value) => {
        return value < 20 ? true : false
    }
},
```



#### 组件中插槽的使用Slot

插槽的声明很简单，只要在子组件中加入`<slot></slot>`标签即可，然后在父组件中使用双标签进行调用

```html
<script>
    const app = Vue.createApp({
        template: `
        <h2>欢迎光临红浪漫-请选择您的技师</h2>
        <ji-shi > 谢大脚 </ji-shi>
        `
    })

    app.component('JiShi', {
        template: `
        <div>
            <span>经过你的慎重考虑.最终选择了。</span>
            <span>
                <slot> </slot>

            </span>
        </div>
    `
    })

    const vm = app.mount("#app")
</script>
```

这时候去浏览器可以看到，页面出现了我们想要的结果。你可以让页面更丰富，因为插槽支持任何的DOM元素，比如我们加入一个`<div>`然后让字体变成红色和50像素的字体大小。

![image-20230418170638597](vue.assets/image-20230418170638597.png)

现在调用两次`<ji-shi>`组件，给与不同的样式也是可以的。

![image-20230418170704021](vue.assets/image-20230418170704021.png)

##### 插槽中使用子组件

插槽可以强大到直接使用`子组件`，接下来就作一个在插槽中使用子组件的小例子。可以先声明一个最简单的子组件。这个子组件叫做`project`

```html
app.component('project', {
        template: `<span style="color:blue;">项目是胖哥老三样</span>`
    })
```

有了组件后直接可以在父组件的插槽中进行使用，代码如下

```html
        <ji-shi > 
                <div style="color:red;font-size:50px;">
                    谢大脚，<project />
                </div>
        </ji-shi>
```





##### 插槽中使用动态数据

插槽中也可以直接使用动态数据，也就是我们常说的数据项，比如定义一个数据项,然后在插槽中使用，直接就可以使用了。

```html
const app = Vue.createApp({
    data() {
        return {
            jishi: '晓红'
        }
    },
    template: `
        <h2>欢迎光临红浪漫-请选择您的技师</h2>
        <ji-shi > 
                <div style="color:red;font-size:50px;">
                    {{jishi}},<project />
                </div>
        </ji-shi>
        <ji-shi > <div style="color:green;font-size:50px;">刘英</div> </ji-shi>
    `
})
```

这时候需要注意的是一个变量作用域的问题，比如我们子组件里也有一个数据项`jishi`，然后给他赋值为`谢大脚`。

```html
app.component('JiShi', {
    data() {
        return {
            jishi: '谢大脚'
        }
    },
    template: `
    <div>
        <span>经过你的慎重考虑.最终选择了。</span>
        <span>
            <slot> </slot>

        </span>
    </div>
`
})
```

会发现，浏览器中仍然显示的是`晓红`，这时候我们得出了一个结论，也是方便你记忆。

+ 父模板里调用的数据属性，使用的都是父模板里的数据
+ 子模版里调用的数据属性，使用的都是子模版里 的数据



##### 默认插槽的使用

编写一个全局的组件 `JiShi`

```html
app.component('JiShi',{
        template:`
            <div>
                你选择了<slot></slot>为你服务。
            </div>
        `
    })	
```

有了插槽后就可以在使用组件的时候直接传递值了。

![image-20230418172057418](vue.assets/image-20230418172057418.png)

现在来了一位新客人，第一次来，不好意思点技师，那我们就需要给他一个默认值，比如默认值是“晓红”。默认值的关键语法就是在`<slot>`插槽中直接输入值就可以了。

![image-20230418172112695](vue.assets/image-20230418172112695.png)

这种编写方法，在有值传递过来的时候，会显示正常的值，没有值的时候就会显示默认值"晓红"。

![image-20230418172126698](vue.assets/image-20230418172126698.png)



访问结果：

![image-20230418172142857](vue.assets/image-20230418172142857.png)



##### 具名插槽的使用

来看一个需求，就是如果你去洗脚城，需要经历三个过程：给顾客安排位置、选择技师、选择项目。

这是一个过程，是有先后顺序的，包括在页面上的显示也是要有顺序的。于是我们写了一个组件。组件代码如下。

```html
app.component('HongLangMan',{
        template:`
            <div>
                 <div>1.男宾一位，请上二楼。</div>
                 <div>2.你选择了大脚为你服务</div>
                 <div>3.你点了198元泰式按摩</div>
            </div>
        `
    })
```

程序编写的需求是这样的，选择谁为你服务不变，也就是第二个div中的内容不变。但是第一句和第三句要能在父组件里使用插槽的方法进行定义。你这时会发现程序有问题了，要把`<slot>`放在哪里？好像放在什么地方都不太合适，我们索性放两个`<slot>`，一个放在上面，一个放在下面，测试一下。

```html
app.component('HongLangMan',{
    template:`
        <div>
                <slot></slot>
                <div>2.你选择了大脚为你服务</div>
                <slot></slot>
        </div>
    `
})
```

在父组件调用的时候传递对应的值，比如把代码写成下面的样子。

```html
const app = Vue.createApp({
    template: ` 
        <h2>欢迎光临红浪漫-请选择您的技师</h2>
        <hong-lang-man>
            <div>1.女宾一位，请上三楼。</div>
            <div>3.顾客选择了全身SPA。</div>
        </hong-lang-man>
    `
})
```

打开浏览器，会发现插槽的位置出现了两次重复的内容。也表示我们第一次的尝试失败了。

Vue中已经提供了具名插槽的使用方法，就是给`<slot>`标签加上一个name属性，你可以把子组件写成下面的样子。

```html
app.component('HongLangMan',{
    template:`
        <div>
                <slot name="one"></slot>
                <div>2.你选择了大脚为你服务</div>
                <slot name="two"></slot>
        </div>
    `
})
```

父组件可以用下面的方式进行调用。

```html
const app = Vue.createApp({
    template: ` 
        <h2>欢迎光临红浪漫-请选择您的技师</h2>
        <hong-lang-man>
            <template v-slot:one><div>1.女宾一位，请上三楼。</div></template>
            <template v-slot:two><div>3.顾客选择了全身SPA。</div></template>
        </hong-lang-man>
    `
})
```

现在就可以在一个组件里，分别定义两个插槽了。



```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo09</title>
    <script src="https://cdn.bootcdn.net/ajax/libs/vue/3.0.2/vue.global.js"></script>
</head>

<body>
    <div id="app"></div>
</body>
<script>
    const app = Vue.createApp({
        template: ` 
            <h2>欢迎光临红浪漫-请选择您的技师</h2>
            <hong-lang-man>
            <template v-slot:one><div>1.女宾一位，请上三楼。</div></template>
            <template v-slot:two><div>3.顾客选择了全身SPA。</div></template>
            </hong-lang-man>
        `
    })
    app.component('HongLangMan',{
    template:`
        <div>
                <slot name="one"></slot>
                <div>2.你选择了大脚为你服务</div>
                <slot name="two"></slot>
        </div>
    `
})
    const vm = app.mount("#app")
</script>
```





##### 具名插槽简写和作用域插槽



在父模板中确定插槽位置时，使用了`v-slot:one`这种方法，其实这个语法可以简写成`#one`。这时候的代码就变成了下面的样子。

```html
const app = Vue.createApp({
    template: ` 
    <h2>欢迎光临红浪漫-请选择您的技师</h2>
    <hong-lang-man>
        <template v-slot:one><div>1.女宾一位，请上三楼。</div></template>
        <template v-slot:two><div>3.顾客选择了全身SPA。</div></template>
    </hong-lang-man>
`
})
```



**作用域插槽**

```html
<script>
    const app = Vue.createApp({
        template: `  
            <h2>欢迎光临红浪漫-请选择您的技师</h2>
            <list />
        `
    })
    app.component('List', {
        data() {
            return {
                list: ['大脚', '刘英', '晓红']
            }
        },
        template: `
            <div>
                <div v-for="item in list">{{item}}</div>    
            </div>
        `
    })

    const vm = app.mount("#app")
</script>
```

编写了一个`list`子组件，然后在list组件里，声明一个list的数据，`v-for`形式循环遍历出来

目前子组件里循环使用的是`<div>`标签，现在要求这个标签是父组件调用时确定，也就是要使用插槽了。



先改造子组件，增加`slot`插槽，增加插槽后的模板代码如下。

![image-20230418193532101](vue.assets/image-20230418193532101.png)

然后在父组件里进行调用，调用方法如下。

![image-20230418193545624](vue.assets/image-20230418193545624.png)



浏览器中查看，打开控制台，可以看到DOM中，是有三个`<span>`标签的。说明`DOM`通过插槽的形式，传递过来了。那接下来的问题，就是父组件如何使用子组件中的变量。

父组件想使用子组件插槽中的值，可以使用`:`绑定的形式进行传递，比如写成`:item="item"`，具体的代码可以写成下面的样子。

![image-20230418193609953](vue.assets/image-20230418193609953.png)

这时候你会发现列表是可以正常显示的，也可以进行更换标签了，可以试着把`<span>`标签换成`<div>`标签来尝试一下

注意这里的`props`是子组件传递过来的数据都是对象，所以我们要加上`.item`才能使用。可以把代码修改一下。

![image-20230418193646036](vue.assets/image-20230418193646036.png)

![image-20230418193710440](vue.assets/image-20230418193710440.png)

==作用域插槽简化写法==

通过解构的形式，是ES6的一种写法，可以去另外学一下ES6关于解构的语法知识



![image-20230418194030084](vue.assets/image-20230418194030084.png)





#### 动态组件和状态保存

```html
<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Demo11</title>
    <script src="https://cdn.bootcdn.net/ajax/libs/vue/3.0.2/vue.global.js"></script>
</head>

<body>
    <div id="app"></div>
</body>
<script>
    const app = Vue.createApp({
        template: ` 
            <h2>欢迎光临红浪漫-请选择您的技师</h2> 
        `
    })

    const vm = app.mount("#app")
</script>
```

编写两个组件，引入两张图片

```html
app.component('dajiao',{
    template:`<img src="https://newimg.jspang.com/xiedajiao01.jpg" />`
})

app.component('liuying',{
    template:`<img src="https://newimg.jspang.com/liuying01.jpg" />`
})
```

父组件中直接使用这两个组件

```html
const app = Vue.createApp({
    template: ` 
        <h2>欢迎光临红浪漫-请选择您的技师</h2> 
        <dajiao />
        <liuying />
    `
})
```

现在的需求是如果显示其中一个组件，另一个组件就不显示。这里我最先想到的是用`v-show`这种代码来实现。

先来定义一个数据项，用来控制显示那个组件，数据项叫做`showItem`，然后在两个子组件的位置增加v-show属性，控制最终的显示。

```html
const app = Vue.createApp({
    data(){
        return {showItem:'dajiao'}
    },
    template: ` 
        <h2>欢迎光临红浪漫-请选择您的技师</h2> 
        <dajiao  v-show="showItem==='dajiao'" />
        <liuying v-show="showItem==='liuying'" />
    `
})
```

时候的`showItem`值是`dajiao`，所以浏览器中应该只显示`dajiao`的组件

再编写一个按钮，用来切换两个组件，按钮需要绑定一个方法`handleClick`,方法中使用了三元运算符来编写这部分内容



```html
methods:{
    handleClick(){
        this.showItem= this.showItem=='dajiao'?'liuying':'dajiao'
    }
},
```

![image-20230418195337056](vue.assets/image-20230418195337056.png)





##### 动态组件优化代码

使用`动态组件`的编程方式，就可以省略`v-show`部分的代码，也可以让代码看起来更加的优雅。

```html
<component :is="showItem" />
```

有了上面这段简短的代码，就可以删除掉下面这两句代码了。

```html
<dajiao  v-show="showItem==='dajiao'" />
<liuying v-show="showItem==='liuying'" />
```

```html
<script>
    const app = Vue.createApp({
        data(){
            return {showItem:'dajiao'}
        },
        methods:{
            handleClick(){
                this.showItem = this.showItem=='dajiao'?'liuying':'dajiao'
            }
        },
        template: ` 
            <h2>欢迎光临红浪漫-请选择您的技师</h2> 
            <component :is="showItem" />
            <button @click="handleClick">切换佳丽</button>
        `
    })
    app.component('dajiao',{
        template:`<img src="https://newimg.jspang.com/xiedajiao01.jpg">`
    })
    app.component('liuying',{
        template:`<img src="https://newimg.jspang.com/liuying01.jpg">`
    })
    const vm = app.mount("#app")
</script>
```



##### 动态组件中的状态保存

动态组件用起来非常方便，现在修改一下`dajiao`组件，把照片变成一个`input`框。

到浏览器中查看，并在输入框中输入文字，在切换组件后。你会发现`input`框中的文字是无法保存的。

为了保存`input`框中的文字，可以使用`<keep-alive>`标签，把动态组件包裹起来。

![image-20230418195946015](vue.assets/image-20230418195946015.png)

这时候就相当于启用了缓存，使用动态组件时，经常配合 `<keep-alive>` 标签一起使用



#### 异步组件和Promise详解

之前做的都是同步组件

**异步组件就是在调用组件时，这个组件并不立即渲染，而是要等带一些业务逻辑完成后，才会进行执行组件内的逻辑和渲染到页面上。**



```html
app.component('async-component',Vue.defineAsyncComponent(()=>{
    return new Promise((resolve,reject)=>{
        setTimeout(()=>{
            resolve({
                template:`<div>这是一个异步组件</div>`
            })
        },3000)
    })

}))
```

这段代码中，新建了一个组件叫做`async-component`，然后用`defineAsyncComponent()`声明这是一个异步组件，在组件内部我们用`Promise`来完成逻辑。逻辑非常简单，用`setTimeout`控制3秒后渲染模板`template`，展示内容。也就是说3秒后，组件才知道最终展示的内容是什么。这就是一个典型的异步组件。

异步组件经常在去后台请求数据的时候进行使用，也可以把一个大项目拆分成很多小的异步组件，然后根据需要，异步加载这些小项目。





#### provide 和 inject多级组件传值

需求是，要写一个子组件，然后子组件里调用另一个子组件（也可以想象成孙子组件），然后从最上层的父组件里传递值给子组件。



```html
<script>
    const app = Vue.createApp({
        data(){
            return {house:'北京别墅一套'}
        },
        template: `<div>我有一套房子，我先传给我的儿子</div> `
    })

    app.component('child',{
        template:`
            <div>我是子组件，我要把房子再传给我儿子。</div>
        `
    })

    app.component('child-child',{
        template:`
            <div>我是孙子，等待接收房子</div>
        `
    })
    const vm = app.mount("#app")
</script>
```



##### 常用传递方式

现在的需求就是一层层传递下去，我们可以使用`props`的形式进行接收，然后继续传递，代码可以可成这样。

```html
<script>
    const app = Vue.createApp({
        data(){
            return {house:'北京别墅一套'}
        },
        template: `
            <div>我有一套房子，我先传给我的儿子</div>
            <child :house="house" />
         `
    })

    app.component('child',{
        props:['house'],
        template:`
            <div>我是子组件，我要把房子再传给我儿子。</div>
            <div>儿子接收{{house}}</div>
            <child-child :house="house" />
        `
    })

    app.component('child-child',{
        props:['house'],
        template:`
            <div>我是孙子，等待接收房子</div>
            <div>孙子接收{{house}}</div>
        `
    })
    const vm = app.mount("#app")
</script>
```

这时候到浏览器中查看一下结果，可以发现结果是可以成功的。每次用props接收，然后再用绑定属性的方式传递给下一层。



现在需求变化了，富豪北京三环内还有一套200平方的房子，**不想通过儿子的手，直接传递给孙子**，那如何操作那？

##### 多级组件传值provide和inject

可以使用使用provide传递和inject接收了，先在数据项的下面声明一个`provide`。

![image-20230418202343290](vue.assets/image-20230418202343290.png)

儿子组件不用作任何更改，直接在孙子组件里用`inject`接收就可以了。

![image-20230418202357286](vue.assets/image-20230418202357286.png)
