
## js执行机制
js是单线程 == 同步 
为了避免阻塞 引入异步 另一个线程 管理异步任务
主线程完成任务 查询异步任务 异步任务符合条件 加入主线程
主线程完成任务 插队

setTimeout	在异步队列里创建一个函数，时间到了，符合条件。可以在时间后输入参数
setInterval	在异步队列里创建一个函数，每当时间到了，符合条件。

try{} catch(error){} error{}


异步编程的解决方案
回调函数 node
promise 
async
ES6诞生以前，异步编程的方法，大概有如下四种：回调函数、事件监听、发布/订阅、Promise对象；ES6中，引入了Generator函数；ES7中，async更是将异步编程带入了一个全新的阶段。

异步任务必须指定回调函数，当主线程开始执行异步任务，就是执行对应的回调函数。


建立主线程 判断引入异步 符合条件 主线程完成 异步的回调函数进入主线线程。
Prpromiseomise > setImmediate > setTimeout(0)

### promise

    var promise = new Promise(function(resolve, reject) {
    		// ... some code
    		if( /* 异步操作成功 */ ) {
    			resolve(value);
    		} else {
    			reject(error);
    		}
    });

	promise(function(){
		//... some code
	})

|方法|参数|描述|
|---|---|---|
|then|/|原型方法|
|catch|/|原型方法|
|all|flex-start flex-end center space-between space-around|父极 副轴 行距|
|race|row row-reverse column column-reverse|父极 主轴方向|
|resolve|nowrap wrap wrap-reverse|父极 换行 不换行 换行 向副轴反方向换行|
|reject|/|父极主轴方向 换行|
|try|flex-start flex-end center space-between space-around|提案|
|done|number 默认0|附加方法|
|finally|number 默认0|附加方法|

### callback
callback 函数是一种以参数形式传递给另一个函数的函数。
回调函数不一定是异步的，回调函数是一种在异步操作

如果您的网站上存在多个 AJAX 任务，那么您应该为创建 XMLHttpRequest 对象编写一个标准的函数，并为每个 AJAX 任务调用该函数。
该函数调用应该包含 URL 以及发生 onreadystatechange 事件时执行的任务（每次调用可能不尽相同）：
	
	function f1(f){
		if(/* 异步操作成功 */)
		f();
	}
	function f2(){
		//...coding
	}
	f1(f2);

### 事件监听

	f1.on('done', f2);
	function f1(){
		setTimeout(function (){
		// f1的任务代码
		f1.trigger('done');
		}, 1000);
	}
	function f2(){
		//...coding
	}
### Generator 

	返回值是Iterator对象
	
	//对象简写 *abc(){}=function* abc(){}
	function *generator(){
		yield 1;
		yield *b;//b 应为有iterator接口、generator对象的对象或generator对象
		let abc=yield;//next可以为abc赋值
	}
	var a=generator();
	a.next();//返回{value,done}


### asytnc await
	
	返回值是promise对象

## 对象

### 工厂模式

	function createPerson(name){
		var o=new Object;
		o.name=name
		o.getname=function(){
			return this.name
		}
	}
### 构造函数
	function Person(name){
		this.name=name;
		this.getname=function(){
			return this.name
		}
	}
### 原型
	function Person(){;}
	person.prototype={
		this.name="name";
		this.getname=function(){
			return this.name
		}
	}
### 构造函数 和 原型的结合
	function Person(){
		this.name=name;
	}
	person.prototype={
		this.getname=function(){
			return this.name;
		}
	}

## this
### 箭头函数 ()=>{}
箭头函数中的 this 确实和调用时的上下文无关 
怎么理解

1.放在初始化里，指向构造函数对象的实例
2.放在方法里，指向对象



实际上箭头函数中并不只是 this 和普通函数有所不同，箭头函数中没有任何像 this 这样自动绑定的局部变量，包括：this，arguments，super(ES6)，new.target(ES6)……
优点 适合函数式编程


point: 需要使用arguments 可使用展开运算符 ...
### call&&applay
1、方法定义
call方法: 
语法：call([thisObj[,arg1[, arg2[,   [,.argN]]]]]) 
定义：调用一个对象的一个方法，以另一个对象替换当前对象。 
说明： 
call 方法可以用来代替另一个对象调用一个方法。call 方法可将一个函数的对象上下文从初始的上下文改变为由 thisObj 指定的新对象。 
如果没有提供 thisObj 参数，那么 Global 对象被用作 thisObj。 

apply方法： 
语法：apply([thisObj[,argArray]]) 
定义：应用某一对象的一个方法，用另一个对象替换当前对象。 
说明： 
如果 argArray 不是一个有效的数组或者不是 arguments 对象，那么将导致一个 TypeError。 
如果没有提供 argArray 和 thisObj 任何一个参数，那么 Global 对象将被用作 thisObj， 并且无法被传递任何参数。