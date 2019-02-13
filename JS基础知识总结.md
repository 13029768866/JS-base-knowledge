# 一、变量

## 1.1、变量提升

    =>当栈内存(作用域)形成，JS代码自上而下执行之前，浏览器首先会把所有带 “VAR”/“FUNCTION” 关键词的进行提前 “声明” 或者 “定义” ，这种预先处理机制称之为 “变量提升”


    =>声明(declare)：var a  （默认值undefined）
    
    =>定义(defined)：a=12 （定义其实就是赋值操作）


    [变量提升阶段]
    
    =>带“VAR”的只声明未定义
    
    =>带“FUNCTION”的声明和赋值都完成了


    =>变量提升只发生在当前作用域（例如：开始加载页面的时候只对全局作用域下的进行提升，因为此时函数中存储的都是字符串而已）
    
    =>在全局作用域下声明的函数或者变量是“全局变量”，同理，在私有作用域下声明的变量是“私有变量” [带VAR/FUNCTION的才是声明]


    =>浏览器很懒，做过的事情不会重复执行第二遍，也就是，当代码执行遇到创建函数这部分代码后，直接的跳过即可（因为在提升阶段就已经完成函数的赋值操作了）

## 1.2、变量相关问题

[**1、有无var的区别.html**](https://github.com/13029768866/JS-base-knowledge/blob/master/1%E3%80%81%E5%8F%98%E9%87%8F%E9%97%AE%E9%A2%98%E5%88%86%E6%9E%90/1%E3%80%81%E6%9C%89%E6%97%A0var%E7%9A%84%E5%8C%BA%E5%88%AB.html)

[**2、条件判断下的变量提升**](https://github.com/13029768866/JS-base-knowledge/blob/master/1%E3%80%81%E5%8F%98%E9%87%8F%E9%97%AE%E9%A2%98%E5%88%86%E6%9E%90/2%E3%80%81%E6%9D%A1%E4%BB%B6%E5%88%A4%E6%96%AD%E4%B8%8B%E7%9A%84%E5%8F%98%E9%87%8F%E6%8F%90%E5%8D%87.html)

[**3、重名问题处理.html**](https://github.com/13029768866/JS-base-knowledge/blob/master/1%E3%80%81%E5%8F%98%E9%87%8F%E9%97%AE%E9%A2%98%E5%88%86%E6%9E%90/3%E3%80%81%E9%87%8D%E5%90%8D%E9%97%AE%E9%A2%98%E5%A4%84%E7%90%86.html)

[**4、暂时性死区.html**](https://github.com/13029768866/JS-base-knowledge/blob/master/1%E3%80%81%E5%8F%98%E9%87%8F%E9%97%AE%E9%A2%98%E5%88%86%E6%9E%90/4%E3%80%81%E6%9A%82%E6%97%B6%E6%80%A7%E6%AD%BB%E5%8C%BA.html)

[**5、全局变量和私有变量.html**](https://github.com/13029768866/JS-base-knowledge/blob/master/1%E3%80%81%E5%8F%98%E9%87%8F%E9%97%AE%E9%A2%98%E5%88%86%E6%9E%90/5%E3%80%81%E5%85%A8%E5%B1%80%E5%8F%98%E9%87%8F%E5%92%8C%E7%A7%81%E6%9C%89%E5%8F%98%E9%87%8F.html)

[**6、arguments简单了解.html**](https://github.com/13029768866/JS-base-knowledge/blob/master/1%E3%80%81%E5%8F%98%E9%87%8F%E9%97%AE%E9%A2%98%E5%88%86%E6%9E%90/6%E3%80%81arguments%E7%AE%80%E5%8D%95%E4%BA%86%E8%A7%A3.html)

[**7、JS中的堆棧内存释放.html**](https://github.com/13029768866/JS-base-knowledge/blob/master/1%E3%80%81%E5%8F%98%E9%87%8F%E9%97%AE%E9%A2%98%E5%88%86%E6%9E%90/7%E3%80%81JS%E4%B8%AD%E7%9A%84%E5%A0%86%E6%A3%A7%E5%86%85%E5%AD%98%E9%87%8A%E6%94%BE.html)

![变量相关7图解](./images/变量相关7答案.png)[**8、堆栈内存释放问题.html**](https://github.com/13029768866/JS-base-knowledge/blob/master/1%E3%80%81%E5%8F%98%E9%87%8F%E9%97%AE%E9%A2%98%E5%88%86%E6%9E%90/8%E3%80%81%E5%A0%86%E6%A0%88%E5%86%85%E5%AD%98%E9%87%8A%E6%94%BE%E9%97%AE%E9%A2%98.html)

![变量问题7图解](./images/变量问题8答案.png)

# 二、面向对象OOP

## 2.1、单例模式（Singleton pattern）

```
高级单例模式形式：
组成：命名空间 ， 闭包 ， 返回值是一个对象存放需要暴露方法
var nameSpace = (function () {
    function fn(){

    }
    return {
        fn: fn
    }
})()
```

### 2.1.1、单例设计模式优点

1. 防止冲突。
2. 使用方便。（工作使用单例模式封装utils）

```
//	=>	魏振江
var wzjRender = (function () {
    var fn = function () {
        
    };
    return {
        init: function () {

        },
        fn:fn
    }
})();
skipRender.init();


//	=>	魏振江1
var wzj1Render = (function () {
    var fn = function () {

    };
    return {
        init: function () {
            fn();//=>调取自己模块中的方法直接调取使用即可
            wzjRender.fn();//=>调取别人模块中的方法
        }
    }
})();
weatherRender.init();
```

### 2.1.2、单例模式习题

[**1、单例模式小练习.html**](https://github.com/13029768866/JS-base-knowledge/blob/master/2%E3%80%81%E9%9D%A2%E5%90%91%E5%AF%B9%E8%B1%A1/1.1%E3%80%81singleton-pattern%E5%B0%8F%E7%BB%83%E4%B9%A0.html)

![单例模式练习图解](./images/单例练习答案.png)

## 2.2、对象，类，实例的区别

```
面向对象编程，需要我们掌握：“对象、类、实例” 的概念
    对象：万物皆对象
    类：对象的具体细分（按照功能特点进行分类：大类、小类）=>JS中的基本数据类型
    实例：类中具体的一个事物（拿出类别中的具体一个实例进行研究，那么当前类别下的其它实例也具备这些特点和特征）
```

### 2.2.1、JS中类的详细分析

![](./images/JS中的类.png)

## 2.3、构造函数

```
  基于构造函数创建自定义类（constructor）
    1.在普通函数执行的基础上“new xxx()”，这样就不是普通函数执行了，而是构造函数执行，当前的函数名称之为“类名”，接收的返回结果是当前类的一个实例
 
    2.自己创建的类名，最好第一个单词首字母大写
 
   3.这种构造函数设计模式执行，主要用于组件、类库、插件、框架等的封装，平时编写业务逻辑一般不这样处理
```

### 2.3.1、JS中创建值类型的两种方式

1、字面量方式

```
var obj = {};
```

2、构造函数模式

```
var obj = new Object();
=> 注意构造函数创建的是引用数据类型。
```

### 2.3.2、普通函数和构造函数执行区别

1、普通函数执行

```
1.形成一个私有的作用域
2.形参赋值
3.变量提升
4.代码执行
5.栈内存释放问题
```

2、构造函数执行

```

```

