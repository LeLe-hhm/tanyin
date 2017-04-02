$(function () {

    /*========方法的调用========*/
    init();
    var Data = {};
    /*========方法的定义========*/

    /*初始化*/
    function init() {
        getInlandDiscount();
    }
    /*请求国内折扣数据*/
    function getInlandDiscount() {
        $.get(url, function (res) {
            //用一个中间空对象来存储数据
            Data = res;
            console.log(res.result.length)
            //渲染数据方法的调用
            render();
        })
    }

    /*渲染数据*/
    function render() {
        //八条数据一组加载
        var newData = { result: [] };
        var leng = 8;
        //当剩余的数据不足八条的时候做一个判断 并给length赋值Data数据的length
        if (Data.result.length <= 8) {
            leng = Data.result.length;
        }
        for (var i = 0; i < leng; i++) {
            // 需要加载data.result的第一条数据，并且，加载完了之后 要删除掉第一条数据。然后把剩下的数据都往前面移动一个位
            // shift:从集合中把第一个元素删除，并返回这个元素的值。
            newData.result.push(Data.result.shift());
        }
        var html = template("模板ID", newData);
        //这里不能用jquery的html()方法 
        $("容器盒子").append(html);
        flag = false;
    }
    //加一个开关 防止数据请求时模板有意外的报错 保险做法
    var flag = false;
    //窗口滚动事件
    window.onscroll = function () {
        当数据加载完 或flag为真 就return 不向下执行了
        if (Data.result.length == 0 || flag) {
            return;
        }
        // 多余的总高度
        //要是页面还有其他模块自己添加
        var height = $("一般是ul").height() + $("页面头部区域").height() + $("页面底部").height() - $(document.body).height();
        //disBottom表示ul还剩下多少高度         用户滑动的距离
        var disBottom = height - $(document.body).scrollTop();
        // console.log(disBottom);
        //50 可以自己定义
        if (disBottom < 50) {
            // console.log("加载数据")
            flag = true;
            //数据的渲染
            render();
        }
    }
})