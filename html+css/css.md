## 目录
## css(层叠样式表—负责页面的表现	)
* [css编写位置](#a)
    * 内联样式
    * 内部样式表
    * 外部样式表
* [css基本语法](#b)
* [选择器](#c)
    * 常用的选择器
    * 元素之间的关系
* [选择器的优先级(权重)](#d)
* [声明块](#e)
* [样式](#f)
    * 基础样式
    * 样式的继承
    * 样式的冲突
* [块元素和内联元素](#g)
    * 块元素
    * 内联元素
* [盒模型](#h)
    * 内容区
    * 内边距
    * 边框
    * 外边距
        * 内联元素的盒模型
* [文档流](#i)
    * 元素在文档流中的特点
        * 块元素
        * 内联元素
    * 浮动（float）
    * 脱离文档流
    * 高度塌陷
    * 定位
        * 相对定位
        * 绝对定位
        * 固定定位
    * 层级
    * 偏移量
* [透明度](#j)
* [浏览器默认样式](#k)
* [几个相关样式](#l)
    * display
    * visibility
    * overflow
* [单位](#m)
    * 像素 px
    * 百分比 ％
    * 颜色
    
    <br/><br/><br/><br/><br/><br/><br/><br/>
    
    
## css(层叠样式表—负责页面的表现	)
#### <div id='a'>一.css编写位置</div>
1. 内联样式
    * 编写到元素的 `style` 属性中
    * 使用内联样式属于结构和表现耦合，不方便复用和后期维护不推荐使用的
      
            <div style="...."></div>  
2. 内部样式表
    * 将样式编写到网页的 `style` 标签中
        
            <style type="text/css">
                  P{   ....  }
            </style>
3. 外部样式表
    * 将样式编写到外部的 css 文件中，然后通过 link 标签来引入到当前页面
    * 区别 `src` 和 `href`  
         * `<img src="" />`  
            img这种元素我们称为替换元素，引入这种替换元素使用的是 `src`
         * `<a href="" >aaa</a>	`    
            `<link rel="stylesheet" type="text/css" href="" />`  
            `a` 和 `link` 这种非替换元素引用资源时都是使用 `href`
    * 外部样式表可以在多个页面中进行复用，并且方便我们的后期维护，也可以利用到浏览器的缓存，提高用户的访问速度。
     
            <link rel="stylesheet" type="text/css" href="style.css" />
                        
#### <div id='b'>二.css基本语法</div>
* 语法格式：选择器 声明块
    
          p {
          color:red;
          font-size:50px;
          }
#### <div id='c'>三.选择器</div>
通过选择器可以选中页面中的指定元素，并且可以将选择器后声明块中的样式应用到这些元素上
>常用的选择器
1. 元素选择器
    - 作用：选中页面中所有的指定标签名的元素
    - 语法：标签名{  }   
    - 例子: `p{  }  h1{  }  div{  }`
2. id选择器
    -作用：根据id属性值选中页面中唯一的一个元素
    - 语法：#id属性值{  }   
    - 例子: `#p1{  } #box1{  }`
3. 类选择器
    - 作用：根据元素的class属性值选中元素
    - 语法: .class属性值{}  
    - 例子：`.p2{ }  .box{ }`
4. 并集选择器（选择器分组）
    - 作用：同时选中多个选择器对应的元素
    - 语法：选择器1,选择器2,选择器N{}   
    - 例子：`div , p , #box1{ }`
5. 交集选择器
    - 作用：选中同时符合多个选择器的元素
    - 语法：选择器1选择器2选择器N{}  
    - 例子：`div.box{  } p.p1{  }`
6. 通配选择器
    - 作用：选中页面中的所有元素
    - 语法：`*{  } `  
    - 注意：性能差，少用
7. 后代元素选择器
    - 作用：选中指定祖先元素的指定后代元素
    - 语法：祖先 后代{ }    
    - 例子：`#box span{}`
8. 子元素选择器
    - 作用：选中指定父元素的指定子元素
    - 语法：父元素 > 子元素{}   
    - 例子：`#box > span{}`    
9. 伪类选择器 
    * 伪类都是用来表示元素所处在的一个状态
        > 浏览器是根据用户的历史记录来判断一个链接是否访问过的
    * 超链接相关的4个伪类
        * `:link`   - 正常的链接（未访问过）
        * `:visited`  - 已访问过的链接
            > 由于隐私的原因，`visited` 这个伪类只能设置字体的颜色,  
            `:hover` 和 `:active` 可以为超链接以外的元素设置
        * `:hover`  - 鼠标移入的元素
        * `:active`  - 鼠标点击的元素
            > a的伪类书写顺序要求    `:link  :visited  :hover :active`
   
* 元素之间的关系  
    * 父元素
        - 直接包含子元素的元素
        - 父元素也是祖先元素
    * 子元素
        - 直接被父元素包含的元素
        - 子元素也是后代元素
    * 祖先元素
        - 直接或间接包含后代元素的元素
    * 后代元素
        - 直接或间接被祖先元素包含的元素
    *   兄弟元素
        - 拥有相同父元素的元素
#### <div id='d'>四.选择器的优先级(权重)</div>
        
* 内联样式  优先级 1000
* id选择器   优先级 100
* 类和伪类	优先级 10
* 元素选择器	 优先级 1
* 通配选择器	 优先级 0
* 继承的样式 	 没有优先级



#### <div id='e'>五.声明块</div>
 声明块由一对`{  }`括起来，它里边是一对一对的声明，
    每个声明都是一个名值对的结构，一个样式名对应一个样式值。样式名和样式值之间使用`:`连接，以`;`结尾。
#### <div id='f'>六.样式</div>
1. 基础样式

            color 字体颜色
            background-color 背景颜色
            font-size 字体大小
            width 元素的宽度
            height 元素的高度
2. 样式的继承
     * 为祖先元素设置的样式也会同时应用到它的后代元素上，这一特性我们称为样式的继承
     * 样式的继承实际上是对开发的一个简化，但是并不是所有的样式都会被继承。
     * 比如：背景相关的 边框相关的 宽度 高度。。。。 具体的继承性可以参考文档
 
3. 样式的冲突:   
     * 当使用不同的选择器，选中同一个元素并设置相同的样式时，此时会发生样式的冲突.这时采用哪个选择器设置的样式由选择器的优先级来决定，优先级高的优先显示.  
     * 当比较选择器的优先级时，需要将多个选择器的优先级相加然后在计算,优先级较高的优先显示，对优先级进行相加时不会超过选择器的最大的数量级
    （选择器分组不会相加计算而是单独计算）
     * 如果两个选择器的优先级一样，则谁在下边就使用谁
     * 如果为一个样式添加一个`!important`，则该样式将会获得一个最高的优先级.
     将会优先于所有的样式来显示，这个`!important`尽量避免使用     
#### <div id='g'>七.块元素和内联元素</div>
1. 块元素( block )  
    - 在页面块元素无论自身的大小总会独占页面的一行
    - 在网页中一般都是使用块元素对页面进行布局
    - 学习过的块元素
       `div h1~h6 ul li dl ol dt dd ....`

2. 内联元素( inline 行内元素)
    - 内联元素在页面中只占自身的大小，不会独占一行，如果一行中容不下所有的内联元素则会换到下一行显示
    - 在页面中一般使用内联元素来选中文字，来为文字设置样式的
    - 学习过的内联元素
       `a span img ....`
       
3. 注意  
    - 一般页面中都是块元素去包含内联元素，而不使用内联元素去包含块元素
    - `a` 元素可以包含任何元素，但是除了 `a` 本身
    - `p` 元素中不能放任何的块元素
    
#### <div id='h'>八.盒模型</div>
CSS中将网页中的每一个元素都想象成了一个矩形盒子，将元素都想象成盒子是为了方便网页的布局。  
这些盒子从里到外由以下几个部分组成  

1. 内容区（content）  

   - 元素的所有的子元素和内容这些都是在它的内容区中存在的
   - 通过 `width` 和 `height` 来设置内容区的大小
   - `width`：设置内容区的宽度
   - `height`：设置内容区的高度
2. 内边距（padding）
    - 内容区和边框之间的距离是内边距，内边距会影响到盒子的大小
    - 一共有上 右 下 左 四个方向的内边距
    - 分别`padding-top`  `padding-right`  `padding-bottom` `padding-left`
    - 也可以通过 `padding` 来同时指定四个方向的内边距
    - 规则：
        - 四个值   `padding:上 右 下 左`;
        - 三个值   `padding:上 左右 下`;
        - 两个值   `padding:上下 左右`;
        - 一个值   `padding:上下左右`;
3. 边框（border）
    - 边框是盒子可见框的最外部
    - 边框会影响到盒子的可见框的大小
    - 设置边框，需要同时设置三个样式：宽度 颜色 样式
        - `border-width` - 边框的宽度  
        - `border-color` - 边框的颜色  
        - `border-style` - 边框的样式
    - 这三个样式可以同时指定四个边框，或者也可分别指定，规则和 `padding` 一样
    - 还有一些单独设置某一个边的样式的:
        - `border-xxx-width `    
        - `border-xxx-color `  
        - `border-xxx-style`
    - border 简写属性
        - 通过 `border` 可以同时设置四个边的边框，而且没有顺序要求  
        - `border : red solid 10px`
        - 除了 border，还提供了四个 border-xxx，专门用来单独设置某一个边的样式
            - `border-top`      
            - `border-right`      
            - `border-bottom`     
            - `border-left`
    - 边框样式可选值：
        - `solid` 实线
        - `dotted` 点状虚线
        - `dashed` 虚线
        - `double` 双线


* 盒子的可见框的大小，由内容区、内边距和边框共同决定  
     * 整个盒子的宽度:  
     border-left-width + padding-left + width + padding-right + border-right-width  
     * 整个盒子的高度:  	
     border-top-width + padding-top + height + padding-bottom + border-bottom-width
4. 外边距（margin）

    - 盒子与盒子之间的距离称为外边距
    - 外边距不会影响盒子的可见框大小，会影响到盒子的位置
    - 同样有四个方向的外边距
        - `maring-top`   
        - `margin-right`    
        - `margin-bottom`    
        - `magin-left`
    - 简写属性 `margin` 和 `padding` 的规则相同.
    - 由于元素默认是自左向右，自上向下排列的.
    所以当我们修改元素的上或左外边距会影响到元素自身的位置，
    而设置下或右外边距时会影响其他的元素
    - 外边距可以设置为负值，如果设置为负值，则元素会向相反的方向移动
    - 水平外边距可以设置为 `auto`
        * 如果设置为 `auto` 则浏览器会自动计算外边距
        * 如果将左或右外边距设置为 `auto`，则浏览器会使元素左或右外边距为最大值，
        * 如果将左和右同时设置为 `auto`，则浏览器会使元素的左右外边距相等，
        * 我们经常利用该特性使一个元素在其父元素中水平居中 `margin : 0 auto;`
    - 垂直外边距的重叠
      - 垂直方向相邻的外边距会发生重叠现象
      - 兄弟元素之间的相邻垂直外边距会取最大值
         > 兄弟元素中，一个元素设置浮动后，与其兄弟元素的垂直外边距会求和，而不是取最大值.因为其已经脱离文档流
      - 子元素的垂直外边距会传递给父元素
    - 相邻的水平方向的外边距不会重叠而是取和

* 内联元素的盒模型
    - 内联元素不支持 `width` 和 `height`
    - 内联元素支持水平方向的内边距和边框
        也可以设置垂直方向的内边距和边框，但是不会影响页面布局
    - 内联元素支持水平方向的外边距，不支持垂直方向的

#### <div id='i'>九.文档流</div>
文档流是网页的最底层,我们所创建的元素默认都是在文档流中。
1. 元素在文档流中的特点

    * 块元素
        * 块元素在文档流自上向下垂直排列
        * 块元素在文档流中的默认宽度是父元素100%
        * 块元素在文档流中默认高度被内容（子元素）撑开
    * 内联元素
        * 内联元素在文档流中自左向右排列，
          如果一行不足以容纳所有的元素则会另起一行继续自左向右。
        * 内联元素在文档流中的宽度和高度默认都被内容撑开
2. 浮动（float）
    * 通过设置浮动可以使元素完全脱离文档流,然后向页面的左上或右上进行浮动
    * 通过float来设置浮动
    * 可选值：  
        * none 默认值 元素在文档流中，没有浮动
        * left 元素向左浮动
        * right 元素向右浮动
    * 浮动的特点:
        * 浮动元素会盖住文档流中的元素
        * 元素设置浮动以后会向页面的左上或右上移动
        * 浮动元素遇到父元素的边框或其他的浮动元素时也会停止移动
        * 浮动元素的上边如果是一个没有浮动的块的元素，不会超过该块元素
        * 浮动元素不会超过他上边的浮动的兄弟元素，最多一边齐
        * 文字不会被浮动元素所覆盖，而是环绕在浮动元素的周围，可以通过该特点来设置文字环绕图片的效果
        * 设置浮动会使元素完全脱离文档流

3. 脱离文档流
    * 元素脱离文档流以后会具有如下的特点
        * 块元素   
            * 块元素脱离文档流以后，不再独占一行
            * 块元素脱离文档流以后，宽和高默认都被内容撑开
        * 内联元素
            * 内联元素脱离文档流以后会变成块元素
            
4. 高度塌陷

    * 一个块元素如果不设置高度，默认是被内容撑开的
    但是当子元素浮动以后，将会完全脱离文档流，导致无法撑起父元素的高度，导致父元素的高度塌陷
    父元素高度塌陷以后，其他元素将会自动向上移动，导致页面的布局混乱
    * 可以通过开启元素的BFC来处理高度塌陷的问题
        * W3C规定每一个元素都有一个隐含的属性BFC，该属性可以设置开启或关闭，默认情况下该属性都是关闭的
            >  BFC（Block Formatting Context）
          块级格式化上下文
      * 开启BFC以后，元素会具有如下的特性：
        * 子元素的垂直外边距不会传递给父元素	
        * 开启BFC的元素不会被浮动元素所覆盖
        * 开启BFC以后，元素可以包含浮动子元素
      * 开启BFC的方式:
        * 设置元素浮动  
        * 设置元素绝对定位
        * 设置元素的display为inline-block
        * 设置元素的overflow为一个非visible的值
             > 一般通过overflow：hidden，来开启元素的bfc，从而解决高度塌陷的问题
      
5. 定位  

* 定位是一种高级的非常灵活的布局的方式，通过定位可以将元素摆放到页面的任意位置
* 通过position属性来设置元素的定位
* 可选值：
    * static 默认值 元素没有开启定位
    * relative 开启元素的相对定位
    * absolute 开启元素的绝对定位
    * fixed 开启元素的固定定位
* 相对定位relative特点：  
    * 开启相对定位以后，如果不设置偏移量元素不会发生任何变化
    * 相对定位的元素不会脱离文档流
    * 相对定位不会改变元素的性质，块还是块 内联还是内联
    * 相对定位的元素是相对于其自身在文档流中的位置定位
    * 相对定位会提升元素的层级
* 绝对定位absolute特点：
    * 开启绝对定位以后，如果不设置偏移量元素的位置不会发生变化
    * 绝对定位的元素会脱离文档流
    * 绝对定位会改变元素的性质，块元素宽高被内容撑开，内联元素变成块元素
    * 绝对定位的元素相对于离他最近的开启了定位的祖先元素进行定位，  
      如果所有的祖先元素都没有开启定位则相对于浏览器窗口进行定位  
      一般情况下开启一个元素的绝对定位时，都会同时开启它父元素的相对定位  
    * 绝对定位会提升元素的层级
* 固定定位fixed特点：
    * 固定定位也是一种绝对定位，所以它的大部分特点都会绝对定位相同，
    * 不同的是固定定位元素永远相对于浏览器窗口进行定位，
    * 并且固定定位的元素不会随页面滚动
6. 层级
    * 元素的层级关系:
       * 定位 > 浮动 > 文档流
    * 可以通过z-index来设置定位元素的层级，
      层级越高越优先显示
      - z-index需要一个整数作为参数，数值越大层级越高
      - 如果两个元素的层级一样，则显示下边的元素
      - 父元素永远不会盖住子元素
      z－index只对开启了定位的元素起作用！！！
      开启了定位的元素的层级都是一样的，此时下边的元素会盖住上边的
      
7. 偏移量
* 开启了定位的元素可以通过偏移量来设置元素的位置
    * top      －当前元素距离定位元素顶部的距离
    * bottom－当前元素距离定位元素底部的距离     
    * left      －当前元素距离定位元素左侧的距离
    * right    －当前元素距离定位元素右侧的距离
* 偏移量只对开启了定位的元素起作用,
  一般情况下四个偏移量我们只需要使用两个，即可为一个元素进行定位，一个水平方向的一个垂直方向的

#### <div id='j'>十.透明度</div>
* 通过opacity来设置元素的透明度
* 它需要一个0-1之间的值
    * 0 表示完全透明
    * 1 表示完全不透明
    * 0.5 表示半透明
    * 只支持ie9及以上的浏览器，ie8不支持
* 在IE8及以下的浏览器中需要使用滤镜来设置透明效果  
  `filter:alpha(opacity=透明度)`
  - 这里的透明度需要0-100之间的值，具体的规则和opacity是一样就是换成百分值	
#### <div id='k'>十一.浏览器默认样式</div>
浏览器为一些元素添加了一些默认的样式，为了确保页面在没有样式表时也可以浏览，
但是这些默认样式会为我们的开发带来一些影响，一般情况下我们都需要清除这些默认的样式
- 清除默认样式

			*{
				margin:0;
				padding:0;
			}
			ul{
			    list-style:none;
			}
#### <div id='l'>十二.几个相关样式</div>
* display

    * 可以设置元素的类型
    * 可选值：
      - none 元素不在页面中显示，并且不会占据页面的位置
      - block 元素作为一个块元素显示
      - inline 元素作为一个内联元素显示
      - inline-block 元素作为行内块元素显示，既不独占一行，也可以设置宽和高
* visibility
    * 可以设置元素的显示状态
    * 可选值：
        - visible 默认值 元素在页面中可见
        - hidden 元素在页面中隐藏，但是会占据页面中的位置
* overflow
    * 设置父元素如何处理溢出的内容
    * 可选值：
        - visible 默认值 溢出的内容在父元素以外的位置显示
        - hidden 溢出的内容会被裁剪，不会显示
        - scroll 溢出的内容会被裁剪，可以通过滚动条来查看完整内容
                    默认会生成水平和垂直双方向的滚动条
        - auto 根据需要自动生成滚动条
#### <div id='m'>十三.单位</div>
1. 像素 px

    * 屏幕中的一个一个小点就是一个像素，它是我们用的最多的单位
2. 百分比 %
    * 除了像素，也可以将样式的值设置为一个百分比的值，
    * 如果设置一个百分比的值，元素将会自动根据父元素的指定属性去计算自身的样式
    * 使用百分比作为单位，当父元素的大小改变时，子元素会等比例改变
        * 比如：width:20% 将会将width的值设置为父元素width的20%
    * 一般我们做一些响应式的自适应的网页时或者移动端的页面时，会大量的使用百分比的值
3. 颜色
    * 使用单词
        * 可以直接使用颜色的单词来设置颜色
        * 比如：red yellow blue green orange 。。。。
        * 但是单词使用起来比较麻烦，而且单词也不能把所有的颜色都描绘出来
    * RGB值
        * RGB值指光的三元素，通过红色 绿色 蓝色 三种光的浓度来搭配出不同的颜色
        * 方式一:
            * rgb(红色,绿色,蓝色)
              - 红色，绿色，蓝色需要一个0-255之间的值，来设置浓度
                 0表示最小，255表示最大
              - 比如：红色 rgb(255,0,0)
              - 除了0-255之间的值，也可以设置一个0% - 100%之间的值，
              这些值最终也会转换为0-255之间的数
               0%就相当于0 100%相当于255
        * 方式二:
            * 使用十六进制的RGB值，来表示颜色
              0 1 2 3 4 5 6 7 8 9 a b c d e f
              - 语法：#红色绿色蓝色
              - 它需要三组两位的十六进制数字来表示颜色
              两位的十六进制数字 00 - ff
              - 比如红色：#ff0000
              - 如果颜色是两位两位重复的还可以进行简写
              比如：#aabbcc 可以写成 #abc
        