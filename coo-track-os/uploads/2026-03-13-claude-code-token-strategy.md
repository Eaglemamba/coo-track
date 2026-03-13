# Claude Code 產品生態與使用策略討論摘要

**日期：** 2026-03-13
**來源：** 基於 Tw93 文章《你不知道的 Claude Code》的延伸討論
**情境：** David 目前使用 Max 5X 方案，主要透過 claude.ai Projects 生成教學文件 + Claude Code CLI（家中 MacBook Air）

-----

## 1. Anthropic 產品線釐清

討論釐清了四個容易混淆的產品：

|產品                 |本質                        |介面                        |檔案存取              |Agent 治理能力                                  |
|-------------------|--------------------------|--------------------------|------------------|--------------------------------------------|
|**claude.ai**      |對話式 AI + Code Execution 沙盒|Web / 手機 App / 桌面 App（同一個）|沙盒每次重置，無持久存取      |無（沒有 /compact、Hooks、Subagents）              |
|**Claude Code CLI**|終端機 agentic coding 工具     |Terminal                  |完整本地檔案系統 + git    |完整（Tw93 文章的所有功能）                            |
|**Cowork**         |Claude Code 的非技術版         |Claude 桌面 App 內建          |指定資料夾的本地檔案        |部分（有 folder-specific instructions，但粒度不如 CLI）|
|**Remote Control** |CLI session 的遠端操控橋接       |手機 App / 瀏覽器連到本地 session  |透過本地 MacBook 的完整環境|完整（等同 CLI，因為執行在本地）                          |

**關鍵區別：** claude.ai 側邊欄的 `</> Code` 是 Code Execution（沙盒），不是 Claude Code CLI。兩者呼叫同樣的模型，但周邊工程機制完全不同。

-----

## 2. Tw93 六層架構模型重點

Tw93 基於半年深度使用提出的 Claude Code 六層架構：

1. **Context Layer** — CLAUDE.md / Skills / Memory / Rules
1. **Control Layer** — Hooks / Permissions / Sandbox
1. **Tool Layer** — MCP Servers / Built-in / Custom Tools
1. **Execution Layer** — Subagents / Plan Mode
1. **Verification Layer** — Tests / Lint / Screenshots
1. **Governance Layer** — Health Check / Anti-patterns / Iteration

**核心論點：** 卡住的原因幾乎不是模型不夠聰明，而是上下文被污染、控制層缺失、或驗證閉環斷裂。

**所有 CLI 治理命令（/btw、/compact、/clear、/context、/rewind、/insight、Hooks JSON、.claude/rules/）都是 Claude Code CLI 獨有功能，claude.ai 和 Code Execution 皆不可用。**

-----

## 3. Remote Control 功能分析

2026 年 2 月推出的功能，解決「人不在電腦前但想用 CLI 完整能力」的需求。

### 運作方式

- MacBook 上執行 `claude remote-control`，產生 session URL + QR code
- 手機 Claude App 或任何瀏覽器連入，操控本地 session
- 執行始終在本地 MacBook 上，只有聊天訊息和工具結果透過加密通道傳輸
- 對話在所有連接裝置間同步，可從終端機、瀏覽器、手機交替發送訊息

### 限制

- MacBook 必須保持喚醒（用 `caffeinate` 指令防止深度休眠）
- 每台機器同時只能跑一個 Remote Control session
- 目前不支援自動跳過權限確認 — 每個新操作需要手動批准
- 需要穩定網路（但頻寬需求低，正常家用網路足夠）
- 如果筆電休眠或斷網，session 會自動重連

### 可用性

- Pro 和 Max 方案皆可使用（Max 優先）
- 可以從遠端下達新指令、審查結果、給下一個任務

-----

## 4. David 的使用情境與策略

### 現狀

- Max 5X 方案，每週額度只用到約 60%
- 主要在 claude.ai Projects 生成雙語教學文件（高 token 消耗）
- Claude Code CLI 僅在家中 MacBook Air 前使用
- 行動中透過手機用 claude.ai Code Execution + GitHub clone（利用 GitHub 作為持久層繞過沙盒重置限制）

### Token 消耗觀察

- **教學文件**（雙語、長篇）：單份約 80,000-100,000 tokens，5 份長文件可吃掉整個 5 小時週期 100% 額度
- **HTML 應用程式開發**（如 MindMap 優化）：token 消耗低，半小時內可完成，一個週期可做多個
- 原因：教學文件同時踩中所有高消耗因素（長原文 + 複雜 Master Prompt + 大量雙語輸出 + 多次檔案寫入來回）

### 建議的三軌工作流

|場景               |工具                               |適合任務                                            |
|-----------------|---------------------------------|------------------------------------------------|
|MacBook 開著（不管人在哪）|Remote Control 手機操控              |低 token 任務：GitHub 維護、Dashboard 更新、Skills 開發、小修小補|
|MacBook 關著 / 不在身邊|claude.ai Code Execution + GitHub|中度開發、文件工作、工作相關任務                                |
|專屬時段（晚上/週末）      |claude.ai Projects               |高 token 教學文件生成（每週期 2-3 份為宜）                     |

### 同步雙軌使用

- 公司電腦用 claude.ai 做工作相關任務
- 同時家中 MacBook 透過 Remote Control 跑個人專案
- 兩邊消耗同一個 Max 5X 額度，但低 token 的 CLI 任務不會和工作搶資源
- 可將閒置的 40% 額度利用起來

### Token 優化建議

- Opus 消耗約為 Sonnet 的 3 倍，80% 任務用 Sonnet 即可
- 寫好的 CLAUDE.md 可減少 20-30% 的 token 消耗
- 教學文件視為「高消耗特殊任務」，排在專屬時段
- 用 `/cost` 監控 session 消耗，用 `/compact` 主動管理上下文

-----

## 5. 待進一步探索的問題

- Cowork 在非程式碼工作流（batch record review、deviation triage）的實際體驗
- Remote Control 的權限批准機制是否有更自動化的方式
- Hooks 在非 CLI 場景的等價物（Make.com Router? claude.ai System Prompt?）
- Claude Code Skills 從 claude.ai Projects 遷移到 CLI 的具體路徑
- Prompt Caching 對教學文件生成 token 消耗的潛在優化空間

-----

*此摘要供跨專案討論使用，可作為 Claude Code 使用策略的基線文件。*
