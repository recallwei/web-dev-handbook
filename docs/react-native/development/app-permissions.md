# 应用权限

## 打开系统应用设置页面

```ts
const handleOpenSettings = () => {
  if (Platform.OS === 'ios') {
    Linking.openURL('app-settings:')
  } else {
    Linking.openSettings()
  }
}
```
