---
title : :app:compileDebugKotlin
date : 2021-08-23_Mon 21:12
aliases : [error]
---
Source Type :: #📥/📄 <br>
Source URL :: https://stackoverflow.com/questions/59893018/flutter-execution-failed-for-task-appcompiledebugkotlin?rq=1<br>
Note Type :: #📝 <br>
Topics :: [[🍃Flutter MOC]]<br>
Parent Link :: [[🍃Tricks]]<br>

---
# :app:compileDebugKotlin

1. flutter clean
2. Delete android/.gradle
3. Go to android/build.gradle, upgrade `ext.kotlin_version` to ==\<latest\>==. In my case(1.3.0 -> 1.5.10), `ext.kotlin_version = '1.5.10'`