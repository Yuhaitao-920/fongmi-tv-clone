# FongMi TV (clone)

基于 [FongMi/TV](https://github.com/FongMi/TV) 的完整 Android 源码复刻工程，源码导入自本账号下已验证可构建的 `webhtv`（GPL-3.0）。

## 说明

- 源码为完整工程，包含定制 media3 依赖（`third_party/maven/` 内的 aar）和所有原生库，可直接编译出可安装的 APK。
- 基础版本为 `5.6.0`（versionCode 560），是 FongMi/TV 的二次开发分支。
- 本仓库不含任何影视资源、接口或爬虫配置。

## 构建 APK

进入 **Actions → Build Android APK → Run workflow**：

- `variant`：选择要构建的变体，或 `all` 一次构建全部 4 个：
  - `mobileArm64_v8a` — 手机 64 位（对应常见安装包）
  - `mobileArmeabi_v7a` — 手机 32 位
  - `leanbackArm64_v8a` — 电视/盒子 64 位
  - `leanbackArmeabi_v7a` — 电视/盒子 32 位
- `create_release`：勾选后同时创建 GitHub Release。

构建环境由工作流自动配置（JDK 21 + Android SDK 37.0 + Python 3.10），无需本地环境。产物在对应 Run 页面的 **Artifacts** 下载。

未配置发布签名时使用 Android 默认 debug 签名，APK 可正常安装；如需与既有安装无缝覆盖，请在仓库 Secrets 配置 `RELEASE_KEYSTORE_BASE64` / `RELEASE_KEY_ALIAS` / `RELEASE_STORE_PASSWORD` 后改用 release 构建。

## 许可

遵循上游 GPL-3.0 协议，详见源码内 LICENSE。
