# 知味厨房手机端

主责：A。当前已创建 Flutter 安卓基础工程，页面仍是默认计数器示例，业务功能尚未实现。

## 本机运行

本机使用纯英文项目路径 D:\GitCode\AIKitchen。旧目录 D:\软创\GitCode\AIKitchen 保留作备份，请勿在两份目录同时开发。

启动 Android Studio 中的模拟器，然后在 mobile 目录运行：

```powershell
$env:FLUTTER_STORAGE_BASE_URL = "https://storage.flutter-io.cn"
flutter pub get
flutter devices
flutter run -d emulator-5554
```

设备编号以 flutter devices 的实际结果为准。首次下载可能较慢。

## 本次验证（2026-11-17）

- 已安装 NDK 28.2.13676358 和 Android SDK Platform 36。
- Gradle 下载使用华为云镜像，并使用 Gradle 官方 SHA-256 校验。
- Android 项目优先使用阿里云依赖镜像，保留原仓库作为后备。
- 英文路径下 flutter run --no-resident --no-pub 编译、安装、启动成功（Android 16 x86_64 模拟器）。
- 中文路径虽然能跳过 Gradle 检查，但 aapt 仍不能正常读取安装包，因此采用英文路径，不依赖跳过检查。

以上验证的是基础示例工程，不代表菜单、排程、AI或后端功能已经实现。