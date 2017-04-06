    $(function() {

        // =============方法调用============
        init();


        var Data = {};
        // ================方法定义============
        function init() {
            getTOP10Data();
        }
        // 熱門品牌排行數據請求

        function getTOP10Data() {
            $.ajax({
                url: 'http://139.199.157.195:9090/api/getbrandtitle',
                success: function(data) {
                    Data = data;
                    rendom();
                }
            });
        }

        // 对数据渲染并控制 
        function rendom() {
            alert(22)
            var newData = { result: [] };

            // 页面一打开就加载10条数据
            if (Data.result.length <= 8) {
                leng = Data.result.length;
            }
            var leng = 10;
            for (var i = 0; i < leng; i++) {
                newData.result.push(Data.result.shift());
            }
            var html = template('top10Tmp', newData);
            // 用html会覆盖页面原先的内容
            $('.contant').append(html);
        }

        // 页面滚动事件 满足条件就渲染剩下的数据
        $(window).scroll(function() {
            if (Data.result.length == 0) {
                return;
            }
            // ul还有剩余的多少没有加载出来
            // var height = $('.contant > ul').height() + $('#header').height() + $('#footer').height() - $(document.body).height();
            // console.log('body:' + $(document.body).height());
            // console.log(window.innerHeight);
            var dis = window.innerHeight - $(document.body).scrollTop() - 100;
            // console.log(dis);
            // 如果剩下的高度不足50 就渲染数据
            console.log(dis)
            if (dis < 50) {
                console.log('数据加载了')
                rendom();
            }
        })
    });     //数据的渲染
            render();
        }
    }
})