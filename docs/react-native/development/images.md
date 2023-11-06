# 图片

## 背景图片

在 React Native 中，你可以使用 `ImageBackground` 组件来设置背景图片。  
`ImageBackground` 通常将其子组件放在其内部，以便在其上方显示文本或按钮等内容。

```tsx
return (
  <ImageBackground source={...} style={{width: '100%', height: '100%'}}>
    <Text>Inside</Text>
  </ImageBackground>
);
```

## iOS 设置缓存限制

:::danger{title="警告"}
此配置暂时没有成功，可能存在问题。
:::

### RCTSetImageCacheLimits

React Native 暴露了一个 `RCTSetImageCacheLimits` API 可以覆盖默认的图片缓存限制。该方法需要在 `AppDelegate.mm` 的 `didFinishLaunchingWithOptions` 中调用。

```objectivec
RCTSetImageCacheLimits(imageSizeLimit, totalCostLimit);
```

### 参数

| 参数名称       | 类型   | 描述                 |
| -------------- | ------ | -------------------- |
| imageSizeLimit | number | 单张图片缓存大小限制 |
| totalCostLimit | number | 总缓存大小限制       |

### 示例

如下代码，设置了图片缓存限制为 4MB，总缓存限制为 200MB：

```objectivec title="AppDelegate.mm" {9}
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:(NSDictionary *)launchOptions
{
  self.moduleName = @"ReactNativeDemoApp";
  // You can add your custom initial props in the dictionary below.
  // They will be passed down to the ViewController used by React Native.
  self.initialProps = @{};

  // 设置缓存
  RCTSetImageCacheLimits(4 * 1024 * 1024, 200 * 1024 * 1024);

  return [super application:application didFinishLaunchingWithOptions:launchOptions];
}
```
