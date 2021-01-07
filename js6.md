## 概念

#### js事件循环机制

> JavaScript的事件分为两种，宏任务（macro-task）和微任务（micro-task）
>
> - **宏任务**：包括整体代码script，setTimeout()，setInterval()
> - **微任务**：Promise.then(非new Promise)、process.nextTick
>
> 事件执行顺序：先执行宏任务，然后执行微任务。 **宏任务 => 微任务的Event Queue => 宏任务的Event Queue**
>
> 任务可以有同步任务和异步任务，同步的进入主线程，异步的进入Event Table并注册函数，异步事件完成后，会将回调函数放入Event Queue（宏任务和微任务是不同的Event Queue），同步任务执行完成后，会从Event Queue中读取事件放入主线程执行，回调函数可能还包含不同的任务，因此会循环执行上述操作。
>
> 
>
> 



#### 重复repeat(n)

> 返回一个新的字符串，原字符串重复n次

#### 字符串中找到符合条件的数据includes(), startsWith(), endsWith()

> includes('',n)，返回布尔值，表示是否找到了参数字符串。从第`n`个位置直到字符串结束
>
> startsWith('',n),返回布尔值，表示参数字符串是否在原字符串的头部。从第`n`个位置直到字符串结束
>
> endsWith('',n)：返回布尔值，表示参数字符串是否在原字符串的尾部。针对前`n`个字符

#### at()

> 返回字符串给定位置的字符

#### 补全长度padStart()，padEnd()

> 补全长度
>
> padStart(n,'')，n指定字符串的长度，‘’表示用来补全的字符串
>
> eg.
>
> ```js
> '123456'.padStart(10, '0') // "0000123456"
> '12'.padStart(10, 'YYYY-MM-DD') // "YYYY-MM-12"
> '09-12'.padStart(10, 'YYYY-MM-DD') // "YYYY-09-12"
> ```

#### 模板字符串  反引号``

> 可以当作普通字符串，定义多行字符串，嵌入变量
>
> eg.
>
> ```js
> // 普通字符串
> `In JavaScript '\n' is a line-feed.`
> 
> // 多行字符串
> `In JavaScript this is
>  not legal.`
> 
> console.log(`string text line 1
> string text line 2`);
> 
> // 字符串中嵌入变量
> let name = "Bob", time = "today";
> `Hello ${name}, how are you ${time}?`
> ```

#### 解析数据Number.parseInt(), Number.parseFloat() （解析int，float）

> - ES6 将全局方法`parseInt()`和`parseFloat()`，移植到`Number`对象上面，行为完全保持不变。
>
> - Number.isInteger()用来判断一个数值是否为整数。
>
> - Number.EPSILON代表极小的常量，Number.EPSILON 为 Math.pow(2, -52)
>
>   Number.EPSILON * Math.pow(2, 2)即如果两个浮点数的差小于这个值，我们就认为这两个浮点数相等。

#### Math对象方法

> - Math.trunc()用于去除一个数的小数部分，返回整数部分。
>
> - Math.sign方法用来判断一个数到底是正数、负数、还是零。对于非数值，会先将其转换为数值。
>
>     它会返回五种值。
>
>     1.参数为正数，返回`+1`；
>
>     2.参数为负数，返回`-1`；
>
>     3.参数为 0，返回`0`；
>
>     4.参数为-0，返回`-0`;
>
>     5.其他值，返回`NaN`。
>
> - Math.cbrt方法用于计算一个数的立方根。
>
> - 指数运算符（`**`）   Math.pow（）
>
>   ```js
>   let b = 4;
>   b **= 3;
>   // 等同于 b = b * b * b;
>   ```
>
> - 

#### 扩展运算符（...）

> 将一个数组转为用逗号分隔的参数序列
>
> ```js
> console.log(1, ...[2, 3, 4], 5)
> // 1 2 3 4 5
> 
> 
> //扩展运算符还可以将字符串转为真正的数组。
> [...'hello']
> // [ "h", "e", "l", "l", "o" ]
> ```

#### 复制数组

> 不会对原有的数组造成影响，直接等于的话相当于是赋予地址，对其操作会影响到原数组
>
> ```js
> const a1 = [1, 2];
> // 写法一
> const a2 = [...a1];
> // 写法二
> const [...a2] = a1;
> ```

#### 数组判断Array.isArray()

> `Array.isArray()`方法用于确定传递的值是否是一个`Array`
>
> ```js
>  Array.isArray([]) => true;
>  Array.isArray({}) => false;
> ```

#### 数组转化Array.from和Array.of()

> Array.from()：将类似数组的对象或者可遍历的对象（Set和Map）转为数组
>
> Array.of()：将一组值转换为数组
>
> ```js
> let arrayLike = {
>     '0': 'a',
>     '1': 'b',
>     '2': 'c',
>     length: 3
> };
> 
> // ES6的写法
> let arr2 = Array.from(arrayLike); // ['a', 'b', 'c']
> 
> Array.of(3, 11, 8) // [3,11,8]
> ```

#### 数组遍历方法 entries()，keys() 和 values()

> 可以用`for...of`循环进行遍历，唯一的区别是`keys()`是对键名的遍历、`values()`是对键值的遍历，`entries()`是对键值对的遍历。
>
> ```js
> for (let index of ['a', 'b'].keys()) {
>   console.log(index);
> }
> // 0
> // 1
> 
> for (let elem of ['a', 'b'].values()) {
>   console.log(elem);
> }
> // 'a'
> // 'b'
> 
> for (let [index, elem] of ['a', 'b'].entries()) {
>   console.log(index, elem);
> }
> // 0 "a"
> // 1 "b"
> ```

#### 数组方法

> **every**(function(item){return item>2})：查询是否每一项都满足某一条件  Boolean
>
> **some()**：有符合条件的，就返回true  Boolean
>
> > ```js
> > const isBiggerThan10 = (element, index, array) => {
> >   return element > 10;
> > }
> > 
> > [2, 5, 8, 1, 4].some(isBiggerThan10);  
> > // false
> > 
> > [12, 5, 8, 1, 4].some(isBiggerThan10); 
> > // true
> > 
> > ```
>
> **filter()**：返回符合条件的值  新数  组  
>
> > ```js
> > var arr= [1,10,20,30]
> > var brr = arr.filter((item)=>{
> >     return item>10;
> > })
> > //[20,30]
> > ```
>
> **map()**：原数组的每一项运行给定函数，返回一个新数组
>
> **foreach()**：对数组中的每一项运行给定的函数，不返回值
>
> **join()**：**数组转化为字符串**。不给`join()`方法传入任何值，则使用逗号作为分隔符
>
> **push()**：将新数据逐个添加到数组末尾，返回值：修改后数组的长度
>
> > 将一个数组添加到另一个数组的尾部
> >
> > > ```js
> > > let arr1 = [0, 1, 2];
> > > let arr2 = [3, 4, 5];
> > > arr1.push(...arr2);
> > > ```
>
> **pop()**：数组末尾移除最后一项，返回值：移除的项
>
> **shift()**：移除数组第一项。返回值：移除的项
>
> **unshift()**：一次性将所有值插入数组前端，返回值：新数组长度
>
> **reserve()**：反转数组顺序。返回值：排序后数组
>
> **sort()**：排序。按照字符编码排序，参数可选
>
> > ```js
> > response.sort(this.compare("id"));
> > 
> > compare(p) {
> >         return function (m, n) {
> >           const a = m[p];
> >           const b = n[p];
> >           return b - a; //降序
> >         };
> > }
> > ```
>
> **concat()**：数组合并。不影响原数组，两个数组连接（注：不传递参数时，只是浅拷贝当前数组）
>
> > 连接多个数组（数组的合并）
> >
> > > ```js
> > > // ES5的合并数组
> > > arr1.concat(arr2, arr3);
> > > // [ 'a', 'b', 'c', 'd', 'e' ]
> > > 
> > > // ES6的合并数组
> > > [...arr1, ...arr2, ...arr3]
> > > // [ 'a', 'b', 'c', 'd', 'e' ]
> > > ```
>
> **slice(start，end)**：截取元素。不影响原数组，返回值：返回这个数组从`start`位置到`end`位置(不包含)的一个子数组
>
> **splice(a，b，c)**：插入或者删除元素。a指定插入或删除的起始位置；b指定删除元素的个数，c可选，指定要插入的新元素
>
> **indexOf(search,start)**：查找元素，返回首次出现的位置。没有找到则返回`-1`，`start`代表从`start`位置开始寻找
>
> **find()**：返回数组中满足提供的测试函数的第一个元素的值
>
> > `find`方法，用于找出第一个符合条件的数组成员，
> >
> > `find`方法的回调函数可以接受三个参数，依次为当前的值、当前的位置和原数组。
> >
> > ```js
> > [1, 5, 10, 15].find(function(value, index, arr) {
> > return value > 9;
> > }) // 10
> > ```
>
> **findIndex()**：返回第一个符合条件的数组成员的位置
>
> > `findIndex`方法，返回第一个符合条件的数组成员的位置，如果所有成员都不符合条件，则返回`-1`。
>
> > ```js
> > [1, 5, 10, 15].findIndex(function(value, index, arr) {
> > return value > 9;
> > }) // 2
> > ```
>
> **includes()：**包含判断。判断数组是否包含一个指定的值，返回：Boolean
>
> > ```js
> > let a = [1, 2, 3];
> > a.includes(2); 
> > // true 
> > a.includes(4); 
> > // false
> > ```
>
> **reduce()**：总和。需要两个参数，第一个是执行化简操作的函数，化简函数的任务就是用某种方法把两个值组合或化简为一个值，并返回化简后的值。
>
> > ```js
> > var total = [0, 1, 2, 3].reduce(function(sum, value) {
> >   return sum + value;
> > }, 0);
> > // total is 6
> > ```
>
> **fill(value, start, end)**：填充。用一个固定值填充数组中起始索引到终止索引内的全部元素，start, end不选则默认全部元素
>
> > ```js
> > ['a', 'b', 'c'].fill(7)
> > // [7, 7, 7]
> > 
> > //fill方法还可以接受第二个和第三个参数，用于指定填充的起始位置和结束位置。
> > ['a', 'b', 'c'].fill(7, 1, 2)
> > // ['a', 7, 'c']
> > ```
>
> flat()：默认拉平一层
>
> > ```js
> > [1, 2, [3, [4, 5]]].flat()
> > // [1, 2, 3, [4, 5]]
> > [1, 2, [3, [4, 5]]].flat(2)
> > // [1, 2, 3, 4, 5]
> > 
> > //如果不管有多少层嵌套，都要转成一维数组，可以用Infinity关键字作为参数。
> > [1, [2, [3]]].flat(Infinity)
> > // [1, 2, 3]
> > ```

#### 对象键值遍历

> Object.keys()，Object.values()，Object.entries()
>
> 

#### 字符串方法match()`、`replace()、search()、split()

> match()：和RegExp的exec()方法相同，接受一个参数，正则表达式或者RegExp对象
>
> search()：返回字符串第一个匹配项的索引
>
> replace()：字符串中的替换函数， 接受两个参数
>
> split()：接受字符串参数或者RegExp对象，返回一个数组

#### 函数参数默认值（）

> 可直接写在参数定义的后面
>
> ```js
> function log(x, y = 'World') {
>   console.log(x, y);
> }
> 
> log('Hello') // Hello World
> log('Hello', 'China') // Hello China
> log('Hello', '') // Hello
> ```
>
> ​	

#### rest参数（不定长参数）

> 形式为**...变量名**，是一个**数组**，该变量将多余的参数放入数组中，后面**不能跟其他参数**
>
> ```js
> function add(...values) {
>   let sum = 0;
> 
>   for (var val of values) {
>     sum += val;
>   }
> 
>   return sum;
> }
> 
> add(2, 5, 3) // 10
> ```
>
> 

#### 箭头函数

> ```js
> var f = v => v;
> 
> // 等同于
> var f = function (v) {
>   return v;
> };
> 
> 
> 
> //如果箭头函数不需要参数或需要多个参数，就使用一个圆括号代表参数部分。
> var f = () => 5;
> // 等同于
> var f = function () { return 5 };
> 
> 
> //如果箭头函数的代码块部分多于一条语句，就要使用大括号将它们括起来，并且使用return语句返回。
> var sum = (num1, num2) => { return num1 + num2; }
> 
> //由于大括号被解释为代码块，所以如果箭头函数直接返回一个对象，必须在对象外面加上括号，否则会报错。
> let getTempItem = id => ({ id: id, name: "Temp" });
> ```
>
> 

#### Set

> 类似于数组，没有重复的值
>
> 属性
>
> - `Set.prototype.constructor`：构造函数，默认就是`Set`函数。
> - `Set.prototype.size`：返回`Set`实例的成员总数。
>
> 方法
>
> - `add(value)`：添加某个值，返回 Set 结构本身。
> - `delete(value)`：删除某个值，返回一个布尔值，表示删除是否成功。
> - `has(value)`：返回一个布尔值，表示该值是否为`Set`的成员。
> - `clear()`：清除所有成员，没有返回值。
>
> 遍历操作
>
> - `keys()`：返回键名的遍历器
> - `values()`：返回键值的遍历器
> - `entries()`：返回键值对的遍历器
> - `forEach()`：使用回调函数遍历每个成员
>
> 使用 Set 可以很容易地实现并集（Union）、交集（Intersect）和差集（Difference）
>
> ```js
> let a = new Set([1, 2, 3]);
> let b = new Set([4, 3, 2]);
> 
> // 并集
> let union = new Set([...a, ...b]);
> // Set {1, 2, 3, 4}
> 
> // 交集
> let intersect = new Set([...a].filter(x => b.has(x)));
> // set {2, 3}
> 
> // 差集
> let difference = new Set([...a].filter(x => !b.has(x)));
> // Set {1}
> ```

#### Map

> 键值对的集合
>
> `set(key, value)`方法：将某个对象当作键
>
> `get(key)`方法：读取键
>
> `delete(key)`：删除了键。
>
> `has(key)`：判断是否含有该键。
>
> `clear()`:清楚所有成员
>
> 遍历方法和set类似

#### 对象合并Object.assign()

> `Object.assign`方法的第一个参数是目标对象，后面的参数都是源对象。
>
> ```js
> const target = { a: 1 };
> 
> const source1 = { b: 2 };
> const source2 = { c: 3 };
> 
> Object.assign(target, source1, source2);
> target // {a:1, b:2, c:3}
> ```

#### 为对象添加属性和方法

> **（1）为对象添加属性**
>
> ```js
> class Point {
>   constructor(x, y) {
>     Object.assign(this, {x, y});
>   }
> }
> ```
>
> 上面方法通过`Object.assign`方法，将`x`属性和`y`属性添加到`Point`类的对象实例。
>
> **（2）为对象添加方法**
>
> ```js
> Object.assign(SomeClass.prototype, {
>   someMethod(arg1, arg2) {
>     ···
>   },
>   anotherMethod() {
>     ···
>   }
> });
> 
> // 等同于下面的写法
> SomeClass.prototype.someMethod = function (arg1, arg2) {
>   ···
> };
> SomeClass.prototype.anotherMethod = function () {
>   ···
> };
> ```

#### Proxy代理

> 指在目标对象之前架设一层拦截，外界对该对象的访问都必须先通过这层拦截
>
> 它可以对外界的访问进行过滤和改写
>
> ```js
> //target参数表示所要拦截的目标对象，handler参数也是一个对象，用来定制拦截行为。
> var proxy = new Proxy(target, handler);
> 
> //eg.
> //第一个参数是所要代理的目标对象 是一个空对象
> //第二个参数是一个配置对象，该配置对象有一个get方法用来拦截对目标对象属性的访问请求，可以看到，由于拦截函数总是返回35，所以访问任何属性都得到35。
> var proxy = new Proxy({}, {
>   get: function(target, property) {
>     return 35;
>   }
> });
> proxy.time // 35
> proxy.name // 35
> proxy.title // 35
> ```

#### Promise

> ```js
> const promise = new Promise(function(resolve, reject) {
>   // ... some code
> 
>   if (/* 异步操作成功 */){
>     resolve(value);
>   } else {
>     reject(error);
>   }
> });
> ```
>
> `resolve`函数的作用是，将`Promise`对象的状态从“未完成”变为“成功”（即从 pending 变为 resolved），在异步操作成功时调用，并将异步操作的结果，作为参数传递出去；`reject`函数的作用是，将`Promise`对象的状态从“未完成”变为“失败”（即从 pending 变为 rejected），在异步操作失败时调用，并将异步操作报出的错误，作为参数传递出去。
>
> ```js
> //Promise实例生成以后，可以用then方法分别指定resolved状态和rejected状态的回调函数。
> //第一个回调函数是Promise对象的状态变为resolved时调用，
> //第二个回调函数是Promise对象的状态变为rejected时调用
> //这两个函数都接受Promise对象传出的值作为参数
> promise.then(function(value) {
>   // success
> }, function(error) {
>   // failure
> });
> 
> ```
>
> 异常回调catch（建议）
>
> ```js
> getJSON('/posts.json').then(function(posts) {
>   // ...
> }).catch(function(error) {
>   // 处理 getJSON 和 前一个回调函数运行时发生的错误
>   console.log('发生错误！', error);
> });
> ```
>
> 结束回调finally
>
> ```js
> //不管 Promise 对象最后状态如何，都会执行的操作
> promise
> .then(result => {···})
> .catch(error => {···})
> .finally(() => {···});
> ```
>
> 

#### for...in和for...of

> `for...in`循环主要是为遍历对象而设计的
>
> `for...in`循环可以遍历数组的键名。
>
> `for...of`循环调用遍历器接口，数组的遍历器接口只返回具有数字索引的属性
>
> `for...of`循环可以遍历数组的键值

#### 模块

> CommonJS是运行时加载，先生成一个对象，在从这个对象上读取需要的方法
>
> ES6模块。通过export命令显式指定输出的代码。再通过import输入
>
> ```js
> // ES6模块
> import { stat, exists, readFile } from 'fs';
> ```
>
> 上面代码的实质是从`fs`模块加载 3 个方法，其他方法不加载。这种加载称为“编译时加载”或者静态加载，即 ES6 可以在编译时就完成模块加载，效率要比 CommonJS 模块的加载方式高。当然，这也导致了没法引用 ES6 模块本身，因为它不是对象。
>
> 
>
> export关键字输出该变量
>
> ```js
> // 写法一
> export var m = 1;
> 
> // 写法二
> var m = 1;
> export {m};
> 
> // 写法三
> var n = 1;
> export {n as m};
> ```
>
> `import`命令加载模块
>
> ```js
> // main.js
> import {firstName, lastName, year} from './profile.js';
> 
> function setName(element) {
>   element.textContent = firstName + ' ' + lastName;
> }
> ```
>
> `export default`命令(一个模块只能有一个默认输出)，为模块指定默认输出，import加载模块时可以指定任意名字
>
> ```js
> //第一组是使用export default时，对应的import语句不需要使用大括号；第二组是不使用export default时，对应的import语句需要使用大括号。
> 
> 
> // 第一组
> export default function crc32() { // 输出
>   // ...
> }
> 
> import crc32 from 'crc32'; // 输入
> 
> // 第二组
> export function crc32() { // 输出
>   // ...
> };
> 
> import {crc32} from 'crc32'; // 输入
> ```
>
> 
>
> 适用场合
>
> （1）按需加载。
>
> `import()`可以在需要的时候，再加载某个模块。
>
> ```js
> button.addEventListener('click', event => {
>   import('./dialogBox.js')
>   .then(dialogBox => {
>     dialogBox.open();
>   })
>   .catch(error => {
>     /* Error handling */
>   })
> });
> ```
>
> 上面代码中，`import()`方法放在`click`事件的监听函数之中，只有用户点击了按钮，才会加载这个模块。
>
> （2）条件加载
>
> `import()`可以放在`if`代码块，根据不同的情况，加载不同的模块。
>
> ```js
> if (condition) {
>   import('moduleA').then(...);
> } else {
>   import('moduleB').then(...);
> }
> ```
>
> 上面代码中，如果满足条件，就加载模块 A，否则加载模块 B。
>
> （3）动态的模块路径
>
> `import()`允许模块路径动态生成。
>
> ```js
> import(f())
> .then(...);
> ```
>
> 上面代码中，根据函数`f`的返回结果，加载不同的模块。

#### 浏览器加载

> 浏览器允许脚本异步加载
>
> ```js
> //async一旦下载完，渲染引擎就会中断渲染，执行这个脚本以后，再继续渲染（下载完就执行）
> //defer要等到整个页面在内存中正常渲染结束，DOM 结构完全生成，以及其他脚本执行完成（渲染完执行）
> 
> <script src="path/to/myModule.js" defer></script>
> <script src="path/to/myModule.js" async></script>
> ```
>
> 上面代码中，`<script>`标签打开`defer`或`async`属性，脚本就会异步加载。渲染引擎遇到这一行命令，就会开始下载外部脚本，但不会等它下载和执行，而是直接执行后面的命令。
>
> 

#### await和async

> 1.即使前一个异步操作失败，也不中断后面的异步操作=>将await放在try...catch中
>
> ```js
> async function myFunction() {
>   try {
>     await somethingThatReturnsAPromise();
>   } catch (err) {
>     console.log(err);
>   }
> }
> 
> // 另一种写法
> 
> async function myFunction() {
>   await somethingThatReturnsAPromise()
>   .catch(function (err) {
>     console.log(err);
>   });
> }
> ```
>
> 2.多个`await`命令后面的异步操作，如果不存在继发关系，最好让它们同时触发
>
> ```js
> let foo = await getFoo();
> let bar = await getBar();
> ```
>
> 若确实希望多个请求并发执行，可以使用`Promise.all`方法
>
> ```js
> async function dbFuc(db) {
>   let docs = [{}, {}, {}];
>   let promises = docs.map((doc) => db.post(doc));
> 
>   let results = await Promise.all(promises);
>   console.log(results);
> }
> ```

#### RegExp正则表达式

> JavaScript有两种方式创建一个正则表达式：
>
> 第一种方式是直接通过`/正则表达式/`写出来，第二种方式是通过`new RegExp('正则表达式')`创建一个RegExp对象。
>
> **注意，如果使用第二种写法，因为字符串的转义问题，字符串的两个`\\`实际上是一个`\`。**
>
> 
>
> \d`可以匹配一个数字
>
> `\w`可以匹配一个字母或数字
>
> `*`表示任意个字符（包括0个）
>
> `+`表示至少一个字符
>
> `?`表示0个或1个字符
>
> `{n}`表示n个字符
>
> `{n,m}`表示n-m个字符
>
> `\s`可以匹配一个空格（也包括Tab等空白符）
>
> `A|B`可以匹配A或B
>
> `^`表示行的开头，`^\d`表示必须以数字开头
>
> `$`表示行的结束，`\d$`表示必须以数字结束
>
> 
>
> - `[0-9a-zA-Z\_]`可以匹配一个数字、字母或者下划线；
> - `[0-9a-zA-Z\_]+`可以匹配至少由一个数字、字母或者下划线组成的字符串，比如`'a100'`，`'0_Z'`，`'js2015'`等等；
> - `[a-zA-Z\_\$][0-9a-zA-Z\_\$]*`可以匹配由字母或下划线、$开头，后接任意个由一个数字、字母或者下划线、$组成的字符串，也就是JavaScript允许的变量名；
> - `[a-zA-Z\_\$][0-9a-zA-Z\_\$]{0, 19}`更精确地限制了变量的长度是1-20个字符（前面1个字符+后面最多19个字符）。
>
> **方法**
>
> exec()： 每次只返回一个匹配项
>
> test()：匹配则返回true
>
> ```
> var text="000-00-0000"
> var pattern=/\d{3}-\d{2}-\d{4}/
> pattern.test(text)
> ```
>
> 

####   原型链

> 每一个实例对象有一个_ proto _属性，指向的构造函数的原型对象，构造函数的原型对象也是一个对象，也有 _ proto _属性，这样一层一层往上找就形成了原型链

#### 事件委托

> 实际上就是利用事件冒泡，只指定一个事件处理程序程序，就可以管理某一类型的所有事件。
>
> #### 事件委托怎么实现：
>
> 首先看一个例子： 子节点实现相同的功能：
>
> ```html
> <ul id="ul1">
>     <li>111</li>
>     <li>222</li>
>     <li>333</li>
>     <li>444</li>
> </ul>
> 复制代码
> ```
>
> 实现的功能是点击li，弹出123
>
> ```js
> window.onload = function(){
>     var oUl = document.getElementById("ul1");
>     var aLi = oUl.getElementsByTagName('li');
>     for(var i=0;i<aLi.length;i++){
>         aLi[i].onclick = function(){
>             alert(123);
>         }
>     }
> }
> ```
>
> 上面代码首先找到ul，然后遍历li，然后点击li的时候，又要找一次目标的li的位置，才能执行最后的操作，每次点击都要找一次li；
>
> 如果用事件委托的方式做呢:
>
> ```js
> window.onload = function(){
>     var oUl = document.getElementById("ul1");
>    oUl.onclick = function(){
>         alert(123);
>     }
> ```
>
>
> 这里用父级ul做事件处理，当li被点击时，由于冒泡原理，事件就会冒泡到ul上，因为ul上有点击事件，所以事件就会触发，但是这样点击ul也会触发，
>
> 解决方案： `Event`对象提供了一个属性叫`target`，可以返回事件的目标节点，我们称为事件源。即`target`可以表示为当前的事件操作的`DOM`。兼容性问题：标准浏览器用`ev.target`，IE浏览器用`event.srcElement`，此时只是获取了当前节点的位置，可以用`nodeName`来获取具体是什么标签名，这里返回是大写的，需要转成小写`toLowerCase()`来做比较.
>
> 上面的例子是每个`li`操作是同样的效果，如果每个li被点击的效果不一样呢:
>
> ```js
> <div id="box">
>         <input type="button" id="add" value="添加" />
>         <input type="button" id="remove" value="删除" />
>         <input type="button" id="move" value="移动" />
>         <input type="button" id="select" value="选择" />
>  </div>
> 复制代码
> window.onload = function(){
>             var Add = document.getElementById("add");
>             var Remove = document.getElementById("remove");
>             var Move = document.getElementById("move");
>             var Select = document.getElementById("select");
>             
>             Add.onclick = function(){
>                 alert('添加');
>             };
>             Remove.onclick = function(){
>                 alert('删除');
>             };
>             Move.onclick = function(){
>                 alert('移动');
>             };
>             Select.onclick = function(){
>                 alert('选择');
>             }
>             
>         }
> ```
>
> 上面代码4个按钮，点击每一个做不同的操作，至少需要4次`DOM`操作，用事件委托进行优化：
>
> ```js
> window.onload = function(){
>             var oBox = document.getElementById("box");
>             oBox.onclick = function (ev) {
>                 var ev = ev || window.event;
>                 var target = ev.target || ev.srcElement;
>                 if(target.nodeName.toLocaleLowerCase() == 'input'){
>                     switch(target.id){
>                         case 'add' :
>                             alert('添加');
>                             break;
>                         case 'remove' :
>                             alert('删除');
>                             break;
>                         case 'move' :
>                             alert('移动');
>                             break;
>                         case 'select' :
>                             alert('选择');
>                             break;
>                     }
>                 }
>             }
>             
>         }
> ```
> 
>用事件委托就只用一次`DOM`操作就能完成操作，提高性能
> 
>

#### 原型（prototype、proto、constructor）

> #### 概念：
>
> 1. 构造函数：用来初始化新创建的对象的函数是构造函数。
> 2. 实例对象：通过构造函数的`new`操作创建的对象是实例对象。（可以用一个构造函数，构造多个实例对象）
>
> ```js
> function Foo(){};
> var f1 = new Foo;
> var f2 = new Foo;
> console.log(f1 === f2);//false
> ```
>
> 3.原型对象及`prototype`：构造函数有一个`prototype`属性，指向对应实例对象的原型对象。通过同一个构造函数实例化的多个对象具有相同的原型对象。这个属性可以用来实现继承。
>
> ```js
> function Foo(){};
> Foo.prototype.a = 1;
> var f1 = new Foo;
> var f2 = new Foo;
> 
> console.log(Foo.prototype.a);//1
> console.log(f1.a);//1
> console.log(f2.a);//1
> ```
>
> 4.constructor`：原型对象有一个`constructor`属性，指向该原型对象对应的构造函数。由于实例对象可以继承原型对象的属性，所以实例对象也拥有`constructor`属性，同样指向原型对象对应的构造函数。
>
> ```js
> console.log(Foo.prototype.constructor === Foo);//true
> console.log(f1.constructor === Foo);//true
> ```
>
> 5._ proto _：实例对象有一个`proto`属性，指向该实例对象对应的原型对象。
>
> ```js
> console.log(f1.__proto__ === Foo.prototype);//true
> ```