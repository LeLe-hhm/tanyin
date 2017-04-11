## 上午课程内容复习
- angular是什么东西
    + spa(单页面应用程序)
    + 框架
- 安装angular
    +
    + npm
    + bower
    + cdn  --> jsonp --> script标签可以跨域
- 指令
    + ng-app
    + ng-click --> ng-dblclick,ng-change... 只要是js有的,angular一定有
    + 文本框的值 --> ng-model="abc"
    + ng-init="a=1"
- 表达式
    + {{abc}} 渲染
    + {{ 2 + 3 }} js表达式
    + {{ [] }}


$demo.css('background','blue');
$demo.css('background');


笔记本 由内存、屏幕、电池...组成

创建笔记本
var 笔记本 = angular.module('笔记本',['内存','屏幕'])

angular.module('笔记本')

mvc --> c


1. 用dom选择器选择出来所有的DOM元素
2. 给注册按钮绑定onclick事件，当点击的时候触发了事件，回调函数
3. 密码


ng-app
ng-controller

注册按钮加一个事件 ng-click="" ---> 数据模型

数据模型里面应该有这四个东西 --》 双向数据


innerHTML,.value

input ng-model

面向对象,localStorage MVC



MVC

什么是面向对象：

angular是一个基于MVC的一个框架

M
V
C

面向对象的好处：只需要知道结果，不需要知道过程 ===> 开发起来效率高一点

MVC：
1 提高我们的开发效率
2 实现职责分离 (m,v是分开二个写)

假设我们用jquery来写的
当我们页面的DOM结构发生变化，js代码需不需要改
$('.a .b .c') --> 能不能页面和js是二个人写 百分百不可以

MVC：

好处：
M V C
一个模型可以被很多视图所采用
MVC --> angular.js ,各种java,php,python,rails,c++, express


面向过程

事件委托

react.js vue.js express --> 纯粹采用MVC


MVVM

哪块代码是model
哪块代码是view

mvc mvvm

mv*