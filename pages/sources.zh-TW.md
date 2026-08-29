---
title: 應用程式來源
description: 一些應用程式來源的特定資訊
---

# 應用程式來源 {#app-sources}

新增、檢查更新和安裝應用程式的方式因來源和使用者為該應用程式設定的設定而異。

以下選項適用於所有應用程式，無論其應用程式來源如何：

- 僅追蹤：啟用此選項後，您可以接收應用程式的更新通知，而無需嘗試實際下載其 APK。這對於追蹤沒有 APK 或無法透過 Obtainium 輕鬆擷取 APK 的應用程式的更新非常有用。有些應用程式來源只允許追蹤，例如 [ApkMirror](#apkmirror)。請注意，[版本偵測](app_tracking.md/#version-detection)對任何新增為僅追蹤的應用程式都不起作用。
- 版本偵測：請參閱[版本偵測](app_tracking.md/#version-detection)部分。
- 透過規則運算式篩選 APK：當一個應用程式版本有多個 APK 時，系統會提示使用者手動選擇一個。這除了操作不方便之外，還意味著應用程式將不會在背景靜默更新，即使在其他情況下可以這樣做。該選項可讓使用者指定一個規則運算式，用於篩去不匹配的 APK（最好只有一個選項）。
- 盡可能按 CPU 架構篩選 APK：該選項將使 Obtainium 自動篩選掉任何與使用者裝置不兼容的 APK。篩選邏輯非常簡單，是基於 APK 檔名，因此並不總是可靠的，在許多情況下，使用者可能仍需要自己進行篩選。
- 應用程式名稱：這允許使用者為應用程式指定自己的名稱，而不是使用 Obtainium 擷取的名稱。
- 停用背景更新：該選項將防止應用程式在背景靜默更新，即使背景更新已啟用，並且該應用程式符合在背景更新的所有條件。
- 跳過更新通知：透過此選項，Obtainium 將避免通知使用者此應用程式有可用更新或已在背景更新。

除此以外，每個應用程式還有額外的特定應用程式來源選項。其中大多數選項不言自明，而且可能會經常更新，因此本 Wiki 不涉及這些選項。不過，有些應用程式來源確實有更特殊的行為，需要更多解釋說明，下文將對此進行介紹。

## 當前支援的應用程式來源 {#currently-supported-app-sources}

- 開源——通用：
    - [GitHub](https://github.com/)
    - [GitLab](https://gitlab.com/)
    - [Codeberg](https://codeberg.org/)（Forgejo）
    - [F-Droid](https://f-droid.org/)
    - 第三方 F-Droid 儲存庫
    - [IzzyOnDroid](https://android.izzysoft.de/)
    - [SourceHut](https://git.sr.ht/)
- 其他——通用：
    - [APKPure](https://apkpure.net/)
    - [Aptoide](https://aptoide.com/)
    - [Uptodown](https://uptodown.com/)
    - [itch.io](https://itch.io/)
    - [Huawei AppGallery](https://appgallery.huawei.com/)
    - [騰訊應用程式寶](https://sj.qq.com/)
    - [Vivo 應用程式商店](https://h5appstore.vivo.com.cn/)
    - [RuStore](https://rustore.ru/)
    - [Apk4Free](https://apk4free.net/)
    - [CoolAPK](https://www.coolapk.com/)
    - [Farsroid](https://farsroid.com/)
    - [LiteAPKs](https://liteapks.com/)
    - Jenkins Jobs
    - [APKMirror](https://apkmirror.com/)（僅追蹤）
    - [RockMods](https://rockmods.net/)（僅追蹤）
- 特定應用程式：
    - [Telegram 應用程式](https://telegram.org)
    - [Neutron Code](https://neutroncode.com)
- 下載直連
- “HTML”（後備）：返回包含 APK 檔案連結的 HTML 頁面的任何其他連結

## GitHub {#github}

GitHub 對特定時間內的 API 請求數量設定了上限。由於 Obtainium 使用 GitHub API 抓取發布資訊，因此如果你有幾十個以上的來自 GitHub 來源的應用程式，就可能會遇到“速率限制”錯誤。您可以新增個人存取權杖以解決此問題。

GitHub 還允許開發者托管其應用程式的多個版本。這通常是指同一應用程式的舊版本，但也可能包括預發布版本、變體等。——因此，Obtainium 提供了各種篩選條件，讓您可以瀏覽這些版本，並準確抓取您感興趣的版本。

一些額外選項具有不太明顯的含義：

- **驗證最新標籤**：啟用後，Obtainium 將選擇開發者標記為"最新"的版本，而不是按時間順序最近的版本。兩者通常相同，但在某些情況下可能不同。這會額外消耗一次 GitHub API 調用（從而更快達到速率限制）。
- **排序方式**：控制當有多個版本可用時的排序方式。預設按日期排序，"智能名稱"排序嘗試從版本標題推斷版本順序，"名稱"排序使用嚴格的字母數字排序。"帶日期備援的智能名稱"選項使用基於名稱的排序，但在名稱無法比較時備援到基於日期的排序。
- **使用最新資產日期作為發布日期**：啟用後，顯示的發布日期將是版本中最近上傳資產的時間，而不是版本本身的發布時間。
- **檢查儲存庫重新命名**：啟用後，Obtainium 將偵測儲存庫是否已重新命名，並提示您相應更新應用程式的連結。

您還可以在來源專屬設定中提供 **GitHub 代理前綴**（例如 `gh-proxy.com`）。設定後，所有 GitHub API 請求都將透過該代理路由，這有助於解決某些地區的速率限制或存取問題。

GitHub 來源支援**搜尋**，並允許您按最低星標數篩選結果。

### 建立 GitHub 個人存取權杖 {#creating-a-github-personal-access-token}

1. 登錄 [GitHub](https://github.com)。
2. 進入開發者設定中的 [Fine-grained tokens](https://github.com/settings/personal-access-tokens)。
3. 選擇 **Generate new token**。
4. 給 Token 命名並設定有效期。
5. 滾動到底部，選擇 **Generate token**。
6. 複製 Token 並將其貼上到 Obtainium 設定中。請立即複製您的 Token，因為您將無法再次查看。

## GitLab {#gitlab}

GitLab 發行版中的 APK 有時會以非標準方式附加，導致 Obtainium 無法輕鬆取得。GitLab API 提供了更可靠的擷取 APK 的方式，但沒有 API 密鑰就無法使用。雖然這對大多數 GitLab 儲存庫來說都不是問題，但您可以在 Obtainium 的設定中新增自己的個人存取權杖，以便在極端情況下更可靠地擷取 APK。

與 GitHub 一樣，GitLab 也允許開發者托管同一應用程式的舊版本，因此我們會根據情況提供其他選項。

### 建立 GitLab 個人存取權杖 {#creating-a-gitlab-personal-access-token}

1. 登錄 [GitLab](https://gitlab.com)。
2. 進入設定中的[個人存取權杖](https://gitlab.com/-/user_settings/personal_access_tokens)。
3. 選擇**新增新權杖**。
4. 給權杖命名並設定有效期。
5. 勾選 `read_api`。
6. 滾動到底部，選擇**建立個人存取權杖**。
7. 複製權杖並將其貼上到 Obtainium 設定中。請立即複製您的權杖，因為您將無法再次查看。

!!! info "何時需要這樣做？"
    請參閱[該解釋](https://github.com/ImranR98/Obtainium/issues/3#issuecomment-1234695412)，瞭解 GitLab 發行版中的非標準 APK 附件

## F-Droid 第三方儲存庫 {#f-droid-third-party-repo}

與大多數其他來源不同，F-Droid 儲存庫在同一連結下包含多個應用程式的資訊。這意味著，除了版本庫連結之外，您還必須單獨在"應用程式 ID 或名稱"字段中提供所需的應用程式名稱或應用程式套件名稱。如果您不確定特定儲存庫中包含哪些應用程式，可以使用[匯入/匯出](ui_overview.md/#importexport-page)上的 "搜尋來源"按鈕來尋找。

請注意，Obtainium 無法自動判斷給定連結是否指向第三方 F-Droid 儲存庫。這意味著，預設情況下，向 Obtainium 新增第三方 F-Droid 儲存庫將導致錯誤使用 [HTML 來源](#html)（Obtainium 在無法識別任何連結時使用的後備源）。您必須從"覆寫來源"下拉選單中手動選擇"F-Droid 第三方儲存庫"，才能解決這個問題。

附加的版本選擇選項具有不同的行為：

- **嘗試選擇建議的版本代碼**：Obtainium 將嘗試使用 F-Droid 儲存庫標記為建議/當前版本的版本代碼。這是預設設定，適用於大多數儲存庫。
- **自動選擇最高版本代碼**：Obtainium 將選擇儲存庫中版本代碼號最高的版本，而不是建議的版本。如果儲存庫未正確標記建議版本，或者您希望確保始終獲得數字上最高的版本，此選項非常有用。

## APKMirror {#apkmirror}

APKMirror 是一個“僅追蹤”源。這意味著，雖然您可以將 APKMirror 連結新增到 Obtainium 以取得更新通知，但無法下載和安裝應用程式。這是因為 APKMirror 的維護者不允許這樣做（參見 [issue #44](https://github.com/ImranR98/Obtainium/issues/44)）。

由於 APKMirror 使用 RSS 源偵測新版本，您可以使用“按規則運算式篩選版本標題”選項來縮小其追蹤的版本範圍。

## HTML {#html}

“HTML”源是一個後備選項，可用於任何 Obtainium 不明確支援的應用程式來源。由於其靈活性，它也是支援小眾、不太流行的來源，而不會使 Obtainium 變得臃腫的一種方式。

HTML 來源的工作原理：

1. 首先向使用者提供的來源連結發送請求，並將響應解析為 HTML。然後在頁面上尋找連結。
2. 過濾掉某些連結。預設情況下，這是任何不以 `.apk` 結尾的連結，但您可以使用“自訂 APK 連結過濾器”來指定自己的過濾器。
3. 對剩餘連結進行排序。這種排序是對整個連結進行字母數字排序，但你也可以選擇只對連結的最後一段進行排序。最後一段通常是檔名，但如果在步驟 2 中使用了自己的過濾器，則可能不是。
4. 在所有剩餘連結上應用程式另一個可選的使用者定義過濾器。該過濾器與第 2 步中的過濾器的區別在於，它是所有應用程式來源都有的更通用的過濾器——它繼承自父類 `AppSource`（[應用程式來源](#app-sources)中描述的 APK 過濾器選項）。在某些情況下使用它可能比在步驟 2 中使用一個更複雜的規則運算式更簡單（示例請參見[該評論](https://github.com/ImranR98/Obtainium/issues/954#issuecomment-1745977857)）。與中間連結選項結合使用時也很有用。
5. 在剩餘的連結中，它會選擇第一個（如果啟用了反向選項，則選擇最後一個）。
6. 現在我們有了最終的 APK 連結，我們需要一個唯一的發布 ID 與之匹配，這樣當 ID 有所變更時，我們就知道該應用程式有更新可用。對於其他源，唯一髮布 ID 就是應用程式的版本，但對於 HTML 來源，可能無法擷取版本字串。因此，預設情況下，將是連結的哈希值。有三種偽版本化方法可用：
    - **部分 APK 哈希**（預設）：APK 檔案部分的哈希值。這比連結哈希更可靠，因為它取決於檔案內容，但需要下載部分 APK 進行計算。
    - **APK 連結哈希**：APK 下載連結的哈希值。連結更改時此值會更改。
    - **ETag**：使用來自 APK 下載響應的 HTTP ETag 標頭。當伺服器提供穩定的 ETag 但下載連結本身在不同版本間不變時，此方法很有用。
    - 此外，連結中通常會嵌入版本字串。Obtainium 本身並不預知如何擷取這些字串（不同的網站會有不同的擷取方法），因此使用者可以選擇指定一個規則運算式，應用程式於連結以擷取版本——這就是"版本擷取"的作用。
    - 但通常很難找到一個既能準確匹配版本，又能排除多餘字符的規則運算式。為此，我們提供了"規則運算式匹配組"選項，讓使用者指定規則運算式中的哪個組作為版本。
    - 還有一個"擷取整個頁面的版本"開關。啟用後，Obtainium 將嘗試在 HTML 頁面的任何位置尋找版本字串，而不僅僅在連結 URL 中。當版本顯示在頁面上但未嵌入下載連結時，此功能非常有用。
    - 版本擷取功能其實並無必要——使用連結哈希值更簡單、更可靠。有些使用者可能只是想要它，因為真實版本看起來更漂亮/更準確，而且它允許 Obtainium 在大多數情況下使用[版本偵測](app_tracking.md/#version-detection)。

您還可以為 HTML 來源設定**自訂請求標頭**。當目標網站需要特定標頭才能正確提供 APK 時，您可以覆蓋預設標頭（例如 User-Agent）。

至於**中間連結**過濾器，如果使用該過濾器（請參閱 [issue #820](https://github.com/ImranR98/Obtainium/issues/820)，瞭解在何種情況下該過濾器有用），HTML 來源會在正常流程之前新增一個預備步驟：

1. 在初始 HTML 頁面上尋找連結。
2. 過濾掉與中間連結過濾器不匹配的任何連結。
3. 抓取剩餘的第一個連結，然後將該連結作為輸入提供給上述正常 HTML 來源流程。

中間連結步驟有自己的子選項，用於控制如何過濾和排序連結：

- **按架構自動過濾**：如果從連結文本中可偵測到 CPU 架構，則自動過濾中間連結。
- **按連結文本過濾**：啟用後，中間連結過濾器規則運算式將應用程式於可見的連結文本，而不是 URL 本身。
- **匹配 `<a>` 標籤外的連結**：也匹配出現在標準錨標籤之外的連結（例如嵌入在頁面中的 JavaScript 資料結構中）。
- **跳過排序 / 反向排序 / 按最後連結段排序**：這些選項控制在選擇第一個連結之前中間連結的排序方式。

## 關於其他應用程式來源的備注 {#notes-for-various-other-sources}

- HTML：HTML 來源包括預設的請求標頭，這些標頭應適用於大多數網站。在某些情況下（例如 [SourceForge](https://sourceforge.net/)），您可能需要刪除它們（也有可能需要自訂）。
- Codeberg：該源的附加選項幾乎與 GitHub 相同，並且也支援搜尋。
- F-Droid：任何來自 F-Droid 的應用程式都可能使用不同的密鑰[簽名](https://developer.android.com/studio/publish/app-signing)，與其他源的相同應用程式不同。這意味著從 F-Droid 發布的特定應用程式更新到來自其他源（如 GitHub）的應用程式很可能會失敗。
- 騰訊應用程式寶：來自該源的 APK 可能為純 32 位（[armeabi-v7a](https://developer.android.com/ndk/guides/abis#v7a)）架構，無法安裝在使用較新 Arm 架構 SoC 的某些裝置上。
- itch.io：從 itch.io 下載可能需要處理"自訂定價"頁面和 Cloudflare 保護的下載連結。某些應用程式可能需要透過 HTML 來源的請求標頭選項設定自訂 Cookie 或標頭。
- 任何沒有與之關聯的特定伺服器的來源（如[第三方 F-Droid 儲存庫](#f-droid-third-party-repo)、Jenkins 和 SourceHut）都不會被 Obtainium 自動識別。您必須從"覆寫來源"下拉選單中手動選擇正確的來源。
- 某些源（如 APKPure）可能提供 [XAPK 檔案](https://apkpure.com/xapk.html)而非 APK 檔案。Obtainium 的 XAPK 支援不完整，可能無法可靠運行。
