# this在浏览器中与node环境中的困惑？

在node环境中和浏览器中执行相同的js代码，我们发现两者有时执行结果并不一样，我们通过以下代码分析一下原因

```
var a = function () { this.b = 3}
var c = new a();
var b =7;
a();
console.log(b)  // 3
console.log(c.b) // 3
```

在浏览器中打印结果我们知道是```3 3```，分析如下：

1.在javascript中普通函数的this指向调用者，这里的```a()```函数a在全局环境中执行，所以函数执行时this指向全局window对象，并修改了b,因而console.log(b)为3。

2.在javascript中构造函数中this是指向对象实例的，在执行```new  a()```这里执行代码this指向新创建的对象，每一个对象内部都有一个变量b：3。因而console.log(c.b )= 3。

在node环境中我们执行以上代码结果却是：```7 3```

查阅资料我们可以了解到node环境中的全局对象和浏览器中有所不同，在浏览器中的全局对象为window替代了node中的全局对象global,我们在node环境中打印this结果为```{}```,**在函数a内部打印this，发现它打印了全局global，并且在这个全局global中可以看到一个变量b值为3。**而我们定义的b只属于当前的模块，只能在这个模块中使用，要在其他地方使用需要exports出去，并在需要用的地方require,具体了解可以看nodejs作用域 。

