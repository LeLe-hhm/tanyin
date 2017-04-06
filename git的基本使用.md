## Git

### 什么是Git?
  - Git是一款源代码管理工具(版本控制工具)
    - 我们写的代码需要使用Git进行管理。
  1.0是稳定
  2.0加了新功能
  - 源代码有必要管理起吗？
  - 有必要，因为人工的去处理不同的版本，做相应备份会很麻烦。
  - svn,vss,vcs,tfs.....
  -Git是linux之父当年为了维护linux---linus之前也是手动维护合并把文件发给Linus
  - BitKeeper(收费)
  - 有人想破解(不给提供免费使用)
  - linus自己写了一个版本管理的工具（Git）


### 分布式版本管理工具，集中式
  - git属于分布式
  - svn集中式 

### git安装

### git初始化一个仓库
  - 其实就是创建了一个.git隐藏目录
  - 命令:` git init `;初始化 有一个.get 隐藏文件夹
    + 想在哪个目录创建.git目录，就是哪个目录打开工具然后写命令.
    + 一般是在项目的根目录执行这个命令.
    + 查看文件 ls 或者 ls -a


### 自报家门
  - 配置用户名 : `git config user.name "testName"`  
  - 配置邮箱   : `git config user.email "test@sina.com"`
  - 查看配置信息: `git config --list`


### 把代码提交到仓库中
  - 1.先把代码添加到暂存区(就相当于放到仓库门口)
    + 命令:`git add 文件路径`
    + 示例:`git add ./reademe.md`
    + 可以使用`git add .`这个命令，批量把当前目录下所有修改过的文件添加到暂存区。

  - 2.把暂存区的文件提交仓库里
    + 命令: `git commit -m "注释" `
    + 示例: `git commit -m "我们添加了一个新的功能"`
    + -m 表示指定一个字符串，作为提交的说明(相当于注释);

  - 合并add 与commit 命令
    + `git commit -a -m "这是使用合并添加与提交的操作"`;
    + 这里-a参数表明把所有修改后的文件一起添加到暂存区.(只是对修改后的文件有效，对于新添加的文件没有作用)


### 查看工作区状态
  - 命令:`git status`


### 添加忽略文件
  - 在项目中有一些文件是不需要提交的,我们需要把它忽略掉
  - 需要在.git文件夹所在目录新建一个名为.gitignore的文件
    然后在这个文件中写上需要被忽略的文件的路径。
    示例: /css/a.css
        : /css/*.css
        : /a.html


### 比对文件差异
  - 命令: `git diff`
    + 用来比较工作区内容与最近一次提交的内容的区别
    + 如果暂存区没有文件，就会将工作与代码与最近一次提交对比
  - 命令：`git diff --cached`  比较暂存区的文件和仓库中文件的区别
  - 对比之前某两次提交的文件的差异
    + 命令:`git diff [版本号1] [版本号2] [想比较的文件路径]`

### 查看日志
  - 命令:`git log`,可以查看每一次提交的日志
  - 命令:`git log --oneline` 表示使用简洁的形式输出提交日志


### 版本回退
  - 命令:`git reset --hard Head~1`
    + 这是将代码回退到上上一次提交时的状态
  - 命令:`git reset --hard Head~2`
    + 回退到上上上次
  - 命令:`git reset --hard Head~0`
    + 回退到上次提交时的状态,~0可以省略

  - 命令:`git reset --hard 版本号`
    + 通过每次提交时生成的版本号来回退版本

  - 通过`git reflog`命令可以查看之前所有版本切换的操作记录，可以通过这个命令得到的版本号回退到指定的版本。

### 创建分支
  - 命令:`git branch [分支名]`
    + 创建一个新分支
  - 命令:`git branch`
    + 查看当前所有的分支

### 切换分支
  - 命令:`git checkout [分支名]`
    + 切换分支后可以在切换后的分支中进行正常的操作

### 合并分支
  - 命令:`git merge [分支名]`
    + git会将指定的分支合并到当前分支.

### 删除分支
  - 命令:`git branch -d [分支名]`
    + 删除指定分支，-d参数表示要执行删除操作

### git提交中的冲突
  - 如果git不能自动合并分支，就会有冲突，我们需要手动解决冲突，然后再次提交


## github
### github与git
  - git 版本管理工具
  - github 就是一个网站，只是这个网站提供git服务器的功能


### 上传代码到git服务器(push)
  - 命令:`git push [远程服务器地址] [远程服务器的分支]`
     + 示例:`git push https://github.com/xxxxxxx.git master`

  - 上传时可以使用一些简化的命令
    + 将远程服务器地址写成变量的形式
      * `git remote add [变量名]  [远程服务器地址]`
      * 示例:`git remote add origin https://github.com/xxxxxxxxx.git`
      * 这样之后就可以直接使用origin来代替git push 后面写的地址了
        `git push origin master`
  - 还可以尽一步简化
    + 在push时加上-u参数，就会默认建立本地当前分支与远程指定分支的关联,下一次push时就不需要输入分支名了`git push origin`;

## git使用ssh方式上传代码与github
  - git生成公钥和私钥
    + 命令:`ssh-keygen -t rsa`生成的公钥与私钥文件会在当用户目录的.ssh目录下.


### 把代码push到服务器时需要先pull一下
  - 在pull之后如果远程的代码与本地的代码有冲突，git会先自动合并冲突，如果不能自动合并，就必需我们手动去处理冲突。

### 从服务器上pull代码到本地
  - 如果本地没有.git目录，需要先初始化一下。
  - 命令:`git pull [远程服务器地址] [远程的分支]`

### gh-pages分支-搭建博客.
  - 需要把自已博客的网页代码上传到github上的gh-pages分支
  - 然后就直接访问了
    + 访问的url形式: [github用户名].github.io/[仓库的名字]/[具体的页面]


### sourceTree , tortoiseGit

http://t.cn/R6tx5jJ
### npm
  - 官网[https://www.npmjs.com]
  - node package manager
  - 命令:
    + 初始化:`npm init`
    + 安装指定包:`npm install jquery --save`
    + 删除指定包:`npm remove jquery --save`
    + 下载安装package.json中dependencies属性对的文-件:`npm install --production`

### browser-sync
  - 更改代码之后自动刷新浏览器
  - 需要使用npm进行全局安装:`npm install browser-sync -g`,-g表示安装到全局
  - 使用:`browser-sync start --server --files "./index.html,app.css,./css/*.css,*.*" `
  - --files参数指定要监视的文件，后面跟要监视的文件的文件路径以逗号分隔。

## gulp
  [官网](http://www.gulpjs.com)
  [中文网](http://www.gulpjs.com.cn)

- 前端自动化构建工具
  js压缩,var x,xname，混淆
  合并.
  css压缩
  html压压缩

- grunt ,webpack...


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

### gulp 使用

#### 使用时还需要在项目中通过npm非全局安装gulp
  - `npm install gulp --save-dev`


#### 还需要在当前项目根目录添加一个gulpfile.js文件来写具体的任务代码.

### gulp的一些插件
  - 也是使用npm安装
  - 对js代码进行压缩 gulp-uglify
  - 对代码进行合并 gulp-concat
  - 对css进行压缩 gulp-cssnano
  - 对html进行压缩 gulp-htmlmin

