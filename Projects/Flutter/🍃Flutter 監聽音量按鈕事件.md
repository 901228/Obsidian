---
title : 🍃Flutter 監聽音量按鈕事件
date : 2021-09-09_Thu 10:22
aliases : [platform integration]
---
Source Type :: #📥/📄 <br>
Source URL :: https://zespia.tw/blog/2020/07/15/flutter-volume-button-events/<br>
Source Author :: [[@ZESPIA]]<br>
Note Type :: #📝 <br>
Topics :: [[🍃Flutter MOC]]<br>
Parent Link :: [[🍃Tricks]]<br>

---
# 🍃Flutter 監聽音量按鈕事件
用 MethodChannel 讓 Flutter 跟平台原生語言做溝通 (`Android -> Java, Kotlin`, `IOS -> Swift, Objective-c`)

## Android
Android 目前推薦用 Kotlin 作為開發語言，因此選擇使用 Kotlin。

### import
#### MainActivity.kt
```kotlin
import android.os.Build
import android.os.Bundle
import android.view.KeyEvent
import android.view.View
import android.view.WindowManager
import android.content.Context
import androidx.annotation.NonNull

import io.flutter.embedding.android.FlutterActivity
import io.flutter.embedding.engine.FlutterEngine
import io.flutter.plugin.common.EventChannel
import io.flutter.plugin.common.EventChannel.StreamHandler
import io.flutter.plugin.common.MethodChannel

import io.reactivex.rxjava3.disposables.Disposable
import io.reactivex.rxjava3.kotlin.subscribeBy
import io.reactivex.rxjava3.subjects.PublishSubject
```

#### /android/app/build.gradle
```gradle
...
dependencies {
	...
	implementation "io.reactivex.rxjava3:rxkotlin:<version>"
	...
}
...
```

### MethodChannel
#### Kotlin
```kotlin
// 用這個變數來控制要不要攔截 keydown 事件
private var interceptKeyDownEnabled = false

override fun configureFlutterEngine(flutterEngine: FlutterEngine) {
  super.configureFlutterEngine(flutterEngine)

  // Method channel 的名字可以隨便取，只要確保在 Android/iOS 和 Flutter 兩邊用的名字一致就好了
  MethodChannel(flutterEngine.dartExecutor, "com.example/method").setMethodCallHandler { call, result ->
    when (call.method) {
      "interceptKeyDown" -> {
        interceptKeyDownEnabled = true
        // 如果成功的話就用 result.success 回傳結果
        result.success(true)
        // 失敗的話則是用 result.error 回傳錯誤
        // result.error("ERROR_CODE", "error message", null)
      }
      "uninterceptKeyDown" -> {
        interceptKeyDownEnabled = false
        result.success(true)
      }
      else -> {
        // 其他沒有 handle 到的 method 就回傳 result.notImplemented
        result.notImplemented()
      }
    }
  }
}

override fun onKeyDown(keyCode: Int, event: KeyEvent?): Boolean {
  if (interceptKeyDownEnabled) {
    // 攔截 keydown 事件
    return true
  }

  return super.onKeyDown(keyCode, event)
}
```

#### Flutter
```dart
final methodChannel = MethodChannel('com.example/method');

// 開始攔截 keydown 事件
await methodChannel.invokeMethod('interceptKeyDown');

// 停止攔截 keydown 事件
await methodChannel.invokeMethod('uninterceptKeyDown');
```


### EventChannel
#### Kotlin
```kotlin
private var interceptKeyDownEnabled = false

// 用 Rx 來傳遞事件，也可以改用其他類似的 library
private val keyDownSubject = PublishSubject.create<String>()

override fun configureFlutterEngine(flutterEngine: FlutterEngine) {
  super.configureFlutterEngine(flutterEngine)

  MethodChannel(flutterEngine.dartExecutor, "com.example/method").setMethodCallHandler { call, result ->
    // ...
  }

  // Event channel 的名字可以隨便取，只要確保在 Android/iOS 和 Flutter 兩邊用的名字一致就好了
  EventChannel(flutterEngine.dartExecutor, "com.example/event").setStreamHandler(object : StreamHandler {
    var dispose: Disposable? = null

    override fun onListen(arguments: Any?, events: EventChannel.EventSink?) {
      // 開始訂閱事件
      dispose = keyDownSubject.subscribeBy (
        onNext = { events?.success(it) },
        onError = { events?.error("KEY_DOWN_EVENT", it.message, it) },
        onComplete = { events?.endOfStream() }
      )
    }

    override fun onCancel(arguments: Any?) {
      // 停止訂閱事件
      dispose?.dispose()
      dispose = null
    }
  })
}

override fun onKeyDown(keyCode: Int, event: KeyEvent?): Boolean {
  if (interceptKeyDownEnabled) {
    // 在按下音量 +/- 鍵的時候，送事件到 Rx subject 並攔截 keydown 事件
    when (keyCode) {
      KeyEvent.KEYCODE_VOLUME_DOWN -> {
        keyDownSubject.onNext("volumeDown")
        return true
      }
      KeyEvent.KEYCODE_VOLUME_UP -> {
        keyDownSubject.onNext("volumeUp")
        return true
      }
    }
  }

  return super.onKeyDown(keyCode, event)
}
```

#### Flutter
```dart
final eventChannel = EventChannel('com.example/event');

// 訂閱事件
final subscription = eventChannel.receiveBroadcastStream().listen((event) {
  final code = event as String;
  // ...
});

// 取消訂閱
subscription.cancel();
```