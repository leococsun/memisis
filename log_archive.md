\# MIMESIS AI Co-op Horror Game — LLM Wiki 變更日誌 (log.md)



本檔案為 MIMESIS 專案 LLM Wiki 知識庫的唯一追加型（Append-only）時間軸紀錄檔\[cite: 9]。所有針對世界觀設定、AI 智能體行為規範、Prompt 樣板及系統數據 Schema 的變更均需依照時間順序追加記錄，嚴禁刪改歷史紀錄\[cite: 9]。



\## 專案基本資訊



| 項目 | 說明內容 |

| :--- | :--- |

| 專案名稱\[cite: 9] | MIMESIS (AI 協同生存恐怖遊戲)\[cite: 9] |

| 知識庫類型\[cite: 9] | LLM-driven Game System \& Worldbuilding Wiki\[cite: 9] |

| 維護規範\[cite: 9] | ISO-8601 時間戳記 / 語意化版本控制 / 追加寫入 (Append-only)\[cite: 9] |

| 主要維護者\[cite: 9] | 李冠呈 (System Architecture Lead)\[cite: 9] |

| 當前版本\[cite: 9] | v0.1.0-alpha\[cite: 9] |



\---



\## 時間軸變更紀錄



\### 2026-11-17 10:00:00 CST — 專案與 LLM Wiki 初始化

\* \*\*事件類別\*\*：初始化 (Initialization)\[cite: 9]

\* \*\*執行人員\*\*：李冠呈\[cite: 9]

\* \*\*摘要說明\*\*：建立 MIMESIS 專案 LLM Wiki 基礎架構，確立 AI 驅動多人協同恐怖遊戲的核心開發目標\[cite: 9]。

\* \*\*詳細記錄\*\*：

&#x20; \* 初始化 GitHub / Google Drive 知識庫資料夾結構，命名為 MIMESIS AI Co-op Horror Game LLM Wiki\[cite: 9]。

&#x20; \* 確定使用 Markdown 與 Frontmatter Metadata 作為 LLM 檢索 (RAG / Local Search Engine) 之標準格式\[cite: 9]。

&#x20; \* 建立語音擬態 AI (Voice Mimicry Agent) 與環境威脅動態生成 (Dynamic Environmental Threat) 的技術願景文件\[cite: 9]。



\### 2026-11-17 11:30:00 CST — 初始 Schema 與數據結構建立

\* \*\*事件類別\*\*：Schema 建立 (Initial Schema Creation)\[cite: 9]

\* \*\*執行人員\*\*：李冠呈\[cite: 9]

\* \*\*摘要說明\*\*：完成核心 AI 智能體狀態、世界事件與玩家輸入解析的 YAML/JSON Schema 規範草案\[cite: 9]。

\* \*\*詳細記錄\*\*：

&#x20; \* 定義 `AgentMindstateSchema`：包含擬態程度 (Mimicry Ratio)、幻覺恐懼值 (Sanity Cost) 及當前目標策略\[cite: 9]。

&#x20; \* 定義 `WorldEventSchema`：規範恐怖情境觸發條件、聲響傳播半徑與視覺干擾強度\[cite: 9]。

&#x20; \* 定義 `PlayerAudioAnalysisSchema`：訂定玩家語音情緒（緊張、平靜、驚恐）與關鍵字萃取格式\[cite: 9]。



\### 2026-11-17 13:00:00 CST — 初始目錄架構設定

\* \*\*事件類別\*\*：架構設定 (Starting Structure Setup)\[cite: 9]

\* \*\*執行人員\*\*：李冠呈\[cite: 9]

\* \*\*摘要說明\*\*：建置標準目錄階層，劃分 Lore、Agents、Prompts、Schemas 與 Logs 模組\[cite: 9]。

\* \*\*詳細記錄\*\*：

&#x20; \* 部署根目錄結構與導航檔案 (`index.md`, `log.md`, `README.md`)\[cite: 9]。

&#x20; \* 設定 QMD / Vector DB 索引範疇標籤，優化檢索效率\[cite: 9]。

&#x20; \* 啟用 `log.md` 為 Append-only 追蹤模式，確保後續 AI agent 模型調整有完整歷史追溯依據\[cite: 9]。



\---



\## 初始目錄架構樹 (Starting Directory Structure)



```text

MIMESIS-LLM-Wiki/

├── index.md                   # 知識庫總覽與檢索導航\[cite: 9]

├── log.md                     # 本變更紀錄檔 (Append-only Log)\[cite: 9]

├── README.md                  # 專案說明與開發者指引\[cite: 9]

├── schemas/                   # 系統數據結構定義\[cite: 9]

│   ├── agent-mindstate.json   # 怪物/NPC 智能體心理狀態 Schema\[cite: 9]

│   ├── world-event.json       # 世界事件與動態威脅 Schema\[cite: 9]

│   └── player-input.json      # 玩家語音與行為特徵 Schema\[cite: 9]

├── agents/                    # AI 智能體行為規範與記憶系統\[cite: 9]

│   ├── mimesis-entity.md      # 核心擬態實體 (Mimesis Entity) 行為樹與性格設定\[cite: 9]

│   └── dynamic-narrator.md    # 動態氛圍主持人 (AI Director) 邏輯\[cite: 9]

├── lore/                      # 遊戲世界觀與恐怖設定庫\[cite: 9]

│   ├── facility-overview.md   # 故事背景：實驗設施失控事件\[cite: 9]

│   └── entity-manifesto.md    # 擬態生物生理特徵與擬態規則\[cite: 9]

├── prompts/                   # LLM Prompt 樣板庫\[cite: 9]

│   ├── system-prompts.md      # 角色扮演與恐怖氛圍系統 Prompt\[cite: 9]

│   └── audio-synthesis.md     # 語音擬態生成與台詞引導 Prompt\[cite: 9]

└── system/                    # 技術系統與整合介面\[cite: 9]

&#x20;   ├── rag-pipeline.md        # LLM 檢索與記憶檢索架構\[cite: 9]

&#x20;   └── unreal-bridge.md       # Unreal Engine 5 與 LLM API 介面規範\[cite: 9]

```



\## 核心 Schema 規格概要



\### 1. Agent Mindstate Schema

```json

{

&#x20; "$schema": "\[http://json-schema.org/draft-07/schema#](http://json-schema.org/draft-07/schema#)",

&#x20; "title": "AgentMindstate",

&#x20; "type": "object",

&#x20; "properties": {

&#x20;   "agent\_id": { "type": "string" },

&#x20;   "current\_target\_player\_id": { "type": "string" },

&#x20;   "mimicry\_level": { "type": "number", "minimum": 0, "maximum": 1 },

&#x20;   "aggression": { "type": "number", "minimum": 0, "maximum": 1 },

&#x20;   "perceived\_fear\_level": { "type": "string", "enum": \["Low", "Moderate", "High", "Extreme"] },

&#x20;   "active\_strategy": { "type": "string", "enum": \["Stalk", "VoiceMimic", "Ambush", "Retreat"] }

&#x20; },

&#x20; "required": \["agent\_id", "mimicry\_level", "aggression", "active\_strategy"]

}

```



\### 2. World Event Schema

```json

{

&#x20; "$schema": "\[http://json-schema.org/draft-07/schema#](http://json-schema.org/draft-07/schema#)",

&#x20; "title": "WorldEvent",

&#x20; "type": "object",

&#x20; "properties": {

&#x20;   "event\_id": { "type": "string" },

&#x20;   "timestamp": { "type": "string", "format": "date-time" },

&#x20;   "location\_zone": { "type": "string" },

&#x20;   "threat\_level": { "type": "integer", "minimum": 1, "maximum": 5 },

&#x20;   "environmental\_changes": {

&#x20;     "type": "object",

&#x20;     "properties": {

&#x20;       "flickering\_lights": { "type": "boolean" },

&#x20;       "audio\_hallucination": { "type": "boolean" },

&#x20;       "temperature\_drop": { "type": "boolean" }

&#x20;     }

&#x20;   }

&#x20; },

&#x20; "required": \["event\_id", "timestamp", "location\_zone", "threat\_level"]

}

```



\## 後續待辦事項 (Pending Action Items)

\* 撰寫 `agents/mimesis-entity.md` 之多階段擬態邏輯 (Phased Mimicry Lifecycle)\[cite: 9]。

\* 完成 `prompts/system-prompts.md` 的零樣本 (Zero-shot) 恐怖氛圍提示詞測試\[cite: 9]。

\* 整合 Unreal Engine 5 HTTP 通訊模組與 LLM API 代理伺服器\[cite: 9]。

