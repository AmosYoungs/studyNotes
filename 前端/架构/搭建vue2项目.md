### 创建一个vue2项目

- 安装node
- 安装脚手架

```
npm install -g @vue/cli
```

- 创建vue项目

方法一：在命令行界面创建进行相关自定义配置

方法二：终端执行`vue ui`，在浏览器可视化界面进行相关自定义配置

### 设置不同开发环境配置

一、在项目跟目录创建``.env.development``（开发环境），``.env.test``（测试环境），``.env.production``（生产环境）

.env.dev(开发环境配置)

```
NODE_ENV = 'development' //模式
VUE_APP_MODE = 'development' //通过VUE_APP_MODE 变量区分环境
VUE_APP_HOST = ''
```

在``package.json``中设置

```
 "scripts": {
    "serve": "vue-cli-service serve",
    "dev": "vue-cli-service serve --mode development", //对应执行开发环境配置
  },
```

测试环境和生产环境类似处理

### vant按需引入

一、安装vant

```
npm install vant
```

二、安装插件

```
// babel-plugin-import 是一款 babel 插件，它会在编译过程中将 import 的写法自动转换为按需引入的方式
npm i babel-plugin-import -D
```

三、配置

```
  // .babelrc中做如下配置
  plugins: [
    ['import', {
      libraryName: 'vant',
      libraryDirectory: 'es',
      style: true
    }, 'vant']
  ]
```



### vantUI的rem处理

引入```px2rem-cunstom```



### IE兼容处理

如果网站需要支持 IE 的话，建议使用库之前先在页面上引入 [current-script-polyfill](https://www.npmjs.com/package/current-script-polyfill)

