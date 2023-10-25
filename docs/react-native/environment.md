# 环境配置

设备条件：基于 MacOS 系统

## iOS

### 安装基本依赖

- Node：官网下载 LTS 版本
- watchman：通过 Homebrew 下载

```bash
brew install watchman
```

- Xcode：从 Apple Store 下载
- Xcode iOS 17 模拟器
- CocoaPods（Swift、Objective-C 依赖管理）

```bash
sudo gem install cocoapods -V
# Ruby 的版本可能不支持安装 cocoapods，需要安装 activesupport
sudo gem install activesupport -v 6.1.7.6
```

:::tip{title="提示"}
Ruby gem 安装包可能比较慢，加 `-V` 可以看到安装进度
:::

### 找不到 Xcode

```txt
Error: Command failed with exit code 1: xcodebuild -list -json
 xcode-select: error: tool 'xcodebuild' requires Xcode, but active developer directory '/Library/Developer/CommandLineTools' is a command line tools instance
```

```bash
sudo xcode-select -s /Applications/Xcode.app/Contents/Developer
```

### 使用 pnpm

使用 `metro-resolver-symlinks` 解决 pnpm symlink 问题

- [在 React Native 中使用 pnpm](https://blog.swizm.cc/blog/use-pnpm-in-react-native)
- [metro-resolver-symlinks](https://microsoft.github.io/rnx-kit/docs/tools/metro-resolver-symlinks)

## Android

- JDK
- Android Studio
- Android SDK
- Android SDK Platform
- Android 模拟器

## 常见问题

[修改 app.json 应用名称报错](https://stackoverflow.com/questions/64167281/a-module-failed-to-load-due-to-an-error-and-appregistry-registercomponent-wasn)
