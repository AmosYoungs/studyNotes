##### 创建一个Cordova应用

暂不细述

##### 创建一个Vue应用

暂不细述

##### 部署vue应用部署到一个在线服务

暂不细述

##### 在cordova项目中作如下配置，用以加载vue 项目

```
// index.html
// 下面这行配置要删掉否则无法打开页面
<!-- <meta http-equiv="Content-Security-Policy" content="default-src 'self' data: https://ssl.gstatic.com 'unsafe-eval'; style-src 'self' 'unsafe-inline'; media-src *; img-src 'self' data: content:;"> -->
       
 <script>
     window.location.href="http://ip:port/"
</script>

//为app添加Cordova插件原生能力
cordova plugin add xxx
cordova plugin save
// 删除原有项目
cordova platform add ios
// 生成android项目
cordova platform add android
// 编译生成发布包
cordova build android

git config --global --add safe.directory /opt/homebrew/Library/Taps/homebrew/homebrew-core
git config --global --add safe.directory /opt/homebrew/Library/Taps/homebrew/homebrew-cask



// ios 同上
```

- 注意事项：

安卓安装打开应用后提示“err_cleartext_not_permitted”

找到安卓项目目录下的platforms/android/app/src/main/AndroidManifest.xml文件

在application节点添加如下配置

```
android:usesCleartextTraffic="true"
```

##### vue项目中集成cordova原生能力调用

- 方法一

  将Cordova项目中的platform_www目录下的文件拷贝到vue项目的static目录下，并在index.html中动态引入对应的cordova.js。iOS和Android进行判断后分别引入不同的文件。

- 方法二

​       方法一中的资源文件部署到服务上，在index.html中引入在线资源，这样可以减少vue前端包体积

引入对应文件后可以在全局的navigator对象中找到对应的原生能力封装对象，以调用拍照能力为例：

```
 navigator.camera.getPicture((success) => {}, (err) => {}, {

                    quality: 50,

                    destinationType: 1,

                    encodingType: 0,

                    allowEdit: true,

                    sourceType: 1
                })
```

