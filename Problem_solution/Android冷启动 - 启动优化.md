#Android冷启动 - 启动优化
###介绍：
    Android启动时候默认有短暂的白屏现象
###方法
* 在 `drawable` 下新建 `launch_screen.xml` 

```xml
<?xml version="1.0" encoding="utf-8"?>
<layer-list xmlns:android="http://schemas.android.com/apk/res/android"
    android:opacity="opaque">
    
    <item android:drawable="@android:color/white">
    </item>

    <item>
        <bitmap android:src="@mipmap/ic_launcher"
            android:gravity="center" />
    </item>
</layer-list>

```

* 在 `style.xml` 中添加一个新的主题

```xml
    <style name="AppTheme.Launcher">
        <item name="android:windowBackground">@drawable/launch_screen</item>
    </style>
```

* 添加启动的activity的theme
```xml
<activity android:name=".MainActivity"

 +           android:theme="@style/AppTheme.Launcher"><!-- 添加 该属性-->
            <intent-filter>
                <action android:name="android.intent.action.MAIN" />

                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
```

##### 解决启动白屏问题，不需要消耗额外的系统资源启动速度更快，首次启动不会出现白屏现象，体验更好

