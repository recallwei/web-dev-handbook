# 当构建失败时，该怎么做

## 清除构建缓存

### iOS

尝试清除 Xcode 构建缓存，然后重新构建，在导航栏 Product 中点击 Clean Build Folder 之后再点击 Build。

### Android

```bash
cd android
gradlew clean
```

### React Native 命令行

也可以通过 React Native 提供的命令行来清除构建缓存，需要勾选 Gradle cache 和 CocoaPods pod cache。

```bash
react-native clean
```

## iOS - 重新安装 bundle

当 Xcode 提示缺少文件时，可以尝试重新安装 bundle。

```bash
rm -rf Gemfile.lock
bundle install
```
