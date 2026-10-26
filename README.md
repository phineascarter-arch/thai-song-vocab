# 聽泰語歌學泰文 · thai-song-vocab

給完全初學者的泰語歌曲學習 skill：從可核對的泰文歌詞整理繁體中文解釋、羅馬拼音、逐音節聲調、日常詞句與歌曲意象，產出手機可讀的 HTML 學習頁、Markdown 筆記及 Anki CSV。

這是可安裝的 Codex skill，也包含《คิดถึงจัง (มาหาหน่อย)》的使用者提供歌詞學習頁。它獨立於 [thai-series-vocab 追劇版](https://github.com/phineascarter-arch/thai-series-vocab)，不會覆蓋追劇版或英語版。

## 歌曲學習網站

[開啟歌曲學習頁](https://phineascarter-arch.github.io/thai-song-vocab/)：99 行泰文、羅馬拼音、繁中翻譯，每句正常／慢速語音、詳細詞塊拆解與逐詞點按發音。語音固定 Premwadee 女聲，非原唱。原曲使用 Apple Music 外部連結，未提供原唱逐字同步。

本頁依使用者提供的含饒舌版本整理，不保證與 Apple Music 原曲逐句相同。收藏與進度保存在瀏覽器，從本機檔案改到網站時需自行匯出／匯入。iPhone 可用 Safari 開啟，實機播放效果仍需確認。

網站從 `main` 分支的 `/docs` 自動部署；後續推送該目錄即可更新。

## 安裝到 Codex

將這個連結貼到 Codex，輸入：

```text
請使用 skill-installer，將 https://github.com/phineascarter-arch/thai-song-vocab
儲存庫根目錄的 thai-song-vocab 安裝到我的個人 skills 目錄。
```

也可手動安裝。Windows PowerShell：

```powershell
git clone https://github.com/phineascarter-arch/thai-song-vocab.git "$env:USERPROFILE\.codex\skills\thai-song-vocab"
```

macOS／Linux：

```sh
git clone https://github.com/phineascarter-arch/thai-song-vocab.git ~/.codex/skills/thai-song-vocab
```

如果目錄已存在，先確認是不是已安裝的版本，不要直接覆蓋本機修改。安裝後開啟新對話，明確使用 `$thai-song-vocab`。自訂 Codex skills 路徑的使用者，請改用自己的目錄。

透過 git clone 安裝的版本可在確認沒有未提交修改後，於 skill 目錄執行 `git pull --ff-only` 更新；其他安裝方式則使用同一安裝工具更新，先保留本機自訂內容。

## 使用

### 先從歌曲連結開始

```text
使用 $thai-song-vocab，幫我整理這首泰語歌：
歌名：
歌手：
官方 MV 或歌詞影片連結：
我是完全初學，請製作 HTML 學習頁、繁中筆記及 Anki CSV，
保留羅馬拼音、中文聲調與 Premwadee 女聲。
```

Skill 先找可讀且可核對的泰文來源。只有連結時，會依可使用範圍提供歌曲摘要、意象分析及極短節錄學習；不會直接重製整首受版權保護歌詞、完整羅馬拼音或整首逐行翻譯。

### 提供歌詞，製作逐段學習版

```text
使用 $thai-song-vocab，依照我下方提供的泰文歌詞製作逐段學習版。
歌名／歌手／版本：
官方連結：
歌詞：
（在這裡貼上歌詞，或附上 TXT／LRC／SRT／VTT 檔案）
```

會針對實際提供的內容區分字面意思、自然繁中翻譯與意象解讀；完整逐段版的每行都提供正常／慢速語音，以及可展開的詞義、句中作用與獨立詞塊發音，再另整理精選字卡。重複副歌只建卡一次，變字的副歌保留差異。有真實時間碼才提供定位回看；沒有就連回原曲，不猜時間。

## 交付與學習方式

- **HTML 學習頁**：搜尋、段落篩選、收藏／學會、隱藏中文自測、正常／慢速語音、逐詞拆解獨立點按發音（泰文下方附該詞羅馬拼音）、原曲回看、選擇題複習，以及 CSV／筆記／進度匯出。
- **Markdown 筆記**：主題摘要、拼音圖例、詞句拆解、意象解讀與來源限制。
- **Anki CSV**：兩欄正反面，正面泰文，背面繁中、羅馬拼音、聲調與用法。匯入時確認牌組和正反面預覽；文字 CSV 不含 Anki 語音媒體。

成果預設放在任務工作區的 `outputs/thai-song-vocab/{歌手slug}/{歌名slug}/`。HTML 是可獨立開啟的單檔；收藏與進度保存在目前瀏覽器，可匯出 JSON 備份，不會自動跨裝置同步。

## 發音與 iPhone

固定使用 **Microsoft Premwadee Neural 泰語女聲**（`th-TH-PremwadeeNeural`）。既有產製方式是第三方 Python 工具 `edge-tts` 呼叫 Microsoft Edge 線上語音服務，產出 MP3 後內嵌進頁面。工具不是聲音供應商，也不是 Microsoft 官方 SDK。

產生音訊需要可用工具及網路；若無法取得，會說明缺少音訊，不暗中換回其他聲音。頁面播放已內嵌 MP3 時，不需要登入語音服務或安裝泰文語音。固定女聲是技能設定，不代表安裝 skill 就已安裝語音工具或取得任何 API 憑證。

以 HTML audio、使用者點按播放與原生控制項支援 iPhone 使用情境，提供正常及慢速。不同裝置仍須實際測試；未經 iPhone 實機驗證時會明示限制。

羅馬拼音與中文聲調協助讀標準口語；合成語音不是歌唱示範或原唱音色。只有實際聽過對應音訊才描述唱法、連音或延音；無音訊核對時會註明。

## 檔案

```text
SKILL.md                       歌曲學習流程與內容範圍
agents/openai.yaml             Codex 顯示名稱與啟動範例
references/learning-page.md    HTML 資料格式、互動與驗證
references/voice.md            固定女聲、MP3 產製與 iPhone 播放
```

部署 GitHub Pages 或其他網站需另行要求；安裝 skill 不會自動發布學習內容。歌曲、歌詞及原唱錄音的權利屬原權利人，本專案不代表歌手或唱片公司的官方產品。


## 線上學習

- [คิดถึงจัง (มาหาหน่อย)：使用者提供歌詞版](https://phineascarter-arch.github.io/thai-song-vocab/)
- [ใจให้ไป — BIG 3 featuring แอ๊ป ธิดาศิริ](https://phineascarter-arch.github.io/thai-song-vocab/jai-hai-pai/)

兩首皆提供逐句翻譯、羅馬拼音、每句與每詞女聲、慢速重聽和聽音選詞。遊戲從逐詞拆解抽題，可按段落、目前句或搜尋篩選，作答後顯示拼音與中文並跳回原句。
