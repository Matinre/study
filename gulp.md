#### gulp

> ##### 安装
>
> > npm install -g gulp //全局安装
> >
> > npm install gulp //全局安装后，还需要在项目中安装。目录切换到项目文件夹，执行
> >
> > npm install --save-dev gulp //gulp写入项目package.json的依赖中
>
> ##### 建立gulpfile.js文件
>
> > 此时我们的目录结构是这样子的：
> >
> > ├── gulpfile.js
> > ├── node_modules
> > │ └── gulp
> > └── package.json
> >
> > 要运行gulp任务，只需切换到存放`gulpfile.js`文件的目录(windows平台请使用cmd或者Power Shell等工具)，然后在命令行中执行`gulp`命令就行了，`gulp`后面可以加上要执行的任务名，例如`gulp task1`，如果没有指定任务名，则会执行任务名为`default`的默认任务。
>
> ##### gulp.src()
>
> > 获取流  读取需要操作的文件
> >
> > ```js
> > var gulp = require('gulp');
> > gulp.src(globs[, options])
> > ```
> >
> > 我们可以使用下面这些特殊的字符来匹配我们想要的文件：
> >
> > - `*` 匹配文件路径中的0个或多个字符，但不会匹配路径分隔符，除非路径分隔符出现在末尾
> > - `**` 匹配路径中的0个或多个目录及其子目录,需要单独出现，即它左右不能有其他东西了。如果出现在末尾，也能匹配文件。
> > - `?` 匹配文件路径中的一个字符(不会匹配路径分隔符)
> > - `[...]` 匹配方括号中出现的字符中的任意一个，当方括号中第一个字符为`^`或`!`时，则表示不匹配方括号中出现的其他字符中的任意一个，类似js正则表达式中的用法
> > - `!(pattern|pattern|pattern)` 匹配任何与括号中给定的任一模式都不匹配的
> > - `?(pattern|pattern|pattern)` 匹配括号中给定的任一模式0次或1次，类似于js正则中的(pattern|pattern|pattern)?
> > - `+(pattern|pattern|pattern)` 匹配括号中给定的任一模式至少1次，类似于js正则中的(pattern|pattern|pattern)+
> > - `*(pattern|pattern|pattern)` 匹配括号中给定的任一模式0次或多次，类似于js正则中的(pattern|pattern|pattern)*
> > - `@(pattern|pattern|pattern)` 匹配括号中给定的任一模式1次，类似于js正则中的(pattern|pattern|pattern)
> >
> > 下面以一系列例子来加深理解
> >
> > - `*` 能匹配 `a.js`,`x.y`,`abc`,`abc/`,但不能匹配`a/b.js`
> > - `*.*` 能匹配 `a.js`,`style.css`,`a.b`,`x.y`
> > - `*/*/*.js` 能匹配 `a/b/c.js`,`x/y/z.js`,不能匹配`a/b.js`,`a/b/c/d.js`
> > - `**` 能匹配 `abc`,`a/b.js`,`a/b/c.js`,`x/y/z`,`x/y/z/a.b`,能用来匹配所有的目录和文件
> > - `**/*.js` 能匹配 `foo.js`,`a/foo.js`,`a/b/foo.js`,`a/b/c/foo.js`
> > - `a/**/z` 能匹配 `a/z`,`a/b/z`,`a/b/c/z`,`a/d/g/h/j/k/z`
> > - `a/**b/z` 能匹配 `a/b/z`,`a/sb/z`,但不能匹配`a/x/sb/z`,因为只有单`**`单独出现才能匹配多级目录
> > - `?.js` 能匹配 `a.js`,`b.js`,`c.js`
> > - `a??` 能匹配 `a.b`,`abc`,但不能匹配`ab/`,因为它不会匹配路径分隔符
> > - `[xyz].js` 只能匹配 `x.js`,`y.js`,`z.js`,不会匹配`xy.js`,`xyz.js`等,整个中括号只代表一个字符
> > - `[^xyz].js` 能匹配 `a.js`,`b.js`,`c.js`等,不能匹配`x.js`,`y.js`,`z.js`
>
> ##### gulp.dest()
>
> > 写文件 gulp.dest(path[,options])
> >
> > gulp的使用流程一般是这样子的：首先通过`gulp.src()`方法获取到我们想要处理的文件流，然后把文件流通过pipe方法导入到gulp的插件中，最后把经过插件处理后的流再通过pipe方法导入到`gulp.dest()`中，`gulp.dest()`方法则把流中的内容写入到文件中
>
> ##### gulp.task()
>
> > 定义任务
> >
> > gulp.task(name[, deps], fn)
> >
> > - **-name** 为任务名
> >   **deps** 是当前定义的任务需要依赖的其他任务，为一个数组。当前定义的任务会在所有依赖的任务执行完毕后才开始执行。如果没有依赖，则可省略这个参数
> >   **fn** 为任务函数，我们把任务要执行的代码都写在里面。该参数也是可选的。
>
> ##### gulp.watch()
>
> > 监视文件的变化，当文件发生变化后，我们可以利用它来执行相应的任务
> >
> > gulp.watch(glob[, opts], tasks)
> >
> > - **glob** 为要监视的文件匹配模式，规则和用法与`gulp.src()`方法中的`glob`相同。
> >   **opts** 为一个可选的配置对象，通常不需要用到
> >   **tasks** 为文件变化后要执行的任务，为一个数组
> >
> > ```js
> > gulp.task('uglify',function(){
> >   //do something
> > });
> > gulp.task('reload',function(){
> >   //do something
> > });
> > gulp.watch('js/**/*.js', ['uglify','reload']);
> > ```
> >
> > 
>
> > 让task按顺序执行，series（）方法
> >
> > 以最大并发来运行tasks，parallel（）方法