\# 《MIMESIS》 LLM Wiki 變更紀錄 (Log)



本文件完整記錄 \*\*《MIMESIS》\*\* 專案 LLM 知識庫（LLM Wiki）之版本演進、原始資料匯入（Ingestion）與架構規範調整歷史\[cite: 8]。



| 專案名稱 | 知識庫版本 | 狀態 | 維護類型 |

| :--- | :--- | :--- | :--- |

| 《MIMESIS》\[cite: 8] | v1.0.0-alpha\[cite: 8] | 正常維護中\[cite: 8] | 系統初始化與資料匯入\[cite: 8] |



\---



\## \[2026-11-17] init | 初始化 《MIMESIS》 LLM Wiki 目錄結構與 AGENTS.md 規範

\* \*\*架構建立\*\*：完成專案根目錄初始化，建置 `raw/` 原始資料庫與 `wiki/` 結構化知識庫雙層架構\[cite: 8]。

\* \*\*規範制定\*\*：新增 `AGENTS.md` 作業指引，確立 AI Agent 於處理文本擷取、檔案命名與跨文件引用時之標準程序\[cite: 8]。

\* \*\*索引環境配置\*\*：設置檢索加強生成（RAG）所需之基礎元資料欄位與標籤分類規則\[cite: 8]。



\## \[2026-11-17] ingest | 11/5 Hotfix Patch Notes (新增 raw/2026-11-05\_Hotfix\_Patch\_Notes.md，建立 wiki/Game\_Mechanics\_Owls\_and\_Turrets.md 涵蓋貓頭鷹與噪音偵測砲塔機制)

\* \*\*原始檔案歸檔\*\*：匯入 `raw/2026-11-05\_Hotfix\_Patch\_Notes.md`，保存 11 月 5 日修補程式之完整變更說明\[cite: 8]。

\* \*\*知識庫文件建置\*\*：新增 `wiki/Game\_Mechanics\_Owls\_and\_Turrets.md` 專題頁面\[cite: 8]。

\* \*\*核心機制彙整\*\*：

&#x20; \* \*\*貓頭鷹機制 (Owls)\*\*：紀錄聲音觸發半徑、警戒轉化閾值與夜間視角偵測範圍調整\[cite: 8]。

&#x20; \* \*\*噪音偵測砲塔 (Noise-Detecting Turrets)\*\*：包含聲音分貝門檻、目標鎖定延遲參數及多重聲源優先級判定邏輯\[cite: 8]。

