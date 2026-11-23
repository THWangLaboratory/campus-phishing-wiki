# 這個連結可以點嗎？

給大學生的釣魚訊息辨識教學，採用校園生活情境闖關，透過「帳號停用、包裹補費、意外獎學金」三個自製案例，練習獨立查證。

## 成果入口

- [HTML 教學簡報](index.html)：11 頁、三道決策題、即時解析與首次作答評分。
- [LLM Wiki](wiki.html)：6 篇官方來源、5 個 Wiki 頁面、15 個來源可追溯重點。
- [流程、檢查紀錄與反思](workflow.html)。
- [繳交說明](繳交說明.txt)。

GitHub 儲存庫中的 HTML 連結用來檢視原始檔；實際互動請使用部署完成後的 GitHub Pages，或下載整份專案並用瀏覽器開啟 `index.html`。

## LLM Wiki 建立方式

先討論教學主題、對象與呈現方式，再開始生成。使用者選擇釣魚訊息辨識與校園情境闖關；Codex 協助讀取官方資料，將摘要、標籤、適用範圍與來源對應匯入 `dist/knowledge.json`，整理成可互相連結的 Wiki。

這是 LLM 協作編輯的靜態 Wiki，不含瀏覽時的模型 API 或向量資料庫。來源筆記保存摘要與官方 URL，未鏡像全文。若課程指定特定 Wiki 平台，需再匯入該平台。

## Workflow 與實際紀錄

討論需求 → 取得來源 → 檢查來源及適用範圍 → 摘要入 Wiki → 查詢 Wiki → 必要重點覆蓋檢查 → 生成教學 HTML → 功能與呈現驗證。

檢查缺少依據時，回到查詢調整；Wiki 本身沒有答案時才補資料。這次 HTTPS／獎學金問題連續兩輪未取回完整重點，調整查詢詞與取回筆數後，第三輪通過。詳見 [三輪原始檢查紀錄](grounding-history.json) 與 [最終查詢結果](retrieval.json)。

## 重現與驗證

安裝 Node.js 後，在專案根目錄執行：

```sh
node scripts/retrieve.mjs
node scripts/check-grounding.mjs
node scripts/build.mjs
node scripts/validate.mjs
```

檢查涵蓋來源對應、內部連結、JavaScript 語法、11 頁導覽及三題全部 27 種作答組合。重跑會更新檢索時間，並附加新的覆蓋檢查紀錄。

Chrome 已實際載入首頁並目視檢查。逐關瀏覽器操作與手機實機驗證尚未完成，請參考 [瀏覽器檢查紀錄](browser-check.json)，不要將程式模型測試視為完整視覺測試。

## GitHub Pages

線上版以 main 分支根目錄發佈。完整的資料夾版本、Node 腳本與部署設定收錄在 full-project.zip。

## AI 協作

使用者選定主題與闖關形式；Codex 協助查找來源、編輯 Wiki、製作 HTML 與檢查腳本。所有學校、訊息、金額與示例網址皆為虛構教學設計。


