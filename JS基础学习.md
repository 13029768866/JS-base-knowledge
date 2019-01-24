# 一、书籍推荐

1. 犀牛书
2. 你不知道的JS
3. JS高程
4. ES6入门

# 二、变量（variable）

## 2.1、定义

它不是具体的值，只是一个用来存储具体值得容器后者代名词

## 2.2、声明方式

1. var(ES3)
2. function--(函数名也是变量，只不过存储的值是函数类型)
3. let (ES6)
4. const (ES6)  
5. import (ES6)
6. class (ES6)

## 2.3、变量提升机制

1. var变量声明提升值为undefined，function不光变量声明提升还进行赋值操作
2. 函数执行开辟私有作用域，先执行变量声明提升，再形参赋值
3. 写不写var的区别

```
console.log(a);       	=>undefined
console.log(window.a); 	=>undefined
var a = 12;			
console.log(a);			=>12
console.log(window.a);	=>12


console.log(a);       	=>报错
console.log(window.a); 	=>undefined
a = 12;					=>解析为window.a的简写
console.log(a);			=>12
console.log(window.a);	=>12

结论：有var的本质是一个变量，没有var的本质是window下的一个属性，window的属性和变量名相同的存在映射关系。
```

### 2.3.1、变量提升小栗子

```
console.log(a,b);  		=>undefined，undefined
var a=12,
b= 12;
function fn(){
    console.log(a,b);	=>undefined,12
    var a = b =13;
    console.log(a,b);   =>13,13             
}
fn();
console.log(a,b);		=>12,13
```



# 三、数据类型

## 3.1、分类

1. 基本数据类型

   ```
   number--数字
   string--字符串
   boolean--布尔
   null
   undefined
   ```

2. 引用数据类型

   ```
   object--对象
   	普通对象、数组对象、正则对象、日期对象
   ```

3. Symbol--唯一的值

## 3.2、数据类型转化特殊情况

1. **只有0/NaN/空字符串/null/undefined转化成布尔类型值为false,其余都为true**
2. **{}+'str'=>NaN,对象拼接字符串会转化成数字类型运算**

## 3.3、数据类型检测方法

1. typeof  =>只能区分简单数据类型，null和所有复杂数据类型返回【Object,Object】
2. instanceof
3. constructor
4. Object.prototype.toString.call()

# 四、JS对象运行机制简单分析

1. 当浏览器（内核/引擎）渲染和解析JS时候，会提供一个供JS代码运行的环境，我们称为‘全局作用域（global / window scope）’
2. 代码自上而下执行，从左到右，从里到外
3. **基本数据类型按值操作**
4. **引用数据类型现在堆内存开辟空间，然后对象按照键值对，函数存储函数体字符串，并且此空间有一个16进制地址**
5. **switch case中每一种case比较都是基于“===”来完成的**

## 4.1、小栗子

```
 var obj = {
     n:10,
     m:obj.n*10
 }
 console.log(ojb.m);
 =>Uncaught TypeError: Cannot read property 'n' of undefined
 
 // 答案解析
 1、现在堆内存开辟空间，存储键值对，并解析
 2、变量声明提升obj只定义，未赋值，是undefined
 3、基本数据类型没有属性
 
 
 let obj = {
     n:10,
     m:obj.n*10
 }
 console.log(ojb.m); 
=>Uncaught ReferenceError: obj is not defined

// 答案解析
let没有变量声明提升，堆内存解析obj.m时候找不到obj
```

## 4.1、小栗子1

```
  var num = parseInt('width:35.5px');
        if(num == 35.5){
            alert(0);            
        }else if(num == 35){
            alert(1);            
        }else if(num == NaN){
            alert(2);            
        }else if(typeof num == ‘number’){
            alert(3);            
        }else{
            alert(4);            
        }
// 答案 =>  字符串3
// 解析
1、parseInt遇见一个非有效数字字符返回结果,所以是NaN
2、NaN ！= NaN
3、NaN的数据类型是number
4、alert返回的结果是string类型
```

# 五、JS函数的运行机制简单分析

