
### npm ：用来下载前端的库、工具、框架
  - 官网[https://www.npmjs.com]
  - node package manager
  - 命令:
    + 初始化:`npm init`
    + 安装指定包:`npm install jquery --save`
    + 删除指定包:`npm remove jquery --save`
    - 直接从别人那里把package.json 拷贝过来  怎么下载里面的的工具? 
    + 下载安装package.json中dependencies属性对的文-件:`npm install --production`

    -下载指定的版本号 : 'npm install jquery@3.3.3 --save'
    - 移除工具 ： 'npm remove jquery --save'
    - npmjs.com 官网查询工具名字
    - 补充 
      + 打开官网  'npm docs name'
      例：'npm docs jquery' 打开jQuery官网
      -
        npm install name --save ->项目中真的会用的上的库、框架
        npm install name --save-dev ->用来下载一些压缩、优化我们当前项目代码的前端工具
        npm install name -g ->下载前端工具
        例：npm install -g browser-sync 
### browser-sync
  - 更改代码之后自动刷新浏览器
  - 需要使用npm进行全局安装:`npm install browser-sync -g`,-g表示安装到全局
  - 使用:当前根目录cmd: `browser-sync start --server --files "./index.html,app.css,./css/*.css,*.*" `
  - --files参数指定要监视的文件，后面跟要监视的文件的文件路径以逗号分隔。
    "*.*" 匹配当前的文件
    "*/*.*" 可以匹配当前文件夹里面的文件
   +  "*.*,*/*.*"

   - 检测版本：browser-sync --version
## gulp
  [官网](http://www.gulpjs.com)
  [中文网](http://www.gulpjs.com.cn)

- 前端自动化构建工具
  js压缩,var x,xname，混淆
  合并.
  css压缩
  html压压缩

- 其他工具： grunt ,webpack...


### 核心就5个方法
  - task,gulp中是一个个任务的形式来实现功能。
    + task('任务名',function(){
      .....
    });
  - src
    + src('./*.js')
  - dest('./minjs/')// 指定处理后的文件的输出路径.
  - watch('./*.js',['任务名1','任务名2']);
  - run('任务名');//执行指定的任务.
  
### gulp的安装
  - 使用npm 进行安装
  - `npm install gulp-cli -g`;



#### 使用时还需要在项目中通过npm非全局安装gulp
  - `npm install gulp --save-dev`

### gulp 使用

#### 还需要在当前项目根目录添加一个gulpfile.js文件来写具体的任务代码.
  - 在当前根目录新建gulpfile.js,在这里面写gulp代码
    + gulp代码 
      例:var gulp = require('gulp');//引入gulp
         var uglify = require('gulp-uglify');//引入js压缩插件
         gulp.task('lele', function() { //任务
             gulp.src('./1.js')
                 .pipe(uglify())
                 .pipe(gulp.dest('./hm'))
                //新建一个hm文件夹，并把压缩后的1.js代码保存到hm文件夹中
        })
        
  - gulp代码写完之后 进行压缩 运行的指令：gulp [任务名]
       例： gulp lele

 

### gulp的一些插件
  - 也是使用npm安装
    下载插件指令 
      例：'npm install gulp-uglify --save-dev'
  - 对js代码进行压缩 gulp-uglify
  - 对css进行压缩 gulp-cssnano
  - 对代码进行合并 gulp-concat
  - 对html进行压缩 gulp-htmlmin

    +压缩多个js文件
    var gulp = require('gulp');
    var uglify = require('gulp-uglify');
    var concat = require('gulp-concat');
    gulp.task('lele',function(){
      //多个文件,要用[]
      gulp.src(['./1.js','./2.js'])
      //把1.js,2.js合并到all.js 中
          .pipe(concat('all.js'))
          //压缩
          .pipe(uglify())
          //把all.js保存到hm文件中
          .pipe(gulp.dest('./hm'))
    })
    
    +压缩html
    var gulp = require('gulp');
    var htmlmin = require('gulp-htmlmin');
    gulp.task('ceshi',function(){
       gulp.src('1.html')
      .pipe(htmlmin({removeComments:false,collapseWhitespace:true,collapseBooleanAttributes:true,removeEmptyAttributes:true,removeScriptTypeAttributes:true,removeStyleLinkTypeAttributes:true,minifyCSS:true,minifyJS:true}))
      .pipe(gulp.dest('./dist'));
     });