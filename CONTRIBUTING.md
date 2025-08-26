# 貢獻指南

歡迎參與本專案！無論是回報錯誤、補充內容、修正章節、貢獻程式碼或文檔，您的參與都非常重要。請依照以下流程協助維護本專案品質。

<br>

## 環境需求

- `Rust` 與 `Cargo` 版本 ≥ 1.84  <br>
    安裝步驟請參考：[Install Rust](https://www.rust-lang.org/tools/install)  <br>
    （搭建 mdBook 用）

- [mdBook](https://github.com/rust-lang/mdBook) 版本 ≥ v0.4.52。
    利用 Rust 的套件管理工具 `Cargo` 來安裝，安裝步驟：
    ```bash
    cargo install mdbook
    ```

- 以上兩者皆安裝完成後，請接著執行：
    ```bash
    rustc --version
    ```
    ```bash
    cargo --version
    ```
    ```bash
    mdbook --version
    ```

- 選用工具：
  - [mdbook-toc](https://github.com/badboy/mdbook-toc)
    自動在每頁生成本章目錄

  - [mdbook-mermaid](https://github.com/badboy/mdbook-mermaid)
    支援 Mermaid 語法，方便繪製流程圖、時序圖

<br>

## 專案架構

- `src/`：主文檔內容（Markdown 格式）
- `LICENSES`：
- `book.toml`：mdBook 設定檔
- `SUMMARY.md`：目錄結構
- `assets/`：圖片、補充資料
- `CONTRIBUTING.md`：貢獻指南
- `ti_mmwave/`：德州儀器相關資源與章節

<br>

## 如何貢獻

1. **Fork 本專案**  

   Fork 此專案到自己的 GitHub

2. **建立分支** 

   建議使用 descriptive branch name，例如 `feature/add-mmwave-algorithms`

3. **撰寫 / 修改內容**

   - 新增或修正 Markdown 章節

   - 請遵循章節命名及目錄規範（見 `SUMMARY.md`）

   - 圖片請放在 `assets/` 資料夾

4. **本地預覽書籍**  
   
   執行
   ```bash
   mdbook serve
   ```
   後，開啟預設 [http://localhost:3000](http://localhost:3000)，或直接開啟預覽：
   ```bash
   mdbook serve --open
   ```

5. **提交 Pull Request**  
   - PR 請詳述修改內容

   - Commit message 請遵循 [Conventional Commits](https://www.conventionalcommits.org/zh-hant/v1.0.0/) 格式 (請善用 Copilot :)

   - 請確保本地編譯無誤（`mdbook build`）

6. **等待審核與討論**  
   貢獻內容將由維護者審核，必要時協助修改、合併

<br>

## 貢獻範疇

- 修正錯誤、排版、語法、~~翻譯~~

- 增加章節、案例、演算法、工具教學

- 貢獻相關資源、學習路徑、環境設定

- 回報問題（請開 issue，並詳述步驟與環境、版本）

<br>

## 風格建議

- 章節標題與目錄請統一語言（建議中文、可中英並列）

- 檔案命名採用英文（如 `mmwave_basics.md`）

- 內容清楚、條理分明、分段明確

- 圖片需有說明文字

- 待架構完整時做 i18n

<br>

## 本地開發與測試

1. **預覽書籍（Hot Reload）**
   ```bash
   mdbook serve --open
   ```
   - 預設於 http://localhost:3000 開啟預覽

   - 文件變更會自動刷新

2. **編譯書籍（Build）**
   ```bash
   mdbook build
   ```
   - 產生靜態網頁於 `book/` 資料夾

3. **測試書籍（Test）**
   ```bash
   mdbook test
   ```
   - 執行自動化測試（需 mdBook 支援的測試語法）

4. **清理建置檔案（Clean）**
   ```bash
   mdbook clean
   ```
   - 移除舊的建置輸出

### 開發建議

- 編輯 Markdown 內容時，建議隨時預覽 (`mdbook serve --open`)

- 完成編輯請務必執行 `mdbook build` 確認沒有語法錯誤

- Pull Request 前請跑 `mdbook test`，確保測試通過

### 其他工具

- 若使用 Mermaid、PlantUML 等工具，請參考本專案 `book.toml` 配置與相關說明

### 常見問題

- 若遇到 mdBook 相關錯誤，請先嘗試 `mdbook clean` 後再 `mdbook build`

- 如遇指令無法執行，請確認已安裝最新版 mdBook

<br>

## 作者與貢獻

- 若你的貢獻屬於「新增章節、主要重構、腳本或工作流程」，可在同一個 PR 將你的名字加入 AUTHORS.md（按字母順序）。

- 一般小變更（拼字、行內修正）會透過 `scripts/update_contributors.sh` 進入 CONTRIBUTORS.md。

<br>

## 聯絡方式

- issue 討論區：GitHub Issues
- Pull Request 討論區：GitHub PR
- 緊急聯絡： mellivorandy@gmail.com

---
<br>

> 感謝您的貢獻！ <br>
> 如果有任何問題，請隨時開 issue 或 PR 討論。
