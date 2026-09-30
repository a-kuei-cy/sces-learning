# 興嘉學習大冒險 V2.2｜安全登入版

## 安全設計
- `index.html` 不含教師密碼、管理者密碼。
- 密碼存放在 Google Apps Script 的 Script Properties。
- 登入成功後由 GAS 核發 8 小時 Token。
- 題庫修改、學生名單管理、排行榜刪除等動作都由 GAS 再驗證 Token。
- 教師不能執行管理者專屬的刪除操作。

## GAS Web App
https://script.google.com/macros/s/AKfycbyxec9bqPFTVCrzezDWAMSDp0q5pdQxTcE54inQWmGt1nhnIAyqELpoEDfnP2pU3-g9jQ/exec

## 首次設定
1. 開啟原 Google Apps Script 專案。
2. 將 ZIP 中 `Code.gs` 完整取代原內容。
3. 儲存。
4. 在 Apps Script 編輯器執行一次 `setupScriptProperties()`。
5. 到「專案設定 → 指令碼屬性」。
6. 修改：
   - `TEACHER_USERNAME`
   - `TEACHER_PASSWORD`
   - `ADMIN_USERNAME`
   - `ADMIN_PASSWORD`
7. 不要把密碼寫入 `index.html`。
8. 部署 → 管理部署作業 → 編輯 → 建立新版本 → 部署。
9. GitHub Pages 上傳新的 `index.html`。

## 權限
學生：班級＋姓名登入、選科目單元、闖關、全對榮譽榜。
教師：題庫匯入匯出、新增題目、學生名單、統計。
管理者：教師功能＋刪除科目／單元／題目／排行榜。
