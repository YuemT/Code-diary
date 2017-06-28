## Vue
## 一.Vue是什么?
![](./vue的特点.png)
* 一位华裔前Google工程师开发的前端js库
* 一个MVVM框架
    ![](./mvvm.png)
* 核心概念
    * 数据绑定
    * 组件
    * 虚拟DOM
* 借鉴 angular 的模板和数据绑定技术
* 借鉴 react 的组件化和虚拟 DOM 技术
* 体积小，运行效率高，编码简洁，PC/移动端开发都合适
* 它本身只关心 UI,可以轻松引入 vue 插件和其他第三方库开发项目
* Vue包含一系列的扩展插件：
    * vue-cli ---脚手架，用来创建一个模版项目
        > command line interface 命令行接口
    * vue-resource
    * vue-router ----路由，用来构建单页面应用SPA
    * vuex ---状态管理
        
## 二.学习Vue？
* Vue.js官网:
    * http://cn.vuejs.org/
* 尤雨溪知乎主页: 
    * https://www.zhihu.com/people/evanyou/answers
* vue的github主页:
    * https://github.com/vuejs
* 掘金专题:
    * http://gold.xitu.io/tag/Vue.js
## 三.准备工作
1. 安装Chrome开发插件:

    * Vue.js devtools
2. 安装Webstorm提示插件:
    * settings ==> plugin ==> browser repositories ==> 搜索vue.js ==>下载并重启
3. 将vue项目通过git进行版本控制
    * 创建远程仓库
        * github => create a new repository
    * 创建本地仓库
        * 指定git的忽略列表(可以自动生成的文件)
            * .gitignore => .idea
        * 初始化本地仓库
            * terminal => git init => git add * => git commit -m "init vue test app"
                * 代码添加到本地仓库中(版本区)
            * git remote add origin + 远程仓库路径url
                * 关联到远程 
            * git push origin master
                > master -> 从本地 master 分支推送到远程 master 分支
## 四.对比几个常用的js库
> jQuery,zepto,angular,react,vue  
        
* jQuery,zepto 
    * 称为函数库，是对DOM(还有ajax)的封装
    * 直接操作DOM从而更新DOM更新页面
* angular,react,vue  
    * 称为结构化框架，MVVM,用于在浏览器端动态构建页面，并与用户交互
    * angular(先于react出现) 有模版(包含js代码的html，表达式，指令，)，双向数据绑定等概念
        * model <=> view 
        * model => view 更新页面
    * 数据驱动DOM，直接操作数据，实现页面变化，不会直接操作DOM(这部分工作被隐藏)
        * 组件化
            * 功能组件，方便复用，便于维护
        * 虚拟DOM
            * 快，页面更快展现，更快更新
            * 一个一般的对象，与一个真实的DOM元素相对应，我们操作的是虚拟DOM，通过虚拟DOM来批量的操作真实DOM
            * React 会通过 DOMdiff 算法，高效的区别哪些虚拟DOM发生了变化，把虚拟DOM的变化同步到真实DOM中去(最小化页面重绘)  
    * Vue
        * 借鉴 angular 的模板和数据绑定技术
        * 借鉴 react 的组件化和虚拟 DOM 技术
        * 体积小，运行效率高，编码简洁，PC/移动端开发都合适
## 五.进一步学习Vue
 > 声明式渲：Vue.js的核心是允许采用简洁的模版语法来声明式的将数据渲染进DOM
* 下载vue开发版本／cdn引入／NPM模块化开发
1. helloVue
    1. 引入Vue.js
    2. 创建Vue对象
        * el : 指定根element(选择器)
        * data : 初始化数据(页面可以访问)
    3. 双向数据绑定 : v-model
    4. 显示数据 : {{xxx}}
    5. 理解vue的mvvm实现
     > 注意: 需要在webstorm中安装vue.js插件
            
            <div id="test">
                <input type="text" v-model="msg">
                <p>{{msg}}</p>
            </div>
            
            <script type="text/javascript" src="../js/vue.js"></script>
            <script type="text/javascript">
                new Vue({
                    el:'#test',
                    data:{
                         msg:'tangtang'
                    }
                })
            </script>
2. 列表
    1. 在data中初始数组数据
    2. 在页面中遍历显示: v-for
    3. 练习：显示信息列表
    
                <ul id="test">
                  <li v-for="(todo,index) in todos">{{index+1}}--{{todo.id+'~~'+todo.name}}</li>
                </ul>
                <script type="text/javascript" src="../js/vue.js"></script>
                <script>
                new Vue({
                    el:'#test',
                    //data的值是一个对象，可以直接写一个对象，
                    // 也可以通过函数，返回一个对象，后者操作更灵活
                    data:function () {
                        return{
                            todos:[
                                {id : 2, name : '吃饭'},
                                {id : 4, name : '睡觉'},
                                {id : 6, name : '打豆豆'}
                            ]
                        }
                    }
                })
                </script>
        
3. 事件

    1. 绑定监听的指令:  
        * v-on:xxx="函数名或函数调用"
        * @xxx="函数名或函数调用"
    2. 定义事件处理的函数:
    
                methods : {
                  函数名 : function( ){...}
                }
    3. 练习：倒序排列字符串
            
                <div id="app"><!--就是mvvm中的view-->
                  <p>{{msg}}</p>
                  <!--<button v-on:click="reverse">倒序</button>-->
                  <button @click="reverse">倒序</button>
                </div>
                
                <script type="text/javascript" src="../js/vue.js"></script>
                <script type="text/javascript">
                  new Vue({ // vm对象
                    el : '#app',
                    data : { // 一般数据  model对象
                      msg: 'I Love You!'
                    },
                    methods: { // 事件回调函数
                      reverse () {
                        //this是Vue实例对象
                        this.msg = this.msg.split('').reverse().join('')
                      }
                    }
                  })
                </script>
4. 综合练习：  
* 综合使用以下技术:  
    1. 页面指令:  
        v-model  
        @click  
        @keyup.enter  
        v-for / $index  
        v-text  
    2. Vue对象  
        初始化数据: data  
        事件处理函数: methods  
* 功能，动态添加删除todoList
    
            <div id="app">
              <input type="text" v-model="inputTodo" @keyup.enter="addTodo">
              <ul>
                <li v-for="(todo, index) in todos">
                  {{todo.name}}
                  <button @click="removeTodo(index)">X</button>
                </li>
              </ul>
            </div>
            
            <script type="text/javascript" src="../js/vue.js"></script>
            <script type="text/javascript">
              new Vue({
                el : '#app',
                data : {
                  inputTodo: '',
                  todos: [
                    {id : 2, name : '吃饭'},
                    {id : 3, name : '睡觉'},
                    {id : 5, name : '打豆豆'}
                  ]
                },
                methods : {
                  addTodo () {
                    // 判断是否是正常输入
                    var inputTodo = this.inputTodo.trim()
                    if(!inputTodo) {
                      return
                    }
                    // 根据输入创建todo对象
                    var todo = {
                      id: Date.now(),
                      name: inputTodo
                    }
                    // 添加到todos
                    this.todos.unshift(todo)
                    // 清除输入数据
                    this.inputTodo = ''
                  },
                  removeTodo (index) {
                    this.todos.splice(index, 1)
                  }
                }
              })
            </script>
5. 模版语法
    1. 表达式 :  
        * 语法: {{exp}} 或 {{{exp}}}  
        * 功能: 向页面输出数据  
        * 可以调用对象的方法     
    2. 强制数据绑定:
        * 适用场景:
            * 标签内部是动态数据，但标签属性为html内置的属性而不是指令的时候，动态数据会当作字符串解析，这个时候需要强制数据绑定
        * 完整写法:  
        
                 v-bind:xxx='yyy'  //yyy会作为表达式解析执行  
        * 简洁写法:  
        
                  :xxx='yyy'  
    3. 事件监听:  
        * 完整写法:  
        
                v-on:keyup='xxx'  
                v-on:keyup='xxx(参数)'  
                v-on:keyup.enter='xxx'  
        * 简洁写法: 
        
                @keyup='xxx'
                @keyup.enter='xxx'
    4. 实例应用：
            
                <div id="app">
                <h2>1. 表达式</h2>
                    {{msg}}<br/>
                    {{msg.toUpperCase()}}
                <h2>2. 强制数据绑定:</h2>
                     <a v-bind:href="url">尚硅谷</a>
                     <a :href="url">尚硅谷</a>
                <h2>3. 事件监听:</h2>
                    <input type="text" @keyup.enter="test1">
                    <input type="text" @keyup.enter="test2($event)">
                </div>
                
                <script type="text/javascript" src="../js/vue.js"></script>
                <script type="text/javascript">
                var vm = new Vue({
                    el:'#app',
                    data:{
                        msg:'tangtang',
                        url:'http://www.atguigu.com'
                    },
                    methods:{
                        test1(event){
                            alert(event.target.value)
                        },
                        test2(event){
                            alert(event.target.value+"-----"+this.msg)
                        }
                    }
                })
                      console.log(vm);//数据代理(vm代理data中数据的操作 读／写)
                      vm.msg='yueyue' //外部写入修改数据
                </script>
6. 计算属性
    * 计算属性
        * 在computed属性对象中定义计算属性的方法
        * 在页面中使用{{方法名}}来显示计算的结果
    * 监视属性:
        * 通过vm对象的$watch()或watch配置来监视指定的属性
        * 当属性变化时, 回调函数自动调用, 在函数内部进行计算
    * 计算属性高级:
        * 通过get/set方法实现对属性数据的显示和监视
        * 计算属性存在缓存, 多次读取只执行一次
    * 实例应用：     
            <div id="demo">
              姓: <input type="text" placeholder="First Name" v-model="firstName" ><br>
              名: <input type="text" placeholder="Last Name" v-model="lastName"><br>
              姓名1(单向): <input type="text" placeholder="Full Name" v-model="fullName"><br>
              姓名2(单向): <input type="text" placeholder="Full Name" v-model="fullName2"><br>
              姓名3(双向): <input type="text" placeholder="Full Name2" v-model="fullName3"><br>
            </div>
            
            <div id="demo">
              姓: <input type="text" placeholder="First Name" v-model="firstName" ><br>
              名: <input type="text" placeholder="Last Name" v-model="lastName"><br>
              姓名1(单向): <input type="text" placeholder="Full Name" v-model="fullName"><br>
              姓名2(单向): <input type="text" placeholder="Full Name" v-model="fullName2"><br>
              姓名3(双向): <input type="text" placeholder="Full Name2" v-model="fullName3"><br>
            </div>
            
            <script type="text/javascript" src="../js/vue.js"></script>
            <script type="text/javascript">
                var vm = new Vue({
                    el:'#demo',
                    data:{
                        firstName:'tang',
                        lastName:'yueming',
                        fullName2:'tang-yueming'
                    },
                    computed:{
                        fullName(){//相当于只是指定了get
                            console.log('fullName1()')
                            return this.firstName + '-' + this.lastName
                        },
                        fullName3:{
                            get(){//获取当前属性值，当读取当前属性值时回调
                                return this.firstName + '-' + this.lastName
                            },
                            set(value){//监视当前属性值的变化，当属性值发生变化时调用
                                var name = value.split('-')
                                this.firstName = name[0],
                                this.lastName = name[1]
                            }
                        }
                    },
                    watch:{
                        firstName(value){//value 是新值
                            //当firstName发生改变时，更新fullName2
                            this.fullName2 = value + "-" + this.lastName
                        }
                    }
                })
                vm.$watch('lastName',function(value){
                    //更新fullName2
                    this.fullName2 = this.firstName + "-" + value
                    }
                )
            </script>
7. class 与 style 绑定
    * 动态绑定class  
        * :class="a" a是一个data属性
        * :class="{ 'class-a': isA, 'class-b': isB }"   其中isA/isB是布尔型data属性
        * :class="[classA, classB]" 其中classA/classB是字符串值
    * 动态绑定style
        * :style="{ color: activeColor, fontSize: fontSize + 'px' }"  其中activeColor/fontSize是data属性
    * 实例应用:
        
                <div id="demo">
                      <p class="classB" :class="a">测试v-bind:class 变量语法</p>
                      <p :class="{classA:isA, classB:isB}">测试v-bind:class 对象语法</p>
                      <p :class="['classA', classB]">测试v-bind:class 数组语法</p>
                    
                      <p :style="{ color: activeColor, fontSize: fontSize + 'px' }">测试v-bind:style</p>
                </div>
                
                <script type="text/javascript" src="../js/vue.js"></script>
                <script type="text/javascript">
                      new Vue({
                            el : '#demo',
                            data : {
                                  a: 'classA',
                                  isA: false,
                                  isB: true,
                                  classB: 'classB',
                                  activeColor: 'green',
                                  fontSize: 30
                            }
                      })
                </script>
8. 条件渲染
    * 切换一个元素:
        * v-if  ---- 移除元素
        * v-else ---- 隐藏元素
        * v-show
    * 切换多个元素
        * `<template v-if="ok">`  //不能用v-show 不会生成dom元素
        
    * 注意: 如果需要频繁切换 v-show 较好，如果在运行时条件不大可能改变 v-if 较好
    * 实例应用：
            
                <div id="demo">
                    <h1>测试: 切换一个元素</h1>
                    <p v-if="ok">我喜欢你</p>
                    <p v-else>你喜欢我</p>
                    <p v-show="ok">来自星星的你</p>
                
                    <h1>测试: 切换多个元素</h1>
                    <template v-if="ok">
                        <h2>xxxx</h2>
                        <h2>yyyy</h2>
                        <h2>zzzzz</h2>
                    </template>
                    <button @click="ok=!ok">切换</button>
                </div>
                
                <script type="text/javascript" src="../js/vue.js"></script>
                <script type="text/javascript">
                  new Vue({
                      el: '#demo',
                      data:{
                          ok: true
                      }
                  })
                </script>
9. 列表渲染
    * 遍历显示数组 : v-for / index
    * 遍历显示对象 : v-for / key
