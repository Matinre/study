> DOM
>
> > HTML输出流（绝对不能在文档加载完成之后使用，不然会覆盖文档）
> >
> > > document.write("");	
> >
> > 寻找元素
> >
> > > document.getElementById("id名")；
> > >
> > > document.getElementsByTagName("元素名比如p");	//相同元素找第一个
> >
> > 改变内容
> >
> > > document.getElementById("id名").innerHTML=值	//将新值传入
> >
> > 改变属性
> >
> > > document.getElementById("id名").href=“值”	//改变href的属性
> >
> > document.getElementById("id名").value	//取到该id的值
>
> 注释：// 单行注释	/* 多行注释 */
>
> 变量
>
> > 字符串：var str="hello";
> >
> > 数字：var num=2;
> >
> > 布尔值：var flag=true;
> >
> > 数组：var arr=[1,2,3,4];	var arr=new Array("hello","like");
>
> 运算符
>
> > ==，只是比较值；
> >
> > ===，比较类型
> >
> > 逻辑运算符：&&，||，！
> >
> > 三元运算符：判断条件？符合：不符合
>
> 全局变量和局部变量
>
> > ```
> > <script>
> > 	var n=10;m=10	//都是全局变量
> > 	function demo(){
> > 		var i=10;	//局部变量
> > 		x=10;	//全局变量，但是一定是在demo方法执行之后才可以在外部取到它的值
> > 	}
> > </script>
> > ```
>
> 异常
>
> > ```
> > try{
> > 	var e=document.getElementById("id名").value;
> > 	if(e==""){
> > 		throw "请输入";	//自定义异常
> > 	}
> > }catch(err){
> > 	alert(err);		//弹出请输入
> > }
> > ```
> >
> > 