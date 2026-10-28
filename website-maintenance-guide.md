# 林依瑩個人網站維護說明

適用版本：2026-10-28 上線版。網站沿用原生 HTML、CSS 與少量 JavaScript，日常更新不需要安裝 npm 套件或執行 build。

## 1. 先找到正確的檔案

| 項目 | 位置／用途 |
| --- | --- |
| 正式網站 | [https://yiying010.github.io/](https://yiying010.github.io/) |
| 個人網站儲存庫 | [yiying010/yiying010.github.io](https://github.com/yiying010/yiying010.github.io) |
| 發布分支與位置 | `main` 分支，儲存庫根目錄 |
| 首頁主檔 | [index.html](https://github.com/yiying010/yiying010.github.io/blob/main/index.html) |
| 圖片資料夾 | [assets](https://github.com/yiying010/yiying010.github.io/tree/main/assets) |
| 部署進度 | [Actions](https://github.com/yiying010/yiying010.github.io/actions) |
| 魚骨洞天作品程式 | [yiying010/fishbone](https://github.com/yiying010/fishbone) |

個人網站的檔案結構如下：

```text
yiying010.github.io/
├── index.html                  網頁文字、版面樣式、手機選單
├── README.md                   專案說明與預覽方式
└── assets/
    ├── avatar.png              左上角似顏繪 Logo
    ├── profile.jpg             首頁個人形象照
    ├── project-01.png          魚骨洞天專案截圖
    └── teacher-training.png    教師培訓現場照片
```

`index.html` 裡的 `<style>…</style>` 是視覺樣式，`<body>…</body>` 是頁面內容，最下方的 `<script>…</script>` 處理手機選單。只改文字或圖片時，通常只需調整頁面內容與圖片檔案。

開始修改前，先從 GitHub 儲存庫選擇 **Code → Download ZIP** 備份目前版本。之後以 GitHub `main` 分支的最新內容為準，避免把較舊的本機檔案重新覆蓋上去。

## 2. 日常維護的兩種方式

### A. 少量文字：直接在 GitHub 編輯

1. 登入能管理此儲存庫的 GitHub 帳號。
2. 開啟儲存庫，確認分支是 `main`，點進 `index.html`。
3. 點鉛筆圖示 **Edit this file**。
4. 找到要修改的原本文字，保留前後的 HTML 標籤。
5. 檢查修改差異，再點 **Commit changes…**。
6. 填寫簡短說明，例如「更新工作經驗描述」。目前個人網站可選 **Commit directly to the main branch**；這會觸發公開網站更新。若改用新分支或日後啟用分支保護，需先將變更合併回 `main`。
7. 到 Actions 確認部署成功，再檢查正式網址。

GitHub 網頁編輯器的 Preview 不等於完整網站的瀏覽器預覽；排版變更適合先在本機查看。[GitHub 官方：編輯檔案](https://docs.github.com/en/repositories/working-with-files/managing-files/editing-files)

### B. 圖片、版面或多處內容：先在本機修改

1. 下載最新原始碼並解壓縮。
2. 使用純文字／程式碼編輯器開啟 `index.html`，以 UTF-8 儲存。
3. 將圖片放進 `assets/`，修改文字或程式碼。
4. 依第 6 節啟動本機預覽。
5. 確認桌機與手機顯示後，依第 7 節上傳。

不要用 Word 儲存 HTML 原始碼，以免加入額外格式。

## 3. 如何更新文字與聯絡資訊

### 找到對應位置

在編輯器搜尋以下名稱或原本的句子；行號可能隨修改而改變，因此以文字與 `id` 定位比較穩定。

| 要更新的內容 | 在 `index.html` 搜尋 |
| --- | --- |
| 首頁姓名與定位 | `id="home"`、`hero-position` |
| 首頁完整簡介 | `hero-description` |
| 個人格言 | `hero-note` |
| 學歷與關於我 | `id="about"` |
| 六項專長 | `id="skills"`、`skill-card` |
| 工作經驗 | `id="experience"`、`experience-item` |
| 專案名稱與說明 | `id="projects"`、`project-content` |
| 教師培訓內容 | `id="training"` |
| 工具清單 | `tools-list` |
| Email、GitHub、電話 | `id="contact"` |

例如更新首頁定位，只修改標籤中間的文字：

```html
<p class="hero-position">研究 × 教育 × AI × 數位專案</p>
```

更新段落時保留 `<p>…</p>`；新增一點工作內容時，可在原本的 `<ul>…</ul>` 中加入一組 `<li>新的工作內容</li>`。

若定位或簡介有大幅調整，也一併檢查檔案上方的 `<title>`、`meta name="description"`、`og:title` 與 `og:description`，讓搜尋與分享資訊保持一致。這些中繼資料的 `content="…"` 內容要保留引號。

### 更新電話或 Email：連結與畫面文字要一起改

目前電話的兩個位置如下：

```html
<a class="contact-row" href="tel:0923737519">
  <span>
    <span class="label">PHONE / 聯絡電話</span>
    <span class="value">0923737519</span>
  </span>
  <span class="contact-arrow" aria-hidden="true">↗</span>
</a>
```

換號碼時，同時修改 `href="tel:…"` 和 `class="value"` 裡的數字。Email 同樣要一起更新 `mailto:…` 和畫面顯示的地址。一般網址則修改 `href="https://…"`。

若文字需要顯示 `&`、`<`、`>`，請分別使用 `&amp;`、`&lt;`、`&gt;`，避免被誤認成 HTML 語法。

## 4. 如何更換照片

### 最省事的方法：沿用圖片檔名

| 圖片 | 要替換的檔案 | 現在的顯示方式 |
| --- | --- | --- |
| 導覽列 Logo | `assets/avatar.png` | 1:1 裁切；桌機 36px、手機 31px |
| 首頁個人照 | `assets/profile.jpg` | `object-fit: cover`；手機顯示圓形頭像 |
| 魚骨洞天截圖 | `assets/project-01.png` | 等比例完整顯示 |
| 教師培訓照片 | `assets/teacher-training.png` | 等比例完整顯示 |

用新圖片取代同一路徑的檔案，即可沿用目前的圖片連結。請保留正確的檔案格式；例如 JPEG 圖片不能只把副檔名改成 `.png` 當作轉檔。

在 GitHub 更新圖片：進入 `assets` 資料夾 → **Add file → Upload files** → 選取新圖 → 確認檔名與資料夾位置 → **Commit changes**。[GitHub 官方：上傳檔案](https://docs.github.com/en/repositories/working-with-files/managing-files/adding-a-file-to-a-repository)

### 改用新檔名時

例如將培訓照片改成 `teacher-training-2027.jpg`：

1. 先上傳到 `assets/teacher-training-2027.jpg`。
2. 在 `index.html` 搜尋 `teacher-training.png`，修改圖片路徑。
3. 更新 `alt` 說明、圖片原始寬高及照片下方的 `figcaption`。

```html
<!-- 下列寬高是示範值，請改成新圖片的原始像素尺寸。 -->
<img
  src="assets/teacher-training-2027.jpg"
  alt="新的教師培訓現場內容說明"
  width="1600"
  height="900"
  loading="lazy">
```

`width`、`height` 填原圖像素比例，網頁仍會由 CSS 自動縮放。建議以簡短英文、小寫字母、數字及連字號命名圖片，例如 `project-02.png`，並保持大小寫一致。

### 頭像與個人照的裁切

- **似顏繪 Logo**：保留 `.brand-mark` 的尺寸與 1:1 比例。現在 `.brand-mark img` 使用 `object-fit: cover`、`scale(1.28)`、`transform-origin: 50% 18%` 聚焦頭肩。換新圖後若帽子太靠近邊緣，可先將縮放倍率稍微降低，再檢查 31px 手機尺寸。
- **首頁個人照**：搜尋 `.profile-img`。目前用 `object-position: 50% 15%` 控制裁切位置；更換照片後，需以實際預覽調整臉部位置，並保留 `object-fit: cover`。
- **完整截圖與培訓照片**：目前使用自動高度，保留圖片比例。不要額外把寬高都寫死成不同於原圖的比例。

目前個人照網址含有 `profile.jpg?v=2`。問號後面是快取版本，不是檔名。若沿用同名照片但一直看到舊圖，可將 HTML 中出現的 `profile.jpg?v=2` 全部改為 `profile.jpg?v=3`；目前包含首頁照片及分頁圖示。若圖片改成其他檔名，也一起更新這兩處及對應的圖片格式。

## 5. 如何新增專案

不必另外新增網頁。新增專案卡片後，原本「專案成果」導覽仍會跳到同一個專案區塊。

### 第一步：準備素材

準備專案名稱、背景、你的角色、執行過程、可確認的成果、實際使用工具、截圖、Demo 與 Repository 網址。圖片可命名為 `assets/project-02.png`。

### 第二步：找到插入位置

搜尋 `id="projects"`。目前結構為：

```html
<section class="section projects-section" id="projects" ...>
  <div class="wrap">
    <!-- 區塊標題 -->
    <article class="project-card">
      <!-- 原本的魚骨洞天專案 -->
    </article>
    <ol class="project-process">
      <!-- 原本專案的四個流程 -->
    </ol>

    <!-- 將新專案卡片貼在這裡，仍在 wrap 和 section 裡面。 -->
  </div>
</section>
```

以上是定位示意，省略號與註解不需要取代原本程式碼。新增卡片時，不要重複新增 `id="projects"`，也不要刪除區塊結尾的 `</div>`、`</section>`。

為了讓卡片之間留白，可在原檔案的 `<style>` 區塊內、其他專案樣式旁，加入一次：

```css
.project-process + .project-card,
.project-card + .project-card {
  margin-top: 32px;
}
```

### 第三步：貼上新專案範例

以下是編輯模板；請先把示範名稱、圖片說明、網址、工具及尺寸全部換成真實內容，再部署。`example.com` 是範例網址。

```html
<article class="project-card">
  <figure class="project-visual">
    <div class="project-visual-header">
      <span>PROJECT / 02</span>
      <span>專案領域</span>
    </div>
    <a class="project-preview"
       href="https://example.com/demo"
       target="_blank"
       rel="noopener noreferrer"
       aria-label="開啟新專案 Demo（另開視窗）">
      <img src="assets/project-02.png"
           alt="新專案的實際操作畫面說明"
           width="1600" height="900"
           loading="lazy">
    </a>
    <figcaption>專案名稱 · 畫面說明</figcaption>
  </figure>

  <div class="project-content">
    <p class="project-type">專案名稱 / 領域</p>
    <h3>新專案名稱</h3>
    <p>說明專案需求、目標，以及你負責的工作。</p>
    <p>說明執行過程、測試方式，以及可確認的成果。</p>
    <ul class="tags" aria-label="專案使用工具與方法">
      <li>實際使用的工具</li>
      <li>實際採用的方法</li>
    </ul>
    <div class="project-links" aria-label="專案連結">
      <a class="button primary"
         href="https://example.com/demo"
         target="_blank" rel="noopener noreferrer">
        體驗 Demo <span aria-hidden="true">↗</span>
      </a>
      <a class="button"
         href="https://github.com/your-account/your-project"
         target="_blank" rel="noopener noreferrer">
        GitHub Repository <span aria-hidden="true">↗</span>
      </a>
    </div>
  </div>
</article>
```

- **沒有 Demo**：刪除 Demo 按鈕；將包住截圖的 `<a class="project-preview" …>` 改成 `<div class="project-preview">`，並將對應的 `</a>` 改成 `</div>`。
- **沒有公開 Repository**：刪除該 Repository 按鈕。若兩個按鈕都沒有，可一併刪除整個 `.project-links` 容器。
- **尚未有圖片**：先準備圖片再引用，避免上線後出現破圖。
- **需要專案流程**：可在新卡片後複製一份原本的 `<ol class="project-process">…</ol>`，再更新每一步的文字。

若要修改既有魚骨洞天的 Demo 網址，記得同時更新截圖外層連結與「體驗 Demo」按鈕。

## 6. 如何在本機預覽

在「含有 `index.html` 與 `assets/` 的資料夾」開啟終端機，執行：

```sh
python3 -m http.server 8000 --bind 127.0.0.1
```

開啟 [http://127.0.0.1:8000/](http://127.0.0.1:8000/)。這個終端機／服務必須保持執行，結束時按 `Ctrl+C`。

- 出現「127.0.0.1 拒絕連線」：先確認預覽服務是否仍在執行，再重新啟動。
- 顯示資料夾清單：通常是從錯誤資料夾啟動，請進入有 `index.html` 的位置。
- 顯示連接埠已被使用：可改用 `8001` 啟動，並改開 `http://127.0.0.1:8001/`。
- 本機網址供這台電腦預覽使用；分享網站時使用正式的 `https://yiying010.github.io/`。

用瀏覽器開發者工具切換手機尺寸，至少檢查 320px、390px、430px，並用自己的手機開啟正式網址確認實際操作。

## 7. 如何重新部署到 GitHub Pages

### 使用 GitHub 網頁上傳

1. 本機確認修改完成。
2. 若有新增或更名的圖片，先到儲存庫 `assets` 資料夾上傳並提交，讓新圖片路徑先存在。
3. 回到儲存庫根目錄，上傳修改後的 `index.html`；有修改 `README.md` 時再一併上傳。
4. 確認替換的是 `main` 分支根目錄中的檔案，填寫提交說明並提交。
5. 開啟 [Actions](https://github.com/yiying010/yiying010.github.io/actions)，查看本次提交對應的 **pages build and deployment**。
6. 等待狀態為 **Success**，並確認 `build`、`deploy` 成功。只看到「檔案已提交」時，部署可能仍在進行。
7. 開啟 [正式網站](https://yiying010.github.io/)，核對剛修改的文字與圖片。

提交到發布分支後，GitHub Pages 會自動更新；無須每次重設 Pages 或新增工作流程。發布來源可在 **Settings → Pages → Build and deployment** 檢查：此網站目前使用 `main` 的根目錄；若是分支發布，介面為 **Deploy from a branch → main → /(root)**。[GitHub 官方：設定發布來源](https://docs.github.com/en/pages/getting-started-with-github-pages/configuring-a-publishing-source-for-your-github-pages-site)

上傳原始碼時，選擇 `index.html`、`README.md` 與所需的 `assets` 圖片。網站 ZIP 用於備份和傳送，GitHub Pages 不會自動把上傳的 ZIP 解壓成網站。

### 已熟悉 Git 時的替代方式

在已 clone 且設定好 Git 驗證的儲存庫內，先同步 `main`，再開始修改：

```sh
git switch main
git pull --ff-only origin main
```

修改及本機預覽後：

```sh
git diff --check
git add index.html assets/
# 若這次有修改 README.md，再執行：git add README.md
git diff --cached --stat
git commit -m "Update portfolio content"
git push origin main
```

若 `pull` 出現本機變更或衝突訊息，先保留手上的修改再處理。若終端機無法推送，可使用上述 GitHub 網頁上傳方式；瀏覽器登入與終端機的 Git 驗證是分開的。

## 8. 上線後的快速檢查表

- [ ] 網址是 `https://yiying010.github.io/`，且看到剛更新的內容。
- [ ] 左上角頭像、個人照、專案截圖及培訓照片皆載入正常。
- [ ] 桌機與手機沒有橫向溢出，照片沒有變形，文字沒有被遮住。
- [ ] 手機選單可展開、關閉，點選後會跳轉及收合。
- [ ] Demo、Repository、個人 GitHub 等外部連結可開啟。
- [ ] Email、電話的畫面文字與 `mailto:`、`tel:` 目標一致。
- [ ] 沒有留下範例網址、待填文案或引用不存在的圖片。
- [ ] Actions 中，這次提交對應的 Pages 部署已成功。

## 9. 常見問題與還原方式

| 情況 | 處理方式 |
| --- | --- |
| 正式網站仍是舊版 | 確認改的是正確儲存庫與 `main`，再查看這次提交的 Actions；部署成功後重新整理或用無痕視窗檢查。 |
| 只有照片還是舊圖 | 檢查是否上傳到正確路徑；可更新圖片網址版本參數，例如 `?v=3`。 |
| 圖片不見 | 檢查 `assets/` 路徑、大小寫、副檔名與圖片是否已提交；不要將電腦上的 `/Users/…` 路徑填入網頁 `src`。 |
| 點照片會去錯誤 Demo | 檢查 `.project-preview` 外層的 `href`，並與 Demo 按鈕網址一起更新。 |
| 文字後面的版面亂掉 | 比較修改前後，檢查是否漏掉 `</p>`、`</div>`、`</article>`，或刪到引號、CSS 大括號。 |
| Actions 部署失敗 | 點開失敗的那次執行及紅色工作，查看錯誤內容；保留錯誤訊息以便排查。 |
| 本機預覽與線上不同 | 確認上傳了目前預覽的檔案，並等待部署完成後刷新正式網站。 |

需要還原時，可從先前備份取出正確檔案，或在 GitHub 的檔案 History／提交歷史中找到之前版本，再將同一版本的 HTML 與對應圖片重新提交至 `main`。這樣能保留修改歷史，也會再次觸發部署。

本指南整理時的已驗證版本為 [`1fef97b`](https://github.com/yiying010/yiying010.github.io/commit/1fef97b5d8f1dee70013203bb55ecfa0736ea90f)，[對應部署紀錄](https://github.com/yiying010/yiying010.github.io/actions/runs/40619542714)已成功。之後若有新修改，請以新的成功版本作為備份基準。

## 10. 交給 Codex 協助時，可直接使用的描述

> 請更新我的個人網站 yiying010/yiying010.github.io，沿用現在的 HTML 架構與視覺。要修改的內容如下：……。圖片用途分別是：……。先確認桌機與手機排版，再部署到 https://yiying010.github.io/，並確認 GitHub Pages 成功及正式網站內容已更新。需要登入 GitHub 時再告訴我。
