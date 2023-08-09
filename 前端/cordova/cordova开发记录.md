E掌通

添加插件

cordova plugin add cordova-plugin-app-version

cordova plugin rm cordova-plugin-app-version

cordova plugin add jpush-phonegap-plugin --variable APP_KEY=e8a7c56c5a61f22ed69d1d11

cordova plugin rm jpush-phonegap-plugin --variable APP_KEY=e8a7c56c5a61f22ed69d1d11

删除插件

极光推送生产

cordova plugin add jpush-phonegap-plugin --variable APP_KEY=a1ad1a1f36bc1239ab691ace

cordova plugin rm jpush-phonegap-plugin --variable APP_KEY=a1ad1a1f36bc1239ab691ace

极光推送测试

cordova plugin rm jpush-phonegap-plugin --variable APP_KEY=0274dcdd22bff34aa67688af

cordova plugin add jpush-phonegap-plugin --variable APP_KEY=0274dcdd22bff34aa67688af

cordova plugin add jpush-phonegap-plugin@4.8.6 --variable APP_KEY=0274dcdd22bff34aa67688af

本地极光推送集成google版

cordova plugin add local-plugin/cordova-plugin-jcore

cordova plugin add local-plugin/jpush-phonegap-plugin --variable APP_KEY=0274dcdd22bff34aa67688af

生产

cordova plugin add local-plugin/jpush-phonegap-plugin --variable APP_KEY=a1ad1a1f36bc1239ab691ace





cordova plugin rm cordova-plugin-camera

cordova plugin add cordova-plugin-camera

cordova plugin rm cordova-plugin-badge

cordova plugin add cordova-plugin-badge

cordova plugin rm cordova-plugin-inappbrowser

cordova plugin add cordova-plugin-inappbrowser

安卓更新谷歌应用市场要求版本11及以上

cordova platform remove android

cordova platform add android@11.0.0

cordova plugin rm cordova-plugin-whitelist  安卓10以上不再需要安装该插件，会报错

cordova plugin rm cordova-plugin-file-transfer这个插件要换新的

cordova plugin add https://github.com/apache/cordova-plugin-file-transfer.git

cordova plugin rm cordova-plugin-statusbar 换新的

cordova plugin add cordova-plugin-statusbar

cordova plugin rm cordova-plugin-splashscreen 这个插件也不支持了，内置到了core，避免互相影响删除

config.xml的变更记录

 <preference name="StatusBarStyle" value="default" />





iOS webView渲染引擎替换原先默认使用的是UIWebViewEngine在新的iOS系统版本中对position：fixed元素支持有问题，更新为使用WKWebViewEngine修复问题

添加插件支持

cordova plugin add cordova-plugin-wkwebview-engine

展业通 ID：com.taipinghk.ezt





cordova plugin rm jpush-phonegap-plugin --variable APP_KEY=c1d670a62597b1b26ca955a5

```
cordova plugin add jpush-phonegap-plugin@3.8.6 --variable APP_KEY=c1d670a62597b1b26ca955a5

```