### minimist使用说明

- 参数说明

```
minimist(args,opts={})
```

**args：** 

node执行指令的参数，一般取process.argv.slice(2) ；

process.argv返回一个数组，第一个元素固定为启动 Node.js 进程的可执行文件的绝对路径名；

第二个元素固定为正在执行的 JavaScript 文件的路径 之后的元素才是实际传参；

**opts：**

  对于命令参数的处理规则设定说明：

  opts.string - 字符串或字符串数组，其元素对应的指令参数将始终被当作字符串

  opts.boolean - 布尔值、字符串或字符串数组，其元素对应的指令参数将始终被处理为布尔值。如果设置为布尔值true则所有带有双横线“--”且没有“=”的参数将被处理为布尔值

  opts.alias - 一个对象（其所有元素值为字符串）或两个字符串数组，用来为参数设置别名

  opts.default - 一个对象，将参数（元素名）映射为指定的默认值

  opts.stopEarly - 值为true时，将第一个非参数字符串之后的所有参数放入argv._

  opts['--'] - 值为true时，将双横线“--”以前的所有参数放入argv._ ，将双横线之后的所有参数放入argv['--']

  opts.unknown - 定义一个函数，当出现opts中未定义的指令参数，该函数将会被调用。如果该函数返回false，则未知的参数将不会被放入argv。

- 示例

  

```
// minimist-test.js

const minimist = require('minimist');
var miniArgv = minimist(process.argv.slice(2));
console.log(miniArgv);
```

```
 node minimist-test.js hello c=1 -r --t yy  r --s true  false  --oo  --test=build
 // 输出
 {
  _: [ 'hello', 'c=1', 'r', 'false' ], //被独立处理为字符串的放这
  r: true,
  t: 'yy',
  s: 'true',
  oo: true, // --后面什么也没有被处理为Boolean值为true
  test: 'build' // --后面有等于所以build被处理为字符串
}
```

