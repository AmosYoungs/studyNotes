# node.js模块化理解

Node.js采用Common.js规范，在Nodejs中将代码合理拆分到不同的文件中，每一个文件就是一个模块，文件路径就是模块名。

在编写每个模块时，都有require,exports,modules三个预先定义好的变量提供使用。

> Node.js中模块分类

- 核心模块（已经封装好的内置模块）
- 自定义模块
- 第三方模块（npm下载的第三方模块）

## 模块的导出

exports导出模块 ，require导入模块。还有一种使用module.exports导出，系统默认是module.exports，并默认导出一个空对象，exports只是module.exports指向内存指针的一个拷贝，因而只能设置或更改导出属性。

代码示例：

> 示例一

a.js

```
let a = 1;
let b = 2;
```

index.js

```
let a = require("./a")
console.log(a)
```

**执行node index.js结果：默认导出空对象**

```
{}
```

> 示例二

修改a.js

```
let a = 1;
let b = 2;

exports.a = a
module.exports.b =b 
```

**输出结果：说明exports和module.exports操作同一个对象exports = module.exports**

```
{ a: 1, b: 2 }
```

> 示例三

修改a.js

```
let a = 1;
let b = 2;

exports.a = a
module.exports.b =b 
exports = {user:'tt'} 
```

**输出结果：exports指向了新的对象，不影响a.js导出对象，exports只是module.exports的一个指针拷贝，exports只能设置导出属性，module.exports才能修改导出对象**

```
{ a: 1, b: 2 }
```

## 模块的初始化

一个模块中的js代码仅在模块第一次被使用时执行，并且在使用过程中进行初始化，之后缓存起来便于后续使用。