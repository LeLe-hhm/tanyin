<script>
    //    替换子字符串的操作replace()
    //    这个方法接受两个参数：第一个参数可以是一个 RegExp 对象或者一个字符串（这个字符串不会被转换成正则表达式）
    //    第二个参数可以是一个字符串或者一个函数。
    //    如果第一个参数是字符串，那么只会替换第一个子字符串。
    //    要想替换所有子字符串，唯一的办法就是提供一个正则表达式，而且要指定全局（g）标志，
    var text = "cat, bat, sat, fat";
    var result = text.replace("at", "ond");
    console.log(result); //"cond, bat, sat, fat"
    result = text.replace(/at/g, "ond");
    console.log(result); //"cond, bond, sond, fond"

    //    split()，这个方法可以基于指定的分隔符将一个字符串分割成
    //    多个子字符串，并将结果放在一个数组中。
    //    split()方法可以接受可选的第二个参数，用于指定数组的大小，
    //    以便确保返回的数组不会超过既定大小
    var colorText = "red,blue,green,yellow";
    var colors1 = colorText.split(","); //["red", "blue", "green", "yellow"]
    var colors2 = colorText.split(",", 2); //["red", "blue"]
    var colors3 = colorText.split(/[^\,]+/); //["", ",", ",", ",", ""]
   
   //    trim()方法。这个方法会创建一个字符串的副本，删除前置及后缀的所有空格，然后返回结果
    var stringValue = " hello world ";
    var trimmedStringValue = stringValue.trim();
    console.log(stringValue); //" hello world "
    console.log(trimmedStringValue); //"hello world"

    //    涉及字符串大小写转换的方法有 4 个： toLowerCase()、 toLocaleLowerCase()、 toUpperCase()和 toLocaleUpperCase()。
    //    toLowerCase()和 toUpperCase()是两个经典的方法，借鉴自 java.lang.String 中的同名方法
    //    toLocaleLowerCase()和 toLocaleUpperCase()方法则是针对特定地区的实现。
    var stringValue = "hello world";
    console.log(stringValue.toLocaleUpperCase()); //"HELLO WORLD"
    console.log(stringValue.toUpperCase()); //"HELLO WORLD"
    console.log(stringValue.toLocaleLowerCase()); //"hello world"
    console.log(stringValue.toLowerCase()); //"hello world"
   
   //    concat()，用于将一或多个字符串拼接起来，返回拼接得到的新字符串
    var stringValue = "hello ";
    var result = stringValue.concat("world");
    alert(result); //"hello world"
    alert(stringValue); //"hello"

    //    基于子字符串创建新字符串的方法： slice()、 substr()和 substring()
    //    都会返回被操作字符串的一个子字符串，而且也都接受一或两个参数
    //    第一个参数指定子字符串的开始位置，
    //    第二个参数（在指定的情况下）表示子字符串到哪里结束。

    //    slice()和substring()的第二个参数指定的是子字符串最后一个字符后面的位置。
    //    substr()的第二个参数指定的则是返回的字符个数。
    //    如果没有给这些方法传递第二个参数，则将字符串的长度作为结束位置。
    //    与concat()方法一样， slice()、 substr()和 substring()也不会修改字符串本身的值对原始字符串没有任何影响
    var stringValue = "hello world";
    console.log((stringValue.slice(3))); //"lo world"
    console.log((stringValue.substring(3))); //"lo world"
    console.log(stringValue.substr(3)); //"lo world"
    console.log(stringValue.slice(3, 7)); //"lo w"
    console.log(stringValue.substring(3, 7)); //"lo w"
    console.log(stringValue.substr(3, 7)); //"lo worl"

    //    在传递给这些方法的参数是负值的情况下
    //    slice()方法会将传入的负值与字符串的长度相加
    //    substr()方法将负的第一个参数加上字符串的长度，而将负的第二个参数转换为 0。
    //    substring()方法会把所有负值参数都转换为 0
    var stringValue = "hello world";
    console.log(stringValue.slice(-3)); //"rld"
    console.log(stringValue.substring(-3)); //"hello world"
    console.log(stringValue.substr(-3)); //"rld"
    console.log(stringValue.slice(3, -4)); //"lo w"
    console.log(stringValue.substring(3, -4)); //"hel"
    console.log(stringValue.substr(3, -4)); //""（空字符串）
   
   //    用于访问字符串中特定字符的方法是： charAt()和 charCodeAt()
    //    这两个方法都接收一个参数，即基于 0 的字符位置。
    //    其中， charAt()方法以单字符字符串的形式返回给定位置的那个字符
    var stringValue = "hello world";
    alert(stringValue.charAt(1)); //"e"
    //charCodeAt()返还的是字符编码
    var stringValue = "hello world";
    alert(stringValue.charCodeAt(1)); //输出"101"
   
   //    从字符串中查找子字符串的方法： indexOf()和 lastIndexOf()
    //    都是从一个字符串中搜索给定的子字符串，然后返子字符串的位置（如果没有找到该子字符串，则返回-1）。
    //    区别在于： indexOf()方法从字符串的开头向后搜索子字符串，
    //    lastIndexOf()方法是从字符串的末尾向前搜索子字符串
    var stringValue = "hello world";
    console.log(stringValue.indexOf("o")); //4
    console.log(stringValue.lastIndexOf("o")); //7
</script>

