## 一、数据类型

### 1.1基本类型与扩展类型

TypeScript与javascript共享相同的基本类型，并新增以下类型

- 元组Tuple
- 枚举enum
- Any与Void

```js
// 数字，二、八、十六进制都支持
let decLiteral: number = 6;
let hexLiteral: number = 0xf00d;

// 字符串，单双引都行
let name: string = "bob";
let sentence: string = `Hello, my name is ${ name }.

// 数组，第二种方式是使用数组泛型，Array<元素类型>：
let list: number[] = [1, 2, 3];
let list: Array<number> = [1, 2, 3];

let u: undefined = undefined;
let n: null = null;
```

## 二、常见问题

### 2.1 给window对象添加属性提示语法错误

动态声明:

```
(<any>window)['il8n'] = il8n;
```

