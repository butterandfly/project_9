# 实战：Gulp
## 什么是gulp？

## 入门

### First Step: 创建gulpfile
安装好gulp后，首先你需要在项目目录下创建一个gulpfile.js：
```bash
touch gulpfile.js
```

该文件理所当然地需要用到gulp模块，所以我们可以在gulpfile.js里面加入下面这段代码：
```
// gulpfile.js

var gulp = require('gulp');
```

下面，我们通过一些实际的例子来学习怎么使用gulp。

### 使用gulp合并css文件
  我们先尝试解决一个最简单的情况。假设现在我们的页面有两个比较重要的模块，日期选择器与自定义下拉框；他们的css文件分别写在datepicker.css与dropdown.css中，且都存放在css目录下。
    不同的模块使用不同css文件，这样利于代码管理；但我们可不想每个css文件都重新在html中导入，一个非常不错的选择是将所有css合并成一个css文件。以前我们用的是grunt，现在可以试试gulp。
      不过在编写gulpfile之前，我们首先要安装一个相关的模块：
      
```bash
npm install gulp-concat --save-dev
```

gulp-concat模块用于文件内容的拼接。接下来我们可以修改我们的gulpfile.js：
```javascript
// gulpfile.js

var gulp = require('gulp');
// concat模块用于并接文件内容
var concat = require('gulp-concat');

// 该任务用于合并所有css文件到app.css中
gulp.task('catcss', function() {
  gulp.src('./css/*.css')
    .pipe(concat('app.css'))
    .pipe(gulp.dest('./css/'))
});
```

在讲解上面这段代码之前，我们先试试其作用。项目目录下输入一下命令：
```bash
gulp catcss
```

终端应该会输出一些成功信息。试试查看css目录下的app.css文件，里面就是datepicker.css与dropdown.css的内容。
现在我们研究一下gulpfile.js里面的代码。
```javascript
gulp.task('catcss', function() {
```

gulp模块中的`.task`方法用于定义一个任务，第一个参数是任务名，第二个参数是任务执行的内容（function）。

```
gulp.src('./css/*.css')
```
  `gulp.src`方法通过表达式匹配到一系列文件，这里我们得到css目录下的所有css文件。

```
.pipe(concat('app.css'))
```
Gulp中的`.pipe`与unix下面的“管道”(|，或pipe)非常类似。这里我们把`gulp.src('./css/*.css')`中得到的内容用过管道传输给concat模块处理；完成后会把`gulp.src`中所有文件的内容合并，并保存在app.css文件中。

```
.pipe(gulp.dest('./css/'))
```
`gulp.dest`方法指明一个目标目录，上一个pipe中得到的文件在目标目录里生成。

#### 完善
上面我们学会了怎么用gulp合并所有css文件，但实际中css的目录可能不是这样。对于一个大的前端项目，代码更应按照模块来放置。
在项目下我们建立一个名为components的目录，而每个模块都作为一个目录放在components下面；模块对应的js、css、模板文件都放在模块目录下。所以当前的目录结构如下：
```bash
components
└── datepicker
    └── datepicker.css
```

另外，我们把合并后的css文件放在source目录下；所以，gulpfile.js要做如下的修改：

```
// gulpfile.js

var gulp = require('gulp');
// concat模块用于并接文件内容
var concat = require('gulp-concat');

// 该任务用于合并所有css文件到app.css中
gulp.task('catcss', function() {
    gulp.src('./component/*/*.css')
    .pipe(concat('app.css'))
    .pipe(gulp.dest('./source/'))
});
```

### 使用gulp压缩css(uglify)
压缩css也是grunt常见的工作之一，这里我们亦尝试用gulp来代替。
