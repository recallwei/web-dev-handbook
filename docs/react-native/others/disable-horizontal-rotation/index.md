# 禁用横屏模式

## iOS

iOS 需要在 Xcode 中设置，取消勾选 **iPhone Orientation** 中的 `Landscape Left` 和 `Landscape Right` 选项，如下图所示：

![iOS](./img/1.png)

## Android

Android 需要在 `/android/app/src/main/AndroidManifest.xml` 中的 activity 添加 `android:screenOrientation="portrait"` 属性。

```xml title="AndroidManifest.xml" {12}
<manifest xmlns:android="http://schemas.android.com/apk/res/android">
    <uses-permission android:name="android.permission.INTERNET" />
    <application
      android:name=".MainApplication"
      android:label="@string/app_name"
      android:icon="@mipmap/ic_launcher"
      android:allowBackup="false"
      android:theme="@style/AppTheme">
      <activity
        android:name=".MainActivity"
        android:label="@string/app_name"
        android:screenOrientation="portrait"
        android:configChanges="keyboard|keyboardHidden|orientation|screenLayout|screenSize|smallestScreenSize|uiMode"
        android:launchMode="singleTask"
        android:windowSoftInputMode="adjustResize"
        android:exported="true">
        <intent-filter>
            <action android:name="android.intent.action.MAIN" />
            <category android:name="android.intent.category.LAUNCHER" />
        </intent-filter>
      </activity>
    </application>
</manifest>
```