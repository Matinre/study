#### Vue-cli3.0快速搭建项目

> 卸载旧版本vue-cli ：npm uninstall vue-cli -g
>
> 安装新版本：npm install -g @vue/cli 
>
> 搭建新项目：**vue create 搭建新项目**（小写）
>
> 

#### Vue概念

> **MVC**
>
> M:model,只负责数据库的CRUD
>
> V：view，视图层，页面的呈现
>
> C：controller，业务逻辑层，封装逻辑代码，包括分发路由和处理业务
>
> **MVVM**（提供了数据的双向绑定）
>
> M:保存的是每个页面单独的数据
>
> V：就是每个页面中的html结构
>
> VM：调度者，分隔了M和V，每当V层想获取后保存数据的时候，都要由VM做中间的处理

#### 基本代码

> ```js
> <div id="app">  --new的Vue实例会控制这个元素中的所有内容，v
> 	<p>++++{{ msg }}----</P>  --插值表达式
> </div>
> 
> <script>
> //new出来的vm对象就是VM的调度者
> var vm=new Vue({
> 	el:'#app'，  //表示这个实例要控制页面上的哪个区域,V
> 	//这里的data就是M
> 	data:{  //data属性，存放的是el中要用到的数据，
> 		msg:'Hello!'，  //方便把数据渲染到页面上，减少手动操作DOM元素
> 	}，
> 	methods:{  //定义当前Vue实例所有可用的方法
> 		show：function(){
> 			alert('dhfjd');
> 		}
> 	}
> })
> <script>
> ```
>
> 

#### 生命周期

> created：在模板渲染成html前调用（初始化某些属性值，然后再渲染成视图）
>
> mounted：在模板渲染成html后调用（初始完页面后，再对dom节点进行操作）
>
> **数据初始化放到created，及早发送请求获取数据**
>
> **依赖dom必须存在的情况，放到mounted(){this.$nextTick(() => { /* code */ })}里面**

#### 插值表达式、v-text、v-html区别

> **v-cloak**: 解决插值表达式的闪烁问题，可以隐藏未编译的 Mustache 标签直到实例准备完毕
>
> [v-cloak] { display: none }
>
> ```html
> <div v-cloak>
>   {{ message }}  --插值表达式
> </div>
> ```
>
> **v-text**：和插值表达式作用一样，显示绑定内容
>
> **v-cloak和v-text区别**
>
> 1.v-text没有闪烁问题
>
> 2.v-text会覆盖元素中原本的内容，插值表达式会替换自己的这个占位符，不会把整个元素内容清空
>
> **v-html：**里面可含有标签，不会当作普通文本输出

#### v-bind指令（缩写    ：绑定的属性）

> v-bind是提供用于绑定属性的指令
>
> ```html
> <input type='button' value='按钮' v-bind:title="mytitle + ‘123’ ">  --mytitle可在对应控制区域里的data中申明。可后期加入
> ```
>
> v-bind：简写为 ：绑定的属性

#### v-bind绑定class属性

> 1.直接传递一个数组
>
> ```js
> <div v-bind:class="[activeClass, errorClass,flag?'active':''（或者{'active':flag}）]"></div>
> 
> data: {
>   activeClass: 'active',
>   errorClass: 'text-danger',
>   flag:true  --class样式为active
> }
> ```
>
> 2.对象语法
>
> ```js
> <div
>   class="static"
>   v-bind:class="{ active: isActive, 'text-danger': hasError }"
> ></div>
> 
> data: {
>   isActive: true,
>   hasError: false
> }
> ```

#### v-bind绑定style属性

> 1.传递一个数组
>
> ```js
> <div v-bind:style="[baseStyles, overridingStyles]"></div>
> 
> data: {
>   baseStyles: ｛color：‘red’，'font-weight':200｝,
>   overridingStyles: ｛'font-style':'italic'｝
> }
> ```
>
> 2.对象语法
>
> ```js
> <div v-bind:style="{ color: activeColor, fontSize: fontSize + 'px' }"></div>
> 
> data: {
>   activeColor: 'red',
>   fontSize: 30
> }
> ```

#### v-on指令（缩写@）

> v-on绑定事件 click、mouseover
>
> ```html
> <input type='button' value='按钮' v-on:click="show">  --show在对应控制区域里的methods中申明。  加小括号可给函数传参
> ```
>
> **click事件修饰符**
>
> .stop 阻止冒泡，阻止父元素的点击事件
>
> .prevent 阻止默认行为
>
> .capture 从外到里捕获事件
>
> .self 只有点击自己才触发事件
>
> .once 只触发一次
>
> **[按键修饰符](https://cn.vuejs.org/v2/guide/events.html#按键修饰符)（@keyup）**
>
> .enter .tab 等等
>
> 可自定义全局按键修饰符 Vue.config.keyCodes.f2=113;
>
> 可自己定义一个方法

#### v-model(双向绑定)

> v-bind只能进行数据的单向绑定
>
> v-model只能用在表单元素
>
> ```html
> <input type='button' value='按钮' v-model="something">  --something可在对应控制区域里的data中申明
> ```

#### v-for指令

> 在组件中，使用v-for循环的时候，如果v-for有问题，必须使用唯一的key值，
>
> 为每项提供一个唯一 `key` 属性（number | string）：
>
> ```html
> <div v-for="item in items" v-bind:key="item.id">
>   <!-- 内容 -->
> </div>
> ```
>
> 1.把一个数组作为元素
>
> ```html
> <p v-for='item(或者(item,i)) in list'>{{i}}---{{item}}</p>
> 
> data:{
> 	list:[1,2,3,4,5]
> }
> ```
>
> 2.使用对象
>
> ```html
> <div v-for="(value, name, index) in object">
>   {{ index }}. {{ name }}: {{ value }}
> </div>/p>
> 
>  data: {
>     object: {
>       title: 'How to do lists in Vue',
>       author: 'Jane Doe',
>       publishedAt: '2016-04-10'
>     }
>   }
> 
> ```

#### v-if和v-show指令

> v-if:每次重新下创建或者删除元素，有较高的切换性能消耗
>
> v-show:每次不会重新进行DOM的删除和创建操作，只是切换了元素的display：none，有较高的初始渲染消耗
>
> 频繁切换用v-show，元素可能永远不会被显示则推荐v-if

#### [自定义指令](https://cn.vuejs.org/v2/guide/custom-directive.html)

> Vue.directive()定义全局指令
>
> //参数1：指令名称，定义的时候不需要加v-前缀，使用时需要添加
>
> //参数2：一个对象，对象上有一些指令相关的函数，这些函数可以在特定阶段执行相关操作
>
> ```js
> <input v-focus="'blue'">
> 
> //公有指令
> Vue.directive('focus',{
> 	bind:function(e1，binding){  //每当指令绑定到元素上时，会立即执行bind函数，只执行一次
>         //在每个函数中，
>         //第一个参数永远是e1,表示被绑定了指令的那个元素，这个el参数，是一个原生的JS对象，也就是DOM对象
>         e1.focus();
>         //第二个参数是binding，一个对象，可获取指令绑定的值
>         binding.name/value/expression
>         
>         //样式相关的操作，一般可以在bind中执行
>         e1.style.color='red';
> 	},
> 	inserted:function(){  //表示元素插入到DOM中的时候，执行，触发一次
> 		//和js行为有关的操作，最好在inserted中去执行，防止不生效
>         e1.focus();		
> 	},
> 	updated:function(){  //表示vNode组件更新的时候，执行，可触发多次
> 				
> 	},
> })
> 
> 
> //自定义私有指令 过滤器有两个条件（过滤器名称和处理函数）
> directives：｛  
>     'focus'：｛
>     	bind:function(e1，binding){ },
>         inserted:function(){ },
>     ｝
> ｝
> ```
>
> 

#### Vue调试工具vue-devtools

#### 过滤器（就近原则，私有和公有过滤器名称一致时，优先先调用私有）

> **过滤器使用方法：**
>
> ```js
> <!-- 在双花括号中 -->  --可以有多个过滤器，叠加|
> {{ message | capitalize }}
> 
> <!-- 在 `v-bind` 中 -->
> <div v-bind:id="rawId | formatId"></div>
> 
> 
> //过滤器的定义语法
> 
> 1.公有过滤器
> //Vue.filter('过滤器的名称'，function(){})  
> //过滤器中的function，第一个参数永远是  过滤器管道符前面传递过来的数据；后面可有多个参数，参数可以是自己定义的数据
> Vue.filter('过滤器的名称'，function(data,arg1，arg2){
>     
> })
> 
> 2.私有过滤器
> //私有过滤器  过滤器有两个条件（过滤器名称和处理函数）
> filters：｛  
>     dataFormat:function(dataStr,pattern){
>             
>     }
> ｝
> ```
>
> **过滤器的定义语法**
>
> ```js
> //1.公有过滤器
> <div id="app">
>     <p>{{ msg|msgFormat('mm')}}</p>  msgFormat过滤器将msg这个数据传过去 进行操作
> </div>
> //2.私有过滤器
> <div id="app2">
>     <p>{{ msg|dataFormat('mm')}}</p>  
> </div>
> 
> //1.公有过滤器
> Vue.filter('msgFormat'，function(msg,args){  //msg是传过来的原有的数据
>     return msg.replace("aa",args);
> })
> 
> data:{
>     msg:'dd aa  bb aa'
> }
> 
> //2.私有过滤器
> var vm2=new Vue({
> 	el:'#app2'，  
> 	data:{  
> 		msg:'Hello!'，  
> 	}，
> 	methods:{}，
> 	filters：｛  //私有过滤器
>     		dataFormat:function(dataStr,pattern){
>             
>         	}
>     	｝
> })
> ```
>
> 

#### Vue-resource发请求

> **前提**：先导包，由于Vue-resource依赖于Vue，所以要注意先后顺序，先vue.js,后vue-resource.js
>
> **提示**：
>
> 1.可全局配置数据接口的根域名： **Vue.http.option.root="";**  //如果全局配置了根路径，单据发起http请求时，应该以相对路径开头，前面不能带/
>
> 2.｛emulateJSON：true｝可全局配置， **Vue.http.option.emulateJSON=true;** 
>
> ```js
> //发送get请求
> this.$http.get('url').then(function(result){
>     //通过result.body拿到服务器返回的成功数据
> 	console.log(result.body);
> })
> 
> //发送post请求
> //post接收表单格式的提交  即application/x-www-form-urlencoded
> //手动发起的post请求，默认没有表单格式，所以有些服务器处理不了，
> //所以post方法的第三个参数option需要设置 提交的内容类型 为 普通表单数据 即｛emulateJSON：true｝
> this.$http.post('url'，｛data｝，｛emulateJSON：true｝).then(function(result){
>     //通过result.body拿到服务器返回的成功数据
> 	console.log(result.body);
> })
> 
> //发送jsonP请求（用于浏览器的安全性问题，不允许ajax访问协议不同、域名或端口号不同的数据接口，所以通过动态创建script标签，把script标签的src属性，指向数据接口的地址。）
> //实现过程
> //1.现在客户端定义一个回调方法，预定义对数据的操作
> //2.再把这个回调方法的名称，通过url传参的形式，提交给服务器的数据接口
> //3.服务器数据接口组织好要发送给客户端的数据，再拿着客户端传过来的回调方法的名称，拼接成一个调用这个方法的字符串，发送给客户端去解析执行
> //4.客户端拿到服务器返回的字符串之后，当作script脚本去解析执行，这样就拿到了JSONP的数据了
> this.$http.jsonp('url').then(function(result){
> 	console.log(result.body);
> })
> 
> ```
>
> 

#### [Vue动画](https://www.jianshu.com/p/f2d047dc1dc2)

> 1.Vue动画
>
> 2.配合第三方CSS动画库，animate.css
>
> 3.钩子函数
>
> > ```js
> > <div id="example-4">
> > <button @click="show = !show">
> >  Toggle
> > </button>
> > <transition
> >  v-on:before-enter="beforeEnter"
> >  v-on:enter="enter"
> >  v-on:after-enter="afterEnter"
> >   >
> >  <p v-if="show">
> >    Demo
> >  </p>
> > </transition>
> > </div>
> > 
> > new Vue({
> > el: '#example-4',
> > data: {
> >  show: false
> > },
> > methods: {
> >  beforeEnter: function (el) {
> >  	//e1表示要执行动画的DOM元素
> >   	//beforeEnter表示动画入场之前，此时，动画尚未开始
> >      //可设置元素在开始动画之前的起始样式
> >  },
> >  enter: function (el, done) {
> >   	//表示动画开始之后的样式，
> >      //可以设置完成动画之后的 结束状态
> >      
> >      //这句话没有实际作用 如果不写，出不来动画效果
> >      e1.offsetWidth；
> >      //设置位移
> >      e1.style.transform="translate(150px,450px)";
> >      //设置过渡属性
> >      e1.style.transition='all 1s ease';
> >      
> >      //done函数就是afterEnter函数的引用
> >      done();
> >  },
> >  afterEnter: function (el) {
> >    	//动画完成之后调用
> >  }
> > }
> > })
> > ```
> >
>
> 列表的过渡
>
> > 一般会设置move ，它会在元素的改变定位的过程中应用
> >
> > //v-move和v-leave-active配合使用，能够实现列表后续元素渐渐飘上来
> >
> > .v-move{  transition：all 0.6s ease };
> >
> > .v-leave-active{ position:absolute }

#### 组件

> 模块化：从代码逻辑的角度进行划分，方便代码分层开发，保证每个功能模块的职能单一
>
> 组件化：从UI界面的角度进行划分，前端的组件化，方便UI组件的重用
>
> **创建组件的三种方式**
>
> + 使用extend
>
> ```js
> //组件名称使用了驼峰，则在引用组件的时候，需要将大写改成-
> <my-com1></my-com1>
> 
> //使用Vue.extend来创建全局的vue组件
> var com1= Vue.extend({
> //template指向的模板内容，必须只能有一个根元素
> template:'<h3>ahdjhdjs</h3>'  //指定组件要展示的html结构
> })
> //使用vue.component('组件名称',创建出来的组件模版对象)
> //第一个参数：组件名称，就是将来在引用组件的时候，以一个标签形式来引入
> //第二个参数：vue.extend创建的组件
> Vue.component('myCom1',com1);
> ```
>
> + 直接使用component
>
> ```js
> <my-com1></my-com1>
> 
> Vue.component('myCom1',{
> template:'<h3>ahdjhdjs</h3>'  //指定组件要展示的html结构
> });
> ```
>
> + 定义id（推荐）
>
> ```html
> <my-com1></my-com1>
> 
> <template id="tmp1">
> <div>
> 	<h1>dfsdg</h1>
> 	    <span>fgfdg</span>
> </div>
> </template>    
> 
> <script>
> Vue.component('myCom1',{
> 		template:'#tmp1'，  //指定模版id
>    //组件中的data必须是一个方法，还必须返回一个对象
>    //组件中的data 使用方式和实例中的data一样
> 	data:function(){  
>  		return {}
> 		}
> 	});	
> </script>
> ```
>
> **私有组件**
>
> ```js
> components:{  //定义私有组件
> 	login:{
> 		template:'<h1>dfsdg</h1>j'  //template:'#tmp1'  //指定模版id
> 	}
> }
> ```
>
> **组件的切换** 
>
> 通过 Vue 的 `<component>` 元素加一个特殊的 `is` attribute 来实现
>
> ```js
> <div>
> <a href="" @click.prevent="comName='login'">登录</a>
> 	<a href="" @click.prevent="comName='register'">注册</a>
> 	
> 	//comName是要展示的组件的名称
> 	<component :is="comName"></component>
> </div>
> 
> Vue.component('login',{
> template:'<h3>登录组件</h3>'
> })
> Vue.component('register',{
> template:'<h3>注册组件</h3>'
> })
> 
> data:{
> comName:''
> }
> ```
>
> **父子组件传值**
>
> > ```js
> > //1.子组件使用父组件的值
> > //父组件通过属性绑定的方式，将数据传入子组件内部
> > //子组件通过props数组来接收父组件的值
> > 
> > //2.子组件使用父组件的方法，父组件向子组件传值
> > //父组件通过事件绑定，将方法传给子组件
> > //子组件通过this.$emit（）来触发，也可传值给父组件
> > <div id='app'>
> >     //parentmsg是自定义属性
> >     <com1 v-bind:parentmsg="msg"></com1>
> > 	//func是自定义属性
> > 	//show如果带（），说明是先执行方法后再将结果返回，
> > 	<com2 @func="show"></com2>
> > </div>
> > 
> > <template id="tmp1">
> >     <div>
> >     	<h1>这是子组件</h1>
> > 		<input type="button" value="按钮" @click="myclick">
> >     </div>
> > </template>       
> > 
> > var vm=new Vue({
> >     el:'#app',
> >     data:{
> >         msg:'父组件的数据'
> >     },
> >     methods:{
> >         show（data）{
> >         	console.log('父组件的show方法'+data)
> >    		}
> >     },
> >     components:{
> >         com1:{
> >             template:'<h1>这是子组件{{parentmsg}}</h1>'，
> >             //父组件传递过来的属性，先在props数组中定义一下，才能使用
> >             //数组中所有props中的数据，都是通过父组件传递给子组件的
> >             //props数据只读，不能修改
> >             props:["parentmsg"],  
> >        		//子组件中的data数据是子组件本身私有的
> >         	data(){
> >     			return{
> >     				title:'123'
> > 				}
> > 			}
> > 	   },
> >         com2:{
> >             template:'#tmp1'，
> >             data(){
> >                 return{ sonmsg:{name:'123' age:6} }
> >             }
> >             methods:{
> >                 myclick(){
> >                     //当子组件的按钮点击时，通过$emit来触发父组件传过来的方法
> >                     //后面可跟参数，然后给父组件传参
> >                     this.$emit('func'，this.sonmsg)
> >                 }
> >             }
> >         }
> >     }
> > })
> > ```
> >
>
> #### [vue父组件异步数据子组件接收](https://www.cnblogs.com/liujingjing/p/10737285.html)
>
> https://www.cnblogs.com/liujingjing/p/10737285.html
>
> 子组件用wach，并且加上deep属性，可以直接在handler里面传入在子组件定义好的方法；
>
> watch:{
>
> ​	XXX:{deep:true,handler:function(){ 需要调用的方法}}
>
> }

#### ref获取DOM元素和组件引用

> ref指向DOM元素
>
> ```
> <p ref="p">hello</p>
> 
> this.$refs.p.innerText
> ```
>
> 

#### vue-router的使用

> ```js
> <div>
>      //1. 跳转
>      <a href="#/login">登陆</a>
>      //这是vue-router提供的元素，专门用来当做占位符，
>      //将来路由规则，匹配到的组件，就会展示到这个router-view
>      <router-view></router-view>
> 
> 
>  	//2.router-link默认渲染为一个a标签
> 	//可带参数  1.query传参?id=10&name=22 或者  2.params传参/12
> 	<router-link to="/login?id=10" tag='span'>登陆</router-link>
> 	<router-view></router-view>	
> </div>
> 
> 
> var login={
>     //params传参时 {{$route.params.id}}
>  	template:'<h1>登录组件---{{$route.query.id}}</h1>',
>     data(){
>         return{
>             msg:'123'
>         }
>     }
>     created(){
>         console.log(this.$route.query.id)
>     }
> }
> 
> //构造函数，传递一个配置对象
> var routerObj=new VueRouter({
> 	routes:[  //路由匹配规则
>      	 {path:'/',redirect:'/login'}, //默认为去/login
>      
> 		//component的属性值，必须是一个组件的模版对象，不能是组件的引用名称
>         //params传参时 /login/:id/:name
> 		{path:'/login',component:login}
> 	]，
> 	linkActiveClass:'myactive'  //自己定义高亮类型
> })
> 
> var vm=new Vue({
>      el:'#app',
>      data:{},
>      methods:{},
>      router:routerObj  //将路由规则对象，注册到vm实例上，用来监听URL地址变化，然后展示对应的组件 
> })
> ```
>
> 路由嵌套
>
> ```js
> <div>
> 	<router-view></router-view>	
> </div>
> 
> <template>
>     <div>
>     	<h1> Account组件 </h1>
> 		<router-link to="/account/login"></router-link>
> 		<router-view></router-view>	
>     </div>
> </template>    
> 
> var account={
>  	template:'#tmp1'
> }
> var login={
>  	template:'<h1>登录组件</h1>'
> }
> 
> //构造函数，传递一个配置对象
> var routerObj=new VueRouter({
> 	routes:[  
> 		{
>             path:'/account',
>             component:account,
>             children:[
>                 {path:'login',component:login}
>             ]
>         }
> 	]，
> 	linkActiveClass:'myactive'  //自己定义高亮类型
> })
> 
> var vm=new Vue({
>      el:'#app',
>      data:{},
>      methods:{},
>      router:routerObj  //将路由规则对象，注册到vm实例上，用来监听URL地址变化，然后展示对应的组件 
> })
> ```
>
> 命名视图
>
> ```js
> <router-view class="view one"></router-view>
> //放置对应名字的组件 
> <router-view class="view two" name="a"></router-view>
> <router-view class="view three" name="b"></router-view>
> 
> const router = new VueRouter({
>   routes: [
>     {
>       path: '/',
>       components: {
>         default: Foo,
>         a: Bar,
>         b: Baz
>       }
>     }
>   ]
> })
> ```
>
> 

#### watch监听（适合监听虚拟的东西）

> ```js
> var vm=new Vue({
>      el:'#app',
>      data:{
>          firstname:'',  //v-model绑定数据
>          lastname:'',
>          fullname:''
>      },
>      methods:{},
>    	 watch:{
>          'firstname':function(newVal,oldVal){
>              this.fullname=this.firstname+'-'+this.lastname;
>          }
>          '$route.path' //可监听路由地址的改变
>      } 
> })
> 
> ```
>
> 

#### computed计算属性（当作普通数据去使用）

> ```js
> var vm=new Vue({
>      el:'#app',
>      data:{
>          firstname:'',  //v-model绑定数据
>          lastname:''
>      },
>      methods:{},
>    	 computed:{
>          //计算属性 ，在引用的时候，直接把他当作普通属性去调用
>          //只要计算属性，这个function内部，所用到的任何data中的数据发生了变化，就会重新计算
>          //求值结果会被缓存起来，方便下次使用
>          'fullname':function(){
>              return this.firstname+this.lastname;
>          }
>      }
> })
> 
> ```
>
> 

#### 插槽（slot和slot-scope）

> 单个（默认）插槽，不设name值
>
> ```html
> <!-- 父组件 -->
> <template>
>     <div>
>         <h3>我是一个父组件</h3>
>         <!--显示子组件，在child组件写入一个HTML模板，该模板会替换子组件的slot-->
>         <child>
>             <div>
>                 aaa
>             </div>
>         </child>
>     </div>
> </template>
> 
> <!-- 子组件 -->
> <template>
>     <div>
>         <h5>我是子组件</h5>
>         <slot></slot>
>     </div>
> </template>
> 
> <!-- 在上面例子中，父组件在<child></child>里面写了html模板，子组件的slot会被该模板覆盖掉！也可以说子组件的插槽被使用了，最终会是下面这个样子 -->
> <div>
>         <h3>我是一个父组件</h3>
>         <div>
>             <h5>我是子组件</h5>
>             <div>
>                 aaa
>             </div>
>         </div>
>  </div>
> ```
>
> 具名插槽
>
> ```html
> <!-- 父组件 -->
> <template>
>     <div>
>         <h3>我是一个父组件</h3>
>         <!--显示子组件-->
>         <child>
>             <div slot="zhang">老张</div>
>             <div slot="wang">老王</div>
>             <div>老李</div>
>         </child>
>     </div>
> </template>
> 
> <!-- 子组件 -->
> <template>
>     <div>
>         <h5>我是子组件</h5>
>         <!--具名插槽-->
>         <slot name="zhang"></slot>
>         <!--具名插槽-->  
>         <slot name="wang"></slot>
>         <!--匿名插槽-->
>         <slot></slot>
>     </div>
> </template>
> 
> <!-- 最终渲染的结果 -->
> <div>
>     <h3>我是一个父组件</h3>
>     <!--显示子组件-->
>     <div>
>         <h5>我是子组件</h5>
>         <div>老张</div>
>         <div>老王</div>
>         <div>老李</div>
>     </div>
> </div>
> ```
>
> 作用域插槽，slot绑定数据
>
> ```html
> <!-- 父组件 -->
> <template>
>     <div>
>         <h3>我是一个父组件</h3>
>         <!--显示子组件-->
>         <child>
>             <template slot="zhang" slot-scope="item">
>                 <div  v-for="sex in item.data">
>                     <p>{{sex}}</p>
>                 </div>
>             </template>
>         </child>
>     </div>
> </template>
> 
> <!-- 子组件 -->
> <template>
>     <div>
>         <h5>我是子组件</h5>
>         <slot name="zhang" :data="sexArr"></slot>
>     </div>
> </template>
> 
> <script>
>     export default {
>         name: "child",
>         data(){
>             return {
>                 sexArr:["男","女"]
>             }
>         }
>     }
> </script>
> ```
>
> 

#### VueX

> - state 存放状态
>
> - mutations state成员操作
>
> - getters 加工state成员给外界
>
> - actions 异步操作
>
> - modules 模块化状态管理
>
> ##### 1.mutations
>
> > 操作state数据的方法集合
> >
> > 默认参数  state（当前VueX对象中的state） ，payload（可选，被调用时传递参数）
> >
> > ```js
> > import Vue from 'vue'
> > import Vuex from 'vuex'
> > 
> > Vue.use(Vuex)
> > 
> > const store = new Vuex.store({
> >     state:{
> >         name:'helloVueX'
> >     },
> >     mutations:{
> >         //es6语法，等同edit:funcion(){...}
> >         edit(state){
> >             state.name = 'jack'
> >         }
> >     }
> > })
> > 
> > export default store
> > 
> > 
> > 
> > //组件调用
> > this.$store.commit('edit',{age:15,sex:'男'})
> > ```
>
> ##### 2.增删state中的成员
>
> > Vue.set 为某个对象设置成员的值，若不存在则新增
> >
> > 例如对state对象中添加一个age成员
> >
> > ```js
> > Vue.set(state,"age",15)
> > ```
> >
> > Vue.delete 删除成员
> >
> > 将刚刚添加的age成员删除
> >
> > ```js
> > Vue.delete(state,'age')
> > ```
> >
> > 
>
> ##### 3.Getters
>
> > 将成员传递给外界
> >
> > 默认参数：state，getters（当前getters对象）
> >
> > ```js
> > getters:{
> >     nameInfo(state){
> >         return "姓名:"+state.name
> >     },
> >     fullInfo(state,getters){
> >         return getters.nameInfo+'年龄:'+state.age
> >     }  
> > }
> > 
> > //组件中调用
> > this.$store.getters.fullInfo
> > ```
>
> ##### 4.Actions
>
> > 异步操作，最终提交mutation方法
> >
> > 默认参数：context（上下文对象） payload（挂载参数）
> >
> > ```js
> > actions:{
> >     aEdit(context,payload){
> >         return new Promise((resolve,reject)=>{
> >             setTimeout(()=>{
> >                 context.commit('edit',payload)
> >                 resolve()
> >             },2000)
> >         })
> >     }
> > }
> > 
> > //组件中调用
> > this.$store.dispatch('aEdit',{age:15})
> > ```
>
> ##### 5.Models
>
> > 每个模块都有自己的state,mutation,action,getter
> >
> > ```js
> > const moduleA = {
> >   state: () => ({ ... }),
> >   mutations: { ... },
> >   actions: { ... },
> >   getters: { ... }
> > }
> > 
> > const moduleB = {
> >   state: () => ({ ... }),
> >   mutations: { ... },
> >   actions: { ... }
> > }
> > 
> > const store = new Vuex.Store({
> >   modules: {
> >     a: moduleA,
> >     b: moduleB
> >   }
> > })
> > 
> > store.state.a // -> moduleA 的状态
> > store.state.b // -> moduleB 的状态
> > ```

#### this.$set(target,key,value)

> - target：要更改的数据源
> - key：要更改的数据（要添加的属性）
> - value：重新要赋的值
>
> ##### 应用场景
>
> ​	需要为对象添加一个新属性时

#### this.$nextTick(async () => { })

> 修改数据之后立即使用这个方法，获取更新后的 DOM。
>
> 即修改数据后没有立即渲染DOM；若需要使用这个DOM节点，则需要套用此方法，获取的是更新后的DOM

#### Vue router 传参

> params传参：
>
> ​	/router1/:id
>
> ​	**当你使用params方法传参的时候，要在路由后面加参数名**
>
> ##### 	  params 传参，push 里面只能是 name:'xxx'，不能是 path:'/xxx'，因为 params 只能用 name 来引入路由，如果这里写成了 path ，接收参数页面会是 undefined。
>
> query：/router1?id=123
>
> ```js
> //router.js
> {
>         path: 'server/create/:id',
>         component: () => import('@/views/deploy/servers/createServer.vue'),
>         name: 'CreateServer'
> }
> 
> //跳转页面
> this.$router.push({
>           name: 'CreateServer',
>           params: {
>             id: row.id
>           },
>           query: {
>             module: 'pending_server',
>             os_type: row.os_type,
>             address: row.address,
>             port: row.staging_port
>           }
> });
> 
> //目标页面通过this.$route.params获取参数
> this.$route.params.alert
> this.$route.query.alert
> ```
>
> 