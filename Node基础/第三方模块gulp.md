#  gulp

基于node平台开发的前端构建工具

##  gulp能做什么

* 项目上线，html，css，js文件压缩合并
* 语法转换es6，less....
* 公共文件抽离
* 修改文件浏览器自动刷新

##  gulp使用

1. 下载  npm install gulp
2. 在项目根目录下创建gulpfile.js文件
3. 重构项目的文件夹结构，src目录放置源代码文件，dist目录放置构建后文件
4. 在gulpfile.js文件中编写任务
5. 在命令行工具中执行gulp任务

##  gulp中提供的方法

* gulp.src():获取任务要处理的文件

* gulp.dest():输出文件

* gulp.task():建立gulp任务

* gulp.watch:监控文件的变化

```javascript
const gulp = require('gulp');
//使用gulp.task()方法建立任务
gulp.task('first',() => {
    //获取任务要处理的文件
    gulp.src('../css/base.css');
    //将处理后的文件输出到dist目录
    .pipe(gulp.dest('./dist/css'));
})
```

##  插件

gulp-htmlmin：压缩html

gulp-file-include：公共文件抽取

less编译：gulp-less

gulp-csso：css压缩

es6转换：gulp-babel

js压缩：gulp-uglify