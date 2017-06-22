## 目录
## JavaScript
JavaScript是运行在浏览器端一门脚本语言，JavaScript的标准称为ECMAScript.  
这一阶段学习JS，主要分成三个部分  
* ES标准
* DOM
* BOM	
#### <div id='a'>一.简介</div>
1. 简介
2. JS代码的编写位置
    * 编写在标签内部的指定属性中
        > 将JS代码编写到HTML的属性中，我们称为结构与行为耦合，不方便维护
    
            <button onclick="....">按钮</button>
            <a href="javascript:...;">超链接</a>
        * 可以将JS代码编写到超链接的href属性中，这样当点击超链接时，将不会跳转页面而是执行这些js代码
             
              <a href="javascript:;">超链接</a>
    * 编写在script标签中
        
            <script type="text/javascript">
            	....
            </script>
            
    * 编写到外部的js文件中,然后通过script标签进行引入
            
            <script type="text/javascript" src="script.js"></script>
3. 基本语法
    * 单行注释     
            
                //注释内容
    * 多行注释
    
                /*
                    注释内容
                */
        （通过注释可以对程序进行解释描述，一定要养成良好的编写注释习惯，通过注释也可以对程序进行一个简单的调试）
    * 在JS中严格区分大小写	
    * 在JS中会忽略多个空格和换行，我们可以通过空格和换行对代码进行格式化
    * JS的每条语句都要以分号结尾，如果不写分号浏览器会自动添加，这一阶段强制要求必须写
4. 字面量
    * 字面量简单理解就是一些固定的值，字面量都是不会改变的，在js中可以直接使用字面量，比如：1 2 3 4 "a" "b" "c"
    * 字面量在实际使用中并不是很方便，一般情况下不会直接使用字面量
5. 变量
    * 变量可以用来保存字面量，变量可以保存不同的字面量，并且可以任意修改。
      我们在开发中，一般不会直接使用字面量，而是使用变量来保存一个字面量，使用变量也可以对字面量进行描述
    * 变量的使用
        1. 声明变量
            * 使用var关键字来声明一个变量
            
                    var a; var b; var c , d , e;
            * 如果使用没有声明的变量，浏览器会报错
        2. 为变量赋值
            * 使用 = 为一个变量赋值 
                    
                    a = 1 ; b = 2 ; c = 3;
            * 如果声明了一个变量但是没有赋值，则此时变量的值是 undefined
        3. 声明和赋值同时进行
            
                var a = 1;
                var b = 2;
                var c = 3 , d = 4 , e = 5;
6. 标识符
    * 在JS中所有可以自主命名的内容都可以认为是一个标识符
    	比如：变量名 函数名 属性名。。。
    * 标识符在JS底层都是使用Unicode编码进行保存的，
      所以理论上讲，只要是Unicode编码中有的都可以作为标识符.
      但是千万不要啥都用，还是要遵循规范
    * 标识符需要遵循如下的规范:
        1. 标识符中可以包含字母、数字 、_ 、$，但是不能以数字开头
        2. 标识符不能是JS中的关键字和保留字
        3. 标识符需要采用驼峰命名法
            - 首字母小写，每个单词开头字母大写
            - 例子：helloWorld xxxYyyZzz
            （不能把关键字、保留字、true、false和null用作标识符）
            
    * 在代码中使用关键字作为标识符在大多数浏览器中都会倒是“Identifier Expected”（缺少标识符）错误。而使用保留字可能不会导致同样的错误，这要视具体的浏览器而定。一般来说，最好不要使用关键字和保留字作为标识符，以便与ECMAScript未来的版本保持兼容。
7. 关键字
    * js中的关键字可用于表示控制语句的开始或结束，或者用于执行特定操作等。按照规则，关键字也是语言保留的，不能用作标识符。
    * 以下就是ECMAScription的全部关键字：
    
            break、else、new、var、 case、  finally 、 return、 void 、 catch  、for  、switch 、 while 、   
            continue、  function  、this 、 with 、  default 、 if 、 throw 、 delete 、 in 、  try 、do 、  
             instranceof、  typeof
8. 保留字
    * ECMA还描述了另外一组不能用作标识符的保留字。尽管保留字在这门语言中还没有任何特定的用途，但它们有可能将来被用作关键字。 
    * 下面是ECMA第3版定义的全部保留字：
            
             abstract 、 enum   、int 、 short 、 boolean  、export  、interface、  static、  byte  、extends 、
              long 、 super 、 char 、 final  、native  、synchronized 、 class  、float 、 package  、throws 、
              const  、goto  、private 、transient 、 debugger、 implements 、protected 、 volatile 、 double、
             import  、public
9. {   &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; }

    * 在JS中可以使用{     }来将多个语句包含起来
    * 在同一个{   }中的语句属于一组语句，一个{   }我们就称为是一个代码块
    * 一个代码块中的语句要么都执行，要么都不执行
    * 在JS中{    }只有分组的作用，没有其他的任何作用
    * 代码块中的内容，对于外部来说是可见的
#### <div id='b'>二.基本数据类型（5种）</div>
1. String（字符串）

    * 在JS中字符串需要使用引号引起来，单引号或双引号
        - 同类型的引号不能嵌套
        - 使用typeof检查一个String类型的值时，会返回 string
        - 使用 \ 来作为转义字符
        
                \"  ---> "
                \' ---> '
                \\ ---> \
                \n ---> 换行
                \t ---> 制表符
                \uxxxx ---> Unicode编码
2. Number（数值）
    - 在JS中所有的数字都是Number类型（包括整数和浮点数）
    - 使用typeof检查一个Number类型的值时会返回number
    - 特殊的数字：    
    
          Infinity 正无穷，当我们使用的数字超过了JS的范围时，会返回Infinity
          NaN（Not a Number）非法数字
    - 注意使用typeof检查Infinity和NaN时都会返回number
    - 其他的进制的数字（并不是所有的浏览器都支持）
    
           二进制 0b开头（兼容性不好）  八进制 0开头    十六进制 0x开头
    - 在JS中可以表示的最大值  
        
            Number.MAX_VALUE   1.7976931348623157e+308
    - 在JS中可以表示的最小值	
        
            Number.MIN_VALUE     5e-324
    - 在JS中，大部分的整数运算都可以确保精确.
    但是如果进行浮点数运算，可能会出现不可预期的结果
    也就是结果是不够精确的，注意不要在JS做精度要求高的运算
3. Boolean（布尔值）
    - 布尔值用来在程序中做逻辑判断的
    - 布尔值一共就有两个
    
    			true 表示真
    			false 表示假
    - 使用typeof检查一个布尔类型的值时，会返回boolean
4. Null（空值）
    - Null专门用来表示为空的对象
    - 它只有一个值：null
    - 使用typeof检查Null时，会返回object
5. Undefined（未定义）
    - Undefined表示声明但没有赋值的变量值是undefined
    - 它只有一个值：undefined
    - 使用typeof检查时，会返回undefined
#### <div id='c'>三.数据类型的转换</div>
1. String
2. Number
3. Boolean
#### <div id='d'>四.引用数据类型</div>
Object（对象） 
1. 对象的分类
2. 对象的创建
3. 对象的属性的操作
4. 函数（function）
#### <div id='e'>五.基本数据类型和引用数据类型的区别</div>
#### <div id='f'>六.函数（function）</div>
1. 函数的创建
2. 函数的调用
3. 参数
4. 返回值
5. 匿名函数（立即执行函数）
6. 构造函数constructor
7. 原型（prototype）
8. call()和apply()
9. this（上下文对象）
#### <div id='g'>七.数组（Array）</div>
1. 创建数组对象
2. 向数组中添加元素
3. 读取数组中的元素
4. 数组的属性和方法
5. 遍历数组
#### <div id='h'>八.包装类</div>
String
#### <div id='i'>九.运算符（操作符）</div>
1. typeof
2. 算数运算符
3. 一元运算符
4. 自增
5. 自减
6. 逻辑运算符
    * 或||
    * 与&&
    * 非!
    * 赋值运算符
    * 关系运算符
    * 相等运算符
    * 三元运算符?:
#### <div id='j'>十.流程控制语句</div>
1. 条件判断语句（if语句）
2. 条件分支语句switch...case
3. 循环语句
    * while
    * do...while
    * for
#### <div id='k'>十一.正则表达式</div>
1. 创建正则表达式的对象
2. 方法
3. 匹配模式
4. 基本语法
#### <div id='l'>十二.作用域</div>
1. 全局作用域
2. 函数作用域
3. 声明提前
    * 变量的声明提前
    * 函数的声明提前
#### <div id='m'>十三.样式的操作</div>
1. 操作内联样式
2. 读取元素当前的样式
3. 其他样式相关的属性,其他获取样式的方式
#### <div id='n'>十四.事件(event)</div>
1. 绑定事件的响应函数
2. 事件对象
3. 事件的冒泡
4. 事件的绑定

#### <div id='o'>十五.DOM</div>
1. 节点（Node）
2. 常用的节点
3. DOM的查询方法
4. DOM的修改

#### <div id='p'>十六.BOM</div>
1. BOM对象
2. Navigator
3. History
4. Location
#### <div id='q'>其他补充</div>

1. Math
2. Date
3. 测试程序的运行的性能
4. debug
5. 文档的加载
6. 异常处理（try...catch...finally）




<br/>
<br/>
<br/>
<br/>
<br/>
<br/>


## JavaScript
#### [一.简介](#a)
1. 简介
2. JS代码的编写位置
3. 基本语法
4. 字面量
5. 变量
6. 标识符
7. {   }
#### [二.基本数据类型（5种）](#b)
1. String
2. Number
3. Boolean
4. Null
5. Undefined
#### [三.数据类型的转换](#c)
1. String
2. Number
3. Boolean
#### [四.引用数据类型](#d)
Object（对象） 
1. 对象的分类
2. 对象的创建
3. 对象的属性的操作
4. 函数（function）
#### [五.基本数据类型和引用数据类型的区别](#e)
#### [六.函数（function）](#f)
1. 函数的创建
2. 函数的调用
3. 参数
4. 返回值
5. 匿名函数（立即执行函数）
6. 构造函数constructor
7. 原型（prototype）
8. call()和apply()
9. this（上下文对象）
#### [七.数组（Array）](#g)
1. 创建数组对象
2. 向数组中添加元素
3. 读取数组中的元素
4. 数组的属性和方法
5. 遍历数组
#### [八.包装类](#h)
String
#### [九.运算符（操作符）](#i)
1. typeof
2. 算数运算符
3. 一元运算符
4. 自增
5. 自减
6. 逻辑运算符
    * 或||
    * 与&&
    * 非!
    * 赋值运算符
    * 关系运算符
    * 相等运算符
    * 三元运算符?:
#### [十.流程控制语句](#j)
1. 条件判断语句（if语句）
2. 条件分支语句switch...case
3. 循环语句
    * while
    * do...while
    * for
#### [十一.正则表达式](#k)
1. 创建正则表达式的对象
2. 方法
3. 匹配模式
4. 基本语法
#### [十二.作用域](#l)
1. 全局作用域
2. 函数作用域
3. 声明提前
    * 变量的声明提前
    * 函数的声明提前
#### [十三.样式的操作](#m)
1. 操作内联样式
2. 读取元素当前的样式
3. 其他样式相关的属性,其他获取样式的方式
#### [十四.事件(event)](#n)
1. 绑定事件的响应函数
2. 事件对象
3. 事件的冒泡
4. 事件的绑定

#### [十五.DOM](#o)
1. 节点（Node）
2. 常用的节点
3. DOM的查询方法
4. DOM的修改

#### [十六.BOM](#p)
1. BOM对象
2. Navigator
3. History
4. Location
#### [其他补充](#q)

1. Math
2. Date
3. 测试程序的运行的性能
4. debug
5. 文档的加载
6. 异常处理（try...catch...finally）