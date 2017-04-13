
## 开放性讨论

- 为什么这几年前端行业好像突然间多了那么多东西
    + 我们现在做的网站不再是简简单单的呈现静态页面，而是一个web应用程序。
    + 一大批后端程序员转型为前端，大大提高了前端的水准。


## Angular简介
 - jQuery ：库
  + 封装了一些常用的方法，我们主动的调用这些方法
    -- 提高了代码的利用，以及代码后期的维护

 - Angular: 前端框架
  + 框架提供了一些结构或者模式，
  + 我们是根据框架提供的结构或者模式去书写代码
  + 由框架帮助我们去执行相应的操作。

### 什么是 Angular

- 一款非常优秀的前端高级 JS 框架
- 最早由 Misko Hevery 等人创建
- 2009 年被 Google 公式收购，用于其多款产品
- 目前有一个全职的开发团队继续开发和维护这个库
- 有了这一类框架就可以轻松构建 SPA 应用程序
- 其核心就是通过指令扩展了 HTML，通过表达式绑定数据到 HTML。
- *Angular不推崇DOM操作，也就是说在NG中几乎找不到任何的DOM操作*

#### 什么是 SPA
- single page application
- 单页应用程序

### 为什么使用 Angular
- spa


### 安装 Angular

- 暴力安装: 直接从本地硬盘中复制一个angular.js文件到项目中

- 通过工具安装
  + npm 方式 `npm install angular`
  + bower 方式 `npm install angular`

- CDN - 扩展内容

*注意，每一种安装方式，本质都是为了拿到angular.js文件*

## Angular 基础概念

### Angular 表达式
- 就是把ng-model对应的值显示到页面中。
- 语法：两个大括号的形式：{{}}
- {{user.name}}
- {{'hello'+ user.name}}
- {{1+2}}
- {{[1,2,3,4]}}


### Angular 的核心特性

- 指令

- MVC

- 模块化  angular.module()

- 双向数据绑定

### 指令

- 在 AngularJS 中将前缀为 ng- 这种属性称之为指令，其作用就是为 DOM 元素调用方法、定义行为绑定数据等

- 简单说：当一个 Angular 应用启动，Angular 就会遍历 DOM 树来解析 HTML，根据指令不同，完成不同操作

- ng-app 告诉angular来管理html代码，管理ng-app所在元素及其子元素。
- ng-click 用来注册点击事件

  >var add = document.getElementById('add');
   add.onclick=function(){
    val = (val-0)+1; // num.value = (num.value - 0) +1
   }

- ng-model：var num = document.getElementById('num').value

- ng-init :进行初始化操作:  ng-init="user.name='小明'"


- ng-bind
    + 用来解决表达式闪烁问题
    + `<p ng-bind="数据模型"></p>`
    *注意：只能够在双标签中使用ng-bind指令*

- ng-cloak
    + 用来解决表达式闪烁问题
    + `<p class="ng-cloak">{{name}}</p>`
    + 利用angular在加载会移除页面上所以名为ng-cloak的样式名的特性。

- ngSanitize模块 第三方插件
`npm install angular-sanitize`
    + 使用的是ng-bind-html指令来渲染数据模型。
    + 使用步骤：
        1.下载第三方插件
        2.引入插件
        3.把这个插件模块的名字写入到主模块函数的第二个参数（数组）里,意味着第三方插件模块的一些东西可以在当前这个页面使用
        例: var app = angular.module('myApp',['naSanitize']);

- ng-repeat
    + 可以用来循环输出数组
    + 写在哪个元素上就是循环哪个元素。
    + 语法：类似于forin 循环
        > `<div ng-repeat="item in data ">{{item}}</div>`
    + track by $index 解决数组中数据有重复的问题
        + `<li ng-repeat="item in tesData track by $index"></li>`

    + 还可以用来渲染key,value对

    + ng-repeat 在遍历里会暴露一些数据模型,
        - $even:提供了一个布尔值，当为true时表示当前数据是第偶数条数据,从索引0开始计算
        - $odd:提供了一个布尔值，当为true时表示当前数据是第奇数条数据,从索引0开始计算
        - $index:当前元素的索引
        - $first,$last ,$middle
- ng-class:
    + 从多种样式中选择一个样式
        - 语法：类似于从一个key,value对象中获取其中一个属性的值
        - ng-class="{'A':'red','B':'blue','C':'green'}"
            + 属性名key是控制器中的$scope的属性值  属性值value是我们自定义的样式类名
    + 从多种样式中选择多个
        - 语法：也是写一个key,value对象，这里的key是我们提供的类样式名，value是一个布尔值，为true时对应的key会被作为样式名加入到class中
        - ng-class="{'red':true,'blue':false,'green':false,'fontSize':true,'coler':true}"

- ng-hide/ng-show
 + ng-hide：需要一个布尔值：当为true时为隐藏当前元素
 + ng-show: 需要一个布尔值：当为true时为显示当前元素

- ng-if:需要一个布尔值：当为true时为显示当前元素
                       为false时是删除当前元素
    + ng-if 产生的作用域问题在另一个文档中有详细说明 这里就不做阐述了
- ng-switch:与ng-switch-when同用，类似与js中的switch case
    例：
```html
    <div ng-switch="name">
            <div ng-switch-when="小明">我是小明</div>
            <div ng-switch-when="小红">我是小红</div>
            <div ng-switch-when="小月">我是小月</div>
    </div>
```

### 其他常用指令

- ng-checked：
  + 单选/复选是否选中,是单向数据绑定
- ng-selected：
  + 是否选中
- ng-disabled：
  + 是否禁用
- ng-readonly：
  + 是否只读

### 常用事件指令

不同于以上的功能性指令，Angular还定义了一些用于和事件绑定的指令：

- ng-blur：失去焦点
- ng-focus：获得焦点
- ng-change：改变事件
- ng-copy：复制事件
- ng-click： ng-click="add()"
- ng-dblclick：双击事件
- ng-submit： 表单提交事件

### 指令的标准使用方式
data-xxx,在使用angular指令时，只需要在原先的指令前加上data-前缀。
x-

### MVC 思想

#### 什么是 MVC 思想
- M:Model 模型  :数据存储，一些业务逻辑
- V:View  视图 ：就是用来展示数据  浏览器上的页面
- C:Controller 控制器: 调度业务逻辑


#### MVVM
- M：
- V:
- VM: ViewModel-  $scope


### 模块(module)
- angular.module('myApp',[])
  > 第一个参数是模块的名字
  > 第二个参数是一个数组，数组的元素是该模块所依赖其他模块的名字
*注意,即使不依赖任何模块，也需要给第二个参数传递一个空数组*
*否则angular.module('myApp')就是去获取名为myApp的模块对象*

### 控制器(controller)
- angular.module('myApp',[]).controller('demoController',function($scope){})
> 第一个参数，是控制器的名字
> 第二个参数，是一个回调函数，在回调函数里写我们想要的js代码。

### 双向数据绑定
- 数据模型的值发生改变，就会导致页面值的改变.
  页面值的改变，就会导致数据模型值的改变，这各种相互影响的关系就是双向数据绑定。
- ng-model

### 单向数据绑定
- 使用表达式显示数据模型的值。


### $watch
- 用于监视数据模型的变化（并且只能监视数据模型的变化）
- $scope.$watch('数据模型名的字符串形式',function(变化后的值,变化前的值){})
- $scope.$watch里的回调函数会默认执行一次。



## CDN - 扩展内容
content delivery network
内容分发网络

- 速度快
- 减轻了服务器自身在带宽压力。


#### angular相关的插件
- batarang插件 --> 必须翻墙


### Angular VS jQuery

- jQuery:库
    + 封装了一些常用的方法，我们主动调用这些方法
- Angular:框架
    + 框架提供了一些结构或者模式，
    + 我们按照框架提供的规则去写代码
    + 然后由框架自己去执行相应的操作

 - 思想上:
    jQuery: 提高了dom操作的开发效率。
    Angular: 不提倡dom操作，几乎没有dom操作(底层还是操作的dom)
        + angular中操作dom `angular.element()` ,叫做jqLite
### angular.element
- 轻量级的jQuery,
*注意：在获取dom对象时传入的参数是一个原生dom对象*





### $scope

- 视图和控制器之间的数据桥梁
- 用于在视图和控制器之间传递数据
- 用来暴露数据模型（数据，行为）

![$scope](./scope.png)

### ViewModel

- $scope 实际上就是MVVM中所谓的VM（视图模型）
- 正是因为$scope在Angular中大量使用甚至盖过了C（控制器）的概念，所以很多人（包括我）把Angular称之为MVVM框架
- 这一点倒是无所谓，具体看怎么用罢了
- 判断 是不是双向数据绑定


## 模块

### 模块的创建
> 通过`anuglar.mdoule()`方法来创建模块.

    *注意,如果传入两个参数就是去创建模块，如果只传入第一个参数，就会变成获取模块。*

### 模块的划分式

#### 1.根据项目中具体的功能去划分模块

#### 2.根据具体的文件功能的类型去划分模块

## 控制器的创建方式

### 传统的方式创建控制器(不推荐使用这种方式)

```javascript
    // 通过全局函数来创建控制器
        // angular会把我们创建的全局函数作为控制器使用
        function demoController($scope){
            $scope.name='小明';
        }
```

### 面向对象的方式创建控制器

```html
    <div ng-controller="demoController as obj ">
        {{obj.name}}
        {{age}}
    </div>
    <!-- 1.引入angular.js文件 -->
    <script src="node_modules/angular/angular.js"></script>
    <script>
        // 3.创建模块
        var app =angular.module('myApp',[]);

        // 4.创建控制器
        app.controller('demoController',function($scope){
            // 可以当作构造函数来使用
            this.name="小明";
            $scope.age=12;
        })
    </script>
```

### 安全的创建控制器的方式
- 原因：angular在控制器的回调函数中是通过参数名来传递参数的。
- 项目上线 代码压缩后会报错
- 通过将第二个参数改为数据组：数据的最后一个参数还是原来的fucntion,数据前的参数是我们想要anuglar传递的参数的字符串形式，fucntion里的参数需要与数组前面的元素一对应。
`app.controller('demoController',['$scope','$log',function($scope,$log){}])`



### 依赖注入的原理
- 参数必须正确传递 不能乱写 比如$scope $log 等 不能用其他字符代替 否则会报错
- 核心是toString()  用正则截取参数
- 获取函数形参的方式


### 总结Angular开发流程

0.通过npm/bower/暴力的方式/cdn 拿到想到angular.js文件。
1.在HTML代码中引入angular.js这个文件
2.在HTML代码上加上ng-app指令，告诉angular来管理我们的代码，这个指令只能使用一次
3.在JS代码中通过`angular.module('模块名',[])`创建一个模块，然后在HTML中的ng-app指令指定一下模块名'ng-app="模块名"'
4. 在JS代码中创建控制器`xxx.controller('控制器的名字',function(){})`,在HTML代码中通过ng-controller指令由我们当前的控制器来管理数据模型`ng-controller="控制器的名字"`
5. 建模（根据页面原型抽象出数据模型）, 最终得到视图模型(ViewModel)
6. 通过`$scope`来暴露页面上所需要使用的一些数据
7. 在HTML代码中通过`ng-model/ng-click/{{}}` 将刚刚暴露的数据绑定到页面上去
8. 在JS中写一些具体业务相关的代码



### 相关链接

- AngularJS 1.x 官方网站
  + https://angularjs.org/
- AngularJS 2.x 官方网站
  + https://angular.io/
- Google Material Design for Angular
  + https://material.angularjs.org
- Angular UI（Angular最大的第三方社区）
  + http://angular-ui.github.io/
- AngularJS中文社区
  + http://www.angularjs.cn/
- AngularJS中文社区提供的文档（不用翻墙）
  + http://docs.angularjs.cn/api
  + http://www.apjs.net/