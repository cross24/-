#javascript笔记之数据类型
  
    javascript数据类型包括：原始数据类型 和 复杂数据类型

## 一、基本数据类型

    javascript有6种原始数据类型：Undefined、Null、Boolean、Number、String、
    
    Symbol（ES6新增）。

## 1.1  Undefined类型
    
    undefined类型只有一个值，即Undefined。

    在什么情况下变量的值为Undefined呢？通常我们认为变量声明但未初始化时，变量会默

    认为Undefined。

    对于var、let 、const声明的变量都是这样吗？
    
    我们来看看三者在声明变量但不初始化情况下的结果：
    
    let a;
    alert(a);   // "undefined"

    var b;
    alert(b);  //"undefined"

    const c;
    alert(c);  //  Missing initializer in const declaration

    所以我们发现var 和let 声明的变量未初始化会被默认为undefined,const声明的变量
    必须要初始化。


    那么值为undefined的变量与未声明的变量又有什么区别呢？
    
    1、一个为undefined，一个报错
    var message;
    // var age;未声明

    alert(message)    //"undefined"
    alert(age)        // 报错
    对于未声明的变量，只能执行一种操作，即typeof,其他都会报错
   
    2、利用typeof检测数据类型，得到的都是undefined
    alert(typeof message)   // undefined
    alert(typeof age)       // undefined

## 1.2 Null类型

    Null类型是第二个只有一个值的数据类型，这个特殊的值是null。从逻辑角度来看，null值表示一
    个空对象指针，而这也正是使用typeof操作符检测null值时会返回"object"的原因((typeof 
    car) //"object")

    如果定义变量准备在将来用于存放对象，那么最好将该变量初始化为null而不是其他值，这样一来，只要检查是否为null值就可以知道相应的变量是否已经保存了一个对象的引用。

## 1.3 Boolean类型
    
    1、Boolean类型只有两个字面值：true和false
    2、Boolean类型字面值区分大小写（True和False都不是Boolean值）
    3、任何类型的值都可以通过Boolean()函数转化为Boolean类型值:
        String:空字符串转化为false,其他字符串都转化为true;
        Number:0/NaN转化为false,其他数字都转化为true;
        Object:null转化为false,其他对象都转化为true;
        Undefined:转化为false

        对于if(){}这种流控制语句都会自动调用Booelan()转化为Boolean值再进行判断

 ## 1.4 Number类型
   
    Number类型可以表示整数和浮点数值
   
    1、整数（支持各种进制整数）
        var intNum = 55;   // 十进制整数
        var intNum8 = 055  // 八进制整数
        var intNum16 = 0xA  // 16进制
        在进行算术计算时，所有以八进制和十六进制表示的数值都会转化为十进制进行运算。
    
    2、浮点数值：
        var floatNum = 1.1;
        由于浮点数值需要的内存空间是保存整数值的两倍，因此ECMAScript会不失时机的将浮点数值转化为整数值，所以：
            var floatNum = 1.; //小数点后面没有数字---解析为1
            var floatNum = 1.0 //整数--解析为1
    
    3、NaN
        NaN即非数值（Not a Number）是一个特殊的数值，这个数值用于表示一个本来要返回数值的操作数未返回数值的情况（例如  10/aaa）
        NaN两大特点：
        （1）任何涉及NaN的操作（例如NaN/10）都会返回NaN
         (2) NaN与任何值都不想等，包括NaN本身（alert( NaN == NaN)  // false）
        针对NaN这两个特点，ECMAScript定义了isNaN()函数，isNaN()在接收到一个值后会尝试将这个值转化为数值，，任何不能被转化为数值的值都会导致这个函数返回true。

    4、数值转化：
        有三个函数可以把非数值转化为数值:Number()、parseInt()、parseFloat()。
        Number()函数可以用于任何数据类型，而另两个函数专门用于把字符串转化成数值
    
## 1.5 String类型
   
    如何转化为字符串？
   
    1、toString():数值、布尔值、都用toString()方法，null和undefined没有这个方法。
        多数情况下调用toString()不必传递参数，但是在调用数值的toString()方法时，可以传递一个参数，输出数值的基数
   
    2、String():
        如果值有toString()方法，则调用该方法并返回相应的结果。
        如果值是null，则返回null,如果是undefined，则返回undefined.
   
    3、+"":要把数值转化为字符串，可以用加号和" "拼接。

## 1.6 Object类型：
   
    Object的每个实例都有以下属性和方法：
   
    1、constructor:保存着用于创建当前对象的函数
   
    2、hasOwnProperty(属性名)：用于检查给定的属性在当前对象实例中（而不是在实例的原型中）是否存在，其中，作为参数的属性名必须以字符串的形式指定
   
    3、isPrototypeOf(object):用于检查传入的对象是否是当前对象的原型。
   
    4、propertyIsEnumerable(属性名)：用于检查给定的属性是否能够使用for-in语句来枚举。


