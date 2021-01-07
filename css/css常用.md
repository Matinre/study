### 水平居中

> ```css
> /* 父元素*/
> .container {
>   display: grid;
>   justify-content: center;
>   align-content: center;
> }
> .container {
>   display: grid;
>   justify-content: center;
>   align-items: center;
> }
> .container {
>   display: grid;
>   justify-items: center;
>   align-content: center;
> }
> .container {
>   display: grid;
>   justify-items: center;
>   align-items: center;
> }
> ```

### 左侧固定300px，右侧自适应布局

> ```css
> .container
>   .left
>   .main
> 
> .container {
>   display: flex;
> }
> 
> .left {
>     /* flex-basis: 定义了在分配多余空间之前，项目占据的主轴空间 */
>   flex-basis: 300px;
>     /* flex-shrink: 定义了项目的缩小比例，默认为1，即如果空间不足，该项目将缩小*/
>   flex-shrink: 0;  /* 防止 .main 区域过大挤压 .left 区域 */
> }
> 
> .main {
>     /*flex-grow 分配空间，属性定义项目的放大比例，默认为0，即如果存在剩余空间，也不放大。*/
>   flex-grow: 1;
> }
> ```

### 左右固定，中间自适应

> ```pug
> .container
>   .left
>   .main
>   .right
> .container {
>   display: flex;
> }
> 
> .left {
>   flex-basis: 300px;
>   flex-shrink: 0;
> }
> 
> .right {
>   flex-basis: 300px;
>   flex-shrink: 0;
> }
> 
> .main {
>   flex-grow: 1;
> }
> ```

### 绘制三角形

> ```css
> .container
>   .left
>   .main
>   .right
> 
> 
> .container {
>   display: flex;
> }
> 
> .left {
>   flex-basis: 300px;
>   flex-shrink: 0;
> }
> 
> .right {
>   flex-basis: 300px;
>   flex-shrink: 0;
> }
> 
> .main {
>   flex-grow: 1;
> }
> ```
>
> 