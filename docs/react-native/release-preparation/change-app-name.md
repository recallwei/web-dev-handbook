# 更改应用名称

## iOS

iOS 应用名称定义在 `/ios/PROJECT_NAME/Info.plist` 文件中，修改 `CFBundleDisplayName` 的值。

```xml title="Info.plist"
<dict>
  <key>CFBundleDisplayName</key>
  <string>YOUR_APP_NAME</string>
</dict>
```

## Android

安卓应用名称定义在 `/android/app/src/main/res/values/string.xml` 文件中，修改 `app_name` 的值。

```xml title="string.xml"
<resources>
    <string name="app_name">YOUR_APP_NAME</string>
</resources>
```

## 参考

- [How to change the app name in react-native(in android and IOS)](https://dev.to/zenkoders/how-to-change-the-app-name-in-react-nativein-android-and-ios-573i)
