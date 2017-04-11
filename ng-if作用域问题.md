## AngularJS中的作用域

### 问题引入

 - 使用 Angular 进行过一段时间的开发后，基本上都会遇到一个这样的坑：

        <div ng-controller="TestCtrl">
        <p>{{name}}</p>
        <div ng-if="show">
            <input type="text" ng-model="name">
        </div>
        </div>
        <script>
        function TestCtrl($scope){
            $scope.show = true;
            $scope.name = 'htf';
        }
        把 p 元素和 input 元素绑定同一个变量，你本以为，在输入框输入内容，p 中显示的肯定也是随之变化的。

        然而并不是这样，不管 input 中的元素怎么变， p 元素中的都没变化，WTF。

        要说这是什么原因，那就要从 Angular 的作用域说起了。

        作用域

        每个 Angular 应用默认有一个根作用域 $rootScope， 根作用域位于最顶层，从它往下挂着各级作用域。

        通常情况下，页面中 ng-model 绑定的变量都是在对应的 Controller 中定义的。如果一个变量未在当前作用域中定义，JavaScript 会通过当前 Controller 的 prototype 向上查找，也就是作用域的继承。

 ### 这又分两种情况
- 基本类型变量

            <div ng-controller="OuterCtrl">
            <p>{{x}}</p>
            <div ng-controller="InnerCtrl">
                <input type="text" ng-model="x">
            </div>
            </div>
            <script>
            function OuterCtrl($scope){
                $scope.x = 'hello';
            }
            function InnerCtrl($scope){
            }
            运行后会发现跟文章开头一样的问题，里面输入框变了，外面的没跟着变。

            原因在于，InnerCtrl 中并未定义 x 这个变量，取值的时候，会沿着原型链向上找，找到了 OuterCtrl 中定义的 x ，然后赋值给自己，在 InnerCtrl 的输入框输入值时，改变的是 InnerCtrl 中的 x ，而对 OuterCtrl 中的 x 无影响。此时，两个 x 是独立的。

            不过，如果你不嫌麻烦的话，用 $scope.$parent 可以绑定并影响上一层作用域中的基本变量：


            <input type="text" ng-model="$parent.x">


- 引用类型变量

        那么，如果上下级作用域想共用变量怎么办呢？

        答案是使用引用类型变量。

        <div ng-controller="OuterCtrl">
        <p>{{x}}</p>
        <div ng-controller="InnerCtrl">
            <input type="text" ng-model="x">
        </div>
        </div>
        <script>
        function OuterCtrl($scope){
            $scope.data = {};
            $scope.data.x = 'hello';
        }
        function InnerCtrl($scope){
        }
        在这种情况下，两者的 data 是同一个引用，对这个对象上面的属性修改，是可以反映到两级对象上的。

        ng-if中的作用域

        前面讲的是两级控制器之间的作用域，那跟前面提到的问题有什么关系呢？那个看着不是只有一个 Controller 吗？

        其实，并不是只有 Controller 可以创建作用域，ng-if 等指令也会（隐式地）产生新作用域。

        总结下来就是，ng-if、 ng-switch 、 ng-include 等会动态创建一块界面的东西，都是自带一级作用域。

        因此，在开发过程中，为了避免模板中的变量歧义，应当尽可能使用命名限定，比如 data.x，出现歧义的可能性就比单独的 x 要少得多。

###总结

        始终将页面中的元素绑定到对象的属性（data.x）而不是 直接绑定到基本变量（x）上。