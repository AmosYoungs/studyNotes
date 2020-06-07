

[TOC]

# 1.pc端网页请求加载进度条

该组件会在浏览器导航栏下方展示一个请求加载进度条

```
npm i nprogress  //安装依赖
import NProgress from 'nprogress' //引入依赖包及css文件
import 'nprogress/nprogress.css'
```

**拦截请求显示进度条**

```
axios.interceptors.request.use(config=>{
NProgress.start();
return config;
});
```

**拦截请求隐藏进度条**

```
axios.interceptors.response.use(config=>{
NProgress.done();
return config;
});
```

