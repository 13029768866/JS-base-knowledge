# HTML

# CSS

# JS

## 1、变量问题

```
1、有无var
	有var：变量，跟window.变量名存在映射关系
	无var：本质就是window属性
2、环境
	全局（window）:全局变量
	私有作用域：私有变量（形参赋值，变量声明）
3、条件判断
	1、首先无论条件是否成立都会进行变量声明提升
	2、函数特殊：老板本浏览器声明并且赋值，新版本浏览器为了迎合es6的块级作用域，类似变量值声明不赋值。
4、重名问题
	不会重新声明，但是会重新赋值。
5、let/const
	没有变量提升，不能重复声明，使用其浏览器会进行重复性检测
	typeof a的结果是undefined，但是es6语法声明a会直接报错，解决原有的JS死区
```



## 、谈谈你对面向对象的理解？

```
JS是基于一门面向对象编程思想开发出来的语言。
比如：数组是Array的实例，函数是Function的实例，对象是Object的实例，JS有很多的内置类，内置类上绑定了许多属性和方法

1、封装：
	提取公共方法
	目的：实现'低耦合，高内聚'
2、多态：
	JS中没有严格意义上的多态
	1）重载：方法名相同，参数的个数和数据类型不相同，执行不同方法（后端重载的意义是为了抗压），JS中没有重载
	2）重写：子类重写父类的方法
3、继承：
	1）原型链继承：
	子类的原型指向父类的实例  B.portotype = new A();
	
	缺点：
	1>	父类的私有属性和公有属性都变成子类的共有属性	
	2>	子类原型上原有的方法会失效
	3>	子类和父类仍然存在关系，可以重写父类原型上的方法,可能对父类的其他实例造成影响			  
		B.prototype.__proto__.getX
		
	2)call继承
	把父类当成普通函数执行，把this指向子类的实例，相当于给子类的实例添加属性和方法
	A.call(this)
	
	缺点：
	这种只能继承父类的私有属性，并不能继承父类原型上的属性
	
	3）组合继承
	通过call继承父类的私有属性，然后让子类原型等于父类原型 B.prototype = A.prototype
	
	缺点：
		1>	子类和父类仍然存在关系，可以轻易重写父类原型上的方法,可能对父类的其他实例造成影响	
		2>	子类原型上原有的方法会失效
	
	4）寄生组合式继承
	通过call继承父类的私有属性，通过Object.create()方法继承父类公有属性，这个方法可以创建一个空对象并使其__proto__指向传入的第一个对象参数	B.prototype = Object.create(A.prototype)
	
	5）	ES6继承
	class和extends
	所有私有属性放在constructor里面，方法放在类里，static设置私有方法
	
	缺点：
	ES6并不能设置父类原型上的公有属性
```

## 、call,apply,bind的区别？

```
1、在严格模式下，不传参数this是undefined；非严格模式下，不传参数，或者参数是null/undefined，this指向window
2、call和apply区别是传参不同，call传参是一个一个传，apply的参数是一个数组
3、bind语法call一模一样，区别在于call函数是立即执行的，而bind是等待执行
```

## 、谈谈你对This的理解？

```
1、给元素的某个事件绑定方法，
    this-->元素本身
2、函数执行，
    严格模式下this-->undefined,
    非严格模式this-->window，
    其余看‘.’前面的主体，this-->函数调用者
3、构造函数或者类
	this-->当前类的实例
4、箭头函数
	箭头函数中没有this，this-->上下文中的this
5、改变this指向,call，apply，bind
```

## 、数组相关问题

### 1.数组去重

```
Array.prototype.myUnique = function myUnique(){
	let obj = {};
	for(let i = 0;i < this.length; i++){
		let item = this[i];
		// 判断对象中是否存在这个属性？不存在加入，存在把最后一项赋值给当前项，数组长度减一，i--继续当前循环
		obj.hasOwnProperty(item)? (this[i] =this[this.length -1],this.length--,i--):obj[item] =item;
	}
	obj = null;
	return this
}
```



## 、谈谈你对MVC和MVVM理解

```
MVC和MVVM是两种设计模式，后端多用MVC，前段多用MVVM
1、MVC
	M（model）:数据层，负责数据处理
	V(view):视图层，用户看到并与之交互的界面
	C(controller):控制器层，M和V的中间人
优点：
	1、三者完全独立耦合性低，M和V复用性高
	2、部署快，生命周期成本低
	3、维护性高
缺点：
	1、不适合小，中型项目
	2、M和V完全隔离只能通过C访问

2、MVVM
	VM：对C进行拆解，让M和V通过VM实现数据驱动，主要内容业务逻辑，网络请求，数据缓存
优点：
	1、数据驱动
	2、通过VM实现双向数据绑定
```

