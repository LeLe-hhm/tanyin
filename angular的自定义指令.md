## angular的自定义指令

### 首先列举一些angular的内部指令
1. ng-app:相当于一个入口，告诉angular来管理我们页面的Html代码
2. ng-click:用于注册点击事件
3. ng-model:用于进行双向数据绑定，
4. ng-init:用于初始化数据模型
5. ng-controller:指向了创建的控制器。
6. ng-bind:也是能够绑定数据模型的值,只能作用于双标签元素
7. ng-cloak:利用了angular会移除所以样式名为ng-cloak的样式的特性。
8. ng-bind-html:用于安全的渲染html代码
9. ng-repeat:渲染数据列表, ng-repeat="item in data  track by $index"
10. ng-class:操作样式{key001:样式名001,key002:样式名002}['key001']
                {'样式名001':布尔值,'样式名002':布尔值}
11.ng-hide/ng-show:显示或隐藏页面元素
12.ng-if/ng-switch ng-switch-when




### 自定义指令简单介绍及使用
- 自定义指令无外乎增强了HTML,提供了额外的功能 (复用、封装)
- 内部指令基本能满足我们的需求。
- 少数情况下我们有一些特殊的需要，可以通过自定义指令的方式实现：

- 通过 模块对象的directive方法创建
    + 有两个参数，第一个参数，是指令的名字：必须是驼峰命名法命名
                  第二个参数和控制器的第二个参数一样,在第二个参数的function里直接返回的一个obj对象
    + 使用时：需要将指令的名字转成小写，并以-分割原先在大小写字母
---javascript
    var app = anrular.module('myApp',[]);
    app.directive('myDirective'[function(){
        var obj = {
            template:<button>这是按钮</button>,

           // 或者是外联式
            templateUrl:'文件路径'

           // 或者是script标签 (type = 'text/ng-temolate',并且有id)
           templateUrl:'script的id'
        }
        return obj;
    }])
--
    +页面引用
        <div my-directive></div>

### 自定义指令中回函数里返回的对象的属性
- template:需要一个字符串，最终这个字符串值被被添加到自定义指令所在标签的innerHTML位置
- templateUrl:需要一个字符串，这个字符串是一个文本文件的路径,anuglar最终会异步请求这个文件，把拿到的内容插入到自定义指令所在的标签的innerHTML位置,
该字符串也可以是script标签的id值，把script标签中的内容当作模板字符串来使用
注意：script的type属性需要为"text/ng-template"

- restrict:也是需要一个字符，可以是A,E,C,M 这4个字符中任何一个，也可以任意的组合，A:以属性的形式使用，E:以自定义标签的形式使用，C:表示以类样式名的形式使用，M:以注释的形式使用
- replace: 需要一个布尔值，为true,会将自定义指令所在的标签替换为模板字符串。

- transclude:转置，是需要一个布尔值，为true时会把自定义指令所在标签的innerHTML值添加到模板字符串中，需要与ng-transclude指令配合使用，ng-transclude指令需要将值插入到哪个元素的innerHTML位置.不能与replace指令同用。

- scope:需要一个对象，可以获取到自定义指令所在标签的属性值：
    {
        属性名:'@test', 属性值需要以@开头,@后面是自定义指令所在标签的属性名，最终在模板字符串中通过表达式可以使用scope的属性名可以直接输出

        test:'@'// 是简写方式
    }
- link:指向一个function，这个function有三个参数：
    + scope: 类似于控制器中的$scope,也可以暴露一些值。
    + element:这是一个jqLite对象，是自定义指令所在标签的jqLite对象
    + attributes:是自定义指令所在标签的所以属性的集合.



## todomvc案例


### todomvc 简单介绍


### todomvc 功能分析

1.显示数据列表
2.添加任务

3.删除任务
    - 使用了数组的splice

4.修改任务
- 只是改变页面是否可以编辑的一个状态


5.切换是任务是否完成的状态

6.批量的切换任务是否完成的状态
    - 使用了ng-change事件

7.清除已完成任务
- 尽量不要在循环中添加或删除数组元素。

7.1 控制清除已完成任务按钮的显示与否 

8.显示未完成的任务数
- 是给ng-bind指定一个方法,方法最终会返回一个具体的值,
- ng-bind 会把这个值渲染到页面。

9.切换不同状态任务的显示与否



## 过滤器(filter)

### 格式化数据的过滤器
- currency 将数字转成货币的形式显示
><!-- 语法在数据模型后面加上 |currency  
        参数，通过冒号:的方式传递-->
    <p>{{money | currency :'￥' }}</p>

- date 将整数形式的日期转换为用户能够识别的形式;
><!-- 语法在数据模型后面加上 |currency  
        参数，通过冒号:的方式传递-->
    <p>{{money | currency :'￥' }}</p>

- limitTo 是控制字符串显示的长度
    + 有两个参数，第一个表示需要显示长度
                第二个表示从哪个索引开始显示

- orderBy,需要一个字符串作为参数：这个字符就是数组中元素的一个属性名
    ,默认是按升序排列的，如果给这个字符前加上一个-号表示降序排列.

- json

- 在js中使用过滤器的方式

```javascript
    // $filter其实是个方法
           // 第一个参数:就是过滤器的名字
           // 会返回一个方法
           //               + 至少有一个参数(就是使用到的数据)
           //               + 其他的参数依次是过滤器所使用到的参数
           var tmp = $filter('date')($scope.myDate,'yyyy年MM月-dd日 HH:mm:ss')
           $scope.tmp=tmp;
```

- 1234588910120
- 1234567891011

### 过滤数据的过滤器
- filter
- 一般是与ng-repeat指令共同使用
- 参数：可以是一个普通类型-angular会对这样的参数进行全局匹配;
        也可以是一个object对象-angular就会根据对象中的属性及属性值去数据中的每一个元素中寻找相应的属性，当前属性值相等的时候数据就会被显示。
