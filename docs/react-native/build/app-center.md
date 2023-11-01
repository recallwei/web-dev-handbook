# 集成 App Center

## 集成 App Center SDK

```bash
pnpm add appcenter appcenter-analytics appcenter-crashes
```

:::tip{title="提示"}
该文章仅支持 React Native 0.60 以上版本集成 App Center。
:::

集成步骤详看：[为 React Native 0.60 自动集成 SDK](https://learn.microsoft.com/zh-cn/appcenter/sdk/getting-started/react-native#31-integrate-the-sdk-automatically-for-react-native-060)

## 登录至 App Center

```bash
appcenter login
```

## 查询应用分发的密钥

```bash
appcenter codepush deployment list --app <所有者名称>/<应用名称> -k
```

## 设置当前应用

```bash
appcenter apps set-current <所有者名称>/<应用名称>
```

## 发布到 Staging 部署

```bash
appcenter codepush release-react -a <所有者名称>/<应用名称> -d <环境名称>
```

如果设置了当前应用，可以省略 `-a` 参数。

## iOS 指定发布构建的目录

npm package 名称和 ios 应用目录名称不一致，执行发布命令会出错，默认寻找的是 `ios/<npm package name>` 目录。n-

```bash
appcenter codepush release-react -d Staging --plist-file ios/<React Native iOS 应用名称>/Info.plist --xcode-project-file ios/<React Native iOS 应用名称>.xcodeproj/project.pbxproj
```

如果遇到如下错误：

```txt
Detecting ios app version:

Using the target binary version value "1.0" from "ios/ReactNativeDemoApp.xcodeproj/project.pbxproj".

Running "react-native bundle" command:

node node_modules/.bin/react-native bundle --assets-dest /var/folders/wx/pwxj2jls6ys7svj4wyrctf240000gn/T/code-push2023101-3009-19dr21e.96h7/CodePush --bundle-output /var/folders/wx/pwxj2jls6ys7svj4wyrctf240000gn/T/code-push2023101-3009-19dr21e.96h7/CodePush/main.jsbundle --dev false --entry-file index.js --platform ios
/Users/bruce/Code/soya-energy-app/node_modules/.bin/react-native:2
basedir=$(dirname "$(echo "$0" | sed -e 's,\\,/,g')")
          ^^^^^^^

SyntaxError: missing ) after argument list
    at internalCompileFunction (node:internal/vm:73:18)
    at wrapSafe (node:internal/modules/cjs/loader:1153:20)
    at Module._compile (node:internal/modules/cjs/loader:1205:27)
    at Module._extensions..js (node:internal/modules/cjs/loader:1295:10)
    at Module.load (node:internal/modules/cjs/loader:1091:32)
    at Module._load (node:internal/modules/cjs/loader:938:12)
    at Function.executeUserEntryPoint [as runMain] (node:internal/modules/run_main:83:12)
    at node:internal/main/run_main_module:23:47
```

需要回滚 app-center 的版本至 `2.3.3`，此处查看 [GitHub 相关 Issue](https://github.com/microsoft/react-native-code-push/issues/1819)。

:::danger{title="警告"}
目前仍未解决该问题。
:::
