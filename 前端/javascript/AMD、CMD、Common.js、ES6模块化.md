

1）**AMD**是Requirejs的标准规范，Requirejs是AMD标准规范的实现。类似JavaScript语言是对ECMAScript规范的实现。

**Requirejs**：是一个AMD框架，异步加载js文件，通过define()函数定义，第一个参数是一个数组，里面定义需要依赖的包；第二个参数是回调函数，通过变量引用模块里面的方法，最后通过return输出。

是一个**依赖前置**、**异步定义**的AMD框架，在定义时需要用到别的模块，就在最前面的数组里面引入。

示例：

``````
define(['package/lib'],function(lib){
	function hello(){
		lib.log('hello');
	}
	return {
		hello:hello
	}
})
``````

2）**CMD**是**SeaJS**的标准规范，是一个同步模块定义。SeaJS是对CMD的实现。（同步是指依赖库执行是在代码运行时在引入的地方执行，RequireJS在引入依赖时就预先执行）

通过define()定义，没有依赖前置，CMD是依赖就近，哪里需要使用依赖就在哪里引入。

示例：

``````
define(function(){
	var $ = require('jquery')
})
``````

3）**CommonJS规范**：node.js的模块系统就是参考遵循了CommonJS规范。浏览器不兼容CommonJS的根本原因在于缺少Node.js的四个环境变量：

- module
- exports
- require
- global

浏览器一般使用AMD、CMD、ES6等定义的模块化开发的。

4）**ES6特性，模块化通过export/import对模块进行导出导入**。