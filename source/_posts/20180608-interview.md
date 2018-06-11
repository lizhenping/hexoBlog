---

title: interview总结

date: 2018-06-08 10:33:35

tags: interview

---

此博文主要是用于介绍interview的经验总结,仅针对个人哈,不足的地方还望多多指教.联系邮箱:1305177077@qq.com

原文转载: https://blog.csdn.net/lhf2009913/article/details/24013315

问题集锦大杂烩:
### 问题1：this的典型用法
### 问题2：display:none & visibility:hidden & opacity:0 的区别 
<!--more-->
## 问题1：this的典型用法
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

  
  

## 问题2：display:none & visibility:hidden & opacity:0 的区别
#### 2.1空间占据问题
1.display:none ->彻底消失,不在文档流中占位,浏览器也不会解析该元素,visibility:hidden是视觉上消失了,在文档流中占位,浏览器会解析该元素;
2. visibility:hidden在性能上高于display:none,是因为display切换时,页面产生回流[当页面中的一部分元素需要改变尺寸,布局,显示隐藏等,页面重新构建等,属于回流]; 3.简而言之,display会引起回流跟重绘,而visibility跟opacity只进行重绘.
#### 2.2子继承问题
1.display:none:不会被子元素继承,但是父亲不在了,子自然就不会显示了.皮之不存,毛之安附  
2.visibility: hidden,会被子继承,可通过visibility:visible使子元素显示出来  
3.opacity:0,也会被子元素继承,但是不能通过opacity:0使其子元素重新显示  
#### 2.3事件绑定
1display:none 的元素都已经不再页面存在了,因此肯定也无法触发它上面绑定的事件        
2visibility:hidden 元素上绑定的事件也无法触发       
3pacity: 0元素上面绑定的事件是可以触发的
```
<div class="div1" @click='btnEvent()'>  
    <p>display:none</p>  
</div>  
<div class="div2" @click='btnEvent()'>  
    <p>visibility:visible</p>  
</div>  
<div class="div3" @click='btnEvent()'>  
    <p>opacity:0</p>  
</div>  
<div>测试display,visibility,opacity是否占据文档流</div>
 .div1,
 .div2,
 .div3 {
  width: 200px;
  height: 200px;
  background: #ccc;
  margin-top: 10px;
}
 .div1 {
  display: none;
}
 .div1 p {
  display: block;
}
 .div2 {
  visibility: hidden;
}
 .div2 p {
  visibility: visible;
}
 .div3 {
  opacity: 0;
}
 .div3 p {
  opacity: 1;
}

```