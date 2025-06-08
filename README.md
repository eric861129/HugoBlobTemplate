# Hugo Pure & Simple

一個極簡、功能豐富的 Hugo 部落格模板，專為希望專注寫作的您而設計。透過 GitHub Actions，只需幾個簡單步驟，就能擁有一個部署在 GitHub Pages 上的個人部落格。

**[→ 點此查看 Live Demo](https://eric861129.github.io/HugoBlobTemplate/)** _(請將此連結替換為您自己的 Demo 網站)_

## ✨ 功能特色

* **🚀 快速部署**：推送至 `main` 分支即可透過 GitHub Actions 自動部署至 GitHub Pages。
* **🎨 簡潔設計**：響應式設計，在桌面和行動裝置上都有良好體驗。
* **🌓 雙色主題**：內建淺色與深色模式，可一鍵切換，並自動記憶偏好。
* **🔍 全文搜尋**：整合 [Pagefind](https://pagefind.app/)，提供快速的離線搜尋功能。
* **💬 留言系統**：支援 [giscus](https://giscus.app/)，利用 GitHub Discussions 實現無廣告的留言互動。
* **📚 功能完整**：
    * 程式碼區塊語法高亮與一鍵複製功能。
    * 為長篇文章自動生成浮動目錄 (TOC)。
    * 自動化的標籤雲 (Tag Cloud) 與文章月曆側邊欄。
    * 外部連結自動在新分頁開啟，提升閱讀體驗。

---

## 🚀 快速開始 (三步驟擁有你的部落格)

### 步驟 1：使用此模板建立您的儲存庫

點擊頁面右上角的 **"Use this template"** -> **"Create a new repository"**。

<img width="800" src="https://user-images.githubusercontent.com/10986872/204873187-27244580-0c3a-4a6c-8968-358a3798dfc3.png">

為您的儲存庫取一個名字 (例如 `my-awesome-blog`)，然後點擊建立。

### 步驟 2：設定 GitHub Pages 的部署權限

1.  進入您剛剛建立的儲存庫，點擊 **Settings** -> **Actions** -> **General**。
2.  捲動到頁面底部，在 "Workflow permissions" 區塊，選擇 **"Read and write permissions"**，並儲存。這能確保 GitHub Actions 有權限將網站推送到 `gh-pages` 分支。

<img width="800" src="https://i.imgur.com/PcmN3xT.png">

### 步驟 3：修改核心設定檔

這是最重要的一步！您需要告訴 Hugo 您的網站網址和儲存庫名稱。

1.  回到儲存庫的程式碼頁面，找到並打開 `hugo.toml` 檔案進行編輯。
2.  **修改 `baseURL`**：將 `baseURL` 的值修改為您的 GitHub Pages 網址。格式為 `https://<您的 GitHub 帳號>.github.io/<您的儲存庫名稱>/`。
3.  **修改其他資訊**：順便修改網站標題 (`title`) 和作者名稱 (`author.name`)。

    ```toml
    # 範例：如果您的 GitHub 帳號是 octocat，儲存庫名稱是 my-blog
    # 那 baseURL 就應該是 "https://octocat.github.io/my-blog/"
    baseURL = "https://octocat.github.io/my-blog/"
    
    title = "Octocat 的開發筆記"
    
    [author]
      name = "Octocat"
    ```
4.  接著，修改部署設定檔：
    * 打開 `.github/workflows/gh-pages.yml`，若直接使用此範例專案，可維持 `baseURL` 為 `/HugoBlobTemplate/`；若另建儲存庫，請改成您的儲存庫名稱，例如 `/my-blog/`。
    * 打開 `.htmltest.yml`，同樣將 `IgnoreURLs` 的值 `/HugoBlobTemplate/.*` 或您的儲存庫名稱調整一致。

5.  儲存並提交 (Commit) 所有變更。

**🎉 恭喜！** 提交後，GitHub Actions 會開始自動部署。幾分鐘後，您就可以在 `https://<您的帳號>.github.io/<您的儲存庫名稱>/` 看到您的新部落格了！

---

## ✍️ 寫作與本地預覽

### 建立新文章

在專案的根目錄下執行以下指令：
```bash
hugo new posts/my-first-post.md
```
然後您就可以在 `content/posts/` 目錄下找到 `my-first-post.md` 並開始用 Markdown 寫作。

### 本地端預覽 (推薦)

1.  **安裝 Hugo (Extended Version)**
    * **macOS**: `brew install hugo`
    * **Windows**: `scoop install hugo-extended` 或 `choco install hugo-extended`
    * **其他系統**: 參考 [Hugo 官方安裝文件](https://gohugo.io/getting-started/installing/)。

2.  **啟動本地伺服器**
    ```bash
    hugo server -D
    ```
    現在，打開瀏覽器訪問 `http://localhost:1313` 即可看到您的網站。

---

## 🔧 進階設定

### 設定留言功能 (giscus)

1.  確保您的部落格儲存庫是**公開 (Public)**的。
2.  前往 [giscus.app](https://giscus.app) 進行設定，並授權 App 存取您的儲存庫。
3.  依照 giscus 網站的指引，啟用儲存庫的 **Discussions** 功能，並選擇一個討論分類 (例如 "Announcements")。
4.  giscus 會產生 `repo`, `repoId`, `category`, `categoryId` 四個值。
5.  將這四個值填入 `hugo.toml` 的 `[params.giscus]` 區塊中。
6.  提交變更後，文章頁面下方就會出現留言區。

### 設定社群媒體外部連結

若要在側邊欄顯示您常用的社群或相關網站連結，可在 `hugo.toml` 裡加入 `[params.social]`
區塊，並以 `名稱 = "網址"` 的方式列出。例如：

```toml
[params.social]
  GitHub = "https://github.com/your-name"
  Twitter = "https://twitter.com/your-name"
  個人網站 = "https://your-blog.com"
```

只要設定完成並重新部署，網站右側的「相關連結」區塊就會列出這些外部連結，並在新分頁開啟。

## ❓ 疑難排解

### 主題切換按鈕消失

1. 確認 `layouts/_default/baseof.html` 中仍包含 `<button id="theme-toggle">` 標記。
2. `assets/css/custom.css` 必須保留與 `#theme-toggle` 相關的樣式設定。
3. 若仍看不到按鈕，請檢查瀏覽器開發者工具，確認 `custom.css` 與頁面底部 JavaScript 是否成功載入。

### 首頁連結 404

若點擊網站標題後跳到錯誤的頁面，請在 `hugo.toml` 將 `baseURL` 設為：

```toml
baseURL = "https://eric861129.github.io/HugoBlobTemplate/"
```

並確保 `.github/workflows/gh-pages.yml` 也使用相同路徑。

---

## 🤝 貢獻

歡迎任何人對此專案做出貢獻！詳情請參考 [CONTRIBUTING.md](CONTRIBUTING.md)。

## 📄 授權

本專案採用 [MIT License](LICENSE) 授權。
