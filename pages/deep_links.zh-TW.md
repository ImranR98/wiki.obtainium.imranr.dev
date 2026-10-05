---
title: 深層連結
description: 透過 obtainium:// 深層連結新增應用程式、匯入設定與觸發更新檢查
---

# 深層連結 {#deep-links}

Obtainium 註冊了 `obtainium://` URI 協定。任何應用程式、網站或 QR Code 都可以將連結交給 Obtainium，省去「開啟 Obtainium、點選新增、貼上連結」的手動流程。共有三種操作。

## 新增單一應用程式 {#add-a-single-app}

```
obtainium://add/<url>
```

或是等效的寫法：

```
obtainium://add?url=<url>
```

會以 `<url>` 作為來源，預先填入「新增應用程式」頁面，效果與手動貼上相同。如果 Obtainium 已在追蹤連結完全相同的應用程式，則會改為開啟該應用程式的頁面，而非新增頁面。

## 匯入完整設定 {#import-a-full-config}

```
obtainium://app/<url-encoded JSON>
obtainium://apps/<url-encoded JSON array>
```

`app` 接受單一應用程式設定物件；`apps` 則接受由這些物件組成的 JSON 陣列，可透過一個連結進行批次匯入。這與應用程式匯出/匯入，以及[社群應用程式設定目錄](https://apps.obtainium.imranr.dev)中的設定所使用的物件格式相同，至少需包含：

```json
{"id": "com.example.app", "url": "https://github.com/example/app", "author": "example", "name": "Example App"}
```

點選連結後，在新增任何內容之前會先顯示含有原始 JSON 的確認對話框，因此這是「點一下再確認一次」，而非靜默安裝。`additionalSettings` 以及設定所支援的其他所有欄位，運作方式都與其他可貼上設定的地方相同。`id` 僅是安裝裝置上用於記錄的鍵值，不需要在任何地方註冊。

## 觸發更新檢查 {#trigger-an-update-check}

```
obtainium://refresh
obtainium://refresh?id=<app id>
```

檢查所有已追蹤應用程式的更新；若指定了 `id`，則只檢查該應用程式。

## 為您的專案加上徽章 {#badging-your-project}

由於 `obtainium://app/` 接受完整設定，專案可以在自己的 README 或下載頁面上放置「Get it on Obtainium」徽章，無需列入[社群應用程式設定目錄](https://apps.obtainium.imranr.dev)。

**取得徽章。** 從[主儲存庫](https://github.com/ImranR98/Obtainium/tree/main/assets/graphics)複製 `assets/graphics/badge_obtainium.png` 並自行託管，而不要直接連結 `raw.githubusercontent.com`——GitHub 不保證支援此種用途，且可能會限制請求速率。此檔案帶有透明邊距；大多數專案會將其裁切，並以約 161x48（其長寬比為 3.36:1）的尺寸顯示。

**選擇連結形式。** 單純的 `obtainium://app/<encoded json>` 連結不需要任何第三方服務，但若未安裝 Obtainium，點選後不會有任何反應。目錄網站提供了一個重新導向頁面，它會驗證內容、嘗試開啟應用程式連結，並在幾秒內沒有回應時，改為顯示「取得 Obtainium」的提示：

```
https://apps.obtainium.imranr.dev/redirect?r=obtainium://app/<encoded json>
```

大多數為自身專案加上徽章的專案都採用這種形式，讓徽章對尚未安裝 Obtainium 的訪客也能發揮作用。

### 實際使用案例 {#seen-in-the-wild}

- [Delta Chat](https://delta.chat/en/download)
- [PrivacyNotes](https://privacynotes.app/#downloads)
