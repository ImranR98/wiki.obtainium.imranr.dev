---
title: 首頁
---

# ![Obtainium Icon](https://raw.githubusercontent.com/ImranR98/Obtainium/main/assets/graphics/icon_small.png) Obtainium Wiki

---

[![立即停火](https://badge.techforpalestine.org/default)](https://techforpalestine.org/learn-more)

從應用程式來源直接取得 Android 應用程式更新。

Obtainium 的核心目標是實現直接從應用程式“源”（可直接下載應用程式安裝套件的網站）下載和安裝 Android 應用程式更新的自動化。這一過程需要自動化，因為使用者可能不願意或不能夠依賴應用程式商店來更新特定的應用程式，但 Android 應用程式（與桌面應用程式不同）通常認為它們將由應用程式商店進行外部更新，因此不包含內建的自我更新功能。

雖然這個概念很簡單，但各種支援的應用程式來源、使用者偏好以及 APK 命名、版本和發布方法卻讓事情變得更加複雜。本 Wiki 解釋了 Obtainium 中可用的各種應用程式來源和設定。

## 尋找應用程式設定 {#finding-app-configurations}

您可以在 [apps.obtainium.imranr.dev](https://apps.obtainium.imranr.dev) 上找到基於社群設定的應用程式設定。

如果找不到想要的應用程式設定，請隨時在[討論頁](https://github.com/ImranR98/apps.obtainium.imranr.dev/issues)上提出議題請求。

或者，在[此項目儲存庫](https://github.com/ImranR98/apps.obtainium.imranr.dev)上建立拉取請求，為網站貢獻一些設定。

## 安裝 {#installation}

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

!!! info "驗證資訊"
    - 應用程式套件名稱：`dev.imranr.obtainium`
    - 簽署憑證的 SHA-256 雜湊值：`B3:53:60:1F:6A:1D:5F:D6:60:3A:E2:F5:0B:E8:0C:F3:01:36:7B:86:B6:AB:8B:1F:66:24:3D:A9:6C:D5:73:62`
        - 注：上述簽名也適用於 F-Droid 版本的 Obtainium，感謝 [可重現構建](https://f-droid.org/docs/Reproducible_Builds/)。這意味著 F-Droid APK 與從相同原始碼構建的 APK 逐字節相同，從而允許您可能更信任的第三方進行獨立驗證。
    - [PGP 公鑰](https://keyserver.ubuntu.com/pks/lookup?search=contact%40imranr.dev&fingerprint=on&op=index)（驗證 APK 哈希值）

## 應用程式內連結 {#in-app-links}

您可以在 Obtainium 的設定頁面底部找到本 Wiki、原始碼和社群應用程式的設定連結。

## 限制 {#limitations}

- 對於某些資料源，資料是透過遍歷網站收集的，很容易因網站設計的改變而中斷。在這種情況下，可能無法使用更可靠的方法。
