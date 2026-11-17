# AGENTS.md — 擬態者 《MIMESIS》 LLM Wiki 系統規範與代理人指引

本文件為 《MIMESIS》（擬態者） AI 合作恐怖遊戲 LLM Wiki 的核心架構規範（Schema）與 LLM Agent 自律指引。本系統遵循 Andrej Karpathy 的 LLM Wiki 設計哲學，將知識庫分為不可變的原始資料層、結構化的提煉知識層以及操作指令層，協助自主代理人進行資料吸收、查詢檢索與定期維護。

---

## 1. 系統三層式架構

LLM Wiki 的儲存與運算機制嚴格分為三層，維護資料從「非結構化原始輸入」到「高品質結構化知識」的單向提煉流程：

* **原始資料層 (`raw/`)**：唯讀（Immutable）資料庫。存放未經加工的遊戲腳本、解包數據（Datamined JSON）、玩家觀察日誌、社群攻略、遊戲版本更新公告（Patch Notes）及音訊轉譯文字。代理人不可直接修改此區檔案。
* **提煉知識層 (`wiki/`)**：可維護（Curated）知識庫。存放由 LLM 代理人自動生成並持續維護的 Markdown 實體頁面、機制剖析、怪物百科及策略指南。所有頁面均須遵守嚴格的前言元資料（Frontmatter）與交叉引用（Wikilinks）格式。
* **系統指令層 (`AGENTS.md`)**：元指令（Meta-prompt）與架構規範。即本檔案，定義代理人的行為準則、更新規範、檢索策略與 CI/CD 流程。

---

## 2. 檔案目錄結構與模組規範

知識庫的實體目錄結構如下所示：

```text
├── raw/
│   ├── game_files/      # 遊戲解包數值、怪物 AI 決策樹狀態機
│   ├── patch_notes/     # 版本更新日誌，如 v1.0.4_mimesis_behavior.md
│   └── transcripts/     # 玩家對話記錄、AI 語音複製採樣文本
├── wiki/
│   ├── index.md         # 全域知識導覽與動態實體索引
│   ├── log.md           # 代理人操作紀錄與知識庫變更歷史
│   ├── entities/        # 擬態怪物種類、玩家裝備、地圖關卡
│   ├── mechanics/       # AI 語音模仿機制、恐懼值系統、聲學傳播算法
│   └── strategies/      # 雙人合作逃生策略、抗擬態識別指南
└── AGENTS.md
```

---

## 3. 索引與日誌運作規則

### 索引檔規範 (`wiki/index.md`)
`index.md` 為全庫的主索引頁面，代理人每次執行 Ingest 或 Lint 操作後必須同步刷新此檔案：

* **實體目錄表**：按類別（Entities, Mechanics, Strategies）列出所有 Wiki 頁面及簡短摘要。
* **標籤網絡（Tag Cloud）**：整理系統中所有的 `#tag` 分類（如 `#ai-behavior`, `#voice-cloning`, `#entity-class-s`）。
* **未解決孤點（Orphan List）**：記錄尚無雙向連結的頁面或尚未補全的懸空引用（Dangling Links）。

### 日誌檔規範 (`wiki/log.md`)
`log.md` 以時間倒序記錄所有 LLM Agent 對知識庫進行的操作，格式如下：

* **時間戳記與版本**：ISO 8601 格式與當前遊戲版本。
* **操作類型**：`[INGEST]`、`[QUERY]`、`[LINT]` 或 `[REFRACTOR]`。
* **變更檔案列表**：新增、更新或刪除的 Markdown 檔案。
* **變更摘要**：說明提煉了哪些新知識，修正了哪些衝突。

---

## 4. 代理人三大核心操作規範

代理人在處理知識庫時，必須嚴格執行以下三種操作流程：

| 操作指令 | 輸入源 | 主要任務與輸出 | 觸發時機 |
| :--- | :--- | :--- | :--- |
| **Ingest** | `raw/` 檔案 | 提取實體、消除重複、建立雙向連結、生成或更新 `wiki/` 頁面 | `raw/` 有新檔案進駐時 |
| **Query** | 用戶提問 | 進行多跳檢索（Multi-hop Reasoning）、交叉驗證、輸出帶引用的解答 | 收到使用者查詢時 |
| **Lint** | `wiki/` 全庫 | 檢查懸空連結、清理矛盾資訊、驗證模組 Frontmatter 完整性 | 定期 CI/CD 或操作後 |

### 1. Ingest (知識吸收與提煉) 流程
1. 讀取 `raw/` 中的新文件，解析遊戲機制或怪物行為數據。
2. 檢查 `wiki/entities/` 是否已存在相同實體。若存在則執行 Update 並記錄差異；若無則根據模板創建新檔。
3. 提取實體間的關聯，強制使用 `[[Entity_Name]]` 格式建立 Wikilinks。
4. 將來源檔案路徑註記於頁面底部的 `## 參考來源` 區塊。
5. 更新 `wiki/index.md` 與 `wiki/log.md`。

### 2. Query (檢索與推理) 流程
1. 解析使用者查詢，提取關鍵字與實體名稱。
2. 利用全域搜尋（如 QMD / BM25 配合向量檢索）尋找 `wiki/` 中的相關頁面。
3. 追蹤 `[[Wikilinks]]` 進行最多 3 層的多跳推理（例如：擬態者A -> 語音複製機制 -> 聲學波形抵消道具）。
4. 組裝最終回答，嚴格附帶來源頁面引用標籤（如 `[source: wiki/entities/...]`）。

### 3. Lint (庫存品質維護) 流程
1. 掃描 `wiki/` 目錄下的所有 Markdown 檔案。
2. 驗證 YAML Frontmatter 是否符合 Schema 規範（包含 `id`, `title`, `tags`, `last_updated`）。
3. 檢測並修復懸空連結（Dangling Links）：若引用的目標實體不存在，於 `index.md` 的未解決孤點列表中登記。
4. 檢測內容矛盾：若兩份頁面關於同一個 AI 行為數值的描述不一致，標註 `#status/contradiction` 並於 `log.md` 發出告警。

---

## 5. 《MIMESIS》 遊戲專屬知識元資料 Schema

所有在 `wiki/` 建立的實體檔案，標題下方必須包含標準 YAML Frontmatter：

```yaml
---
id: entity_mimesis_stalker
title: "擬態潛行者 (Mimesis Stalker)"
category: "Entities/Monster"
game_version: "v1.0.4"
danger_level: "Class-S"
ai_traits:
  - "VoiceCloning"
  - "LidarEvasion"
  - "PanicFeeder"
tags:
  - ai-behavior
  - monster
  - voice-synthesis
last_updated: 2026-11-17
---
```

---

## 6. LLM Agent 提示詞準則 (System Prompt Guidance)

當 LLM 被賦予代理人角色維護此 Wiki 時，必須遵循以下系統性約束：

* **客觀實體導向**：保持嚴肅、技術化與百科全書式的文風。禁止使用帶有主觀情緒的修飾詞，精確描述遊戲機制與 AI 邏輯。
* **不幻覺原則 (Zero Hallucination)**：若 `raw/` 數據不足以支持某一遊戲機制的推論，必須明確標註 `[資料缺漏：需進一步測試]`，嚴禁憑空捏造 AI 參數。
* **雙向連結優先**：任何提及其他怪物、地圖或道具的地方，必須寫成 Markdown 雙向連結形式（例如：當玩家恐懼值突破 80 時，[[wiki/mechanics/fear_system|恐懼系統]]將觸發[[wiki/entities/mimesis_stalker|擬態潛行者]]的主動獵殺狀態）。
* **語義版本控管**：若遊戲更新改動了 AI 行為，應在原有頁面中保留歷史版本描述，並新增當前版本的修正說明，不可直接抹除歷史行為紀錄。

---

## 7. GitHub Repository 整合與 CI/CD 工作流程

為確保 LLM Wiki 在 GitHub 團隊協同開發中的穩定度，系統建立以下自動化流程：

### Git Commit 規範
代理人自動提交變更時，Commit Message 必須遵循 Commitizen 格式：

```text
feat(wiki): add mimesis_stalker entity page
fix(lint): resolve dangling link in fear_system.md
docs(ingest): process raw transcript from patch v1.0.4
```

### GitHub Actions 自動化腳本 (`.github/workflows/wiki-lint.yml`)
當有 Pull Request 提交至主分支時，觸發自動校驗：

* **Markdown Linting**：檢查語法與標題層級規範。
* **Schema Check**：自動解析 YAML Frontmatter 格式。
* **Link Checker**：執行 Python/Node 腳本掃描所有 `[[Wikilinks]]`，確保無斷鏈現象。
* **Auto-Index Update**：確認 PR 是否已包含最新更新的 `index.md` 與 `log.md`，若無則予以阻擋並提示代理人補全。