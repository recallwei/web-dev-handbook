# react-native-flipper

## Android 构建 react-native-flipper 失败

错误信息如下：

```txt
FAILURE: Build failed with an exception.

* What went wrong:
A problem occurred configuring project ':react-native-flipper'.
> Could not create an instance of type com.android.build.api.variant.impl.LibraryVariantBuilderImpl.
   > Namespace not specified. Specify a namespace in the module's build file. See https://d.android.com/r/tools/upgrade-assistant/set-namespace for information about setting the namespace.

     If you've specified the package attribute in the source AndroidManifest.xml, you can use the AGP Upgrade Assistant to migrate to the namespace value in the build file. Refer to https://d.android.com/r/tools/upgrade-assistant/agp-upgrade-assistant for general information about using the AGP Upgrade Assistant.

* Try:
> Run with --stacktrace option to get the stack trace.
> Run with --info or --debug option to get more log output.
> Run with --scan to get full insights.

* Get more help at https://help.gradle.org
```

:::warning{title="暂时解决方案"}
目前没有弄清该错误的产生原因，只能通过固定版本号解决。如有更好的解决方案，欢迎提 PR。  
:::

- `@react-native/gradle-plugin` 降级至 **0.72.11**
- `react-native-flipper` 降级至 **0.163.0**
