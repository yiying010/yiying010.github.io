# 林依瑩｜個人履歷與作品集

沿用原始 GitHub Pages 的純 HTML 架構。頁面、CSS 與少量導覽 JavaScript 均保留在 `index.html`，不需 Node.js、npm、框架或建置步驟。

## 網站維護說明

日後更新文字、更換照片、新增專案與重新部署，請參閱 [完整網站維護說明](website-maintenance-guide.md)。內含檔案對照表、修改範例、可複製的專案模板、部署檢查表與常見問題處理。

## 網站備份下載與還原

- 備份日期：2026-10-28（Asia/Taipei）。
- 備份版本：`backup-2026-10-28-18f675e`，來源提交 `18f675e84aa684756f8db8100111001917b6fbb2`。
- [Release 說明與還原步驟](https://github.com/yiying010/yiying010.github.io/releases/tag/backup-2026-10-28-18f675e)
- [下載完整網站備份 ZIP](https://github.com/yiying010/yiying010.github.io/releases/download/backup-2026-10-28-18f675e/yiying-website-backup-2026-10-28-18f675e.zip)（包含網站、四張圖片與維護說明）。

還原時先備份目前版本，再解壓縮上述 ZIP，將同一份備份的 `index.html`、`assets/`、`README.md` 與 `website-maintenance-guide.md` 放回儲存庫 `main` 分支根目錄並提交；等待 GitHub Pages 部署成功後確認正式網站。詳細操作與校驗碼請見[維護說明第 9 節](website-maintenance-guide.md#9-常見問題與還原方式)。

這是固定日期的歷史備份，不會自動包含後續修改，也不包含這次新增的下載連結。之後更新請先取得 `main` 的最新內容。

## 檔案

- `index.html`：更新個人定位、響應式版面、無障礙導覽、搜尋與分享資訊。
- `assets/profile.jpg`：使用者提供的個人形象照，保存為本地資源；原始照片不另行修圖，僅透過 CSS 調整顯示裁切。
- `assets/avatar.png`：使用者提供的似顏繪，作為導覽列 Logo；以 CSS 聚焦頭肩，維持原桌機 36px、手機 31px 的 1:1 尺寸與圓角，使用 `object-fit: cover`，原圖不另行修圖。
- `assets/project-01.png`：使用者提供的魚骨洞天專案畫面，可點擊開啟 Demo。
- `assets/teacher-training.png`：使用者提供的 AI 教學代理人設計教師培訓現場照片，保留完整畫面。
- `README.md`：專案概覽、預覽方式與維護說明入口。
- `website-maintenance-guide.md`：文字與照片更新、新增專案、重新部署及常見問題的完整操作指南。

## 頁面區塊

首頁 Hero、About、六項 Skills、Experience、Projects、Teacher Training、Tools、Contact。

工作經驗依職能整理，未捏造任職日期、公司名稱、量化成果或技術熟練程度。原站職稱及具名計畫的任職狀態未經重新確認，因此新版使用使用者提供的經驗描述。移除原站地址地圖，將重點放在履歷、作品及聯絡方式。

## 本機預覽

在本資料夾開啟終端機，執行：

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

瀏覽 `http://127.0.0.1:8000/`；結束時按 `Ctrl+C`。也可直接開啟 `index.html`，所有內容、相對圖片路徑與頁內導覽都可運作。

## 部署 GitHub Pages

將 `index.html`、`assets/`、`README.md` 放入原始 `yiying010/yiying010.github.io` 儲存庫根目錄，保留原本其他設定。

1. 提交並推送至原站發布使用的分支；本次下載的分支是 `main`。
2. GitHub 儲存庫 Settings → Pages：沿用原本部署方式。若使用 Deploy from a branch，選擇 `main` 與 `/ (root)`。
3. 等待 Pages 部署成功後，開啟 `https://yiying010.github.io/`。若看到舊版，可重新整理或清除瀏覽器快取。

不需要新增 GitHub Actions、變更網域或執行 build。所有本地資源使用相對路徑，也能在儲存庫子路徑下顯示。

## 專案、照片與聯絡資訊

- 專案 Demo：https://fishbone-cave-yiying.s9551830.chatgpt.site/
- 專案 GitHub Repository：https://github.com/yiying010/fishbone
- 已放入使用者指定的專案畫面與教師培訓現場照片。
- 聯絡電話更新為 `0923737519`，使用 `tel:` 可點擊撥號。
- 已移除 RELATED CHANNEL / YouTube 相關頻道欄位。
- 技術標籤保留已確認的 Generative AI、Codex、需求整理與功能測試；若需增加其他技術，請先確認實際使用情形。

## 本次交付與驗證結果

網站發布沿用原儲存庫的 GitHub Pages 設定；部署狀態可在儲存庫 Actions 與 Deployments 查看。

- 瀏覽器檢查桌機 1280px、平板 768px、手機 390px 與窄螢幕 320px：沒有橫向溢出。
- 手機選單展開、選擇區塊後收合、Esc 關閉及焦點移動正常。
- 六項專長卡片、專案畫面與教師培訓照片均已放入。
- HTML 標籤配對、唯一 ID、頁內連結、本地圖片與 JavaScript 語法檢查通過。
- 透過 HTTP 本機預覽回應 200，沒有觀察到瀏覽器 console 錯誤。
- 發布後以公開網站內容及 GitHub Pages 部署狀態確認更新結果。

## 連結與驗證範圍

- GitHub 個人頁保留，相關影音頻道欄位已依使用者要求移除。
- 保留原站 Email，連結使用 `mailto:`；沒有寄信驗證收件能力。
- 個人照片已替換為使用者提供的本地 JPG，保留原始影像；桌機與手機採不同的顯示裁切。
- Demo 與專案 Repository 已確認 HTTP 200，另開視窗並加上 `rel="noopener noreferrer"`。
- 不依賴外部字型、UI 套件、追蹤服務或外部腳本。
