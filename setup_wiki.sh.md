# GitHub 儲存庫 Wiki 初始化自動化腳本

本指南提供可執行的 Bash 腳本 `setup_wiki.sh`，用於快速建置 GitHub 儲存庫所需的 Wiki 資料夾結構與核心 Markdown 模板文件。

## 預期建立的專案目錄結構

執行腳本後，專案根目錄將會自動生成以下檔案與資料夾配置：

```text
.
├── AGENTS.md
├── index.md
├── log.md
├── raw/
└── wiki/
    └── Mimesis_Game_Overview.md
```

## 可執行腳本內容 (`setup_wiki.sh`)

請將以下程式碼儲存為 `setup_wiki.sh`：

```bash
#!/usr/bin/env bash
#
# setup_wiki.sh
# 
# 說明：
#   此腳本用於自動初始化 GitHub 儲存庫的檔案目錄結構，
#   並建立標準的 Markdown 模板文件（AGENTS.md, index.md, log.md 等）。
#
# 使用方式：
#   1. 給予執行權限：
#      chmod +x setup_wiki.sh
#
#   2. 在專案根目錄執行：
#      ./setup_wiki.sh
#
#   3. 指定特定目標目錄執行（可選）：
#      ./setup_wiki.sh /path/to/target/repo
#

set -euo pipefail

# 取得目標目錄（預設為當前目錄 '.'）
TARGET_DIR="${1:-.}"

echo "🚀 開始初始化 Wiki 目錄與模板文件至：'${TARGET_DIR}'..."

# 1. 建立必要資料夾
echo "📁 建立資料夾結構 (raw/, wiki/)..."
mkdir -p "${TARGET_DIR}/raw"
mkdir -p "${TARGET_DIR}/wiki"

# 2. 初始化 AGENTS.md
echo "📄 建立 AGENTS.md..."
cat << 'EOF' > "${TARGET_DIR}/AGENTS.md"
# Agent 指導原則與規範 (AGENTS.md)

## 專案概述
本文件旨在規範 AI Agent 與自動化工具在執行本儲存庫任務時的操作準則與上下文參考。

## 代理人規則 (Rules of Engagement)
1. **變更記錄**：重大架構變更或自動化生成必須同步更新至 `log.md`。
2. **檔案定位**：原始資料請放置於 `/raw`，整理後的文檔歸檔於 `/wiki`。
3. **索引一致性**：新增文檔時請確認同步更新 `index.md` 索引頁面。
EOF

# 3. 初始化 index.md
echo "📄 建立 index.md..."
cat << 'EOF' > "${TARGET_DIR}/index.md"
# 儲存庫知識庫索引 (Index)

歡迎來到本專案的知識庫入口。

## 導覽與快速連結
* [Agent 指導原則](AGENTS.md)
* [專案開發日誌](log.md)
* [Mimesis 遊戲概括](wiki/Mimesis_Game_Overview.md)

## 資料夾說明
* `/raw`：存放未加工的原始資料、會議記錄或外部輸入文件。
* `/wiki`：存放結構化與系統化的專案文檔。
EOF

# 4. 初始化 log.md
echo "📄 建立 log.md..."
cat << 'EOF' > "${TARGET_DIR}/log.md"
# 專案工作日誌 (Project Log)

| 日期 | 操作者 / Agent | 變更摘要 |
| :--- | :--- | :--- |
| $(date +'%Y-%m-%d') | System | 初始化儲存庫 Wiki 目錄結構與範本 |
EOF

# 5. 初始化 wiki/Mimesis_Game_Overview.md
echo "📄 建立 wiki/Mimesis_Game_Overview.md..."
cat << 'EOF' > "${TARGET_DIR}/wiki/Mimesis_Game_Overview.md"
# Mimesis Game Overview

## 專案簡介
本文件為 Mimesis Game 的核心概述頁面，包含系統架構與基本設計概念。

## 系統架構
* 待補充細節...

## 相關參考資料
* 原始規格與參考資源放置於 `raw/` 資料夾。
EOF

echo "✅ 專案目錄結構與模板文件初始化完成！"
```

## 執行與使用說明

使用以下步驟啟用並執行腳本：

1. **賦予執行權限**：在終端機中輸入以下命令以將腳本標示為可執行。
   ```bash
   chmod +x setup_wiki.sh
   ```

2. **執行初始化**：切換至您的 Git 專案目錄，並直接執行該腳本。
   ```bash
   ./setup_wiki.sh
   ```

3. **驗證結果**：執行完畢後，可以使用 `ls -R` 或 `tree` 命令確認目錄與文件已正確生成。