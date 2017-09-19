声明式渲染 组件化  渐进式框架

vue

调试模式

当 Vue.config.debug 设置为 true 时，Vue 会

打印所有警告的栈的追踪记录
让所有 DOM 里的锚结点都采用注释结点。这会让审查元素结构变得更容易。
调试模式在压缩过的生产版本中是不可用的。

严格模式

默认情况下，Vue 组件从继承链（通过 Vue.extend() 创建）和它在视图里的父组件那里继承所有的资源。在严格模式下，组件只能继承从类继承的资源，不能从父视图层次继承。当启用了严格的模式时，资源应该是全局性的，或者是依赖于需要它们的组件。使用严格模式，能更好的封装组件和增加大型的项目的可重用性。

改变分隔符 (Delimiters)

如果设置了文本插值的分隔符，HTML 插值的分隔符也将改变。只需要用文本分隔符符最外面的字符再包裹一层


weexs vue-native
通用
盒子模型
flex布局
定位

	transform
	transition
	伪类 :focus active disabled wnabled
	background-image linear-gradient
	box-shadow for IOS active, focus, disabled, enabled inset(可选),offset-x,offset-y, blur-radius,color
	opacity
	background-color
文字

	text input 
	color line font-size font-style font-weight text-decoration text-align text-family text-overflow

事件

	touch(start move end) pan(start move end horizantal vertical) swipe longpress
	属性 direction （swipe） changetouches(数组)
事件冒泡

	stopPropagation
	在事件处理函数中，可以使用 e.stopPropagation() 方法，来阻止本次事件向上的传递过程。注意，e.stopPropagation() 与 bubble="true" 不同，前者只会影响当前元素以及父元素的传播，不会影响子元素的传播；后者是为了版本兼容而增加的开关机制，会全局关闭或者开启冒泡机制，两者可以共同存在使用，