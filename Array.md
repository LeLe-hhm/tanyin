<script>
   /*数组的操作方法（concat,slice,splice）*/
    //concat()
    //    concat()方法可以基于当前数组中的所有项创建一个新数组。
    //    具体来说，这个方法会先创建当前数组一个副本，然后将接收到的参数添加到这个副本的末尾，最后返回新构建的数组。
    //    在没有给 concat()方法传递参数的情况下，它只是复制当前数组并返回副本。
    //    如果传递给 concat()方法的是一或多个数组，则该方法会将这些数组中的每一项都添加到结果数组中。
    //    如果传递的值不是数组，这些值就会被简单地添加到结果数组的末尾。
    var colors = ["red", "green", "blue"];
    var colors2 = colors.concat("yellow", ["black", "brown"]);
    console.log(colors); //red,green,blue
    console.log(colors2); //red,green,blue,yellow,black,brown

    //slice()
    //    slice()，它能够基于当前数组中的一或多个项创建一个新数组。
    //    slice()方法可以接受一或两个参数，即要返回项的起始和结束位置。
    //    在只有一个参数的情况下， slice()方法返回从该参数指定位置开始到当前数组末尾的所有项。
    //    如果有两个参数，该方法返回起始和结束位置之间的项——但不包括结束位置的项。
    //    注意， slice()方法不会影响原始数组。
    var colors = ["red", "green", "blue", "yellow", "purple"];
    var colors2 = colors.slice(1);
    var colors3 = colors.slice(1, 4);
    console.log((colors2)); //green,blue,yellow,purple
    console.log((colors3)); //green,blue,yellow

    //splice()
    //splice()主要是向数组的中部插入项
    //    删除：可以删除任意数量的项，只需指定 2 个参数：要删除的第一项的位置和要删除的项数。
    //    例如， splice(0,2)会删除数组中的前两项

    //    插入：可以向指定位置插入任意数量的项，只需提供 3 个参数：起始位置、 0（要删除的项数）
    //    和要插入的项。如果要插入多个项，可以再传入第四、第五，以至任意多个项。
    //    例如，splice(2,0,"red","green")会从当前数组的位置 2 开始插入字符串"red"和"green"。

    //    替换：可以向指定位置插入任意数量的项，且同时删除任意数量的项，只需指定 3 个参数：起
    //    始位置、要删除的项数和要插入的任意数量的项。插入的项数不必与删除的项数相等。
    //    例如，splice (2,1,"red","green")会删除当前数组位置 2 的项，然后再从位置 2 开始插入字符串"red"和"green"。
    var colors = ["red", "green", "blue"];
    var removed = colors.splice(0, 1); // 删除第一项
    console.log((colors)); // green,blue
    console.log((removed)); // red，返回的数组中只包含一项
    removed = colors.splice(1, 0, "yellow", "orange"); // 从位置 1 开始插入两项
    console.log((colors)); // green,yellow,orange,blue
    console.log((removed)); // 返回的是一个空数组
    removed = colors.splice(1, 1, "red", "purple"); // 插入两项，删除一项
    console.log((colors)); // green,red,purple,orange,blue
    console.log((removed)); // yellow，返回的数组中只包含一项
   
   /*数组的方法（检测，转换，增删，查找位置）*/
   var arr = new Array();
    var arr = [1, 2, 3];
    //1.检测数组
    console.log(typeof arr);//object
    console.log(arr instanceof Array);//true
    console.log({} instanceof Array);//false

    //Array.isArray([])ES5方法，低版本不兼容
    console.log(Array.isArray([]));//true
    console.log(Array.isArray({}));//false

    //调用Array类型
    console.log(Object.prototype.toString.call(arr));//[object Array]
    //call强制调用，替换方法里的this

    console.log(Object.prototype.toString.apply(arr));//[object Array]

    //2.转换数组
    console.log(arr);//[1, 2, 3]
    //先以对象的形式输出 刷新把直接量输出 其实就是调用了valueOf
    console.log(arr.valueOf()); //[1, 2, 3]
    //某种程度上说 它就是调用了toString
    console.log(arr.toString()); //1,2,3
    //toString就是调用了join 把每一项的值取出来用逗号拼接
    console.log(arr.join());//1,2,3
    //如果不传参数 默认使用逗号拼接
    console.log(arr.join("-"));//1-2-3
    //传入参数 会用这个参数去拼接每一项

    //3.增删方法
    var arr = [1, 2, 3];
    console.log(arr.push(1, 2, 3, 4));//7 //同时加入多个
    console.log(arr.push(0));//8 //从后面加入 返回新数组的长度
    console.log(arr.pop());//0 //从后面删除 返回删除的元素
    console.log(arr.shift());//1 //从前面删除 返回删除的元素
    console.log(arr.unshift(0));//7 //从前面添加 返回新数组的长度

    //4.查找位置
    var arr = ["a", "a", "z", "a", "x", "a"];
    console.log(arr.indexOf("a"));//0 //从左往右找到第一个
    // 把这个元素的索引返回 然后就没有然后了
    console.log(arr.lastIndexOf("a"));//5 //找的是最后一个
    //["c", "a", "z", "a", "x", "a"]找到数组中每一个a出现的位置
    console.log(arr.indexOf("a", 0));//0
    console.log(arr.indexOf("a", 1));//1 //从1开始 包括1
    console.log(arr.indexOf("a", 2));//3
    console.log(arr.indexOf("a", 1 + 1));//3
    console.log(arr.indexOf("a", 3 + 1));//5
    console.log(arr.indexOf("a", 5 + 1));//-1
   
   
   
   /*数组的排序方法（sort,reverse）*/
   //sort(),reverse()
    //reverse()将原数组中的元素顺序翻转，创造新数组并返回（会改变原数组）
    var arr = [1, 2, 3, 4];
    console.log(arr.reverse());//[4,3,2,1]
    console.log(arr);//[4,3,2,1]

    //sort()将数组的元素做原地排序，并返回该数组
    //    默认情况下， sort()方法按升序排列数组项——即最小的值位于最前面，最大的值排在最后面。
    //    为了实现排序， sort()方法会调用每个数组项的 toString()转型方法，然后比较得到的字符串，以
    //    确定如何排序。即使数组中的每一项都是数值， sort()方法比较的也是字符串，如下所示。
    var values = [0, 1, 5, 10, 15];
    values.sort();
    alert(values); //0,1,10,15,5

    //    比较函数接收两个参数，如果第一个参数应该位于第二个之前则返回一个负数，如果两个参数相等
    //    则返回 0，如果第一个参数应该位于第二个之后则返回一个正数。以下就是一个简单的比较函数：
    function compare(value1, value2) {
        if (value1 < value2) {
            return -1;
        } else if (value1 > value2) {
            return 1;
        } else {
            return 0;
        }
    }
    var values = [0, 1, 5, 10, 15];
    values.sort(compare);
    alert(values); //0,1,5,10,15

    //一般使用，简化版本
    function compare(value1, value2){
        return value2 - value1;//从大到小
        return -(value2 - value1);//从小到大
    }
</script>

