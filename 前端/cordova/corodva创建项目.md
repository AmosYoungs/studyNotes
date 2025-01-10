```
cordova create TPHK-EApp com.taiping.hk.customer
```

```
cordova platform add ios
```

```
cordova platform add android@12.0.0
```

```
检查环境依赖支持
cordova requirements
```

```
sdkman设置java版本，
sdk default java 8.0.352-zulu
sdk default java 11.0.18-zulu
sdk default java 17.0.5-zulu
```

```
删除安卓平台
cordova platform rm android
cordova platform rm ios
```

```
cordova plugin add cordova-plugin-statusbar
cordova plugin rm cordova-plugin-statusbar
cordova plugin add cordova-plugin-camera
cordova plugin rm cordova-plugin-camera
cordova plugin add cordova-plugin-app-version
cordova plugin rm cordova-plugin-app-version
cordova plugin add cordova-plugin-android-permissions
cordova plugin rm cordova-plugin-fingerprint-aio
```

```
NSURL *URL = navigationAction.request.URL;

  NSString *scheme = [URL scheme];
  if ([scheme isEqualToString:@"tel"]) {

   NSString *resourceSpecifier = [URL resourceSpecifier];

   NSString *callPhone = [NSString stringWithFormat:@"telprompt://%@", resourceSpecifier];

   // 防止iOS 10及其之后，拨打电话系统弹出框延迟出现

   dispatch_async(dispatch_get_global_queue(0, 0), ^{

   [[UIApplication sharedApplication] openURL:[NSURL URLWithString:callPhone] options:@{}     completionHandler:**nil**];

   });

  }

  decisionHandler(WKNavigationActionPolicyAllow);
```

`keytool -genkeypair -v -keystore tphk-newepp-release-key.keystore -alias tphk-newepp-release \    -keyalg RSA -keysize 2048 -validity 10000`

file:///Users/hk.cntaiping/Documents/developeTools/Gradle/gradle-7.6-all.zip

