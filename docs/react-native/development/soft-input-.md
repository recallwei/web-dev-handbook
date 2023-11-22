# 软键盘遮挡输入框

## Android 软键盘遮挡输入框

Android 软键盘弹出时根据配置会有不同的行为，比如：

- `adjustResize`：会调整布局，但是会导致页面整体上移
- `adjustPan`：不会调整布局，而是把输入框顶上去，但是会遮挡输入框
- `adjustNothing`：不会调整布局，也不会遮挡输入框，但是会导致页面整体上移

建议使用 `adjustPan`，`adjustResize` 通常会破坏绝对定位。

在 `/android/app/src/main/AndroidManifest.xml` 中配置如下：

```xml
<activity
  android:name=".MainActivity"
  android:windowSoftInputMode="adjustPan">
```

## iOS 软键盘遮挡输入框

使用 `KeyboardAvoidingView` 组件，调整布局。

```tsx
import { KeyboardAvoidingView } from 'react-native'

function Screen() {
  return (
    <KeyboardAvoidingView
      behavior={Platform.OS === 'ios' ? 'padding' : undefined}
      keyboardVerticalOffset={120}
    >
      <TextInput />
    </KeyboardAvoidingView>
  )
}
```
