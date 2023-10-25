# Async Store

Async Store 的包全名为 `@react-native-async-storage/async-storage`，用于存放本地存储数据，类似于浏览器的 LocalStorage。

## 将全部异步存储信息打印至控制台

```ts
class LoggerUtils {
  static async printStorage() {
    console.log('------------------- Async Store -------------------')
    const storage = await AsyncStorage.multiGet(await AsyncStorage.getAllKeys())
    storage.forEach(([key, value]) => {
      console.log(`${key}: ${value}`)
    })
    console.log('')
  }
}
```

## 常见问题

### 返回的结果为错误的对象

如果返回了错误的对象如下：

```txt
 LOG  {"_h": 0, "_i": 0, "_j": null, "_k": null}
```

::: tip{title="提示"}
`AsyncStore.getItem()` 需要使用异步的方法调用。
:::

```ts
// 使用 async/await
async function getStorage(key: string) {
  const value = await AsyncStorage.getItem(key)
  return value
}
```

```ts
// 使用 Promise
let value: string
AsyncStorage.getItem(key).then((res) => {
  value = res
})
```

## 参考

- [Async Storage](https://react-native-async-storage.github.io/async-storage/)
