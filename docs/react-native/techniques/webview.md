# WebView

在 React Native 中集成 WebView，我们使用第三方库 **react-native-webview**，详见 [react-native-webview Guide](https://github.com/react-native-webview/react-native-webview/blob/master/docs/Getting-Started.md)。

## 安装

```bash
pnpm add react-native-webview
```

iOS 使用 CocoaPods，需要在 `/ios` 目录下执行：

```bash
pod install
```

或者：

```bash
npx pod-install # 不需要进入 /ios 目录
```

## 使用

### 外部网页

```tsx
import { WebView } from 'react-native-webview'

export default function WebViewDemo() {
  return (
    <WebView
      source={{ uri: 'https://web-dev.brucesong.xyz' }}
      style={{ marginTop: 20 }}
    />
  )
}
```

### 内联 HTML

```tsx
import { WebView } from 'react-native-webview'

export default function WebViewDemo() {
  return (
    <WebView
      originWhitelist={['*']}
      source={{ html: '<h1>Hello world</h1>' }}
    />
  )
}
```

## 参考

- [React Native WebView Guide](https://github.com/react-native-webview/react-native-webview/blob/master/docs/Guide.md)
- [React Native WebView API Reference](https://github.com/react-native-webview/react-native-webview/blob/master/docs/Reference.md)
