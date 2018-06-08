---
title: interview总结
date: 2018-06-08 10:33:35
tags: interview
---
此博文主要是用于介绍interview的经验总结,仅针对个人哈,不足的地方还望多多指教.联系邮箱:1305177077@qq.com  
原文转载: https://blog.csdn.net/lhf2009913/article/details/24013315  

## 问题1：this的典型用法
<!--more-->  
原则所在: 调用函数的那个对象.
1.纯粹函数调用,比如下面这种情况,指的就是全局的global对象.  
```
     var x = 1;
    function test() {
        this.x = 0;
    }
    test();
    alert(x);//0
```

2.作为构造函数调用[生成新的一个对象,this则指向这个对象].    
```
    function test() {
        this.x = 1;
    }
    var o = new test();
    alert(o.x); //1
```   

3.作为方法调用,那么this就是指这个上级对象,相当于是对象属性是方法.  
    function test() {
        alert(this.x);
    }
    var o = {};
    o.x = 1;
    o.m = test;
    o.m(); //1

4.还有apply调用,this指向的是apply的第一个参数,若参数没有指定,则表示全局的对象哇.   
var x = 0;
function test() {
    alert(this.x);
}

var o = {};
o.x = 1;
o.m = test;
o.m.apply(); //0
o.m.apply(o);//1
