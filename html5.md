#### HTML属性

> ##### 常用的标签属性：
>
> > <h>标签:字体大小，align对齐方式
> >
> > <body>标签：bgcolor背景颜色
> >
> > <a>标签：超链接，target规定在何处打开链接，href链接地址，title提示文本
> >
> > ​          href=‘#’或者href=“javascript：；”都代表链接地址为空
> >
> > ​		 target=“  _ blank” --新窗口打开链接  ；target=“_self” --当前窗口打开链接 （默认）
> >
> > <img>标签：插入图片，src图片路径，title图片标题，alt图片替换文本
> >
> > ​          href=‘#’或者href=“javascript：；”都代表链接地址为空
> >
> > ​		 target=“  _ blank” --新窗口打开链接  ；target=“_self” --当前窗口打开链接 （默认）
> >
> > < p>标签：段落标签，默认情况段落于段落之间有间距
> >
> > < em>：倾斜标签
> >
> > < strong>:加粗标签
> >
> >  < br />:换行标签
> >
> > < hr />:做水平线
> >
> > 特殊符号：&nbsp；（空格）& gt;（>）& lt;（<）
>
> ##### 通用属性
>
> > class：规定元素的类名
> >
> > id：规定元素唯一ID
> >
> > style：规定元素的样式
> >
> > title：规定元素的额外信息
>
> ##### HTML样式
>
> > <link>：资源引用；rel：外部样式表 type=“text/css”：引入文档的类型
> >
> > 外部样式表：
> >
> > ```html
> > <link rel="stylesheet" type="text/css" href="mystyle.css">
> > ```
> >
> > 内部样式表：
> >
> > ```html
> >    <style type="text/css">
> >         body {
> >         background: aquamarine
> >          }
> >         p {
> >         margin-left: 20px
> >         }
> >     </style>
> > ```
> >
> > 内联样式表：
> >
> > ```html
> > <p style="color:red">
> > ```
>
> ##### 表格
>
> > ```html
> > <table>
> >         <caption>重要表格</caption>
> >         <tr>
> >             <th>单元</th>
> >             <th>单元</th>
> >             <th>单元</th>
> >             <th>单元</th>
> >         </tr>
> >         <tr>
> >             <td>内容</td>
> >             <td>内容</td>
> >             <td>内容</td>
> >             <td>内容</td>
> >         </tr>
> >     </table>
> > ```
> >
> > <th>表头，<td>单元格
>
> ##### 列表
>
> > ```html
> > <ul>  --无序
> >     <li>XX</li>
> >     <li>XX</li>
> >     <li>XX</li>
> > </ul>
> > <ol type='' start=''>  --有序
> >     <li>XX</li>
> >     <li>XX</li>
> >     <li>XX</li>
> > </ol>
> > <dl>  --自定义列表
> >     <dt>名词</dt>
> >         <dd>解释</dd>
> >    </dl>
> >    ```
> >    ul，无序；
> >    
> > ol，有序；
> > 
> > dl，dt，dd，自定义
>
> ##### 表单
>
> > <input type="">
> >
> > > checkbox:**复选框**
> > >
> > > radio:**单选框**
> > >
> > > button:**按钮**
> > >
> > > submit:**提交**
> >
> > **下拉列表**
> >
> > <select>
> >     <option>1</option>
> >     <option>2</option>
> >     <option>3</option>
> > </select>
> >
> > **文本域**
> >
> > <textarea cols="10" rows="2">
> >     文本域信息
> > </textarea>
> >
> > 表单内的属性
> >
> > > formaction:可以分别提供动作
> > >
> > > required：若为空不能提交，会提示信息
> > >
> > > placeholder：文本框未输入时显示的文字信息
> > >
> > > list：为单行文本框增加一个list属性，该属性的值为某个datalist元素的id，允许用户自己输入。
> > >
> > > > ```html
> > > > <form>    
> > > >     <input type="text" list="data"/>    
> > > >     <datalist id="data">        
> > > >         <option value="apple">apple</option>       
> > > >         <option value="pear">pear</option>        
> > > >         <option value="orange">orange</option>    </datalist>
> > > > </form>
> > > > ```
> > >
> > > pattern:设置文本框要符合的正则表达式
>
> ##### 背景
>
> > backgroud：设置背景图片
> >
> > bgcolor：设置颜色
>
> ##### 实体（在html中可能有些关键字符不能显示出来，通过实体来表现）
>
> > <的实体是&lt；>的实体是&gt；具体的某些实体可以baidu

#### HTML5

> ```
> <!DOCTYPE html>  --命名文档类型HTML5
> <html>  --说明我们写的是标记语言 html文档
> <head>  --文件头部（描述区）
> <meta charset="utf-8" name='keywords(关键字)' content=''>  --元数据，用来让搜索引擎来给你进行分类
> <title>XXX</title>  --网页标题
> </head>
> <body>  --网页主题
> </body>
> </html>
> ```
>
> 

#### 常见post提交数据方式对应的content-type取值

> 1)`application/x-www-form-urlencoded`:数据被编码为名称/值对,这是标准的编码格式。提交的数据按照 key1=val1&key2=val2 的方式进行编码，key 和 val 都进行了 URL 转码
>
> > POST http://www.example.com HTTP/1.1 
> > Content-Type: application/x-www-form-urlencoded;charset=utf-8 
> >
> > title=test&sub%5B%5D=1&sub%5B%5D=2&sub%5B%5D=3 
>
>  2)`multipart/form-data`:数据被编码为一条消息，页上的每个控件对应消息中的一个部分。
>
>  3)`application/json`:告诉服务端消息主体是序列化后的 `JSON`字符串. 
>
> > POST http://www.example.com HTTP/1.1 
> > Content-Type: application/json;charset=utf-8 
> >
> > {"title":"test","sub":[1,2,3]}   
>
>  4）`text/xml

#### 浏览器缓存机制

> - 强制缓存：当所请求的数据在缓存数据库中尚未过期时，不与服务器进行交互，直接使用缓存数据库中的数据。 `Expire / Cache-Control`
>
> 
>
> - 对比缓存：协商缓存：从缓存数据库中取出缓存的标识，然后向浏览器发送请求验证请求的数据是否已经更新，如果已更新则返回新的数据，若未更新则使用缓存数据库中的缓存数据。 `etag / last-modifield`
>
> **总结**
>
> 1.`HTTP`缓存机制分为**强制缓存**和**协商缓存**两类。
>
> 2.**强制缓存**的意思就是不要问了(不发起请求)，直接用缓存吧。
>
> 3.**强制缓存**常见技术有`Expires`和`Cache-Control`。
>
> 4.`Expires`的值是一个时间，表示这个时间前缓存都有效，都不需要发起请求。
>
> 5.`Cache-Control`有很多属性值，常用属性`max-age`设置了缓存有效的时间长度，单位为`秒`，这个时间没到，都不用发起请求。
>
> 6.`immutable`也是`Cache-Control`的一个属性，表示这个资源这辈子都不用再请求了，但是他兼容性不好，`Cache-Control`其他属性可以参考[MDN的文档](https://developer.mozilla.org/zh-CN/docs/Web/HTTP/Headers/Cache-Control)。
>
> 7.`Cache-Control`的`max-age`优先级比`Expires`高。
>
> 8.**协商缓存**常见技术有`ETag`和`Last-Modified`。
>
> 9.`ETag`其实就是给资源算一个`hash`值或者版本号，对应的常用`request header`为`If-None-Match`。
>
> 10.`Last-Modified`其实就是加上资源修改的时间，对应的常用`request header`为`If-Modified-Since`，精度为`秒`。
>
> 11.`ETag`每次修改都会改变，而`Last-Modified`的精度只到`秒`，所以`ETag`更准确，优先级更高，但是需要计算，所以服务端开销更大。
>
> 12.**强制缓存**和**协商缓存**都存在的情况下，先判断**强制缓存**是否生效，如果生效，不用发起请求，直接用缓存。如果**强制缓存**不生效再发起请求判断**协商缓存**。
>
> 