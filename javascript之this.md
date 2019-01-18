# javascript中的this

this关键词是javasscript中最复杂机制之一，它是一个很特别关键词，被自动定义在所有函数的作用域中。
在javascript中this和其他语言有很大不同，比如java中this是在代码的执行阶段是不可更改的，而javascript中的this是在调用阶段进行绑定的，因

为这一性质使得this难以捉摸，在严格模式和非严格模式下表现不一样，在函数的不同调用方式中this也有区别。所以想对this进行一个总结，希望自己能

对this彻底搞清楚，也加深自己的理解。

## 为什么要使用this

竟然this这么复杂，为什么我们还需要花时间去搞懂它，它到底能给我们带来什么好处呢？下面我们来看一个简单例子：
```
var me = {
    name:'cross'
};
var you = {
    name:'bryant'
}
function speak(){
    console.log("Hello,I'm "+this.name);
}
speak.call(me);    // Hello,I'm cross
speak.call(you);   //  Hello,I'm bryant
```
这段代码，我们看到在不同上下文(对象me,you)中重复使用函数speak(),不用针对每个对象编写单独函数。

如果不使用this,我们需要显示传入一个上下文对象，如下：
```
var me = {
    name:'cross'
};
var you = {
    name:'bryant'
}
function speak(obj){
    console.log("Hello,I'm "+obj.name);
}
speak(me);    // Hello,I'm cross
speak(you);   //  Hello,I'm bryant
```
显然，this提供了一种更优雅的方式来隐士“传递”一个对象引用，因此可以将API设计的更加简洁并且易于复用,随着你的使用模式越来越复杂，显示传递上下文对象会让代码变得越来越混乱，使用this则不会这样。

## this到底是什么

之前我们说过this是在运行时绑定，并不是在编写时绑定.它的上下文取决于函数调用时的各种条件，this的绑定和函数声明的位置没有任何关系，只取决于函数的调用方式。

当一个函数被调用时，会创建一个活动记录（又称为执行上下文），这个记录会包含函数在哪里被调用（调用栈）、函数的调用方法、传入的参数等信息.this就是记录其中一个属性，会在函数执行的过程中用到。

this既不指向函数自身也不指向函数的词法作用域.this实际上是在函数被调用时发生的绑定,它指向什么完全取决于函数在哪里被调用。

## 绑定规则
### 1、默认绑定
首先要介绍的是最常用的函数调用类型：独立函数调用,可以把这条规则看作是无法应用其他规则时的默认规则。
思考一下下面的代码：
```
function foo(){
    console.log(this.a);
}
var a = 2;
foo();   // 2
```
当调用foo()时，this.a被解析成了全局变量a,为什么？因为在本例子中，函数调用时应用了this的默认绑定，因此this指向全局对象。


参考文章：https://juejin.im/post/59748cbb6fb9a06bb21ae36d
         https://github.com/zchen9/code/issues/1