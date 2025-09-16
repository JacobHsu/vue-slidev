# 使用 Slidev 建構 Vue 簡報

這個專案是以 [Slidev](https://github.com/slidevjs/slidev) 為核心的互動式簡報範本，透過 Vue 3 + Markdown 打造可即時預覽的投影片開發流程。複製此倉庫後只要安裝依賴，就能立即開始編輯 slides.md 或加入自訂元件。

## 環境需求

- Node.js 18 以上版本
- [pnpm](https://pnpm.io/) 8 以上版本（建議使用 corepack enable pnpm 啟用）

如需 Playwright 匯出功能，請確保系統能安裝必要的 Chromium 依賴。

## 快速開始

```bash
pnpm install
pnpm dev
```

開發伺服器預設在 <http://localhost:3030> 啟動並自動開啟瀏覽器。修改 slides.md、components/ 或 snippets/ 內的檔案後，Slidev 會即時重新整理畫面。

## 常用指令

- pnpm dev：啟動開發伺服器與即時預覽。
- pnpm build：把投影片打包成 dist/ 內的靜態網站，適合部署到 CDN 或靜態空間。
- pnpm export：匯出 PDF、PNG 或 SPA（第一次執行會詢問格式，亦可加上 --format pdf 等參數）。

更多指令和旗標請參考官方文件：<https://sli.dev/reference/cli.html>。

## 專案結構

- slides.md：主要的 Markdown 投影片檔案，支援 front matter 及程式碼語法高亮。
- components/：客製化 Vue 組件，可在投影片中引用實作互動示例或資料視覺化。
- pages/：額外的 Markdown 頁面，例如講者備忘或附錄。
- snippets/：可透過 @snippet 語法插入的重複使用程式碼片段。
- 
etlify.toml、vercel.json：快速部署到 Netlify/Vercel 的預先設定檔。

靜態資源（圖片、影片、字型…）可放在任意資料夾後以相對路徑引用。

## 投影片編寫技巧

- 善用 [front matter](https://sli.dev/guide/front-matter.html) 設定版型、轉場或註記。
- 需要互動內容時，可在投影片頂部加入 <script setup> 區塊並匯入 Vue 組件。
- 在 slides.md 的 	heme 欄位切換預設主題或改用 @slidev/theme-seriph。
- 在開發網址後加上 ?presenter 可啟用講者模式，提供備忘與計時。

## 匯出與部署流程

1. 執行 pnpm build 產生 dist/ 靜態資產。
2. 選擇部署方式：
   - Netlify：偵測 
etlify.toml 後自動執行 pnpm build。
   - Vercel：依 vercel.json 設定部署並提供預覽網址。
   - 其他平台：直接上傳 dist/ 中內容至任意靜態主機或 CDN。
3. 若需 PDF/PNG，執行 pnpm export --format pdf|png 以取得對應檔案。

## 疑難排解

- 若啟動時無法自動開啟瀏覽器，可手動造訪 <http://localhost:3030>。
- 匯出 PDF 失敗通常與 Playwright 依賴未安裝有關，可執行 pnpm exec playwright install chromium 重新安裝。
- 如需客製 Slidev 行為，可編輯 package.json 內 scripts 或直接使用 CLI 旗標。

---

更多進階資訊請參考 Slidev 官方指南：<https://sli.dev/>。
