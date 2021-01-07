CSS（https://www.xp.cn/css3/）

#### 选择器

> 派生选择器：通过依据元素在其位置的上下文关系来定义样式
>
> > ```
> > <p><strong>XX</strong></p>
> > ```
> >
> > ```
> > p strong{    
> > 	color:firebrick;
> > }
> > ```
>
> id选择器：以#来定义，可以为标有id的html元素指定特有的样式
>
> > ```
> >     <div id="divid">
> >         <p>XXX</p>
> >     </div>
> > ```
> >
> > ```
> > #divid{
> >     color: blueviolet;
> > }
> > ```
> >
> > id选择器可以和派生选择器一起使用 #id p{	}
>
> 类选择器：类选择器以一个点显示
>
> > ```
> > <div class="divclass">
> >         <p>XXX</p>
> > </div>
> > ```
> >
> > ```
> > .divclass {
> >      color: blue;
> > }
> > ```
> >
> > 类选择器可以和派生选择器一起使用	.divclass p{	}
>
> 属性选择器：对带有指定属性的html元素设置样式
>
> > ```
> >     <style>
> >         [title]{
> >             color: brown;
> >         }
> >         [title=te]{
> >             color: blue;
> >         }
> >         [title~="hello"]{
> >             color: blue;
> >         }
> >     </style>
> > ```
> >
> > ```
> > 	<p title="t">属性选择器</p>
> >     <p title="te">属性和值选择器</p>
> >     <p title="hello">满足第三个</p>
> >     <p title="hello fh">满足第三个</p>
> > ```
>
> 伪类选择器
>
> > **伪类**
> >
> > ：first-child｛｝  --第一个子元素
> >
> > ：last-child｛｝  --最后一个子元素
> >
> > ：nth-child（n）｛｝  --选中第n个子元素
> >
> > > 特殊值：n表示所有，2n或even表示偶数，2n+1或odd表示奇数
> >
> > 以上（根据所有的子元素进行排序）
> >
> > ：first-of-type｛｝ 、：last-of-type｛｝、：nth-of-type（n）｛｝  --同类型元素进行排序
> >
> > **伪元素**
> >
> > ：:first-letter{}  --元素第一个字母
> >
> > ：:before{content：‘XXX’}  --元素开始，必须和content结合，不然没有变化
> >
> > ：:after{content：‘XXX’}  --元素最后，必须和content结合，不然没有变化
> >
> > ：:first-line{}  --第一行
> >
> > ：:selection｛｝--表示选中的内容
>

#### 背景

> > 允许应用纯色作为背景，也允许使用背景图像创建相当复杂的效果
>>
> > background-image:url(XXX);  --设置背景图片
> >
> > background-repeat：no-repeat/repeat/repeat-x/repeat-y  --设置平铺属性
> >
> > backgound-position：left/center/right  top/center/bottom  --设置背景图位置
> >
> > backgound-attachment：scroll（滚动）/fixed（固定，跟内容一起滚动）  --背景图的固定
> 

#### 链接的四种状态

> > a:link{ } --未访问的链接状态
>>
> > a:visited{ } --已访问的链接状态
> >
> > a:hover{ } --鼠标滑过状态
> >
> > a:active{ } --鼠标按下去的状态
> >
> > （联合使用时是有顺序的）
> 
> 伪对象选择符
>
> > :before{}
>>
> > :after{}
> >
> > :first-letter{}
> >
> > :first-line{}
> 

#### 盒子模型，浮动

> 盒子模型
>
> > 内容content、内边距padding、边框border、外边距margin
> >
> > **box-sizing：border-box/content-box/inherit**
> >
> > - content-box：总宽度=margin+border+padding+width;即标准模型
> > - border-box：总宽度=margin+width，即IE模型
> > - inherit：继承父元素的box-sizing属性
>
> 浮动
>
> > **浮动特点**
> >
> > 块元素：1.不独占一行  2.宽度和高度默认被内容撑开
> >
> > 行内元素：变为块元素，特点和块元素一样
> >
> > **清除浮动方法：**
> >
> > 1.父级添加overflow：hidden 
> >
> > 2.父级添加height
> >
> > 3.clear：both  在浮动元素下加空div div{clear:both;height:0;overflow:hidden}
> >
> > 4.万能清除浮动法  .clear:after{content:"";width:'100%';height:0;clear:both;overflow:hidden;visibility:hidden;display:block}
>

#### position定位属性

> position定位属性（z-index可设置层级关系）
>
> > ｛position：static/absolute/relative/fixed｝
> >
> > absolute：设置后不占位，位置可偏移（相对于父级容器定位，父级不能是static），left/right/top/bottom
> >
> > relative：设置后占位，位置可偏移（相对于自身）
> >
> > fixed：设置后不占位，位置可偏移（相对于浏览器窗口），固定定位，随着滚动条位置不变 
> >
> > **父相子绝（父级相对定位，子级绝对定位）**
>

#### CSS容器与文本溢出相关属性

> CSS容器与文本溢出相关属性
>
> > **文本属性-容器溢出**
> >
> > ｛overflow：visible/hidden/scroll/auto/inherit｝
> >
> > visible：默认值，内容不会被修剪，会呈现在元素框之外
> >
> > hidden：内容被修剪，并且其余内容不可见
> >
> > scroll：内容被修剪，但是浏览器显示滚动条
>>
> > auto：如果内容被修剪，浏览器显示滚动条
>>
> > inherit：规定从父元素继承overflow属性的值
> >
> > **文本属性-空白空间**
> >
> > ｛white-space：normal/pre/nowrap/pre-wrap/pre-line/inherit｝
> >
> > normal：默认值，多余空白会被 浏览器忽略只保留一个
> >
> > pre：空白被保留，文字变一行  
> >
> > pre-wrap：保留空白符，但是进行正常换行
> >
> > pre-line：合并空白符，正常换行
>>
> > nowrap：合并空白符，不换行，直到遇到< br />为止（常用）
>>
> > **文本属性-文本溢出**（单独写没有作用）
> >
> > ｛text-overflow：clip/ellipsis｝
> >
> > clip：不显示省略号，简单裁剪
> >
> > ellipsis：文本溢出，显示省略号
> >
> > **文本溢出时用省略号代替的方法：**
> >
> > width：  --要有容器宽度
> >
> > white-space：nowrap  --强制文本在一行显示
>>
> > overflow：hidden  --溢出内容隐藏
>>
> > text-overflow：ellipsis  --溢出内容显示省略号
> 

#### 元素类型

> 元素类型
>
> > **块级元素**：div，p，h1，form，hr等   （拥有盒子模型，可设宽高）
> >
> > **内联元素**：span，a，label，select，textarea等   （拥有部分盒子模型（无margin的上下），不能设宽高）
> >
> > **行内块元素**：img，input（可设宽高，不独占一行）
> >
> > **元素的转变**  
> >
> > ｛display：block/inline/inline-block/none｝
>>
> > block：变为块级元素
>>
> > inline：变为内联元素  无高和宽，没有垂直方向的外边距
> >
> > inline-block：变为行内块元素
> >
> > none：隐藏，不占位置
> >
> > ｛visibility：visible/hidden｝ --设置元素显示状态，hidden隐藏并占位
> 
> 2D，3D转换：transform
> 
> > 2D:x，y小写；3D：x，y大写
> 
> 过渡：transition
>
> 动画：animation
>
> 字体属性font-size：1em=16px
> 
> 音频/视频属性
> 
> > ```
> > <audio controls>
> > 	<source src="">
> > 	<embed src="" type="audio/mp3">  --低版本ie
> > </audio>
> > <video controls>
> > 	<source src="">
> > 	<embed src="" type="audio/mp4">
> > </video>
>> ```
> 
>h5新增标签
> 
> > 语义化标签的好处（使结构更加清晰）
> >
> > 长引用：< blockquote>
> >
> > 段引用：< q>
> >
> > < header>、< main>(网页主体，只能有一个)、< footer>
> >
> > nav：导航
> >
> > aside：和主体相关的内容

#### Flex布局

> 可以通过display属性显示给一个元素设置flex(块级元素)和inline-flex（行内元素）
>
> - flex-direction  项目排列方向
>
> > ```css
> > .box {
> >   flex-direction: row | row-reverse | column | column-reverse;
> > }
> > 
> > row（默认值）：主轴为水平方向，起点在左端。
> > row-reverse：主轴为水平方向，起点在右端。
> > column：主轴为垂直方向，起点在上沿。
> > column-reverse：主轴为垂直方向，起点在下沿。
> > ```
>
> - flex-wrap  换行
>
> > ```css
> > .box{
> >   flex-wrap: nowrap | wrap | wrap-reverse;
> > }
> > 
> > nowrap（默认）：不换行。
> > wrap：换行，第一行在上方。
> > wrap-reverse：换行，第一行在下方。
> > ```
>
> - justify-content  对齐方式
>
> > ```css
> > .box {
> >   justify-content: flex-start | flex-end | center | space-between | space-around;
> > }
> > 
> > flex-start（默认值）：左对齐
> > flex-end：右对齐
> > center： 居中
> > space-between：两端对齐，项目之间的间隔都相等。
> > space-around：每个项目两侧的间隔相等。所以，项目之间的间隔比项目与边框的间隔大一倍。
> > ```

#### css加载会造成阻塞吗？

> - css加载不会阻塞DOM树的解析
>
> - css加载会阻塞DOM树的渲染
>
> - css加载会阻塞后面js语句的执行
>
> 避免白屏时间过长，需提高css加载速度，以下提供几种方法：
>
> 1.使用CDN
>
> 2.对css压缩（webpack、gulp）
>
> ##### 浏览器渲染流程：
>
> ​	1.html解析文件，生成DOM树，解析CSS文件生成CSSOM树（DOM解析和CSS解析是两个并行的过程）
>
> ​	2.将DOM 树和CSSOM树结合，生成渲染树
>
> ​	3.根据渲染树 渲染绘制，将像素渲染到屏幕上

#### white-space,word-break,word-wrap

> white-space：控制空白字符的显示，同时还能控制是否自动换行
>
> word-break：控制单词如何被拆分换行
>
> word-wrap：控制长度超过一行的单词是否被拆分