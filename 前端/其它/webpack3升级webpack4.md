安装指定版本webpack

`npm install webpack@4.16.5 webpack-cli -D`

移除CommonsChunkPlugin

```
// new webpack.optimize.CommonsChunkPlugin({
    //   name: 'vendor',
    //   minChunks (module) {
    //     // any required modules inside node_modules are extracted to vendor
    //     return (
    //       module.resource &&
    //       /\.js$/.test(module.resource) &&
    //       module.resource.indexOf(
    //         path.join(__dirname, '../node_modules')
    //       ) === 0
    //     )
    //   }
    // }),
```

配置mode

```
mode: "production";
```

升级vue-loader

```
npm install vue-loader@14.2.2 -S -D

npm install html-webpack-plugin@4.3.0

npm i --save-dev mini-css-extract-plugin@0.9.0
```

调试开发环境不可用报错：

```
Error: Cannot find module 'webpack/bin/config-yargs'

https://github.com/mzgoddard/jest-webpack/issues/27
```

升级依赖

```
npm install  webpack-cli@2.1.3 -S -D
npm install  webpack-dev-server@3.1.4 -S -D
"webpack-cli": "^2.1.3",
"webpack-dev-server": "^3.1.4"
```

配置less

npm i less-loader -D

npm i less -D

重装file-loader

