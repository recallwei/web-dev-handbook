# 更改应用图标

## 制作合适比例的图标

- 比例：1:1
- 图片尺寸：512 x 512
- 图标尺寸：350 x 350（居中，留白边）

## 使用第三方网站生成应用图标

- [App Icon Generator](https://www.appicon.co/)（推荐）
- [Make App Icon](https://makeappicon.com/)

## iOS

iOS 应用图标位于 `/ios/PROJECT_NAME/images.xcassets/AppIcon.appiconset`，替换该文件夹下的图标。  
如果使用 **[App Icon Generator](https://www.appicon.co/)** 生成，直接将解压后的 `AppIcon.appiconset` 文件夹替换即可。

## Android

Android 应用图标位于 `/android/app/src/main/res`，替换 `mipmap-*` 文件夹下的图标。
