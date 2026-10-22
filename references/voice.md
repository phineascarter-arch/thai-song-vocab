# 預設女聲與 iPhone 播放

固定採用使用者已選定的 **Microsoft Premwadee Neural 泰語女聲**，voice ID 為 `th-TH-PremwadeeNeural`，語系 `th-TH`。未經要求不換回 Windows Pattara、男聲或其他女聲。

## 產製

以本次可交付且讀音已核對的泰文學習短句產生 MP3。既有做法是第三方 Python 套件 `edge-tts` 呼叫 Microsoft Edge 線上語音服務；工具不是聲音供應商，也不是 Microsoft 官方 SDK，不宣稱開通了 Azure 付費 API。

工具可用時：

```python
await edge_tts.Communicate(
    thai_text,
    voice="th-TH-PremwadeeNeural",
    rate="+0%",
    pitch="+0Hz",
    volume="+0%",
).save(mp3_path)
```

依目前權限取得所需工具，不假定已安裝、不複製其他聊天的環境絕對路徑或憑證。只送本次學習短句，不送整首錄音或無關使用者資料。單句失敗最多三次，仍失敗則保留筆記與原曲回看並說明缺少音訊；不可用假檔或暗中換聲音。

同一句只產生一份正常速度音檔，慢速透過播放器約 `0.71` 倍 playbackRate 並保留音高。合成語音不是唱歌，不用旋律移調或延音來假裝歌手唱法。

## 頁面

- 每筆資料以 `audio: "data:audio/mpeg;base64,..."` 內嵌 MP3，讓單檔播放不依賴即時 TTS、裝置泰文語音或工作區檔案。
- 用 HTML audio，保留原生 controls 與 `playsinline`。開啟詳細卡片時載入對應音訊，不能顯示無來源的停用播放器。
- iPhone 的播放由使用者點按直接觸發，不自動播放、不在點按與 `play()` 之間等待網路合成。正常／慢速按鈕共用播放器；切換卡片先停止舊音訊。
- 顯示「Microsoft Premwadee Neural 女聲／標準口語合成，非原唱」。播放讀取內嵌檔案，無須使用者登入語音服務。
- 捕捉 `play()` 拒絕與解碼錯誤，提供手動播放與原曲回看。不能因偵測到聲音或播放器存在就宣稱已播放。
- 驗證 MP3 非空且可解碼，操作正常／慢速時觀察進度、paused、rate 與 error。沒有實體 iPhone 時如實說明，桌面通過不代表 iOS 實測通過。
