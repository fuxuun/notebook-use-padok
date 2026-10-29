# 构建轻记

使用 JDK 17、Android SDK Platform 36、Build Tools 35.0.0。Gradle Wrapper 固定 Gradle 8.13，首次运行会下载依赖。

在 Android Studio 打开项目并设置 SDK 路径，或在本地 `local.properties` 配置 `sdk.dir`，不要提交该文件。

Windows：
```powershell
.\gradlew.bat assembleRelease
```

macOS / Linux：
```sh
sh ./gradlew assembleRelease
```

APK：`app/build/outputs/apk/release/app-release.apk`。构建开启代码和资源压缩，当前使用开发签名。不同电脑的签名可能不同，覆盖安装需使用相同签名；密钥不得提交仓库。

`build.ps1` 可复用本地 `.tools` 环境，也可使用已配置的 JDK 和 SDK；`.tools` 不随源码分发。

可选检查（已有测试尚未全部执行通过）：
```powershell
.\gradlew.bat testDebugUnitTest lintDebug
.\gradlew.bat connectedDebugAndroidTest
```

第二条需要已连接并授权 USB 调试的 Android 设备。手写、压感和手掌接触效果需要实际体验。
