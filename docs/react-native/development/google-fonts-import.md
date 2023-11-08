# 引入 Google 字体

## 下载 Google Fonts

在 [Google Fonts](https://fonts.google.com/) 下载字体文件。  
macOS 的字体册，可以直接拖拽字体文件到字体册中安装，然后查看其 PostScript 名称，然后将字体文件名批量修改为 PostScript 名称。

## 添加字体

在项目根目录添加 `assets/fonts` 文件夹，将字体文件放入其中。

## 配置资源目录

在 `react-native.config.js` 中添加如下配置：

```javascript title="react-native.config.js" {6}
module.exports = {
  project: {
    ios: {},
    android: {}
  },
  assets: ['./assets/fonts/']
}
```

## 链接字体文件

```bash
npx react-native-asset
```

### iOS

该命令会在 `Info.plist` 中添加字体文件名，如下：

```xml title="Info.plist"
<key>UIAppFonts</key>
<array>
  <string>xxx-Regular.ttf</string>
  <string>xxx-Bold.ttf</string>
  <string>xxx-Italic.ttf</string>
  <string>xxx-BoldItalic.ttf</string>
</array>
```

### Android

该命令会将字体文件链接到 `android/app/src/main/assets/fonts` 目录下。

## 参考

- [Ultimate guide to use custom fonts in react native](https://mehrankhandev.medium.com/ultimate-guide-to-use-custom-fonts-in-react-native-77fcdf859cf4)
