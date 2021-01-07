#### 变量申明

> 通过$申明  
>
> ```scss
> $highlight-color: #F90;
> .selected {
>   border: 1px solid $highlight-color;
> }
> 
> //编译后
> .selected {
>   border: 1px solid #F90;
> }
> ```
>
> 

#### 嵌套规则

> ```scss
> #content {
>   article {
>     h1 { color: #333 }
>     p { margin-bottom: 1.4em }
>   }
>   aside { background-color: #EEE }
> }
> 
> /* 编译后 */
> #content article h1 { color: #333 }
> #content article p { margin-bottom: 1.4em }
> #content aside { background-color: #EEE }
> ```

#### 父选择器的标识符&

> ```scss
> article a {
>   color: blue;
>   &:hover { color: red }
> }
> 
> /* 编译后 */
> article a { color: blue }
> article a:hover { color: red }
> 
> /* 若不加&  意味着article a下的所有子元素在hover时变红*/
> article a :hover { color: red }
> ```

#### 子组合选择器和同层组合选择器：>、+和~

> 子组合选择器>选择一个元素的直接子元素
>
> 同层相邻组合选择器`+`选择一个元素的后紧跟的元素
>
> 同层全体组合选择器`~`不管它们之间隔了多少其他元素,选择跟在一个元素的同层的元素
>
> 在下例中，你可以用同层相邻组合选择器`+`选择`header`元素后紧跟的`p`元素：
>
> ```scss
> header + p { font-size: 1.1em }
> ```
>
> 你也可以用同层全体组合选择器`~`，选择所有跟在`article`后的同层`article`元素，不管它们之间隔了多少其他元素：
>
> ```scss
> article ~ article { border-top: 1px dashed #ccc }
> ```
>
> 这些组合选择器可以毫不费力地应用到`sass`的规则嵌套中。可以把它们放在外层选择器后边，或里层选择器前边：
>
> ```scss
> article {
>   ~ article { border-top: 1px dashed #ccc }
>   > section { background: #eee }
>   dl > {
>     dt { color: #333 }
>     dd { color: #555 }
>   }
>   nav + & { margin-top: 0 }
> }
> ```
>
> `sass`会如你所愿地将这些嵌套规则一一解开组合在一起：
>
> ```scss
> article ~ article { border-top: 1px dashed #ccc }
> article > footer { background: #eee }
> article dl > dt { color: #333 }
> article dl > dd { color: #555 }
> nav + article { margin-top: 0 }
> ```

#### 嵌套属性

> 把属性名从中划线-的地方断开，在根属性后边添加一个冒号:，紧跟一个`{ }`块，把子属性部分写在这个`{ }`块中
>
> ```scss
> nav {
>   border: {
>   style: solid;
>   width: 1px;
>   color: #ccc;
>   }
> }
> 
> //
> nav {
>   border-style: solid;
>   border-width: 1px;
>   border-color: #ccc;
> }
> ```

