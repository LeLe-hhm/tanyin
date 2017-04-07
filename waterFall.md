<!DOCTYPE html>
<html lang="en">

<head>
    <meta charset="UTF-8">
    <title></title>
    <style>
    * {
        margin: 0;
        padding: 0;
    }
    
    #container {
        overflow: hidden;
    }
    
    .box {
        float: left;
        border: 1px solid #ccc;
        padding: 5px;
    }
    </style>
</head>

<body>
    <div id="container">
        <!--(.box>img[src="images/P_00$.jpg"])*9-->
        <div class="box"><img src="images/P_000.jpg" alt="" /></div>
        <div class="box"><img src="images/P_001.jpg" alt="" /></div>
        <div class="box"><img src="images/P_002.jpg" alt="" /></div>
        <div class="box"><img src="images/P_003.jpg" alt="" /></div>
        <div class="box"><img src="images/P_004.jpg" alt="" /></div>
        <div class="box"><img src="images/P_005.jpg" alt="" /></div>
        <div class="box"><img src="images/P_006.jpg" alt="" /></div>
        <div class="box"><img src="images/P_007.jpg" alt="" /></div>
        <div class="box"><img src="images/P_008.jpg" alt="" /></div>
        <div class="box"><img src="images/P_009.jpg" alt="" /></div>
        <div class="box"><img src="images/P_010.jpg" alt="" /></div>
        <div class="box"><img src="images/P_011.jpg" alt="" /></div>
        <div class="box"><img src="images/P_012.jpg" alt="" /></div>
        <div class="box"><img src="images/P_013.jpg" alt="" /></div>
        <div class="box"><img src="images/P_014.jpg" alt="" /></div>
        <div class="box"><img src="images/P_015.jpg" alt="" /></div>
        <div class="box"><img src="images/P_016.jpg" alt="" /></div>
        <div class="box"><img src="images/P_017.jpg" alt="" /></div>
        <div class="box"><img src="images/P_018.jpg" alt="" /></div>
        <div class="box"><img src="images/P_019.jpg" alt="" /></div>
        <div class="box"><img src="images/P_000.jpg" alt="" /></div>
        <div class="box"><img src="images/P_001.jpg" alt="" /></div>
        <div class="box"><img src="images/P_002.jpg" alt="" /></div>
        <div class="box"><img src="images/P_003.jpg" alt="" /></div>
        <div class="box"><img src="images/P_004.jpg" alt="" /></div>
        <div class="box"><img src="images/P_005.jpg" alt="" /></div>
        <div class="box"><img src="images/P_006.jpg" alt="" /></div>
        <div class="box"><img src="images/P_007.jpg" alt="" /></div>
        <div class="box"><img src="images/P_008.jpg" alt="" /></div>
        <div class="box"><img src="images/P_009.jpg" alt="" /></div>
        <div class="box"><img src="images/P_010.jpg" alt="" /></div>
        <div class="box"><img src="images/P_011.jpg" alt="" /></div>
        <div class="box"><img src="images/P_012.jpg" alt="" /></div>
        <div class="box"><img src="images/P_013.jpg" alt="" /></div>
        <div class="box"><img src="images/P_014.jpg" alt="" /></div>
        <div class="box"><img src="images/P_015.jpg" alt="" /></div>
        <div class="box"><img src="images/P_016.jpg" alt="" /></div>
        <div class="box"><img src="images/P_017.jpg" alt="" /></div>
        <div class="box"><img src="images/P_018.jpg" alt="" /></div>
        <div class="box"><img src="images/P_019.jpg" alt="" /></div>
    </div>
    <script>
    /*思路： 1.第一列的图片浮动，然后再找出这一列中高度最小的那一张
                                    涉及图片属性要写在入口函数中 不然获取不到图片资源 会报错
                                    2.下面紧跟的那一张定位到这个位置
                                            */
    window.onload = function() {
        (function(window, undefined) {
            /*
                这里为甚么不能用querySelectorAll 不能获取后面动态生成的div.box元素
                要用 demo.children 获取所有的盒子
            var boxs = document.querySelectorAll('.box');*/
            
            // 获取外部容器盒子
             var container = document.querySelector('#container');
            // var container = document.getElementById("container");
            var boxs = container.children; //所有的盒子
            // 每一个盒子的宽度
            var picWidth = boxs[0].offsetWidth;
            // 计算一行有多少张图片
            var screenWidth = window.innerWidth; // 屏幕的宽度
            var rowNum = Math.floor(screenWidth / picWidth);
            // 把每一列的高度取出来 然后求出高度最小值
            var arrHeight = []; //用来存放图片的高度

            function fail() {
                // 遍历第一列的图片 把每一张的图片的高度值存放在数组中
                for (var i = 0; i < boxs.length; i++) {
                    if (i < rowNum) {
                        arrHeight[i] = boxs[i].offsetHeight;
                    } else {
                        // 给除了第一列的元素加上定位
                        boxs[i].style.position = 'absolute';
                        // 用getMIn函数求出高度最小值及索引
                        var minHeight = getMin(arrHeight).value;
                        var minIndex = getMin(arrHeight).index;
                        // 给下一个元素定位
                        boxs[i].style.top = minHeight + "px";
                        boxs[i].style.left = minIndex * picWidth + "px";
                        // 更新数组在的值
                        // 添加一张图片后，数组中的最小值加上添加上去的这张图片的高度
                        arrHeight[minIndex] = minHeight + boxs[i].offsetHeight;
                    }
                }
            }
            fail();
            // 页面滚动事件
            window.onscroll = function() {
                if (isBottom()) {
                    // 触底了 要加载图片了
                    var json = [{
                        "src": "images/P_000.jpg"
                    }, {
                        "src": "images/P_001.jpg"
                    }, {
                        "src": "images/P_002.jpg"
                    }, {
                        "src": "images/P_003.jpg"
                    }, {
                        "src": "images/P_004.jpg"
                    }, {
                        "src": "images/P_005.jpg"
                    }, {
                        "src": "images/P_006.jpg"
                    }, {
                        "src": "images/P_007.jpg"
                    }, {
                        "src": "images/P_008.jpg"
                    }, {
                        "src": "images/P_009.jpg"
                    }, ];

                    for (var i = 0; i < json.length; i++) {
                        var div = document.createElement("div");
                        var img = document.createElement("img");
                        div.className = 'box';
                        container.appendChild(div);
                        img.src = json[i].src;
                        div.appendChild(img);
                        fail();
                    }
                }
            }


            // var screenH = window.innerHeight;
            // var pageY = window.pageYOffset;
            // var lastboxHeight = boxs[boxs.length - 1].offsetTop;
            // console.log(screenH);
            // console.log(pageY);
            // console.log(lastboxHeight);
            // 触底判断
            function isBottom() {
                // 页面的高度 + 被卷去的高度 > 最后的盒子的高度 表示触底了
                var screenH = window.innerHeight;
                var pageY = window.pageYOffset;
                var lastboxHeight = boxs[boxs.length - 1].offsetTop;
                if (screenH + pageY > lastboxHeight) {
                    return true;
                }
                // 没有触底
                return false;
            }

            // 分装一个函数 实现数组中最小值及索引的查找并返回
            function getMin(array) {
                var minValue = array[0],
                    minIndex = 0,
                    obj = {},
                    i;
                for (i = 0; i < array.length; i++) {
                    if (minValue > array[i]) {
                        minValue = array[i];
                        minIndex = i;
                    }
                }
                obj.value = minValue;
                obj.index = minIndex;
                return obj;
            }
        })(window)
    }
    </script>
    <!-- <script>
    //因为涉及到了图片宽高 所以要写在window.onload里面

    //第一行是通过左浮动 自然摆放
    //后面是通过JS计算 高度最小的那一行 然后把图片放到那个位置
    window.onload = function () { 
        //找人
        var container = document.getElementById("container");
        var boxes = container.children;//所有的盒子
        //1.找出谁是第一行
        //计算第一行有多少张 或者也就是 页面上有多少列
        //一行有多少张实际上 就是    页面的宽度 / 盒子的宽度
        //页面宽度
        var pageWidth = window.innerWidth;
        //盒子的宽度
        var boxWidth = boxes[0].offsetWidth;
        var column = Math.floor(pageWidth / boxWidth);//都是整数 所以要向下取整
        //console.log(column);
        //2.用一个数组保存 每一列的高度 找出最小值 和最小值的索引
        var arrHeight = [];
        //把每一列的初始高度 保存到数组中
        function waterfall() {
            //找出所有的盒子并处理
            for (var i = 0; i < boxes.length; i++) {
                //先只找出第一行的所有的盒子
                if (i < column) {
                    //boxes[i]//第一行的盒子
                    //把第一行的盒子的高度放到数组中
                    arrHeight[i] = boxes[i].offsetHeight;
                } else {
                    //第一行盒子之后的盒子
                    //根据 保存每行高度的数组中的 最小值去摆放
                    var minHeight = getMin(arrHeight).value;//最小的高度
                    var minHeightIndex = getMin(arrHeight).index;//高度最小的那一列
                    //摆放盒子其实就是设置盒子的top和left
                    //要想设置位置 先要加定位
                    boxes[i].style.position = "absolute";
                    //设置top值 top值就是高度最小的那一列现在的高度
                    boxes[i].style.top = minHeight + "px";
                    //设置left值 left值就是 高度最小的那一列所有图片的offsetLeft
                    //其中第一行的最好找
                    boxes[i].style.left = boxes[minHeightIndex].offsetLeft + "px";
                    //放置图片后 当前列的高度发生了变化 我们要对数组的值进行更新
                    //然后 后续的循环才能根据新的数组 来重新寻找最小值

                    //给数组中之前 数值最小的那一项  加上当前这个图片的高度
                    //在之前的高度的基础上 再加上 新加入的图片的高度
                    arrHeight[minHeightIndex] = minHeight + boxes[i].offsetHeight;
                }
            }
        }

        waterfall();
        //console.log(arrHeight);
        //console.log(minHeight);
        //console.log(minHeightIndex);

        //5.判断触底
        window.onscroll = function () {
            if (bottomed()) {
                //alert("触底了,要加载图片了");
                //加载图片
                var json = [
                    {"src": "images/P_000.jpg"},
                    {"src": "images/P_001.jpg"},
                    {"src": "images/P_002.jpg"},
                    {"src": "images/P_003.jpg"},
                    {"src": "images/P_004.jpg"},
                    {"src": "images/P_005.jpg"},
                    {"src": "images/P_006.jpg"},
                    {"src": "images/P_007.jpg"},
                    {"src": "images/P_008.jpg"},
                    {"src": "images/P_009.jpg"},
                ];
                //.box>img
                for (var i = 0; i < json.length; i++) {
                    //json[i]//每一条数据
                    var div = document.createElement("div");
                    div.className = "box";
                    container.appendChild(div);
                    var img = document.createElement("img");
                    img.src = json[i].src;
                    div.appendChild(img);
                    //新加载出来的盒子 样式有问题 需要重新通过JS设置位置
                    waterfall();

                }
            }
        };

        function bottomed() {
            //窗口的高度+页面被卷去的头部 > 最后一个盒子的offsetTop
            //窗口的高度
            var clientHeight = window.innerHeight;
            //页面被卷去的头部
            var scrollTop = window.pageYOffset;
            //最后一个盒子的offsetTop
            var lastBox = boxes[boxes.length - 1];//最后的盒子
            var lastBoxTop = lastBox.offsetTop;
            //窗口的高度+页面被卷去的头部 > 最后一个盒子的offsetTop
            if (clientHeight + scrollTop > lastBoxTop) {
                return true;//表示触底了
            }
            return false;//没有触底
        }

    };


    function getMin(arr) {
        var min = {};
        min.index = 0;//最小值的索引
        min.value = arr[min.index];//最小值的值
        //遍历数组 一个一个比较
        for (var i = 0; i < arr.length; i++) {
            if (min.value > arr[i]) {
                min.value = arr[i];
                min.index = i;
            }
        }
        return min;
    }

</script> -->
</body>

</html>
