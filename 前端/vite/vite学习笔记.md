**vite的依赖预构建**：

首先vite会找到对应的依赖，然后调用esbuild(对js语法进行处理的一个库)，将其它规范的代码转换成esmodule规范，然后放到当前目录的node_modules/.vite/deps，同时对esmodule规范的各个模块进行统一集成

他解决了三个问题：

1.不同的第三方包会有不同的导出格式（vite无法约束的事情）

2.对路径的处理上可以直接使用/node_modules/.vite/deps,方便路径重写

3.多网络包传输的性能问题（也是原生esmodule规范不敢支持node_modules的原因之一）有了依赖预构建以后无论有多少额外的export和import,vite都会尽可能的将他们进行最后只生成一个或几个模块

（多网络包传输问题是指：浏览器通过路径查找获取文件依赖都通过网络请求的方式，造成了网络性能问题）

通过配置vite.config.js可指定进行依赖预构建的模块

```
optimizeDeps:{
 exclude:[], //将指定数组中的依赖不进行依赖预构建
}
```

小知识：为什么vite.config.js可以书写成esmodule的形式，这是因为vite在读取这个文件的时候会率先node去解析文件语法，如果发现是esmodules规范则将esmodules规范替换成commonjs规范