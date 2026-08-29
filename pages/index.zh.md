---
title: 首页
---

# ![Obtainium Icon](https://raw.githubusercontent.com/ImranR98/Obtainium/main/assets/graphics/icon_small.png) Obtainium Wiki

---

[![立即停火](https://img.shields.io/badge/%F0%9F%87%B5%F0%9F%87%B8_立即停火-techforpalestine.org-000?labelColor=grey&color=D83838)](https://techforpalestine.org/learn-more)

从应用源直接获取 Android 应用更新。

Obtainium 的核心目标是实现直接从应用“源”（可直接下载应用安装包的网站）下载和安装 Android 应用更新的自动化。这一过程需要自动化，因为用户可能不愿意或不能够依赖应用商店来更新特定的应用，但 Android 应用（与桌面应用不同）通常认为它们将由应用商店进行外部更新，因此不包含内置的自我更新功能。

虽然这个概念很简单，但各种支持的应用源、用户偏好以及 APK 命名、版本和分发方法却让事情变得更加复杂。本 Wiki 解释了 Obtainium 中可用的各种应用源和设置。

## 查找应用配置 {#finding-app-configurations}

您可以在 [apps.obtainium.imranr.dev](https://apps.obtainium.imranr.dev) 上找到基于众包的应用配置。

如果找不到想要的应用配置，请随时在[讨论页](https://github.com/ImranR98/apps.obtainium.imranr.dev/issues)上提出议题请求。

或者，在[此项目仓库](https://github.com/ImranR98/apps.obtainium.imranr.dev)上创建拉取请求，为网站贡献一些配置。

## 安装 {#installation}

<div style="text-align: center;">
  <a href="https://github.com/ImranR98/Obtainium/releases">
    <img src="https://github.com/machiav3lli/oandbackupx/raw/034b226cea5c1b30eb4f6a6f313e4dadcbb0ece4/badge_github.png" alt="Get it on GitHub">
  </a>
  <a href="https://apt.izzysoft.de/fdroid/index/apk/dev.imranr.obtainium">
    <img src="https://gitlab.com/IzzyOnDroid/repo/-/raw/master/assets/IzzyOnDroid.png" alt="Get it on IzzyOnDroid">
  </a>
  <a href="https://f-droid.org/packages/dev.imranr.obtainium.fdroid/">
    <img src="https://fdroid.gitlab.io/artwork/badge/get-it-on.png" alt="Get it on F-Droid">
  </a>
</div>
     
!!! info "验证信息"
    - 应用包名：`dev.imranr.obtainium`
    - 签名证书的 SHA-256 哈希值：`B3:53:60:1F:6A:1D:5F:D6:60:3A:E2:F5:0B:E8:0C:F3:01:36:7B:86:B6:AB:8B:1F:66:24:3D:A9:6C:D5:73:62`
        - 注：上述签名也适用于 F-Droid 版本的 Obtainium，感谢 [可重现构建](https://f-droid.org/docs/Reproducible_Builds/)。这意味着 F-Droid APK 与从相同源代码构建的 APK 逐字节相同，从而允许您可能更信任的第三方进行独立验证。
    - [PGP 公钥](https://keyserver.ubuntu.com/pks/lookup?search=contact%40imranr.dev&fingerprint=on&op=index)（验证 APK 哈希值）

## 应用内链接 {#in-app-links}

您可以在 Obtainium 的设置页面底部找到本 Wiki、源代码和众包应用配置的链接。

## 限制 {#limitations}

- 对于某些数据源，数据是通过遍历网站收集的，很容易因网站设计的改变而中断。在这种情况下，可能无法使用更可靠的方法。
