# 引入vux报错解决

一、安装依赖包

分别安装以下依赖：

```npm i vux --save```

````npm ivux-loader --save-dev``  (这个必须要安装)

二、配置相关依赖

修改webpack.base.conf.js

- 引入”vuex-loader“   ```const vuxLoader = require('vux-loader')```
- 修改原来的module.exports的对象赋值给 let webpackConfig
- 新的module.exports修改为：

```
module.exports = vuxLoader.merge(webpackConfig,{
  options: {},
  plugins: [
    {
      name: 'vux-ui'
    }
  ]
})
```

